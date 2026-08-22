---
title: "Where GPU issue cycles actually go"
date: 2026-08-12
tags: [warp scheduling, stalls]
excerpt_text: "Latency hiding is the whole design premise of a GPU. Here is what happens on the workloads where it stops working."
---

The standard explanation of a GPU goes like this: individual threads are slow,
memory is far away, but you keep so many warps resident that whenever one stalls
there is always another ready to issue. Latency is hidden by parallelism. Nobody
waits.

That explanation is correct for a dense GEMM. It is much less correct for a
breadth-first search, a sparse solver, or a stencil with an awkward access
pattern — and it is the gap between those two cases that most of my research
lives in.

## The failure mode

Latency hiding works when the warps waiting are *uncorrelated*. Warp 3 stalls on
a load, warp 7 is ready, the scheduler switches, the pipeline stays busy.

But warps in a thread block usually execute the same instruction stream over
similar data. When they hit the same load, they hit it at roughly the same time.
The scheduler looks for a ready warp and finds that all of them are waiting on
the same class of event. There is nothing to switch to. The issue stage goes
idle even though the functional units are free and the instructions are sitting
right there.

In the suites I measure — Rodinia, Parboil, PolyBench on an A100-class
configuration — around 40% of issue cycles are lost to dependency stalls of this
kind, and roughly three-quarters of those trace back to a load. That is not a
tail case. That is the dominant cost on a large fraction of real GPU code.

## Why more warps is not the answer

The obvious response is to raise occupancy: more warps per SM, more chances that
one is ready. This fails for two reasons.

The first is resource pressure. Occupancy is bounded by registers and shared
memory. Pushing more warps in means cutting the per-thread register budget,
which produces spills, which produce more memory traffic, which is the thing you
were trying to hide.

The second is that correlated stalls do not care how many warps you have. If
every resident warp is blocked on the same dependency pattern, doubling the
warp count doubles the number of blocked warps. Cache thrashing usually makes it
worse.

## What is left

If you cannot get more thread-level parallelism, the remaining slack is
instruction-level parallelism *within* a warp. When a warp stalls on a load,
there are often later instructions in its own stream that do not depend on that
load. In program order they wait. There is no architectural reason they have to.

This is exactly what a CPU's out-of-order engine does, and the obvious objection
applies immediately: a reorder buffer, load-store queue, and rename table
replicated across 64 warps per SM is not a design, it is a joke about area
budgets. GPUs got their throughput by *removing* that machinery.

So the real question is not "should GPUs go out-of-order." It is: **where can
the dependency information come from, if not from per-cycle per-warp hardware?**

A few answers are viable:

- **Reuse it across warps.** Warps executing the same instruction stream have
  the same dependency structure. Analyse it once, share the result.
- **Compute it before execution.** Dependencies in the final SASS binary are
  known statically. Do the analysis once per kernel and encode the outcome in
  bits the instruction encoding is not using.
- **Approximate it.** You do not need a full dependency graph to make a good
  issue decision. Ranking instructions by expected latency and the size of the
  dependent chain behind them recovers most of the benefit at a fraction of the
  cost.

Each of these moves the expensive work off the critical path. That is the design
constraint that actually matters — not whether the mechanism is clever, but
whether it fits in the cycle time and the area budget of a structure that gets
replicated a hundred and eight times.

## The part I find interesting

The compiler already knows most of this. It scheduled the code; it has the
dependence graph. So why not just let it handle everything?

Because the compiler has to be conservative. It cannot resolve pointer aliasing
in general, it does not know actual memory latencies, and it cannot see the
dynamic contention between warps at run time. It leaves real parallelism on the
table for provably safe reasons.

The interesting space is in the middle: static analysis doing the expensive
structural work, hardware making the cheap dynamic call. Most of what I build
lives there.

---

*More on the specific mechanisms in [FlIP](https://doi.org/10.1145/3801487.3801823),
and in the PRISM and HOOP papers as they appear.*
