# Beta Feedback Guide

We are testing whether PulseEngine is a useful engineering product, not whether every run produces an optimization.

## Please report

### Repository shape

High-level only:

- approximate app size;
- React/Vite version range if known;
- number/type of meaningful user journeys;
- whether the repository is production, internal, side project, or demo.

### Installation

- Did install work without help?
- Was configuration obvious?
- Which command or concept caused friction?

### Candidate quality

- Did the candidate actually belong to a later user journey?
- Was there a more obvious candidate PulseEngine missed?
- Did the explanation make sense?

### Experiment quality

- Was the before/after comparison credible?
- Did the runtime/regression gates reflect what you care about?
- Did the isolated-worktree approach increase trust?

### Decision quality

- Did you agree with KEEP / REJECT / NO CANDIDATE / UNSUPPORTED?
- Would you have made the same decision without PulseEngine?
- Did PulseEngine save meaningful engineering time?

### Adoption

- Would you keep it installed?
- Would you run it manually, on PRs, or periodically?
- What would prevent your team from adopting it?
- What outcome would make it worth paying for?

## Do not post publicly

Do not put any of the following into a public GitHub issue:

- proprietary source code;
- secrets or credentials;
- customer information;
- confidential architecture details;
- private repository URLs;
- internal hostnames.

A scrubbed `review-summary.json` is welcome if your organization permits it.
