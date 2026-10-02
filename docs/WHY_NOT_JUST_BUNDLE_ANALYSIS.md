# Why PulseEngine Is Not Just a Bundle Analyzer

Bundle analysis and manual code splitting are important tools. PulseEngine is aimed at a different decision.

A bundle analyzer can answer questions such as:

- What shipped?
- Which modules are large?
- Which chunks contain a dependency?
- How did bundle size change?

Those are necessary facts. They do not by themselves answer:

> Does this code belong to the user's initial journey, or are users paying for it before they need it?

PulseEngine tries to connect bundle/source evidence to **journey timing**, then prove whether changing the loading boundary is actually worthwhile.

## Bundle size is not the decision

A large module can be legitimately required on first render.

A relatively small module can still be a good later-journey candidate when it pulls in additional dependencies or appears across many sessions where the feature is never used.

So PulseEngine does not rank candidates by size alone.

## React.lazy is an implementation mechanism

For some React applications, the eventual code change may use a familiar mechanism such as a dynamic import or lazy boundary.

The difficult part is not writing:

```js
const Feature = lazy(() => import('./Feature'))
```

The difficult questions are:

- Is `Feature` genuinely later in the user's journey?
- Will moving the boundary break rendering, side effects, or tests?
- Does the production build actually improve?
- Is the measured gain large enough to justify another async boundary?
- Can another engineer review the exact change and evidence?

PulseEngine is designed around those questions.

## Why an isolated experiment?

A candidate is not treated as proof.

For a supported candidate, PulseEngine creates a detached Git worktree, applies the candidate there, runs configured checks, re-measures the result, emits review artifacts, removes the temporary worktree by default, and verifies that the original checkout was not changed.

That allows outcomes such as:

- **KEEP** — evidence supports reviewing the change further;
- **REJECT** — the experiment worked technically but the result does not justify the change;
- **NO CANDIDATE** — PulseEngine did not find a supported opportunity worth proposing;
- **UNSUPPORTED** — PulseEngine saw a shape it currently refuses to transform safely.

A KEEP is not automatic permission to merge.

## Why REJECT matters

Performance work has an opportunity cost.

An optimization can be technically correct and still be a bad engineering trade if the measured gain is too small, the new boundary adds complexity, or a required journey/regression check fails.

PulseEngine is intentionally allowed to produce no patch worth keeping.

## Where bundle analysis still fits

PulseEngine does not replace bundle analyzers, browser profilers, RUM, Lighthouse, or application-specific performance work.

Those tools tell you important things about the system.

PulseEngine's narrower job is to help answer:

> **Should this later-journey code stop being part of the initial cost, and can we prove that safely?**

See [How it works](HOW_IT_WORKS.md), [Your first test](FIRST_TEST.md), and the [real beta.17 validation run](VALIDATION_CASE_STUDY.md).
