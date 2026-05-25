# Product Backlog
## Advisor Portfolio Rebalancing & Suitability Review Platform

| Field | Value |
|---|---|
| **Project** | Advisor Portfolio Rebalancing & Suitability Review Platform |
| **JIRA Project** | APR — advisor-portfolio-rebalancing.atlassian.net |
| **Version** | 1.0 |
| **Date** | 25 May 2026 |
| **BRD Reference** | BRD v1.0 |
| **Total Issues** | 80 (8 Epics · 46 User Stories · 26 Tasks) |
| **Total Story Points** | 199 |

---

## Ownership Map

| Assignee | Role | Owns |
|---|---|---|
| Vrushali | Product Owner | All 8 Epics |
| Gaurav | Business Analyst | All 46 User Stories |
| Vivek | UX Designer | 8 UX Design Tasks |
| Rupa | Developer | 10 Dev Tasks |
| Apra | QA Engineer | 8 QA Tasks |

> **★ AI-Added** — Requirements marked AI-Added were inferred to ensure completeness. Must be reviewed before sign-off.

---

## Epic Summary

| Epic | Name | Stories | Dev | UX | QA | Total SP | Priority |
|---|---|---|---|---|---|---|---|
| EP-01 | Advisor Dashboard | 5 | 2 | 1 | 1 | 36 | Critical |
| EP-02 | Portfolio Detail View | 5 | 1 | 1 | 1 | 26 | Critical |
| EP-03 | Rebalancing Proposal | 8 | 2 | 1 | 1 | 56 | Critical |
| EP-04 | Suitability Validation Engine | 6 | 1 | 1 | 1 | 56 | Critical |
| EP-05 | Approval Workflow | 7 | 1 | 1 | 1 | 51 | Critical |
| EP-06 | Audit Trail & Reporting | 5 | 1 | 1 | 1 | 32 | Critical |
| EP-07 | AI Summary Generation | 5 | 1 | 1 | 1 | 31 | High |
| EP-08 ★ | Authentication & Access Control | 5 | 1 | 1 | 1 | 43 | Critical |
| **Total** | | **46** | **10** | **8** | **8** | **331** | |

---

## EP-01 · Advisor Dashboard
**JIRA Epic:** APR-5 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-01 | Epic | Advisor Dashboard | Provide advisors with a centralised portfolio overview showing drift indicators, risk profiles, and proposal status. | Dashboard loads ≤3s; all assigned clients visible with all required fields. | 0 | Critical | Vrushali | Source Docs | APR-5 |
| US-001 | Story | View all assigned client portfolios | As a Financial Advisor, I want to see all my assigned clients on a dashboard so I can prioritise rebalancing actions. | All clients shown; name, risk profile, current vs target %, drift %, last review date; loads in 3s. | 5 | Critical | Gaurav | Source Docs | APR-13 |
| US-002 | Story | Colour-coded drift indicators | As a Financial Advisor, I want colour-coded drift indicators so I can instantly spot portfolios needing attention. | Green ≤5%, Amber 5–10%, Red >10%; legend visible. | 3 | High | Gaurav | Source Docs | APR-14 |
| US-003 | Story | Sort and filter dashboard | As a Financial Advisor, I want to sort and filter the dashboard so I can focus on specific client segments. | Filters: name, risk profile, drift band, date range; results update in <1s. | 3 | High | Gaurav | Source Docs | APR-15 |
| US-004 | Story | Proposal status badge per client | As a Financial Advisor, I want to see the latest proposal status per client so I don't duplicate work. | Status badge: Draft/In Review/Approved/Rejected/None; reflects latest state on load. | 2 | High | Gaurav | Source Docs | APR-16 |
| US-005 ★ | Story | Manual refresh and last-updated timestamp | As a Financial Advisor, I want a manual refresh button and timestamp so I know data is current. | Refresh updates timestamp; no stale data beyond 24h. | 2 | Medium | Gaurav | AI-Added | APR-17 |
| UX-01 | Task | Design advisor dashboard wireframes (S-02) | Design wireframes, hi-fi mockups, and interaction specs for the Advisor Dashboard screen S-02. | Figma wireframes + hi-fi mockup + component spec. | 5 | Critical | Vivek | Source Docs | APR-18 |
| TK-01 | Task | Backend — Portfolio drift calculation API | Implement portfolio drift calculation API returning per-asset-class drift for each assigned client. | API returns drift % per asset class; P95 ≤500ms under 100 concurrent users. | 5 | Critical | Rupa | Source Docs | APR-19 |
| TK-02 | Task | Frontend — Dashboard table component with filters | Build the filterable, sortable dashboard table component per UX spec S-02. | All filter/sort combinations work; WCAG 2.1 AA; responsive at 768px+. | 5 | Critical | Rupa | Source Docs | APR-20 |
| QA-01 | Task | Test advisor dashboard (US-001 to US-005) | Validate all Advisor Dashboard stories against acceptance criteria. | All ACs pass; cross-browser; WCAG scan zero violations; no P1/P2 defects. | 5 | High | Apra | Source Docs | APR-21 |

