# PulseEngine beta.17 — Real Validation Run

This is a real end-to-end validation of the public `0.3.0-beta.17` package against a multi-screen React + Vite application.

The application is private, so this case study deliberately omits proprietary source code, internal URLs, and product-specific implementation details.

## What we tested

We used the same public package and installation path available from the GitHub Release:

```bash
npm install --no-save --package-lock=false ./pulseengine-beta.tgz
npx pulseengine version
npx pulseengine init --project .
npx pulseengine scan --config pulseengine.config.json
npx pulseengine experiment --config pulseengine.config.json
```

The test intentionally exercised an onboarding edge case too: an untracked local npm lockfile was present, but it would not exist in the detached Git worktree.

## Observed result

- public beta download: **PASS**
- package version: **0.3.0-beta.17**
- initialization: **PASS**
- install-command detection: **PASS**
- detected experiment install command: `npm install --include=dev`
- read-only scan: **PASS**
- supported candidates surfaced: **5**
- dominated candidates excluded: **7**
- isolated experiment: **PASS**
- application production build: **PASS**
- configured regression tests: **PASS**
- technical verdict: **KEEP**
- experiment verdict: **KEEP**
- original source checkout unchanged: **true**
- temporary experiment worktree removed: **true**

## Why the install-command result mattered

The previous beta exposed a real failure mode: a locally created but untracked `package-lock.json` could cause PulseEngine to choose `npm ci`, even though that lockfile would not exist in the detached experiment worktree.

Beta.17 changed the rule: PulseEngine only treats a lockfile as suitable for a frozen/CI install when the lockfile is actually tracked in Git and will therefore be available inside the experiment worktree.

This validation reproduced the risky local state and confirmed that beta.17 selected the safe non-frozen install path.

## What this proves — and what it does not

This run demonstrates that the public package can complete the intended technical loop on a real React + Vite application:

```text
public package
  -> init
  -> read-only scan
  -> candidate discovery
  -> detached experiment
  -> build + regressions
  -> before/after evidence
  -> KEEP/REJECT decision
  -> reviewable patch
```

It does **not** prove that PulseEngine will find a valuable candidate in every repository, or that a KEEP verdict should be merged automatically.

A trustworthy REJECT, NO CANDIDATE, or UNSUPPORTED result is also useful beta evidence.

## We want independent results

The next important test is not another repository we control. It is whether independent React + Vite maintainers can run PulseEngine without help, understand the evidence, and agree that the verdict is useful.

If you maintain a suitable repository, start with [Your First PulseEngine Test](FIRST_TEST.md), then submit a [Beta feedback issue](https://github.com/mb2564/pulseengine/issues/new?template=beta-feedback.yml).
