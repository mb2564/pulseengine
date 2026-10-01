# FAQ

## Is PulseEngine open source?

No. The public GitHub repository contains documentation, release assets and feedback tooling. The analysis/experiment engine is proprietary and distributed as a bundled/minified/top-level-mangled beta build.

## Can I use it on a private repository?

Yes, provided you are authorized to test that repository. You do not need to make your repository public to run PulseEngine.

## Do I need to send you my source code?

No. For normal beta feedback, high-level descriptions plus a scrubbed result summary are enough.

## Does PulseEngine upload my repository?

The current beta is designed to run against the repository on the machine/runner where you invoke it. Do not put secrets or proprietary code into a public feedback issue.

## Will it modify my working branch?

The normal scan is read-only. The experiment workflow is designed to apply the proposed change in an isolated detached Git worktree rather than your original checkout.

Always review the generated patch before using it.

## Does KEEP mean I should merge?

No. KEEP means the candidate cleared the configured PulseEngine experiment gates. It is still an engineering proposal requiring review.

## Why can PulseEngine return REJECT?

A change can be technically valid but not worth shipping, or it can improve a metric while breaking a required journey. PulseEngine is intentionally allowed to reject its own idea.

## Why can it return NO CANDIDATE?

Because forcing an optimization where none is supported would make the tool less trustworthy.

## Why can it return UNSUPPORTED?

The beta supports a deliberately narrow transformation model. PulseEngine may identify an opportunity shape that it is not yet willing to rewrite automatically.

## What frameworks are supported?

The current public beta is focused on React + Vite applications.

## Can I run it in CI?

Yes. The CLI includes GitHub workflow scaffolding. Review generated workflow permissions and commands before committing it.

## Does the beta expire?

Beta builds may include an expiration date so testers move to current builds while the product is changing rapidly.

## Why is the engine bundled/minified/top-level-mangled?

We want public testing without publishing the implementation source during early product validation. This raises the cost of casual copying, but it is not claimed to be unbreakable DRM.

## What feedback is most valuable?

The most valuable feedback is not "it ran." We want to know whether the candidate was conceptually correct, whether the evidence changed your decision, whether you trusted the workflow, and whether you would keep/pay for the product.