---

## EP-02 · Portfolio Detail View
**JIRA Epic:** APR-6 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-02 | Epic | Portfolio Detail View | Deep-dive per-client view of holdings, allocation charts, client profile, and proposal history. | Detail page loads ≤3s; all holdings, chart, profile, and history visible. | 0 | Critical | Vrushali | Source Docs | APR-6 |
| US-006 | Story | View all client holdings | As a Financial Advisor, I want to see all holdings with asset class, ticker, quantity, value and allocation. | All 7 fields rendered per holding; loads in 3s. | 5 | Critical | Gaurav | Source Docs | APR-22 |
| US-007 | Story | Current vs target allocation chart | As a Financial Advisor, I want a visual chart comparing current vs target allocation per asset class. | Bar or donut chart; ARIA accessible; readable at 1280x800. | 3 | High | Gaurav | Source Docs | APR-23 |
| US-008 | Story | Client risk profile and goals | As a Financial Advisor, I want to see the client's risk profile, goals and time horizon. | All 3 visible without extra navigation. | 2 | High | Gaurav | Source Docs | APR-24 |
| US-009 ★ | Story | Proposal version history | As a Financial Advisor, I want to see all prior proposals for a client so I have full context. | All proposals listed: ID, date, status, advisor; click opens read-only; paginated at 20+. | 3 | Medium | Gaurav | AI-Added | APR-25 |
| US-010 ★ | Story | Holdings CSV and Excel export | As a Financial Advisor, I want to export holdings data as CSV or Excel for offline analysis. | In-page download; all fields included; CSV and .xlsx formats. | 2 | Medium | Gaurav | AI-Added | APR-26 |
| UX-02 | Task | Design portfolio detail view wireframes (S-03) | Design wireframes and UI specs for the Portfolio Detail View screen S-03. | Figma wireframes + hi-fi mockup + interaction annotations. | 5 | Critical | Vivek | Source Docs | APR-27 |
| TK-03 | Task | Frontend — Allocation chart and portfolio detail page | Build a reusable allocation chart component and the full portfolio detail page per UX spec S-03. | Chart ARIA accessible; renders in all supported browsers; reusable across screens. | 5 | High | Rupa | Source Docs | APR-28 |
| QA-02 | Task | Test portfolio detail view (US-006 to US-010) | Validate Portfolio Detail View stories against acceptance criteria. | All ACs pass; chart accuracy verified; export validated; no P1/P2 defects. | 5 | High | Apra | Source Docs | APR-29 |

---

