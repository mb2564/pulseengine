# Why PulseEngine?

Modern frontend tooling can tell you that a bundle is large.

A profiler can tell you what loaded.

An AI assistant can suggest lazy loading.

Those are useful, but they do not answer the complete engineering question PulseEngine is testing:

> **Which code belongs to a later user journey, can we move it there safely, and is the measured improvement large enough to justify the change?**

PulseEngine treats that as an evidence problem rather than a code-generation problem.

## The gap

A developer can often look at a repository and say:

> "This panel probably doesn't need to load immediately."

The expensive part is everything after *probably*:

- proving what the current initial journey pays for;
- locating the source responsible for that cost;
- deciding whether the code really belongs later;
- checking side-effect and fallback risks;
- applying a narrowly scoped candidate;
- rebuilding in a clean environment;
- proving the boundary actually moved;
- testing the user journey;
- measuring the real difference;
- deciding whether the gain is worth the change;
- packaging all of that evidence for review.

A generic AI assistant can help with pieces of this interactively. PulseEngine's thesis is that the repeatable product is the **closed evidence loop**.

## Why negative results matter

PulseEngine is deliberately designed to say:

- REJECT;
- NO CANDIDATE;
- UNSUPPORTED;
- REVIEW REQUIRED.

A performance tool that always finds something to "optimize" is easy to demo and difficult to trust.

During this beta, we care as much about correct rejection as successful optimization.
