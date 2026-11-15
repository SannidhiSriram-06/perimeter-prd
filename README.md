# Perimeter: v1 Product Requirements Document

This repository contains the v1 Product Requirements Document for **Perimeter**, a self-hosted incident-triage tool for Kubernetes. Perimeter is a team capstone project. The code lives in a separate repository: [SannidhiSriram-06/perimeter](https://github.com/SannidhiSriram-06/perimeter).

When an alert fires on a Kubernetes service, an on-call engineer has to work out what broke and what else it affects. Perimeter narrows that down to the services causally linked to the alerting one, asks an LLM to draft a root-cause report from the ranked evidence, checks the draft's structured claims against that same evidence, and leaves a human to review and finalize the result. It is designed to run inside the customer's own infrastructure.

The PRD defines the next phase of the project: what to build, in what order, and how we will know it works.

## Read the document

- [PRD.pdf](PRD.pdf): the full document with figures, formatted for reading
- [PRD.md](PRD.md): the same content as Markdown
- [assets/](assets): the four figures used in the document

## What the PRD covers

1. **Current state.** An audit of what the project does today, split into built, built with limits, and not built. The figures in this section come from the running code: the architecture diagram, and a real incident created by posting an alert to the local stack. Both use mock telemetry.
2. **Problem and users.** The problem statement and three user personas, each marked as a hypothesis to validate with interviews rather than a finding.
3. **Competitive landscape.** Existing incident-management and AI root-cause tools, their pricing and deployment models, and what that means for Perimeter's positioning.
4. **Where the positioning outruns the product.** A table of claims from the original pitch, what the code actually supports, and which story fixes each gap.
5. **Goals, non-goals and requirements.** Six user stories (S1 to S6) with acceptance criteria written as given/then statements, plus a short list of Phase 2 items that are deliberately out of scope.
6. **Prioritization.** RICE scoring for every story. The estimates are my own judgment calls and are labelled that way.
7. **Success metrics, validation plan, risks and roadmap.** Which numbers to track, which assumptions are still untested, and what ships first.

## The main argument

The project's central claim is that its root-cause drafts can be audited. Blast-radius scoping is a deterministic graph traversal, and the structured claims in each draft are checked against the evidence the model was shown. That claim is only partly true today. The free-text sections of a draft are not fact-checked, and everything the engine reasons about still comes from mock telemetry, with no real trace ingestion yet.

The PRD therefore puts two things ahead of new features:

- Labelling which parts of a draft are machine-checked and which are not (story S6), so unchecked text can never pass as verified.
- Measuring accuracy with real fault injection on instrumented services (story S5), so any number quoted about the product comes from a measurement rather than an assumption.

Figures that depend on mock data are captioned that way, and the document marks its time-saved figures as hypotheses until they are measured.

## About the figures

All four figures were captured from the real project, not mocked up.

| Figure | Source |
| :--- | :--- |
| 1. Architecture | Mermaid diagram from the code repo's README, rendered as an image |
| 2. Incident and blast radius | Output from the local Docker stack after posting one alert, on mock telemetry |
| 3. Review UI wireframes | The existing SVG wireframes in the code repo; the UI is not built yet |
| 4. Evaluation results page | The built admin page, showing an offline dry run labelled as mock data |

A figure showing a model-generated draft with its validation flags is not included, because capturing one needs an LLM API key that was not available when the figures were produced.

## Status

This is version 0.2 of the PRD, dated 15 November 2026, written against `main` at commit `5630574` of the code repository. Repository facts were extracted from the code at that commit. Competitor and pricing information comes from public pages and may have changed since, so the document lists its sources for checking.
