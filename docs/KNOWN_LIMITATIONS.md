# Known Beta Limitations

PulseEngine is intentionally narrow during public beta.

## Framework scope

Current focus:

- React
- Vite
- Git repositories

Other frameworks/build systems should be treated as unsupported unless a release explicitly says otherwise.

## Transformation scope

The current safe patch model is strongest when a later-journey UI boundary already exists across modules.

Some same-file opportunities can be recognized but are intentionally reported as unsupported rather than rewritten.

## Test quality depends on your project

PulseEngine can run configured regression commands and optional runtime journeys, but it cannot invent complete product coverage for a repository that has no meaningful tests.

A KEEP result is therefore evidence for review, not proof of universal correctness.

## Local execution means inspectability

The beta runs on the tester's machine/runner. The distributed engine is bundled, minified and top-level-mangled and does not include source maps, but locally executable software can still be investigated by a sufficiently motivated person.

This beta distribution is meant to prevent casual source copying while validating product demand. It is not a cryptographic secrecy boundary.

## Performance measurement is contextual

A measured improvement is specific to the repository, configuration and experiment conditions used. It should not be generalized to other applications without measurement.

## Beta stability

Commands, report shapes and configuration may change between beta releases. Builds may expire so testers move to current versions.
