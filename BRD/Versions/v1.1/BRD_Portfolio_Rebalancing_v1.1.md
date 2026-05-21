# Business Requirements Document
## Advisor Portfolio Rebalancing & Suitability Review Platform

| Field | Value |
|---|---|
| **Document Type** | Business Requirements Document (BRD) |
| **Project** | Advisor Portfolio Rebalancing & Suitability Review Platform |
| **Version** | 1.1 |
| **Status** | Approved |
| **Date** | 21 May 2026 |
| **Classification** | Confidential — Internal Use Only |
| **Document Owner** | Product Manager – Wealth Advisory |
| **Business Sponsor** | Head of Wealth Advisory |

---

## Table of Contents

1. Executive Summary
2. Business Context & Problem Statement
3. Objectives & Success Metrics
4. Stakeholders & RACI Matrix
5. Scope
6. User Roles & Personas
7. End-to-End User Journey
8. Functional Requirements
9. Non-Functional Requirements
10. Data Requirements
11. Integration Requirements
12. UX / UI Requirements
13. Risks & Mitigation
14. Open Questions & Deferred Decisions
15. Requirements Traceability Matrix
16. Glossary
17. Document Sign-Off

> **★ AI-Added Requirements:** Requirements and sections marked ★ AI-Added were not present in the source documents and have been inferred to ensure completeness, deliverability, and production readiness. These must be reviewed and formally accepted or rejected before baseline sign-off.

---

## 1. Executive Summary

Wealth management firms face growing pressure to modernize manual, error-prone portfolio rebalancing processes. This BRD defines the end-to-end functional, non-functional, and compliance requirements for a web-based Advisor Portfolio Rebalancing & Suitability Review Platform.

The Platform will digitise and automate the rebalancing lifecycle — from portfolio drift detection through proposal authoring, suitability validation, multi-stage compliance approval, client summary generation, and full audit trail.

**Key targets:** 30–40% advisor productivity improvement · 40–50% compliance effort reduction · 6 core epics · 49 functional requirements.

---

## 2. Business Context & Problem Statement

### 2.1 Current State

Wealth advisors currently manage portfolio rebalancing through spreadsheets, email chains, and disconnected compliance checklists.

| Problem Area | Description |
|---|---|
| Process Inefficiency | Manual workflows create 3–5 day delays per proposal, errors, and rework |
| Compliance Risk | Suitability validation is ad-hoc; violations may go undetected |
| Audit Deficiency | No centralised, immutable audit trail |
| Collaboration Gaps | Email-based proposal exchange with no version control |
| Advisor Capacity | Admin tasks limit number of clients each advisor can manage |

### 2.2 Desired Future State

A centralised web platform enabling advisors to view portfolio drift, create structured rebalancing proposals, obtain automated suitability validation, route proposals through a governed approval workflow, and generate compliant client summaries — all with a comprehensive audit trail.

---

## 3. Objectives & Success Metrics

### 3.1 Strategic Objectives

- OBJ-1: Streamline the end-to-end rebalancing workflow within a single digital platform
- OBJ-2: Automate suitability validation to embed compliance-by-design
- OBJ-3: Improve advisor productivity by 30–40%
- OBJ-4: Reduce compliance review effort by 40–50%
- OBJ-5: Establish a centralised, immutable audit trail
- OBJ-6: Enable AI-assisted client communication summaries

### 3.2 Success Metrics

| Metric | Current State | Target (6 months post-launch) | Measurement |
|---|---|---|---|
| Proposal creation time | 3–5 business days | < 1 business day | Platform analytics |
| Compliance review cycles | 2–3 iterations avg | ≤ 1 iteration | Avg revision count |
| Suitability violation escape rate | Not measured | 0% critical violations | Audit log analysis |
| Audit trail completeness | 0% | 100% actions logged | Coverage report |
| Compliance effort per proposal | Baseline TBD | −40–50% hours | Time tracking |

---

## 4. Stakeholders & RACI Matrix