## EP-03 · Rebalancing Proposal
**JIRA Epic:** APR-7 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-03 | Epic | Rebalancing Proposal | Enable advisors to create, edit, version, attach files to, and submit rebalancing proposals with real-time validation. | Full proposal workflow completable without leaving platform; auto-save every 2 min; versions immutably preserved. | 0 | Critical | Vrushali | Source Docs | APR-7 |
| US-011 | Story | Initiate a new rebalancing proposal | As a Financial Advisor, I want to start a proposal from the dashboard or portfolio detail view. | Draft with unique PROP-YYYYMMDD-NNNN ID; accessible from both locations. | 3 | Critical | Gaurav | Source Docs | APR-30 |
| US-012 | Story | Adjust allocations with real-time 100% validation | As a Financial Advisor, I want real-time sum validation so I can't submit an invalid proposal. | Inputs and sliders synchronised; submit disabled when total ≠ 100%; inline error shown. | 5 | Critical | Gaurav | Source Docs | APR-31 |
| US-013 | Story | Pre/post allocation comparison panel | As a Financial Advisor, I want a side-by-side comparison of current vs proposed allocation. | Panel updates within 500ms; shows current %, proposed %, delta, value change. | 3 | High | Gaurav | Source Docs | APR-32 |
| US-014 ★ | Story | Proposal auto-save with last-saved timestamp | As a Financial Advisor, I want auto-save every 2 minutes so I never lose work. | Auto-save without user action; 'Last saved HH:MM:SS' visible; no data lost on tab close. | 3 | High | Gaurav | AI-Added | APR-33 |
| US-015 | Story | Immutable proposal version history | As a Financial Advisor, I want every save to create an immutable version snapshot. | Version increments on each save; prior versions accessible read-only; no version modifiable. | 5 | Critical | Gaurav | Source Docs | APR-34 |
| US-016 | Story | Add free-text notes to proposal | As a Financial Advisor, I want to add notes to provide context for the compliance reviewer. | Notes up to 2,000 chars; live character count; saved with each version. | 2 | High | Gaurav | Source Docs | APR-35 |
| US-017 ★ | Story | Attach supporting PDF documents | As a Financial Advisor, I want to attach up to 5 PDFs max 10 MB each. | PDF type enforced; 10 MB limit; max 5 files; listed with name and size. | 3 | Medium | Gaurav | AI-Added | APR-36 |
| US-018 | Story | Discard draft with confirmation | As a Financial Advisor, I want to discard a draft with a confirmation prompt. | Confirmation required; logged in audit trail; only available in Draft state. | 2 | Medium | Gaurav | Source Docs | APR-37 |
| UX-03 | Task | Design proposal editor and suitability modal (S-04, S-05) | Design wireframes and hi-fi UI specs for Proposal Editor S-04 and Suitability Modal S-05. | Figma wireframes + hi-fi mockup + component spec for both screens. | 8 | Critical | Vivek | Source Docs | APR-38 |
| TK-04 | Task | Backend — Proposal CRUD API with versioning | Implement proposal CRUD API with versioning, auto-save, and file attachment endpoints. | All CRUD operations; immutable versioned snapshots; unique ID format; P95 ≤500ms. | 8 | Critical | Rupa | Source Docs | APR-39 |
| TK-05 | Task | Frontend — Proposal editor UI (Screen S-04) | Build full proposal editor per UX spec S-04: sliders, comparison panel, notes, attachments, version sidebar. | All controls functional; WCAG 2.1 AA; responsive at 768px+. | 8 | Critical | Rupa | Source Docs | APR-40 |
| QA-03 | Task | Test rebalancing proposal workflow (US-011 to US-018) | Validate all Rebalancing Proposal stories against acceptance criteria. | All ACs pass; auto-save tested; file limits verified; version immutability confirmed; no P1/P2 defects. | 8 | Critical | Apra | Source Docs | APR-41 |

---

## EP-04 · Suitability Validation Engine
**JIRA Epic:** APR-8 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-04 | Epic | Suitability Validation Engine | Automatically validate proposal allocations against client risk profiles on submission. | 100% of submissions trigger validation; results ≤5s P95; critical violations block submission. | 0 | Critical | Vrushali | Source Docs | APR-8 |
| US-019 | Story | Auto-trigger validation on submission | As a Financial Advisor, the system should automatically trigger suitability validation when I submit. | Triggers on submit; progress indicator shown; completes ≤5s P95. | 3 | Critical | Gaurav | Source Docs | APR-42 |
| US-020 | Story | Risk profile evaluation with configured rules | As a Compliance Officer, I want the engine to evaluate proposals against configured risk profile rules. | Validates Conservative, Moderate, Aggressive; hard-rule violations always produce Critical result. | 8 | Critical | Gaurav | Source Docs | APR-43 |
| US-021 | Story | Structured validation report display | As a Financial Advisor, I want a clear validation report listing all violated rules. | Report: overall result; each violation: rule ID, severity, plain-language description. | 5 | Critical | Gaurav | Source Docs | APR-44 |
| US-022 ★ | Story | Hard stop for critical violations | As a Compliance Officer, I want critical violations to hard-block submission. | Submit blocked; all critical violations listed; advisor must resolve before resubmitting. | 5 | Critical | Gaurav | AI-Added | APR-45 |
| US-023 ★ | Story | Warning acknowledgement flow | As a Financial Advisor, I want to acknowledge non-critical warnings to submit with awareness. | Warning modal shown; submit only after all checkboxes checked; acknowledgements logged. | 3 | High | Gaurav | AI-Added | APR-46 |
| US-024 ★ | Story | Admin panel for rule configuration | As a Compliance Officer, I want to create, edit, enable, and disable suitability rules. | Rule changes effective on next submission; all modifications logged; admin UI restricted. | 5 | High | Gaurav | AI-Added | APR-47 |
| UX-04 | Task | Design suitability rule administration panel | Design the Suitability Rule Administration panel as part of Admin Screen S-09. | Figma wireframes + hi-fi mockup for rule list, create/edit form, and toggle. | 5 | High | Vivek | AI-Added | APR-48 |
| TK-06 | Task | Backend — Suitability validation engine service | Implement the suitability validation engine supporting Critical and Warning rules. | Engine returns report ≤5s P95; all rule types tested; rules configurable without redeployment. | 13 | Critical | Rupa | Source Docs | APR-49 |
| QA-04 | Task | Test suitability validation engine (US-019 to US-024) | Validate Suitability Validation Engine stories against acceptance criteria. | All ACs pass; hard-stop verified; warning flow tested; performance ≤5s P95; no P1/P2 defects. | 8 | Critical | Apra | Source Docs | APR-50 |

