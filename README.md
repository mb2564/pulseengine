# PulseEngine

**Journey-aware performance engineering for React + Vite.**

PulseEngine looks for code that users are paying to download **before the user journey actually needs it**. It can test a proposed loading-boundary change in an isolated Git worktree, measure the before/after result, run configured safety checks, and return a reviewable patch with an evidence-backed verdict.

> Public beta. The PulseEngine engine is proprietary and is distributed as a compiled evaluation package. This repository intentionally does **not** contain the engine source code.

## Start here

- [Why PulseEngine?](docs/WHY_PULSEENGINE.md)
- [Your first test](docs/FIRST_TEST.md)
- [How it works](docs/HOW_IT_WORKS.md)
- [Interpreting results](docs/INTERPRETING_RESULTS.md)
- [Known beta limitations](docs/KNOWN_LIMITATIONS.md)
- [Feedback guide](docs/FEEDBACK_GUIDE.md)
- [Example feedback](docs/EXAMPLE_FEEDBACK.md)
- [Verify your download](docs/VERIFY_DOWNLOAD.md)
- [FAQ](docs/FAQ.md)

## What PulseEngine does

```text
scan
  ↓
find a later-journey candidate
  ↓
isolated experiment
  ↓
build + regressions + optional browser journey
  ↓
measure before/after
  ↓
KEEP / REJECT / NO CANDIDATE / UNSUPPORTED
  ↓
review.md + candidate.patch
```

PulseEngine does not silently apply a patch to your working checkout and does not automatically merge a KEEP result.

## Current beta scope

Best fit:

- React + Vite
- Git repository
- later-journey UI already separated into module boundaries
- normal build/regression commands available

Same-file component extraction is currently diagnostic-only.

## Install the beta

Requirements: Node.js 22+ and Git.

Download the latest compiled beta asset:

```bash
curl -L \
  https://github.com/mb2564/pulseengine/releases/latest/download/pulseengine-beta.tgz \
  -o pulseengine-beta.tgz
```

Then, from your React/Vite repository:

```bash
npm install --save-dev ./pulseengine-beta.tgz
```

On Windows you can download `pulseengine-beta.tgz` from the latest GitHub Release in your browser and run the same `npm install` command.

## 1. Initialize

```bash
npx pulseengine init --project .
```

Review the generated `pulseengine.config.json` and add your real build and regression commands.

## 2. Run a read-only scan

```bash
npx pulseengine scan --config pulseengine.config.json
```

The scan writes evidence under `.pulseengine/` and does not modify your application source.

## 3. Run an isolated experiment

If the candidate makes sense for your product journey:

```bash
npx pulseengine experiment --config pulseengine.config.json
```

PulseEngine creates a detached Git worktree, applies the candidate there, runs configured checks, re-measures the candidate, optionally runs configured browser journeys, emits an exact patch, removes the worktree by default, and verifies the original checkout was not changed.

Start with:

```text
.pulseengine/review.md
.pulseengine/review-summary.json
.pulseengine/candidate.patch
```

## Optional GitHub PR review

```bash
npx pulseengine github-init --project .
```

Review the generated workflow before committing it. PulseEngine can publish/update one marked review comment on pull requests.

## We want critical feedback

A useful beta result does **not** need to be KEEP. REJECT, NO CANDIDATE and UNSUPPORTED are useful outcomes if the evidence is understandable and correct.

Please open a **Beta feedback** issue and tell us:

- whether setup worked without help
- whether the candidate really belongs to a later journey
- the measured before/after result
- whether the safety/review evidence made sense
- whether PulseEngine missed an obvious opportunity
- whether you would keep it installed
- the biggest reason you would or would not pay for it

Please do **not** paste proprietary source code, secrets, customer data, or internal URLs into a public issue.

## Source and licensing

This GitHub repository is public for distribution, documentation, examples and feedback. **Public does not mean open source.**

The PulseEngine analysis/experiment engine is not included here. The downloadable beta package is a bundled/minified/top-level-mangled evaluation build with no source maps and is covered by the evaluation terms in [LICENSE.md](LICENSE.md).

See [DISTRIBUTION.md](DISTRIBUTION.md) for the public/private boundary.

## Public beta status

This is an **evidence-gathering beta**, not a finished commercial release. The core questions we are testing are:

1. Does PulseEngine find journey-boundary opportunities that developers consider real?
2. Does the isolated experiment produce evidence they trust?
3. Are REJECT / NO CANDIDATE / UNSUPPORTED outcomes useful rather than frustrating?
4. Does the workflow save enough engineering effort that teams would keep it installed?
5. Is that value strong enough to pay for?

See [ROADMAP.md](ROADMAP.md), [CHANGELOG.md](CHANGELOG.md), [SECURITY.md](SECURITY.md), [PRIVACY.md](PRIVACY.md), [SUPPORT.md](SUPPORT.md), and [CONTRIBUTING.md](CONTRIBUTING.md).