| Role | Stakeholder | R | A | C/I |
|---|---|---|---|---|
| Head of Wealth Advisory | Business Sponsor | – | A | C |
| Senior Financial Advisor | Primary end-user rep | R | – | C |
| Compliance Officer | Regulatory gatekeeper | R | A | C |
| Product Manager | Requirements owner | R | A | – |
| Operations Lead | Process & ops alignment | R | – | C |
| Technology Lead | Architecture & delivery | R | – | C |
| Financial Advisor | Day-to-day user | R | – | I |
| Operations Team | Support & data ops | R | – | I |

R = Responsible · A = Accountable · C = Consulted · I = Informed

---

## 5. Scope

### 5.1 In Scope (MVP)

| Epic | Name | Description |
|---|---|---|
| EP-01 | Advisor Dashboard | Portfolio summary with drift indicators, filters, proposal status |
| EP-02 | Portfolio Detail View | Client-level holdings, allocation chart, profile, proposal history |
| EP-03 | Rebalancing Proposal | Create, edit, version, and submit proposals with real-time validation |
| EP-04 | Suitability Validation Engine | Rules-driven suitability checking on submission |
| EP-05 | Approval Workflow | Draft → Compliance Review → Approved/Rejected with notifications |
| EP-06 | Audit Trail & Reporting | Immutable, searchable action log with export |
| EP-07 | AI Summary Generation | AI-assisted plain-language client summary with PDF export |
| EP-08 ★ | Authentication & Access Control | SSO, RBAC, MFA, session management |

### 5.2 Out of Scope

- Real-time market data integration
- Trade execution or order management
- Client self-service portal
- Mobile native application (iOS / Android)
- Integration with external CRM systems (Phase 2) ★
- Regulatory filing to external bodies ★

---

## 6. User Roles & Personas

| Role | Primary Goals | Pain Points | Permissions |
|---|---|---|---|
| Financial Advisor | Create proposals; view drift; generate summaries | Manual data; no real-time drift; approval chasing | Create/edit proposals; own clients; AI summaries |
| Compliance Officer | Review/approve proposals; configure rules; audit trail | Inconsistent formats; no pre-validation | Approve/reject; rule config; full audit access |
| Operations Team | Monitor pipeline; assist advisors | No proposal visibility; no escalation mechanism | View all proposals; manage users; audit trail |
| System Admin ★ | Manage users, roles, SSO | Manual user provisioning | Full admin; user management; system config |

---

## 7. End-to-End User Journey

| Step | Actor | Action / System Response | State | FR Ref |
|---|---|---|---|---|
| 1 | Financial Advisor | Logs in via SSO; system loads role-based dashboard | Authenticated | FR-044, FR-045 |
| 2 | Financial Advisor | Views dashboard with drift indicators and proposal status | Dashboard | FR-001–FR-005 |
| 3 | Financial Advisor | Selects client; views portfolio detail | Portfolio Detail | FR-006–FR-010 |
| 4 | Financial Advisor | Initiates new proposal; system creates DRAFT with unique ID | Draft | FR-011–FR-016 |
| 5 | Financial Advisor | Adjusts allocations; system validates 100% sum in real time | Draft | FR-013–FR-014 |
| 6 | Financial Advisor | Adds notes and attachments; system auto-saves every 2 minutes | Draft | FR-015, FR-018–FR-019 |
| 7 | Financial Advisor | Submits proposal; suitability validation triggered | Validating | FR-022–FR-026 |
| 8 | System | Validation passes; proposal advances to Compliance Review | Compliance Review | FR-024–FR-026 |
| 9 | System | Compliance Officer notified via in-app alert and email | Compliance Review | FR-028 |
| 10 | Compliance Officer | Reviews and approves or rejects with mandatory comment | Compliance Review | FR-029 |
| 11 | System | Decision recorded; audit log updated; advisor notified | Approved/Rejected | FR-030, FR-039–FR-041 |
| 12 | Financial Advisor | Generates AI summary; edits and exports as PDF | Summary | FR-034–FR-038 |

---

## 8. Functional Requirements

All requirements are atomic, uniquely identified, and testable. Requirements marked ★ AI-Added were inferred to ensure completeness.

