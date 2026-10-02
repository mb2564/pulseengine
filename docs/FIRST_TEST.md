# Your First PulseEngine Test

This walkthrough is designed to produce a useful result in about one repository session.

## Pick the right repository

For the current beta, choose a React + Vite application that:

- has at least a few screens, panels, drawers, dialogs, or secondary journeys;
- builds reliably from the command line;
- is already in Git;
- has at least one normal regression/test command if possible;
- is code you are authorized to test.

Do not start with a tiny demo app. PulseEngine is looking for real initial-load work that appears to belong later in the user journey.

## Before you run it

Create or switch to a clean branch and make sure your working tree is in a state you understand.

Check:

```bash
git status
```

Install the current beta package and initialize:

```bash
npm install --save-dev ./pulseengine-beta.tgz
npx pulseengine init --project .
```

Open `pulseengine.config.json`.

PulseEngine auto-detects an install command during `init`. For npm projects it uses `npm ci --include=dev` when a lockfile exists, otherwise `npm install --include=dev`, so build tooling such as Vite and TypeScript is available inside the isolated experiment worktree.

Replace placeholder build/regression commands with the commands your project actually uses. If you override `installCommand`, make sure it installs development dependencies required by your build.

## Run the scan

```bash
npx pulseengine scan --config pulseengine.config.json
```

There are several useful outcomes:

- **candidate found** — inspect whether it really belongs to a later journey;
- **NO CANDIDATE** — useful evidence that PulseEngine did not invent work merely to produce a result;
- **UNSUPPORTED** — the tool sees a shape it currently refuses to transform safely;
- **ERROR** — report the setup/runtime failure so we can improve onboarding.

## If a candidate is found

Before running an experiment, ask one human question:

> If this module/component were not available during the initial journey, would the user reasonably notice?

If the answer is "yes, it is needed immediately," the candidate may be wrong. Please report that.

If the candidate belongs later, run:

```bash
npx pulseengine experiment --config pulseengine.config.json
```

## Read the result in this order

1. `.pulseengine/review.md`
2. `.pulseengine/review-summary.json`
3. `.pulseengine/candidate.patch`

Do not start by reading internal raw evidence files.

## What counts as a successful beta test?

A successful beta test is **not** the same as a KEEP.

A successful test is one where you can answer:

- Did PulseEngine identify the right journey boundary?
- Did it measure a real before/after difference?
- Did the safety checks catch anything important?
- Was the verdict understandable?
- Would you trust the proposed patch enough to review it?
- Would you keep this tool installed?

Please submit those answers using the repository's **Beta feedback** issue form.