---

## EP-05 · Approval Workflow
**JIRA Epic:** APR-9 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-05 | Epic | Approval Workflow | Multi-stage review: Draft → Submitted → Compliance Review → Approved/Rejected with notifications and SLA escalation. | State transitions atomic and logged; in-app ≤30s; email ≤5min; escalation at 5-business-day threshold. | 0 | Critical | Vrushali | Source Docs | APR-9 |
| US-025 | Story | Multi-stage workflow state machine | As a Compliance Officer, I want a structured workflow so proposals follow a defined approval path. | States only transition in defined sequence; all transitions atomic and logged. | 5 | Critical | Gaurav | Source Docs | APR-51 |
| US-026 ★ | Story | Compliance notification on submission | As a Compliance Officer, I want in-app and email notification when a proposal reaches review. | In-app ≤30s; email ≤5min; includes proposal ID, client name, direct link. | 3 | High | Gaurav | AI-Added | APR-52 |
| US-027 | Story | Approve / reject with mandatory comment | As a Compliance Officer, I want to be required to leave a comment on rejection. | Reject blocked if comment < 10 chars; actions update state immediately. | 3 | Critical | Gaurav | Source Docs | APR-53 |
| US-028 ★ | Story | Advisor notification on decision | As a Financial Advisor, I want to be notified when my proposal is approved or rejected. | In-app ≤30s; email ≤5min; includes compliance officer's comment. | 3 | High | Gaurav | AI-Added | APR-54 |
| US-029 | Story | Revision and resubmission after rejection | As a Financial Advisor, I want to revise a rejected proposal and resubmit. | Rejected returns to Draft; advisor can edit and resubmit; creates new version. | 3 | High | Gaurav | Source Docs | APR-55 |
| US-030 ★ | Story | SLA escalation after 5 business days | As an Operations Lead, I want proposals in review for more than 5 business days to auto-escalate. | Escalation fires at 5-business-day threshold excluding weekends and holidays; logged; notification sent. | 5 | High | Gaurav | AI-Added | APR-56 |
| US-031 ★ | Story | Compliance officer delegation | As a Compliance Officer, I want to delegate approval authority for a specified period. | Delegation with start/end date; both officers attributed in audit trail. | 5 | Medium | Gaurav | AI-Added | APR-57 |
| UX-05 | Task | Design compliance review screen and delegation UI (S-06) | Design wireframes and hi-fi specs for Compliance Review S-06 and delegation management UI. | Figma wireframes + hi-fi mockup for proposal panel, approve/reject panel, escalation indicator, delegation UI. | 8 | Critical | Vivek | Source Docs | APR-58 |
| TK-07 | Task | Backend — Workflow state machine, notifications, SLA escalation | Implement workflow state machine, notifications, SLA escalation scheduler, and delegation logic. | All transitions atomic; notifications ≤30s in-app; ≤5min email; escalation scheduler tested. | 13 | Critical | Rupa | Source Docs | APR-59 |
| QA-05 | Task | Test approval workflow and notifications (US-025 to US-031) | Validate all Approval Workflow stories against acceptance criteria. | All ACs pass; state transitions verified; notifications timed; escalation tested; no P1/P2 defects. | 8 | Critical | Apra | Source Docs | APR-60 |

---

