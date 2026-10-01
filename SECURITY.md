# Security

PulseEngine is an early beta developer tool. Treat generated patches as untrusted engineering suggestions until reviewed.

## Safe beta use

- Run PulseEngine only on repositories you are authorized to test.
- Review `pulseengine.config.json` before running.
- Review any generated GitHub workflow before committing it.
- Keep secrets out of configuration and feedback.
- Review `.pulseengine/review.md` and `.pulseengine/candidate.patch` before using a proposed change.
- A KEEP verdict does not mean automatic merge approval.

## Source isolation

The normal scan is read-only.

The experiment path is designed to apply a proposal in a detached Git worktree rather than the developer's original checkout. The original proposal-source files are checked before/after and the experiment workspace is removed by default.

## Reporting

For beta security concerns, open a GitHub issue only if the report contains no secrets or exploitable private-repository information. Otherwise contact the maintainers privately.
