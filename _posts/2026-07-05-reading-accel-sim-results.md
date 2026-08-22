---
title: "Four things to check before you trust an Accel-Sim number"
date: 2026-07-05
tags: [methodology, accel-sim]
excerpt_text: "A simulator will happily give you a confident IPC for a configuration that could not exist. Notes from a few hundred runs."
---

Architecture research on GPUs is mostly simulation, and simulation is mostly
trust. You change one structure, rerun, and read a number off a log. The number
looks precise. It has four decimal places.

Here is what I have learned to check before believing it. None of this is
novel — it is the kind of thing you absorb slowly from broken runs — but I wish
someone had written it down for me at the start.

## 1. Did the kernel actually finish?

The single most common failure I see is a run that terminated early — hit an
instruction limit, ran out of a resource, or silently truncated a trace — and
still produced a plausible-looking IPC. Partial execution biases toward whatever
phase the kernel was in when it stopped, which is usually the warm, well-behaved
prologue.

Check the completed-instruction count against the baseline, not just the IPC.
If your modified configuration executed measurably fewer instructions than the
baseline on a deterministic kernel, something is wrong that IPC will not tell
you about.

## 2. Is the configuration internally coherent?

It is easy to change one parameter and leave a dependent one at its default. You
widen the issue stage but leave the register file ports alone. You add buffer
entries without adjusting the area or the access latency they imply. The
simulator does not object. It models exactly what you specified, including the
parts that could not be built.

Every structural change should come with an explicit answer to: what else does
this change, and did I change it?

## 3. Does the baseline match published silicon?

Accel-Sim's value over earlier simulators is that its A100 configuration has
been validated against real hardware. That validation belongs to the *baseline*
configuration. The moment you modify the front end, you are extrapolating, and
the correlation coefficient in the Accel-Sim paper is no longer yours to cite.

This is not a reason to avoid simulation. It is a reason to state the baseline
you validated against, report the delta rather than the absolute, and be honest
that the delta is a model result.

## 4. Are the wins concentrated in one benchmark?

A geometric mean of 1.12× can mean everything improved by 12%, or that eighteen
benchmarks did nothing and one went up 4×. These are entirely different claims
and only one of them supports a general mechanism.

Always plot per-benchmark. Always look at the worst case, not just the mean.
And report regressions where they exist — reviewers read an unbroken row of
wins across nineteen diverse benchmarks with more suspicion than a result with
one honest loss.

## The underlying point

A simulator is an argument, not a measurement. The number it produces is only
as good as the case you can make that the modelled machine is buildable and the
modelled workload is representative. Most of the work in a good evaluation is
in making that case, not in running the sweeps.