## EP-06 · Audit Trail & Reporting
**JIRA Epic:** APR-10 · **Owner:** Vrushali · **Priority:** Critical

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-06 | Epic | Audit Trail & Reporting | Immutable, searchable, exportable log of all system and user actions. 7-year data retention. | 100% of auditable events captured; all 10 log fields present; CSV export ≤10s for 10,000 records. | 0 | Critical | Vrushali | Source Docs | APR-10 |
| US-032 | Story | Automatic logging of all auditable actions | As a Compliance Officer, I want every user and system action logged automatically. | All event types produce a log entry; no auditable action omitted. | 5 | Critical | Gaurav | Source Docs | APR-61 |
| US-033 ★ | Story | Extended log fields including IP and session ID | As a Compliance Officer, I want log entries to capture IP address and session ID. | All 10 fields present: timestamp, user ID, role, action, entity type and ID, prev and new state, IP, session. | 3 | High | Gaurav | AI-Added | APR-62 |
| US-034 | Story | Immutable read-only audit trail | As a Compliance Officer, I want audit entries to be unmodifiable so the trail is tamper-proof. | No edit or delete in UI for any role; direct DB delete blocked at application layer. | 3 | Critical | Gaurav | Source Docs | APR-63 |
| US-035 ★ | Story | 7-year audit log data retention policy | As a Compliance Officer, I want audit logs retained for 7 years. | Retention policy configured; automated test confirms no premature deletion. | 3 | Critical | Gaurav | AI-Added | APR-64 |
| US-036 ★ | Story | Audit log search, filter, and CSV export | As a Compliance Officer, I want to search and export filtered audit logs. | Filters: date range, user, action type, proposal ID, client ID. CSV export ≤10s for 10,000 records. | 5 | High | Gaurav | AI-Added | APR-65 |
| UX-06 | Task | Design audit trail viewer UI spec (S-07) | Design the Audit Trail Viewer screen S-07 wireframes and hi-fi specification. | Figma wireframes + hi-fi mockup for filterable log table, export button, empty and no-results states. | 5 | High | Vivek | AI-Added | APR-66 |
| TK-08 | Task | Backend — Append-only audit log service | Implement write-once audit log with no-delete constraint, 7-year retention TTL, and filterable query API. | Insert-only enforced at DB; query API supports all 5 filters; P95 ≤500ms; CSV ≤10s for 10,000 records. | 8 | Critical | Rupa | Source Docs | APR-67 |
| QA-06 | Task | Test audit trail completeness and immutability (US-032 to US-036) | Validate Audit Trail stories against acceptance criteria. | All 12 event types trigger entry; all 10 fields verified; edit/delete blocked; export tested; no P1/P2 defects. | 8 | Critical | Apra | Source Docs | APR-68 |

---

## EP-07 · AI Summary Generation
**JIRA Epic:** APR-11 · **Owner:** Vrushali · **Priority:** High

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-07 | Epic | AI Summary Generation | AI-assisted plain-language client summaries from approved proposals. Advisor editable. Branded PDF export. | Summary ≤30s P95; advisor must approve before delivery; original AI text preserved; PDF includes branding. | 0 | High | Vrushali | Source Docs | APR-11 |
| US-037 | Story | Generate plain-language AI client summary | As a Financial Advisor, I want the system to generate a plain-language summary of my proposal. | Summary in plain English; no jargon or return projections. | 5 | High | Gaurav | Source Docs | APR-69 |
| US-038 | Story | AI summary references client goals and horizon | As a Financial Advisor, I want the summary to reference the client's goals and time horizon. | Summary explicitly references at least one of: goals, horizon, or risk profile. | 3 | High | Gaurav | Source Docs | APR-70 |
| US-039 ★ | Story | Advisor edit and save AI summary | As a Financial Advisor, I want to review, edit, and save the AI summary before finalising. | Editable rich-text field; save creates versioned snapshot; original AI output preserved read-only. | 3 | High | Gaurav | AI-Added | APR-71 |
| US-040 ★ | Story | Export AI summary as branded PDF | As a Financial Advisor, I want to export the summary as a branded PDF. | PDF: firm logo, advisor name, client name, proposal ID; readable at A4 or Letter. | 3 | Medium | Gaurav | AI-Added | APR-72 |
| US-041 ★ | Story | 30-second SLA with progress indicator | As a Financial Advisor, I want generation to complete within 30 seconds with a visible progress indicator. | Generation ≤30s P95; spinner visible; timeout error with retry option if exceeded. | 2 | Medium | Gaurav | AI-Added | APR-73 |
| UX-07 | Task | Design AI summary editor UI spec (S-08) | Design the AI Summary Editor screen S-08 wireframes and hi-fi specification. | Figma wireframes + hi-fi mockup for rich-text field, original AI toggle, PDF export, progress spinner. | 5 | High | Vivek | AI-Added | APR-74 |
| TK-09 | Task | Backend — LLM integration for AI summary generation | Implement AI summary generation service using configured LLM provider with prompt engineering and PDF export. | Summaries ≤30s P95; original output preserved; PDF export with all 4 branding fields. | 8 | High | Rupa | Source Docs | APR-75 |
| QA-07 | Task | Test AI summary generation and PDF export (US-037 to US-041) | Validate AI Summary Generation stories against acceptance criteria. | All ACs pass; quality checked; edit and preserve original verified; PDF validated; 30s SLA tested; no P1/P2 defects. | 5 | High | Apra | Source Docs | APR-76 |

---

## EP-08 · Authentication & Access Control ★
**JIRA Epic:** APR-12 · **Owner:** Vrushali · **Priority:** Critical · **Source:** AI-Added

