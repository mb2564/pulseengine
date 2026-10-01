# Interpreting PulseEngine Results

PulseEngine's verdict is intentionally not a single performance number.

## KEEP

A KEEP means the candidate cleared the configured experiment gates and produced enough measured value to remain worth reviewing.

It does **not** mean:

- automatically merge;
- production correctness is guaranteed;
- all user journeys were covered;
- your team no longer needs code review.

## REJECT

A REJECT is often a healthy result.

Examples include:

- performance improvement is too small;
- a required runtime journey fails;
- the intended boundary was not actually achieved;
- configured regression checks fail;
- the experiment creates unacceptable uncertainty.

## NO CANDIDATE

PulseEngine did not find a supported later-journey boundary worth proposing in the current scan.

Please tell us whether that matches your own reading of the application.

## UNSUPPORTED

PulseEngine sees a potentially relevant opportunity shape, but the current beta refuses to generate a transformation for it.

This is especially useful feedback if you believe the shape is common across real applications.

## REVIEW REQUIRED

The machine evidence is incomplete or ambiguous enough that the correct next step is explicit human review rather than a confident KEEP/REJECT.

## The question we care about during beta

After reading the result, ask:

> Did PulseEngine give me evidence I would not have had quickly enough from ordinary code review or a generic AI assistant?

That answer matters more than whether the verdict was positive.