### EP-01 · Advisor Dashboard

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-001 | The system shall display a portfolio summary dashboard listing all assigned clients with: client name, risk profile, current vs target allocation %, drift %, and last review date. | Dashboard loads ≤3s; all assigned clients visible with all 5 required fields. | Source Docs |
| FR-002 | The dashboard shall display colour-coded drift indicators: Green ≤5%, Amber 5–10%, Red >10%. | Indicator colours match thresholds; legend visible on page. | Source Docs |
| FR-003 | The dashboard shall support column sorting and filtering by: client name, risk profile, drift band, and last review date range. | All filter/sort combinations work; results update <1s without full reload. | Source Docs |
| FR-004 | The dashboard shall display the current proposal status per client: Draft / In Review / Approved / Rejected / None. | Status badge reflects latest state on page load; no stale data. | Source Docs |
| FR-005 ★ | The dashboard shall refresh drift data on page load and support a manual refresh button with a last-updated timestamp. | Refresh button present; timestamp updates on each refresh; no stale data beyond 24h. | AI-Added |

### EP-02 · Portfolio Detail View

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-006 | The portfolio detail view shall display all holdings: asset class, security name, ticker, quantity, current market value, current allocation %, and target allocation %. | All 7 fields rendered per holding; page loads ≤3s. | Source Docs |
| FR-007 | The portfolio detail view shall include a visual chart (bar or donut) comparing current vs target allocation per asset class. | Chart renders both allocations; ARIA accessible; readable at 1280×800. | Source Docs |
| FR-008 | The system shall display the client's risk profile, investment goals, and investment horizon on the portfolio detail page. | All 3 fields visible without additional navigation. | Source Docs |
| FR-009 ★ | The portfolio detail view shall display a version history list of all prior proposals: ID, created date, status, advisor name. | All proposals listed; clicking ID navigates to read-only view; paginated at 20+. | AI-Added |
| FR-010 ★ | The system shall allow download of current holdings as CSV or Excel from the portfolio detail view. | Download button present; file contains all fields; triggers without page navigation. | AI-Added |

### EP-03 · Rebalancing Proposal

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-011 | The system shall allow an advisor to initiate a new proposal from the dashboard or portfolio detail view. | New proposal accessible from both locations; created in Draft state. | Source Docs |
| FR-012 | The proposal editor shall allow adjustment of target allocation percentages per asset class. | Input fields and sliders synchronised in real time. | Source Docs |
| FR-013 | The system shall validate in real time that total allocations equal exactly 100%; submit shall be disabled otherwise. | Submit disabled and inline error shown when total ≠ 100%; clears when = 100%. | Source Docs |
| FR-014 | The system shall display a side-by-side comparison of current vs proposed allocation with delta and estimated value change. | Comparison panel updates within 500ms of any allocation change. | Source Docs |
| FR-015 ★ | The system shall auto-save the proposal every 2 minutes; a last-saved timestamp shall be visible. | Auto-save every 2 min without user action; no data lost on tab close. | AI-Added |
| FR-016 ★ | Each proposal shall be assigned a unique ID in format PROP-YYYYMMDD-NNNN. | ID displayed in header; no duplicates; format matches pattern. | AI-Added |
| FR-017 | The system shall maintain immutable version snapshots; every save or status transition creates a new version. | Version number increments on each save; prior versions accessible read-only. | Source Docs |
| FR-018 | The advisor shall be able to add free-text notes (up to 2,000 characters) to a proposal. | Notes field with live character count; saved with each proposal version. | Source Docs |
| FR-019 ★ | The advisor shall be able to attach up to 5 PDF files (max 10 MB each) to a proposal. | PDF type, 10 MB, and 5-file limits enforced; files listed with name and size. | AI-Added |
| FR-020 | The advisor shall be able to discard a Draft proposal with a confirmation prompt. | Confirmation dialog required; discard logged in audit trail. | Source Docs |

