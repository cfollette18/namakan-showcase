# Engineering overview

[← Back to the showcase](../README.md) · [Technology stack](STACK.md)

## The engineering problem

An investing workspace needs more than a useful model response. Users need to understand where a finding came from, inspect the assumptions in a model, reopen an earlier report, and recover when a long-running research session outlives the browser connection.

Namakan joins those workflows while keeping account identity, execution authority, analytical artifacts, and review status separate.

## System responsibilities

| Boundary | Responsibility |
|---|---|
| React workspace | Present conversations, public tool activity, scenario comparisons, artifact readers, and account flows. |
| Hosted API | Verify identity and authorize access to the user's workspace resources. |
| Supabase | Persist memberships, conversations, jobs, events, and private artifact metadata; enforce row-level access. |
| Worker supervisor | Claim durable jobs, maintain leases, coordinate cancellation, and publish authorized results. |
| Isolated research runtime | Run the specialized Hermes/MCP workflow in a fresh constrained environment. |
| External-access broker | Mediate permitted network/model requests and keep provider credentials out of the agent runtime. |
| Artifact layer | Preserve versioned reports/workbooks with integrity metadata and controlled downloads. |
| Review and observability | Record execution outcomes and evaluate research through explicit gates within the appropriate operating scope. |

The public demo runs separately with fictional in-memory content. It renders the real interface without submitting research or accessing private records.

## Selected design decisions

### Keep long-running work outside the browser lifecycle

Research runs through a durable job queue. Stable submission identifiers prevent duplicate enqueueing; ordered events let the interface recover its view after reconnecting. Worker leases and fencing prevent an expired worker from publishing as though it still owns the job.

Expired execution is recorded explicitly rather than silently replaying potentially completed side effects. Cancellation preserves recorded history.

### Isolate the runtime as well as the database

Database row-level security controls which records a caller can access. The agent also needs a restricted execution context: fresh Docker environments, bounded resources, selected research tools, and mediated external access.

Customer execution does not inherit the owner's personal agent profile, home directory, connected accounts, or real provider credentials. The supervisor and broker carry separate responsibilities from the research process.

### Keep evidence attached to the work

Research saves evidence references and calculation context. Reports and models retain immutable versions, making it possible to inspect the result that existed at a particular revision instead of replacing it with the latest output.

Native readers make those artifacts usable before export: users can inspect a model's formulas or a report's sources within the same workspace.

### Treat review as a distinct state

Successfully generating a document does not establish analytical correctness. The owner research pipeline combines deterministic source/arithmetic checks with independently explained coverage, grounding, and quality reviews. Admission to a training dataset has a further gate.

Missing scores remain pending. Synthetic checks do not become training examples. Hosted customer output is not silently routed into the owner's collection pipeline, and independent learning-guide review remains pending.

### Make activity understandable

The interface exposes public operation names, purpose, progress, duration, and results. It does not present private model reasoning as a product feature. Saved conversations and tool activity retain context across follow-ups.

## Verification approach

The private project includes checks for backend validation, evidence/artifact handling, cancellation and recovery, API authorization, database tenant isolation, queue behavior, privacy boundaries, and browser interaction at desktop/mobile sizes.

Browser fixtures exercise visual and account states without generating paid research or contaminating datasets. Database fixtures verify cross-tenant access restrictions. Worker checks cover isolated startup and the model-access broker.

For this public showcase, the four videos were newly recorded from the live public previews. The recording sessions were checked for browser errors and unexpected API/auth calls; gallery playback, media files, links, and responsive layouts were checked separately. No private application test results are presented as fresh showcase measurements.

## Tradeoffs and current limits

- The initial hosted runtime uses a single worker host. Availability and recovery operations remain an operational concern; this is not a high-availability claim.
- Docker containers share the worker host's kernel. The current boundary is not equivalent to independent virtual machines.
- Sensitive-content detection and masking are scoped controls, not proof that arbitrary confidential content can always be recognized.
- Hosted Learn persistence, customer productivity-account connections, and production email delivery have remaining integration or rollout work.
- The public videos demonstrate interaction design with sample content; they are not benchmarks of live inference or financial results.

## Contribution and attribution

Namakan is Clinton Follette's product work across interface design, application development, research workflows, runtime integration, evaluation, and deployment. It builds on the [Hermes Agent](https://github.com/NousResearch/hermes-agent) runtime by Nous Research and the technologies listed in the [stack](STACK.md).

This overview intentionally stays at the system-responsibility level. Source code, method definitions, prompts, rubric contents, datasets, schemas, secrets, and operational identifiers are not distributed here.
