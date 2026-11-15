# Perimeter: v1 Product Requirements Document

The v1 PRD for [Perimeter](https://github.com/SannidhiSriram-06/perimeter), a self-hosted Kubernetes incident-triage tool built as a six-person team capstone.

When an alert fires, Perimeter works out which services are causally linked to the alerting one, drafts a root-cause report from the evidence, and checks the draft's structured claims against that evidence before a human reviews it. This document defines what v1 should do next, in what order, and how we will know it works.

## What the PRD argues

- **Where the product stands.** The proposal is roughly 40% built, and the engine still runs only on mock telemetry. Section 2 separates what is built, what is built with limits, and what is not built.
- **What v1 has to fix first.** The pitch is drafts you can audit, but the free-text parts of a draft are not fact-checked today. The priority is labelling verified versus unverified content (S6) and measuring accuracy with real fault injection (S5), ahead of new features.
- **How it is prioritized.** Stories are ranked with RICE, and the estimates are marked as judgment calls. Open assumptions, such as the time saved per incident and whether data egress is the real adoption blocker, are listed for validation with users.

## Contents

- [PRD.pdf](PRD.pdf): the full document with figures
- [PRD.md](PRD.md): the same document in Markdown
- `assets/`: the figures, taken from the running Perimeter repo (mock telemetry, not production data)
