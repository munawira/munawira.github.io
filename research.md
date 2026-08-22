---
layout: default
title: Research
permalink: /research/
description: GPU microarchitecture research on instruction issue, warp scheduling, and out-of-order execution.
---

<h1>Research</h1>

<p class="lede">GPUs hide latency by switching warps. When every resident warp is
waiting on the same thing, there is nothing left to switch to — and the issue
stage goes quiet.</p>

That is the problem I work on. Modern GPUs run plenty of code that does not look
like a dense matrix multiply: graph traversal, sparse linear algebra, irregular
scientific kernels, and increasingly the ragged parts of ML pipelines. These
workloads have limited data-level parallelism, so thread-level parallelism alone
cannot cover their memory latency. The instruction issue stage becomes the
bottleneck, and the fix has to come from instruction-level parallelism instead.

## Threads of work

<div class="entry">
  <p class="entry-head">Out-of-order issue that a GPU can actually afford</p>
  <p class="entry-sub">FlIP · HOOP</p>
  <p>A CPU-style out-of-order engine is not viable at GPU width — the ROB, LSQ,
  and rename tables do not scale across 64 warps per SM. I look at where the
  ordering information can come from instead: dependence flow reuse across warps
  executing the same instruction stream (FlIP), and once-per-kernel dependency
  analysis on the final SASS binary, encoded as hints in unused instruction bits
  (HOOP). Both replace per-cycle, per-SM scoreboard work with something computed
  once and shared.</p>
</div>

<div class="entry">
  <p class="entry-head">Scheduling by what the stall will cost</p>
  <p class="entry-sub">PRISM · PILOT</p>
  <p>Most warp schedulers rank warps by age or arrival. PRISM ranks instructions
  by a priority score combining expected latency with the size of the dependent
  chain behind them, and applies the same ranking at both the inter-warp and
  intra-warp level. The question I keep returning to: which stall is worth
  avoiding, and can the hardware tell cheaply enough to matter?</p>
</div>

<div class="entry">
  <p class="entry-head">Memory behaviour at the issue boundary</p>
  <p class="entry-sub">Prefetching · uncoalesced access</p>
  <p>Uncoalesced inter-thread accesses generate misses that no scheduler can
  schedule around. Some of my work targets these directly with prefetching
  informed by what the issue stage already knows about the access pattern.</p>
</div>

<div class="entry">
  <p class="entry-head">Where this is heading</p>
  <p class="entry-sub">Emerging directions</p>
  <p>Two directions I am growing into: SM-level co-execution and QoS-aware
  scheduling for LLM inference serving, where multiple tenants contend for one
  GPU; and microarchitecture for quantum error correction decoders, which have
  hard real-time latency budgets and almost no established architectural
  playbook.</p>
</div>

## Methods

I evaluate in [Accel-Sim](https://accel-sim.github.io/) against A100-class
configurations, using SASS-level analysis and NVBit tracing so the instruction
stream matches what real silicon executes. Energy comes from AccelWattch; area
and timing estimates from Synopsys Genus. Benchmarks are drawn from Rodinia,
Parboil, and PolyBench, with additional irregular workloads where the suites
fall short.

## Teaching

At Pillai University I designed and taught Advanced Computer Architecture — the
first course of its kind in the University of Mumbai's undergraduate curriculum
— alongside Operating Systems and a Unity-based game development course. I set
up the department's research lab and its AR/VR lab, and contribute to curriculum
design through the University of Mumbai Board of Studies.

If you are a student interested in computer architecture and want to talk about
where to start, write to me.