### EP-04 · Suitability Validation Engine

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-021 | The system shall automatically trigger suitability validation on proposal submission. | Validation triggers on submission; progress indicator shown; completes ≤5s P95. | Source Docs |
| FR-022 | The engine shall evaluate proposals against configured risk profile rules (Conservative / Moderate / Aggressive). | Validates correctly for all 3 profiles; hard-rule violations always produce Critical. | Source Docs |
| FR-023 | The system shall return a structured validation report: overall result, violation list with rule ID, severity, and description. | All violated rules listed; no violation omitted from report. | Source Docs |
| FR-024 ★ | The system shall block submission when any Critical violation is present. | Submit blocked; error lists each critical violation; must be resolved to proceed. | AI-Added |
| FR-025 ★ | The system shall allow submission with Warnings after the advisor explicitly acknowledges each warning via checkbox. | Warning modal shown; submit only after all checkboxes checked; logged in audit trail. | AI-Added |
| FR-026 ★ | A Compliance Officer or Admin shall be able to create, edit, enable, and disable suitability rules via an admin panel. | Rule changes effective on next submission; all modifications logged in audit trail. | AI-Added |

### EP-05 · Approval Workflow

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-027 | The system shall enforce a multi-stage workflow: Draft → Submitted → Compliance Review → Approved / Rejected. | Transitions only in defined sequence; all transitions atomic and logged. | Source Docs |
| FR-028 ★ | The system shall send in-app and email notifications to Compliance Officers when a proposal reaches review. | In-app ≤30s; email ≤5min; includes proposal ID, client name, direct link. | AI-Added |
| FR-029 | A Compliance Officer shall be able to approve or reject a proposal; rejection requires a mandatory comment (min 10 chars). | Reject blocked if comment < 10 chars; actions update state immediately. | Source Docs |
| FR-030 ★ | The system shall notify the originating advisor via in-app and email when a proposal is approved or rejected. | In-app ≤30s; email ≤5min; includes compliance officer's comment. | AI-Added |
| FR-031 | A rejected proposal shall return to Draft state and be editable and resubmittable by the advisor. | Rejected proposal = Draft; advisor can edit and resubmit; creates new version. | Source Docs |
| FR-032 ★ | The system shall auto-escalate a proposal to Operations Lead if it remains in Compliance Review for more than 5 business days. | Escalation fires at exactly 5-business-day mark (excl. weekends/holidays); event logged. | AI-Added |
| FR-033 ★ | A Compliance Officer shall be able to delegate approval authority for a specified period. | Delegation set with start/end date; delegated approvals show both officers in audit trail. | AI-Added |

### EP-06 · Audit Trail & Reporting

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-039 | The system shall automatically log all user and system actions including: login/logout, proposal CRUD, approval/rejection, rule changes. | All event types produce a log entry; no auditable action omitted. | Source Docs |
| FR-040 ★ | Each audit log entry shall capture: UTC timestamp, user ID, role, action type, entity type, entity ID, previous state, new state, source IP, session ID. | All 10 fields present on every entry; spot-check of 10 random entries confirms. | AI-Added |
| FR-041 | The audit trail shall be read-only; no user including Admins may modify or delete entries. | No edit/delete control in UI; direct DB delete blocked at application layer. | Source Docs |
| FR-042 ★ | Audit logs shall be retained for a minimum of 7 years. | Retention policy configured; no premature deletion. | AI-Added |
| FR-043 ★ | Compliance Officers and Admins shall be able to search audit logs by date range, user, action type, proposal ID, client ID and export as CSV. | All 5 filter dimensions work; CSV export ≤10s for 10,000 records. | AI-Added |

### EP-07 · AI Summary Generation

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-034 | The system shall generate an AI-assisted plain-language client summary for approved proposals. | Summary generated on demand; output in plain English with no jargon. | Source Docs |
| FR-035 | The AI summary shall reference the client's investment goals, time horizon, or risk profile. | Summary explicitly references at least one of the three. | Source Docs |
| FR-036 ★ | The advisor shall be able to edit the AI-generated summary; original AI output shall be preserved. | Editable rich-text field; save creates versioned snapshot; original preserved read-only. | AI-Added |
| FR-037 ★ | The finalised summary shall be exportable as a branded PDF with firm logo, advisor name, client name, and proposal ID. | PDF contains all 4 required fields; readable at A4/Letter. | AI-Added |
| FR-038 ★ | AI summary generation shall complete within 30 seconds P95; a progress indicator shall be shown throughout. | Generation ≤30s P95; spinner visible; timeout error shown if exceeded. | AI-Added |

