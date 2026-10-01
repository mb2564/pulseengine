# PulseEngine Distribution Boundary

PulseEngine uses a split distribution model during beta.

## Public

The public `mb2564/pulseengine` repository is intended to contain only:

- product README and tester documentation
- evaluation/license terms
- safety/privacy guidance
- feedback issue templates
- release notes
- compiled beta release artifacts

## Private

The following remain in the private development repository and must not be copied into the public repository:

- `engine/`
- `lib/`
- implementation tests and fixtures
- candidate-discovery heuristics
- journey-ownership implementation
- source-attribution implementation
- side-effect/risk implementation
- patch-generation implementation
- experiment-evaluation implementation
- internal validation datasets and provenance material that exposes implementation detail

## Release artifact

The public beta artifact is built from the private repository.

The private build pipeline:

1. bundles the CLI and internal modules into one distribution file;
2. minifies the bundle;
3. emits no source maps;
4. excludes private source directories and tests;
5. adds build/version/expiry metadata;
6. packages the result as `pulseengine-beta.tgz`;
7. fails if known private source directories appear in the package.

This is an IP-friction measure, not cryptographic DRM. Any software executed on another person's computer can potentially be inspected. The durable commercial architecture may therefore move sensitive decision logic to a hosted service/GitHub App after beta validation.