| Key | Type | Summary | Story | AC | SP | Priority | Assignee | Source | JIRA |
|---|---|---|---|---|---|---|---|---|---|
| EP-08 ★ | Epic | Authentication & Access Control | SSO, four-role RBAC, MFA for Compliance & Admin, session timeout with warning, and user admin panel. | All roles access only permitted features; MFA enforced; sessions expire at 30 min with 2-min warning. | 0 | Critical | Vrushali | AI-Added | APR-12 |
| US-042 ★ | Story | SSO via SAML 2.0 / OAuth 2.0 | As a System Admin, I want users to authenticate via the firm's IdP so credentials are managed centrally. | Successful SSO login; failed auth blocks access. | 5 | Critical | Gaurav | AI-Added | APR-77 |
| US-043 ★ | Story | RBAC with four roles | As a System Admin, I want four roles with distinct non-overlapping permission sets. | Each role accesses only BRD-defined features; cross-role attempts return HTTP 403 and are logged. | 5 | Critical | Gaurav | AI-Added | APR-78 |
| US-044 ★ | Story | Session timeout with 2-minute warning modal | As a Security Lead, I want sessions to expire after 30 minutes with a 2-minute warning. | Session expires at 30 min; warning modal at 28 min; user can extend from modal. | 3 | High | Gaurav | AI-Added | APR-79 |
| US-045 ★ | Story | MFA for Compliance Officer and Admin | As a Security Lead, I want MFA enforced for Compliance Officers and Admins. | Login blocked without MFA for these roles; MFA challenge shown after primary auth. | 3 | Critical | Gaurav | AI-Added | APR-80 |
| US-046 ★ | Story | Admin user management panel | As a System Admin, I want to create, deactivate, assign roles, and reset credentials. | All 4 operations succeed; deactivated accounts blocked; all changes logged in audit trail. | 5 | Critical | Gaurav | AI-Added | APR-81 |
| UX-08 ★ | Task | Design login screen and admin panel (S-01, S-09) | Design wireframes and hi-fi specs for Login/SSO Entry S-01 and Admin Panel S-09. | Figma wireframes + hi-fi mockup for SSO, MFA challenge, session timeout modal, user management table. | 8 | Critical | Vivek | AI-Added | APR-82 |
| TK-10 ★ | Task | Backend — SSO, RBAC, MFA, session management, user admin API | Implement SAML 2.0 / OAuth 2.0 SSO, RBAC, MFA enforcement, session expiry, and user admin API. | SSO tested; RBAC enforced at API layer; MFA tested; session expiry tested; all changes logged. | 13 | Critical | Rupa | AI-Added | APR-83 |
| QA-08 ★ | Task | Test authentication, RBAC, MFA, and session management (US-042 to US-046) | Validate all Authentication & Access Control stories including penetration testing. | All ACs pass; RBAC bypass attempts blocked; MFA verified; session expiry tested; pen test passes; no P1/P2 defects. | 8 | Critical | Apra | AI-Added | APR-84 |

---

## Complete Issue Index