### EP-08 · Authentication & Access Control ★ AI-Added

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-044 ★ | The system shall support SSO via SAML 2.0 or OAuth 2.0 / OIDC integrating with the firm's IdP. | Successful SSO login via IdP; failed auth blocks access. | AI-Added |
| FR-045 ★ | The system shall enforce RBAC with four roles: Financial Advisor, Compliance Officer, Operations, System Admin. | Each role accesses only permitted features; cross-role attempts return HTTP 403. | AI-Added |
| FR-046 ★ | Sessions shall expire after 30 minutes of inactivity; a 2-minute warning modal shall be shown before expiry. | Session expires at 30-min mark; warning modal at 28 min; user can extend. | AI-Added |
| FR-047 ★ | MFA shall be enforced for all Compliance Officer and System Admin accounts. | Login without MFA for these roles is blocked; MFA challenge shown after primary auth. | AI-Added |
| FR-048 ★ | A System Admin shall be able to create, deactivate, assign roles to, and reset credentials for users. | All 4 operations succeed; deactivated accounts cannot log in; changes logged. | AI-Added |

---

## 9. Non-Functional Requirements

| NFR ID | Category | Requirement | Measurable Target | Source |
|---|---|---|---|---|
| NFR-001 | Performance | Dashboard and Portfolio Detail page load time | P95 ≤3s under 100 concurrent users | Source Docs |
| NFR-002 | Performance | Suitability validation response time | P95 ≤5s end-to-end | Source Docs |
| NFR-003 ★ | Performance | Non-AI REST API response time | P95 ≤500ms | AI-Added |
| NFR-004 | Availability | Platform uptime during business hours (08:00–20:00 Mon–Fri) | ≥99.5% over any rolling 30 days | Source Docs |
| NFR-005 ★ | Scalability | Concurrent authenticated users without degradation | 500 concurrent users; NFR-001–003 thresholds maintained | AI-Added |
| NFR-006 | Security | Data in transit encryption | TLS 1.2+; SSL Labs A or A+ rating | Source Docs |
| NFR-007 ★ | Security | Data at rest encryption | AES-256; no plaintext PII stored | AI-Added |
| NFR-008 ★ | Accessibility | UI accessibility standard | WCAG 2.1 Level AA; zero critical violations on axe scan | AI-Added |
| NFR-009 ★ | Browser Compatibility | Supported browsers | Latest 2 stable releases: Chrome, Firefox, Edge, Safari | AI-Added |
| NFR-010 ★ | Responsiveness | Minimum supported viewport | Fully functional at 768px width (tablet) | AI-Added |
| NFR-011 ★ | Data Retention | Audit log and proposal data retention | Audit: 7 years · Proposals: 5 years | AI-Added |
| NFR-012 | Role-Based Access | Cross-role access enforcement | HTTP 403 on all cross-role attempts; denials logged | Source Docs |
| NFR-013 ★ | Localisation | Timestamp display | UTC + user local timezone shown on all timestamps | AI-Added |
| NFR-014 ★ | Error Handling | User-facing error messages | No raw stack traces or HTTP codes shown to non-Admin users | AI-Added |

---

## 10. Data Requirements

### 10.1 Core Data Entities

| Entity | Key Attributes | Notes |
|---|---|---|
| Client Profile | client_id, full_name, risk_profile (Enum), investment_goals, time_horizon, assigned_advisor_id | Source: mock data MVP; CRM Phase 2 |
| Portfolio Holdings | holding_id, client_id, asset_class, ticker, quantity, current_value, current_allocation_pct, target_allocation_pct | Drift = \|current − target\| |
| Rebalancing Proposal | proposal_id (PROP-YYYYMMDD-NNNN), client_id, advisor_id, status, version, created_at, notes, suitability_result | Immutable after Approved |
| Proposal Version | version_id, proposal_id, version_number, allocations_snapshot (JSON), saved_by, saved_at | Created on every save |
| Suitability Validation Report | report_id, proposal_id, version_id, run_at, overall_result, violations (JSON) | [{rule_id, severity, description}] |
| Compliance Rule | rule_id, rule_name, risk_profile_target, threshold_pct, severity (Critical/Warning), is_active | Configurable by Compliance Officer |
| Audit Log Entry | log_id, timestamp_utc, user_id, role, action_type, entity_type, entity_id, prev_state, new_state, source_ip, session_id | Append-only; no update/delete |
| User Account ★ | user_id, full_name, email, role, is_active, sso_provider_id, mfa_enabled, created_at, last_login_at | Managed by System Admin |

