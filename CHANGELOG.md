# Changelog

## 0.3.0-beta.17

Hardens isolated experiment setup after a live public beta.16 smoke test exposed an untracked-lockfile edge case.

### Fixed

- `pulseengine init` now treats a lockfile as suitable for a frozen/CI install only when that lockfile is tracked in Git and will therefore exist in the detached experiment worktree
- an untracked local `package-lock.json` no longer causes the candidate worktree to run `npm ci` against a missing lockfile
- the evaluation install path no longer needs to modify `package.json` or create a lockfile before the first experiment

### Recommended beta install

```bash
npm install --no-save --package-lock=false ./pulseengine-beta.tgz
```

## 0.3.0-beta.16

Public beta hardening after an external-style Dailune install/experiment smoke test.

### Fixed

- `pulseengine init` now detects npm lockfiles and generates an install command that explicitly includes development dependencies
- npm projects without a lockfile now use `npm install --include=dev` instead of the invalid `npm ci` default
- isolated experiments can build repositories where Vite/TypeScript are devDependencies
- public beta download guidance uses the versioned prerelease asset instead of GitHub's `releases/latest` path

### Validated

- public tarball download and checksum
- install + version + init + scan on Dailune
- detached-worktree build and regression suite
- end-to-end experiment verdict generation

## 0.3.0-beta.15

Initial external public beta packaging.

### Included

- React + Vite scanning
- journey-boundary candidate discovery
- isolated worktree experiments
- baseline/candidate measurement
- configurable regression commands
- optional browser journey verification
- evidence-backed KEEP / REJECT / NO CANDIDATE / UNSUPPORTED outcomes
- human-readable `review.md`
- machine-readable `review-summary.json`
- exact `candidate.patch`
- GitHub PR review workflow scaffolding

### Beta limitations

- current transformation support is intentionally narrow
- same-file opportunity shapes may be reported as unsupported
- public beta packaging is evaluation-only
