# Technology stack

[← Back to the showcase](../README.md)

This inventory describes Namakan's research platform. It distinguishes the hosted application from the local research workspace and names dependencies without publishing implementation code or private configuration.

| Area | Technology | Role in Namakan |
|---|---|---|
| Interface | React 19 + TypeScript | Research conversations, projection models, reports, learning guides, and connection flows. |
| Frontend tooling | Vite | Development and production bundling for the web application. |
| Design | Semantic CSS tokens, Phosphor icons, Cabinet Grotesk | Consistent surfaces, type, controls, states, and responsive layouts. |
| Agent runtime | Python + Hermes Agent | Executes the specialized research workflow and resumes conversation context. |
| Tool protocol | MCP + FastMCP from the Python MCP SDK | A bounded interface for financial evidence, calculations, framework-guided analysis, and artifacts. |
| Model provider | MiniMax integration through Hermes | Model inference; the hosted worker brokers provider access without passing real provider credentials into the agent container. |
| Local service | Starlette + Uvicorn | Local API, event streaming, workspace state, and artifact access. |
| Hosted API | Node.js on Vercel | Authenticated request handling and tenant-scoped access to queued work and saved results. |
| Authentication | Supabase Auth + supabase-js | Account/session flows and verified user identity. |
| Hosted persistence | PostgreSQL via Supabase | Workspaces, memberships, conversations, durable jobs, ordered events, and artifact metadata; row-level security enforces tenant boundaries. |
| File storage | Private Supabase Storage | Published artifacts accessed through authorized, short-lived downloads. |
| Local persistence | SQLite | Local conversations, research records, and learning manifests. |
| Research data | SEC filings / XBRL + yfinance | Company disclosures and market information, with saved source references. |
| Retrieval | HTTPX + Beautiful Soup | HTTP access and readable source extraction within the permitted research workflow. |
| Spreadsheets | XlsxWriter + openpyxl | Excel-compatible models, formula-bearing outputs, and workbook inspection. |
| Reports | ReportLab + python-docx + Matplotlib | PDF/Word documents and financial charts. |
| Content rendering | react-markdown + remark-gfm | Research answers and structured analytical content in the browser. |
| Observability and evaluation | Langfuse | Traces, tool/model usage, explained review outcomes, and separately gated research datasets. |
| Execution | Docker + a supervised Python worker | Per-job isolation, constrained execution, and brokered external access. |
| Deployment | Vercel + Supabase + a separate worker host | Public frontend/API, managed identity/data/storage, and durable agent execution. |
| Verification | pytest + Playwright + Node test runner + database isolation checks | Backend behavior, browser workflows, API boundaries, and tenant/queue policies. |
| Automation | GitHub Actions | Automated checks for the private project. |

Exact dependency locks, deployment identifiers, database schemas, tool implementations, and infrastructure configuration remain private. The showcase gallery itself is plain HTML/CSS and media hosted on GitHub Pages.
