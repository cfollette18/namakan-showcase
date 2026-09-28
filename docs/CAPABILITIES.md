# Capabilities and availability

[← Back to the showcase](../README.md) · [Watch the demos](https://cfollette18.github.io/namakan-showcase/)

## Research

- Ask questions about a company and continue a saved conversation.
- Apply structured methods for income statements, balance sheets, cash flow, competitive advantages, and valuation.
- Retrieve public financial evidence and connect calculations to saved source references.
- Follow visible activity, inspect tool purpose/results, and distinguish running, completed, and failed work.
- Resume viewing activity after a browser reconnect; cancel active work without erasing already recorded history.

The public recording shows tool inspection and a scripted follow-up about reinvestment and shareholder dilution.

## Projections

- Compare bear, base, and bull scenarios over a five-year default horizon, with support up to ten years.
- Inspect annual outputs, growth, margins, share counts, valuation assumptions, and return scenarios.
- Read the workbook directly in Namakan, select sheets/cells, and inspect stored formulas and values.
- Generate versioned Excel-compatible XLSX files in the research engine.
- Work with qualitative factors and explicit assumption changes, keeping analytical judgments connected to model inputs.

The public recording shows the scenario overview, an editable growth input, a workbook formula, assumptions, and the qualitative-factors view. Its values are fictional and its download actions are preview-only.

## Reports

- Combine executive synthesis with income statement, balance sheet, cash flow, moat, and valuation analyses.
- Read financial charts, analytical sections, source references, and review information in the native reader.
- Preserve older versions and distinguish review status from successful file generation.
- Export PDF, Word, and Markdown documents through implemented artifact workflows.

The public recording explores the overview, full report, and sources/review view. The sample is explicitly marked as unreviewed demo content.

## Learn

- Save company-specific guides with takeaways, definitions, explanations, uncertainty, and evidence.
- Expand supporting claims and return to source references.
- Keep personal notes and bookmarks separate from generated content.
- Continue learning from the selected guide, retain immutable revisions, and export PDF or Markdown locally.
- Reject stale note writes instead of silently overwriting newer notes.

The public recording explores a moat guide, expands evidence, and saves a note in the isolated demo session. This does not create a cloud account or persistent customer record.

## Connections and workspace controls

- Configured local Google Sheets/Drive and Microsoft Excel/OneDrive OAuth workflows support optional cloud copies of artifacts.
- Connection screens expose account status and permission context.
- Account/session flows include sign-in, sign-out, recovery, and workspace entry.
- Settings includes a Send with Enter preference and access to connection management.
- Native artifact reading does not depend on exporting to an external productivity service.

## Engineering capabilities

- Durable queueing, idempotency, leases, worker fencing, cancellation, and ordered event replay.
- Tenant-aware API access, PostgreSQL row-level security, and private artifact storage.
- Fresh constrained execution environments with brokered external access and separate credential handling.
- Immutable artifact versions and integrity metadata.
- Deterministic source/arithmetic checks and independently explained research review outcomes in the owner pipeline.
- Observability for operation status, tool/model usage, and privacy decisions, with credential masking and publication gates.

## Availability

Snapshot: September 28, 2026. Product descriptions were checked against the private implementation and runbooks; the public previews were recorded directly from the live website. This is not a fresh end-to-end verification of every hosted feature.

| Surface | Current boundary |
|---|---|
| Public website and four interactive previews | Live at [namakanai.com](https://namakanai.com); fictional sample data, scripted interactions, no model inference. |
| Hosted research and durable execution | Implemented and previously exercised end to end. The initial deployment uses a single worker host and depends on its availability. |
| Research/report/projection engine | Implemented; public previews demonstrate selected interactions rather than authenticating into a customer account. |
| Learn | Implemented in the local workspace and public demo. Hosted persistence, annotations, and worker publication still require dedicated integration. |
| Google/Microsoft connections | Implemented for configured local accounts. Hosted customer connection rollout remains separate. |
| Email onboarding and recovery delivery | Auth flows exist; production email delivery and public onboarding remain operational setup items. |
| Financial research evaluation and dataset collection | Implemented for the dedicated owner research pipeline. Native financial judge collection is not enabled inside hosted customer containers. |
| Customer research data | Kept separate from owner training collections; no automatic training-data admission. |

Recorded demos are visual product evidence. They do not establish response latency, financial accuracy, cloud persistence, or external integration success.