### 10.2 Data Validation Rules

- All monetary values: 64-bit float, 2 decimal places precision
- Allocation percentages: max 2 decimal places; total must equal 100.00%
- Proposal IDs: unique system-wide; enforced at database layer ★
- Risk profile enum: [Conservative, Moderate, Aggressive, Custom] ★
- Email addresses: validated against RFC 5322 format before storage ★

---

## 11. Integration Requirements ★ AI-Added

| ID | Integration Point | Description | Protocol |
|---|---|---|---|
| INT-001 ★ | Identity Provider (SSO) | Authenticate via firm's IdP | SAML 2.0 / OAuth 2.0 + OIDC |
| INT-002 ★ | Email Notification Service | Dispatch workflow notifications | SMTP / REST (SendGrid or AWS SES) |
| INT-003 ★ | AI / LLM Service | Generate client summaries | HTTPS REST (Anthropic API or Azure OpenAI) |
| INT-004 ★ | Document Storage | Store PDF attachments securely | AWS S3 / Azure Blob with SSE-S3 |
| INT-005 ★ | Mock Data Seed (MVP only) | Load mock data at environment startup | Internal seed script |

---

## 12. UX / UI Requirements

### 12.1 Design Principles

- Clarity First: Information hierarchy guides advisors to the most critical action on each screen
- Status Transparency: Every proposal and portfolio displays its current state at all times
- Progressive Disclosure: Complex validation results summarised first; detail on demand
- Error Prevention: Real-time validation guides users away from invalid states ★

### 12.2 Key UI Screens

| Screen | Name | Key UI Elements |
|---|---|---|
| S-01 | Login / SSO Entry | SSO redirect button, firm logo, MFA challenge, error states |
| S-02 | Advisor Dashboard | Sortable/filterable client table, drift colour indicators, proposal status badges |
| S-03 | Portfolio Detail | Holdings table, allocation chart, client profile card, proposal history, CSV export |
| S-04 | Proposal Creator | Allocation editor (inputs + sliders), sum validator, comparison panel, notes, attachments, version sidebar |
| S-05 | Suitability Report Modal | Pass/fail banner, violation list with severity badges, warning acknowledgement checkboxes |
| S-06 | Compliance Review | Proposal summary, suitability report, comment thread, approve/reject panel |
| S-07 ★ | Audit Trail Viewer | Filterable log table (5 dimensions), CSV export button |
| S-08 ★ | AI Summary Editor | AI text in editable rich-text field, original AI toggle, PDF export, last-saved indicator |
| S-09 ★ | Admin Panel | User management table, role assignment, SSO config, suitability rule editor |

### 12.3 Navigation

- Primary nav: Dashboard · Proposals · Audit Trail (Compliance only) · Admin (Admin only)
- Breadcrumb: Dashboard > Client Name > Proposal ID
- All primary actions reachable within 3 clicks from dashboard ★

---

## 13. Risks & Mitigation

| ID | Risk | Probability | Impact | Mitigation |
|---|---|---|---|---|
| R-01 | Mock data doesn't reflect real portfolio complexity | Medium | High | Define representative mock data covering edge cases; compliance review before demo |
| R-02 | Simplified rules engine doesn't capture regulatory nuances | High | High | Document all simplification decisions; plan Phase 2 upgrade; get compliance sign-off |
| R-03 | AI summary quality inconsistent for edge-case portfolios | Medium | Medium | Define prompt engineering standards; track summary edit rate as quality KPI |
| R-04 ★ | SSO integration delays with firm's IdP block end-to-end testing | Medium | High | Implement local username/password fallback for non-production environments |
| R-05 ★ | Audit log volume exceeds storage projections at scale | Low | Medium | Size storage for 500 users × 200 actions/day × 365 × 7 years; archive logs > 1 year |
| R-06 ★ | Scope creep from stakeholders requesting real-time market data | High | Medium | Maintain firm out-of-scope list; formal change control post-baseline |

