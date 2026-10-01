# Example of Useful Beta Feedback

This is an **illustrative** example. It is not a claimed PulseEngine benchmark.

> **Repository:** medium-sized React + Vite internal app, roughly 20 user-facing screens  
> **Outcome:** REJECT  
> **Setup:** worked without help  
> **Candidate:** settings/help module that appeared to belong after the initial dashboard journey  
> **Measured change:** initial gzip improved 1.4%  
> **Journey assessment:** candidate classification looked correct  
> **Verdict assessment:** agreed with REJECT; the gain was too small to justify another async boundary  
> **Review quality:** review.md made the decision understandable without reading raw evidence  
> **Would keep installed:** maybe  
> **Biggest adoption blocker:** need it to find useful candidates on more repositories before putting it in every PR

Why this is valuable:

- it tells us whether the candidate was semantically right;
- it separates candidate quality from performance magnitude;
- it tells us whether the verdict was trusted;
- it exposes the adoption blocker;
- it does not reveal proprietary source code.

A KEEP is not inherently more valuable to the beta than a trustworthy REJECT, NO CANDIDATE or UNSUPPORTED result.
