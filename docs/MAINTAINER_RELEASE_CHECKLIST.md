# Maintainer Release Checklist

This document is for publishing a PulseEngine public beta without accidentally exposing the private engine source.

## Before release

- Private PulseEngine test suite passes.
- Public-package build succeeds.
- Clean-install smoke test succeeds.
- Source-leak checks pass.
- Package contains no `engine/`, `lib/`, `scripts/` or test source.
- Package contains no source maps.
- `npx pulseengine version` reports the intended beta version.
- Expiration date is intentional.
- `SHA256SUMS.txt` is generated.

## Public repository contents

Publish only the contents staged under `pulseengine-public/` plus approved GitHub Release assets.

Never copy the private repository wholesale.

## GitHub Release

Release assets should include:

- `pulseengine-beta.tgz`
- the versioned PulseEngine tarball
- `SHA256SUMS.txt`

Use a prerelease tag while the product remains in beta.

Suggested release title:

`PulseEngine 0.3.0-beta.15 — Public Beta`

## After release

- Open the public README in a logged-out/private browser window.
- Test the release download link.
- Verify the checksum.
- Install the public tarball into a clean React + Vite test repository.
- Run `npx pulseengine version`.
- Run `npx pulseengine init --project .`.
- Confirm GitHub issue forms are visible.
- Confirm no private source, internal URLs, credentials or validation fixtures are public.
