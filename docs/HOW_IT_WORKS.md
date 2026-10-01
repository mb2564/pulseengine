# How PulseEngine Works

PulseEngine is built around a simple question:

> Is the application making users download and initialize code during an early journey even though that code belongs to a later journey?

The beta uses a five-stage workflow.

## 1. Observe the built application

PulseEngine measures the application's current loading shape and associates built output with application source at a high level.

## 2. Identify a journey-boundary candidate

It looks for code that appears to be owned by a later interaction rather than the initial journey.

PulseEngine is deliberately conservative. Some opportunities are reported as unsupported instead of being transformed automatically.

## 3. Create an isolated experiment

The candidate is tested outside your working checkout in a detached Git worktree.

The experiment can:

- apply the proposed boundary change;
- run the project's configured build;
- run configured regression commands;
- measure the candidate build;
- verify the intended loading boundary;
- run configured browser journeys.

## 4. Compare evidence

PulseEngine compares the baseline and candidate rather than assuming that a syntactically valid lazy boundary is a useful optimization.

A candidate can therefore be rejected even if it technically works.

## 5. Produce a review package

The primary output is designed for human review:

- `review.md`
- `review-summary.json`
- `candidate.patch`

Possible outcomes include:

- **KEEP** — the experiment cleared the configured gates and produced a worthwhile result;
- **REJECT** — one or more gates failed or the measured benefit did not justify the change;
- **NO CANDIDATE** — no supported candidate was found;
- **UNSUPPORTED** — PulseEngine recognized an opportunity shape but deliberately did not transform it;
- **REVIEW REQUIRED** — evidence exists but human judgment is still required.

## What PulseEngine is not

PulseEngine is not:

- a generic "make my website faster" chatbot;
- an automatic refactoring bot that silently edits main;
- a replacement for your test suite;
- a guarantee that every repository contains a worthwhile optimization;
- permission to merge a patch without engineering review.

The beta is specifically testing whether this evidence-driven workflow is useful enough that developers want it in real repositories.