| JIRA Key | Issue Key | Type | Epic | Summary | SP | Priority | Assignee | Source |
|---|---|---|---|---|---|---|---|---|
| APR-5 | EP-01 | Epic | EP-01 | Advisor Dashboard | 0 | Critical | Vrushali | Source Docs |
| APR-13 | US-001 | Story | EP-01 | View all assigned client portfolios on dashboard | 5 | Critical | Gaurav | Source Docs |
| APR-14 | US-002 | Story | EP-01 | Colour-coded portfolio drift indicators | 3 | High | Gaurav | Source Docs |
| APR-15 | US-003 | Story | EP-01 | Sort and filter advisor dashboard | 3 | High | Gaurav | Source Docs |
| APR-16 | US-004 | Story | EP-01 | Proposal status badge per client on dashboard | 2 | High | Gaurav | Source Docs |
| APR-17 | US-005 | Story | EP-01 | Manual refresh and last-updated timestamp | 2 | Medium | Gaurav | AI-Added |
| APR-18 | UX-01 | Task | EP-01 | UX — Design advisor dashboard wireframes | 5 | Critical | Vivek | Source Docs |
| APR-19 | TK-01 | Task | EP-01 | Backend — Portfolio drift calculation API | 5 | Critical | Rupa | Source Docs |
| APR-20 | TK-02 | Task | EP-01 | Frontend — Dashboard table component with filters | 5 | Critical | Rupa | Source Docs |
| APR-21 | QA-01 | Task | EP-01 | QA — Test advisor dashboard | 5 | High | Apra | Source Docs |
| APR-6 | EP-02 | Epic | EP-02 | Portfolio Detail View | 0 | Critical | Vrushali | Source Docs |
| APR-22 | US-006 | Story | EP-02 | View all client holdings in portfolio detail | 5 | Critical | Gaurav | Source Docs |
| APR-23 | US-007 | Story | EP-02 | Current vs target allocation chart | 3 | High | Gaurav | Source Docs |
| APR-24 | US-008 | Story | EP-02 | Display client risk profile and investment goals | 2 | High | Gaurav | Source Docs |
| APR-25 | US-009 | Story | EP-02 | Proposal version history on portfolio detail page | 3 | Medium | Gaurav | AI-Added |
| APR-26 | US-010 | Story | EP-02 | Holdings CSV and Excel export | 2 | Medium | Gaurav | AI-Added |
| APR-27 | UX-02 | Task | EP-02 | UX — Design portfolio detail view wireframes | 5 | Critical | Vivek | Source Docs |
| APR-28 | TK-03 | Task | EP-02 | Frontend — Allocation chart and portfolio detail page | 5 | High | Rupa | Source Docs |
| APR-29 | QA-02 | Task | EP-02 | QA — Test portfolio detail view | 5 | High | Apra | Source Docs |
| APR-7 | EP-03 | Epic | EP-03 | Rebalancing Proposal | 0 | Critical | Vrushali | Source Docs |
| APR-30 | US-011 | Story | EP-03 | Initiate a new rebalancing proposal | 3 | Critical | Gaurav | Source Docs |
| APR-31 | US-012 | Story | EP-03 | Adjust allocations with real-time 100% validation | 5 | Critical | Gaurav | Source Docs |
| APR-32 | US-013 | Story | EP-03 | Pre/post allocation comparison panel | 3 | High | Gaurav | Source Docs |
| APR-33 | US-014 | Story | EP-03 | Proposal auto-save with last-saved timestamp | 3 | High | Gaurav | AI-Added |
| APR-34 | US-015 | Story | EP-03 | Immutable proposal version history | 5 | Critical | Gaurav | Source Docs |
| APR-35 | US-016 | Story | EP-03 | Add free-text notes to proposal | 2 | High | Gaurav | Source Docs |
| APR-36 | US-017 | Story | EP-03 | Attach supporting PDF documents to proposal | 3 | Medium | Gaurav | AI-Added |
| APR-37 | US-018 | Story | EP-03 | Discard a draft proposal with confirmation | 2 | Medium | Gaurav | Source Docs |
| APR-38 | UX-03 | Task | EP-03 | UX — Design proposal editor and suitability modal | 8 | Critical | Vivek | Source Docs |
| APR-39 | TK-04 | Task | EP-03 | Backend — Proposal CRUD API with versioning | 8 | Critical | Rupa | Source Docs |
| APR-40 | TK-05 | Task | EP-03 | Frontend — Proposal editor UI | 8 | Critical | Rupa | Source Docs |
| APR-41 | QA-03 | Task | EP-03 | QA — Test rebalancing proposal workflow | 8 | Critical | Apra | Source Docs |
| APR-8 | EP-04 | Epic | EP-04 | Suitability Validation Engine | 0 | Critical | Vrushali | Source Docs |
| APR-42 | US-019 | Story | EP-04 | Auto-trigger suitability validation on submission | 3 | Critical | Gaurav | Source Docs |
| APR-43 | US-020 | Story | EP-04 | Risk profile evaluation with configured rules | 8 | Critical | Gaurav | Source Docs |
| APR-44 | US-021 | Story | EP-04 | Structured suitability validation report display | 5 | Critical | Gaurav | Source Docs |
| APR-45 | US-022 | Story | EP-04 | Hard stop for critical suitability violations | 5 | Critical | Gaurav | AI-Added |
| APR-46 | US-023 | Story | EP-04 | Warning acknowledgement flow | 3 | High | Gaurav | AI-Added |
| APR-47 | US-024 | Story | EP-04 | Admin panel for suitability rule configuration | 5 | High | Gaurav | AI-Added |
| APR-48 | UX-04 | Task | EP-04 | UX — Design suitability rule administration panel | 5 | High | Vivek | AI-Added |
| APR-49 | TK-06 | Task | EP-04 | Backend — Suitability validation engine service | 13 | Critical | Rupa | Source Docs |
| APR-50 | QA-04 | Task | EP-04 | QA — Test suitability validation engine | 8 | Critical | Apra | Source Docs |
| APR-9 | EP-05 | Epic | EP-05 | Approval Workflow | 0 | Critical | Vrushali | Source Docs |
| APR-51 | US-025 | Story | EP-05 | Multi-stage proposal workflow state machine | 5 | Critical | Gaurav | Source Docs |
| APR-52 | US-026 | Story | EP-05 | Compliance notification on proposal submission | 3 | High | Gaurav | AI-Added |
| APR-53 | US-027 | Story | EP-05 | Approve / reject with mandatory comment | 3 | Critical | Gaurav | Source Docs |
| APR-54 | US-028 | Story | EP-05 | Advisor notification on approval / rejection | 3 | High | Gaurav | AI-Added |
| APR-55 | US-029 | Story | EP-05 | Revision and resubmission after rejection | 3 | High | Gaurav | Source Docs |
| APR-56 | US-030 | Story | EP-05 | SLA escalation after 5 business days in review | 5 | High | Gaurav | AI-Added |
| APR-57 | US-031 | Story | EP-05 | Compliance officer approval delegation | 5 | Medium | Gaurav | AI-Added |
| APR-58 | UX-05 | Task | EP-05 | UX — Design compliance review screen and delegation UI | 8 | Critical | Vivek | Source Docs |
| APR-59 | TK-07 | Task | EP-05 | Backend — Workflow state machine, notifications, SLA escalation | 13 | Critical | Rupa | Source Docs |
| APR-60 | QA-05 | Task | EP-05 | QA — Test approval workflow and notifications | 8 | Critical | Apra | Source Docs |
| APR-10 | EP-06 | Epic | EP-06 | Audit Trail & Reporting | 0 | Critical | Vrushali | Source Docs |
| APR-61 | US-032 | Story | EP-06 | Automatic logging of all auditable actions | 5 | Critical | Gaurav | Source Docs |
| APR-62 | US-033 | Story | EP-06 | Extended log fields including IP and session ID | 3 | High | Gaurav | AI-Added |
| APR-63 | US-034 | Story | EP-06 | Immutable read-only audit trail | 3 | Critical | Gaurav | Source Docs |
| APR-64 | US-035 | Story | EP-06 | 7-year audit log data retention policy | 3 | Critical | Gaurav | AI-Added |
| APR-65 | US-036 | Story | EP-06 | Audit log search, filter, and CSV export | 5 | High | Gaurav | AI-Added |
| APR-66 | UX-06 | Task | EP-06 | UX — Design audit trail viewer UI spec | 5 | High | Vivek | AI-Added |
| APR-67 | TK-08 | Task | EP-06 | Backend — Append-only audit log service | 8 | Critical | Rupa | Source Docs |
| APR-68 | QA-06 | Task | EP-06 | QA — Test audit trail completeness and immutability | 8 | Critical | Apra | Source Docs |
| APR-11 | EP-07 | Epic | EP-07 | AI Summary Generation | 0 | High | Vrushali | Source Docs |
| APR-69 | US-037 | Story | EP-07 | Generate plain-language AI client summary | 5 | High | Gaurav | Source Docs |
| APR-70 | US-038 | Story | EP-07 | AI summary references client goals and horizon | 3 | High | Gaurav | Source Docs |
| APR-71 | US-039 | Story | EP-07 | Advisor edit and save AI summary | 3 | High | Gaurav | AI-Added |
| APR-72 | US-040 | Story | EP-07 | Export AI summary as branded PDF | 3 | Medium | Gaurav | AI-Added |
| APR-73 | US-041 | Story | EP-07 | 30-second SLA for AI summary generation | 2 | Medium | Gaurav | AI-Added |
| APR-74 | UX-07 | Task | EP-07 | UX — Design AI summary editor UI spec | 5 | High | Vivek | AI-Added |
| APR-75 | TK-09 | Task | EP-07 | Backend — LLM integration for AI summary generation | 8 | High | Rupa | Source Docs |
| APR-76 | QA-07 | Task | EP-07 | QA — Test AI summary generation and PDF export | 5 | High | Apra | Source Docs |
| APR-12 | EP-08 | Epic | EP-08 | Authentication & Access Control | 0 | Critical | Vrushali | AI-Added |
| APR-77 | US-042 | Story | EP-08 | SSO authentication via SAML 2.0 / OAuth 2.0 | 5 | Critical | Gaurav | AI-Added |
| APR-78 | US-043 | Story | EP-08 | RBAC with four roles and distinct permission sets | 5 | Critical | Gaurav | AI-Added |
| APR-79 | US-044 | Story | EP-08 | Session timeout with 2-minute warning modal | 3 | High | Gaurav | AI-Added |
| APR-80 | US-045 | Story | EP-08 | MFA for Compliance Officer and Admin roles | 3 | Critical | Gaurav | AI-Added |
| APR-81 | US-046 | Story | EP-08 | Admin user management panel | 5 | Critical | Gaurav | AI-Added |
| APR-82 | UX-08 | Task | EP-08 | UX — Design login screen and admin panel | 8 | Critical | Vivek | AI-Added |
| APR-83 | TK-10 | Task | EP-08 | Backend — SSO, RBAC, MFA, session management, user admin API | 13 | Critical | Rupa | AI-Added |
| APR-84 | QA-08 | Task | EP-08 | QA — Test authentication, RBAC, MFA, and session management | 8 | Critical | Apra | AI-Added |
