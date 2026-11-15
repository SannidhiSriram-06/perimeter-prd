# Perimeter: v1 Product Requirements Document

This repo holds the v1 PRD for **Perimeter**, a self-hosted incident-triage tool for Kubernetes. Perimeter was built as a team capstone project. The PRD says what to build next, in what order, and how we'll know it works, starting from an evidence-based account of what the project actually does today.

## Core argument

- **Be honest about the starting point.** About 40% of the original proposal is built, and everything the engine reasons about is still mock telemetry. The PRD separates what is built, built with limits, and not built.
- **The promise has to be true before it is marketed.** Perimeter's claim is drafts you can audit: scoping is a deterministic graph walk, and the draft's structured claims are checked against the evidence. Today the free-text parts of a draft are not checked, so v1 prioritizes labelling verified versus unverified content (S6) and measuring accuracy on real fault injection (S5) over new features.
- **Sequence by evidence and effort.** Stories are ranked with RICE using stated judgment-call estimates, and open assumptions (time saved, whether data egress is the real blocker) are listed as things to validate with users.

## Contents

- [PRD.pdf](PRD.pdf): the PRD with figures, for reading
- [PRD.md](PRD.md): the same document as Markdown
- `assets/`: figures, captured from the running code repo (screenshots of the real stack on mock telemetry, the repo's own diagram, and its existing wireframes)

Code repo: https://github.com/SannidhiSriram-06/perimeter