---

## 14. Open Questions & Deferred Decisions

| ID | Question | Options | Owner | Due |
|---|---|---|---|---|
| Q-01 | Which IdP for SSO: SAML 2.0 or OAuth 2.0/OIDC? | SAML 2.0 / OAuth 2.0 | Tech Lead | Sprint 1 |
| Q-02 | Which AI/LLM provider for summary generation? | Anthropic API / Azure OpenAI | Tech Lead | Sprint 1 |
| Q-03 | Exact set of compliance rules to seed for MVP? | TBD by Compliance Officer | Compliance Officer | Sprint 2 |
| Q-04 | Branding requirements for AI-generated PDF summary? | Firm standard template | Product Manager | Sprint 3 |
| Q-05 | Escalation notifications go to Operations Lead only or also Head of WA? | Operations Lead only / Both | Head of WA | Sprint 2 |
| Q-06 | Target cloud platform: AWS or Azure? | AWS / Azure | Tech Lead | Sprint 1 |

---

## 15. Requirements Traceability Matrix

| FR ID | Epic | JIRA User Story | UX Screen | Source |
|---|---|---|---|---|
| FR-001–FR-005 | EP-01 | As a Financial Advisor, I want to see all my assigned clients on a dashboard | S-02 Dashboard | Source Docs / AI-Added |
| FR-006–FR-010 | EP-02 | As a Financial Advisor, I want to see all holdings and client profile details | S-03 Portfolio Detail | Source Docs / AI-Added |
| FR-011–FR-020 | EP-03 | As a Financial Advisor, I want to create, edit, version, and submit proposals | S-04 Proposal Creator | Source Docs / AI-Added |
| FR-021–FR-026 | EP-04 | As a Compliance Officer, I want proposals auto-validated on submission | S-05 Suitability Modal | Source Docs / AI-Added |
| FR-027–FR-033 | EP-05 | As a Compliance Officer, I want a structured approval workflow with notifications | S-06 Compliance Review | Source Docs / AI-Added |
| FR-034–FR-038 | EP-07 | As a Financial Advisor, I want AI-generated client summaries | S-08 AI Summary Editor | Source Docs / AI-Added |
| FR-039–FR-043 | EP-06 | As a Compliance Officer, I want a searchable, exportable audit trail | S-07 Audit Trail Viewer | Source Docs / AI-Added |
| FR-044–FR-048 | EP-08 | As a System Admin, I want SSO, RBAC, MFA, and user management | S-01, S-09 Auth / Admin | AI-Added |

---

## 16. Glossary

| Term | Definition |
|---|---|
| BRD | Business Requirements Document |
| Drift | Deviation between current and target asset allocation, expressed as a percentage |
| Rebalancing | Adjusting portfolio holdings to restore target asset allocation |
| Suitability | Requirement that recommendations align with client risk profile, goals, and time horizon |
| RBAC | Role-Based Access Control |
| SSO | Single Sign-On |
| MFA | Multi-Factor Authentication |
| Audit Trail | Chronological, immutable record of all system events and user actions |
| MVP | Minimum Viable Product |
| TLS | Transport Layer Security |
| AES-256 | Advanced Encryption Standard with 256-bit key |
| WCAG 2.1 AA | Web Content Accessibility Guidelines v2.1 Level AA |
| IdP | Identity Provider |
| ADF | Atlassian Document Format |

---

## 17. Document Sign-Off

| Name | Role | Signature | Date |
|---|---|---|---|
| | Head of Wealth Advisory (Sponsor) | | |
| | Compliance Officer | | |
| | Product Manager | | |
| | Technology Lead | | |
| | Operations Lead | | |

---

### Version History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 20 May 2026 | Product Management | Initial draft |
| 1.1 | 21 May 2026 | Product Management | Added EP-08 (Auth & Access), notifications, SLA escalation, attachment support, extended NFRs, data entity model, integration requirements, UX screen inventory, RTM |
