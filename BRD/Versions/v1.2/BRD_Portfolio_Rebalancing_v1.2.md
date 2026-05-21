# Business Requirements Document
## Advisor Portfolio Rebalancing & Suitability Review Platform

| Field | Value |
|---|---|
| **Version** | 1.2 |
| **Status** | Approved |
| **Date** | 21 May 2026 |
| **Classification** | Confidential — Internal Use Only |
| **Document Owner** | Product Manager – Wealth Advisory |
| **Business Sponsor** | Head of Wealth Advisory |

> ★ Requirements marked **AI-Added** were inferred to ensure completeness and must be reviewed before sign-off.

---

## 1. Executive Summary

This BRD defines the end-to-end functional, non-functional, and compliance requirements for a web-based Advisor Portfolio Rebalancing & Suitability Review Platform. The Platform digitises the full rebalancing lifecycle — drift detection, proposal authoring, suitability validation, compliance approval, client summary generation, and audit trail.

**Targets:** 30–40% advisor productivity improvement · 40–50% compliance effort reduction · 8 epics · 49 FRs · 80 JIRA issues.

---

## 2. Business Context & Problem Statement

| Problem | Description |
|---|---|
| Process Inefficiency | Manual workflows: 3–5 day delays per proposal |
| Compliance Risk | Ad-hoc suitability checks; violations may go undetected |
| Audit Deficiency | No centralised, immutable audit trail |
| Collaboration Gaps | Email-based proposals with no version control |
| Advisor Capacity | Admin overhead limits client capacity |

---

## 3. Objectives & Success Metrics

| Metric | Current | Target |
|---|---|---|
| Proposal creation time | 3–5 days | < 1 business day |
| Compliance review cycles | 2–3 iterations | ≤ 1 iteration |
| Suitability escape rate | Not measured | 0% critical violations |
| Audit completeness | 0% | 100% actions logged |
| Compliance effort | Baseline TBD | −40–50% |

---

## 4. Stakeholders & RACI

| Role | R | A | C/I |
|---|---|---|---|
| Head of Wealth Advisory | – | A | C |
| Compliance Officer | R | A | C |
| Product Manager | R | A | – |
| Financial Advisor | R | – | I |
| Technology Lead | R | – | C |
| Operations Lead | R | – | C |

---

## 5. Scope — MVP Epics

| Epic | Name | Source |
|---|---|---|
| EP-01 | Advisor Dashboard | Source Docs |
| EP-02 | Portfolio Detail View | Source Docs |
| EP-03 | Rebalancing Proposal | Source Docs |
| EP-04 | Suitability Validation Engine | Source Docs |
| EP-05 | Approval Workflow | Source Docs |
| EP-06 | Audit Trail & Reporting | Source Docs |
| EP-07 | AI Summary Generation | Source Docs |
| EP-08 | Authentication & Access Control ★ | AI-Added |

---

## 6. Functional Requirements

### EP-01 · Advisor Dashboard

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-001 | Display dashboard with all assigned clients: name, risk profile, drift %, last review date, proposal status | Loads ≤3s; all fields visible | Source Docs |
| FR-002 | Colour-coded drift indicators: Green ≤5%, Amber 5–10%, Red >10% | Colours match thresholds; legend visible | Source Docs |
| FR-003 | Sort and filter by client name, risk profile, drift band, date range | All combinations work; updates <1s | Source Docs |
| FR-004 | Show current proposal status per client | Badge reflects latest state on load | Source Docs |
| FR-005 ★ | Manual refresh button with last-updated timestamp | Timestamp updates on refresh; no stale data >24h | AI-Added |

### EP-02 · Portfolio Detail View

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-006 | Display all holdings: asset class, ticker, quantity, value, current %, target % | All 7 fields rendered; loads ≤3s | Source Docs |
| FR-007 | Visual chart: current vs target allocation per asset class | ARIA accessible; readable at 1280×800 | Source Docs |
| FR-008 | Display client risk profile, goals, and horizon | All 3 visible without extra navigation | Source Docs |
| FR-009 ★ | Proposal history: ID, date, status, advisor name | All proposals listed; click → read-only view | AI-Added |
| FR-010 ★ | Download holdings as CSV or Excel | Triggers in-page; all fields included | AI-Added |

### EP-03 · Rebalancing Proposal

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-011 | Initiate proposal from dashboard or detail view | Draft created with unique PROP-YYYYMMDD-NNNN ID | Source Docs |
| FR-012 | Adjust target allocations per asset class | Inputs and sliders synchronised in real time | Source Docs |
| FR-013 | Validate total = 100% in real time; block submit otherwise | Submit disabled; inline error shown when ≠ 100% | Source Docs |
| FR-014 | Side-by-side current vs proposed with delta | Panel updates within 500ms | Source Docs |
| FR-015 ★ | Auto-save every 2 minutes with last-saved timestamp | No data lost on tab close | AI-Added |
| FR-016 ★ | Unique proposal ID: PROP-YYYYMMDD-NNNN | ID displayed; enforced unique at DB layer | AI-Added |
| FR-017 | Immutable version snapshot on every save/transition | Version increments; prior versions read-only | Source Docs |
| FR-018 | Free-text notes up to 2,000 characters | Live char count; saved with each version | Source Docs |
| FR-019 ★ | Attach up to 5 PDFs, max 10 MB each | Type, size, count limits enforced | AI-Added |
| FR-020 | Discard Draft with confirmation dialog | Confirmation required; logged in audit trail | Source Docs |

### EP-04 · Suitability Validation Engine

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-021 | Auto-trigger validation on submission | Triggers on submit; progress shown; ≤5s P95 | Source Docs |
| FR-022 | Evaluate against risk profile rules | Validates Conservative, Moderate, Aggressive | Source Docs |
| FR-023 | Return structured report: result, violations, severity, description | All violations listed; no omissions | Source Docs |
| FR-024 ★ | Block submission on Critical violations | Submit blocked; error lists all critical violations | AI-Added |
| FR-025 ★ | Allow submission with acknowledged Warnings only | All warning checkboxes checked required | AI-Added |
| FR-026 ★ | Admin panel for suitability rule configuration | Rule changes effective on next submission; logged | AI-Added |

### EP-05 · Approval Workflow

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-027 | Multi-stage workflow: Draft → Review → Approved/Rejected | Transitions only in defined sequence; all logged | Source Docs |
| FR-028 ★ | In-app and email notification to Compliance on submission | In-app ≤30s; email ≤5min | AI-Added |
| FR-029 | Approve or reject with mandatory comment (min 10 chars) | Reject blocked without comment | Source Docs |
| FR-030 ★ | Notify advisor on approval/rejection with comment | In-app ≤30s; includes compliance comment | AI-Added |
| FR-031 | Rejected proposal returns to Draft; resubmittable | Creates new version on resubmit | Source Docs |
| FR-032 ★ | Auto-escalate after 5 business days in Compliance Review | Fires at 5-business-day threshold; event logged | AI-Added |
| FR-033 ★ | Compliance officer delegation with start/end date | Both officers attributed in audit trail | AI-Added |

### EP-06 · Audit Trail & Reporting

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-039 | Log all user and system actions | All event types produce a log entry | Source Docs |
| FR-040 ★ | 10-field log entry: timestamp, user ID, role, action, entity type/ID, prev/new state, IP, session ID | All 10 fields on every entry | AI-Added |
| FR-041 | Read-only immutable audit trail | No edit/delete in UI or API for any role | Source Docs |
| FR-042 ★ | 7-year audit log retention | Retention policy enforced; no premature deletion | AI-Added |
| FR-043 ★ | Search by 5 dimensions; CSV export ≤10s for 10,000 records | All filter combinations work | AI-Added |

### EP-07 · AI Summary Generation

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-034 | Generate plain-language client summary | Plain English; no jargon or return projections | Source Docs |
| FR-035 | Reference client goals, horizon, or risk profile | At least one referenced | Source Docs |
| FR-036 ★ | Advisor editable; original AI output preserved read-only | Versioned snapshot on save | AI-Added |
| FR-037 ★ | Export as branded PDF: logo, advisor, client, proposal ID | All 4 fields present; A4/Letter format | AI-Added |
| FR-038 ★ | Generation ≤30s P95; progress indicator shown | Timeout error shown if exceeded | AI-Added |

### EP-08 · Authentication & Access Control ★

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-044 ★ | SSO via SAML 2.0 or OAuth 2.0 / OIDC | Successful SSO login; failed auth blocks access | AI-Added |
| FR-045 ★ | RBAC: 4 roles; cross-role attempts return HTTP 403 | All roles restricted to permitted features | AI-Added |
| FR-046 ★ | Session timeout at 30 min; 2-min warning modal | Warning at 28 min; user can extend | AI-Added |
| FR-047 ★ | MFA for Compliance Officer and Admin | Login blocked without MFA for these roles | AI-Added |
| FR-048 ★ | Admin: create, deactivate, assign roles, reset credentials | All 4 operations succeed; changes logged | AI-Added |

---

## 7. Non-Functional Requirements

| NFR | Category | Requirement | Target | Source |
|---|---|---|---|---|
| NFR-001 | Performance | Page load time | P95 ≤3s / 100 concurrent users | Source Docs |
| NFR-002 | Performance | Suitability validation | P95 ≤5s | Source Docs |
| NFR-003 ★ | Performance | Non-AI API response | P95 ≤500ms | AI-Added |
| NFR-004 | Availability | Uptime business hours | ≥99.5% rolling 30 days | Source Docs |
| NFR-005 ★ | Scalability | Concurrent users | 500 without degradation | AI-Added |
| NFR-006 | Security | Data in transit | TLS 1.2+; SSL Labs A/A+ | Source Docs |
| NFR-007 ★ | Security | Data at rest | AES-256 | AI-Added |
| NFR-008 ★ | Accessibility | WCAG standard | 2.1 Level AA; zero critical violations | AI-Added |
| NFR-009 ★ | Browser | Compatibility | Latest 2: Chrome, Firefox, Edge, Safari | AI-Added |
| NFR-010 ★ | Responsiveness | Minimum viewport | Functional at 768px | AI-Added |
| NFR-011 ★ | Data Retention | Audit / Proposals | 7 years / 5 years | AI-Added |
| NFR-012 | Role-Based Access | Cross-role enforcement | HTTP 403 on all cross-role attempts; denials logged | Source Docs |
| NFR-013 ★ | Localisation | Timestamps | UTC + local timezone on all timestamps | AI-Added |
| NFR-014 ★ | Error Handling | User-facing errors | No raw stack traces shown to non-Admin users | AI-Added |

---

## 8. Data Requirements

| Entity | Key Attributes |
|---|---|
| Client Profile | client_id, full_name, risk_profile, investment_goals, time_horizon, assigned_advisor_id |
| Portfolio Holdings | holding_id, client_id, asset_class, ticker, quantity, current_value, current_allocation_pct, target_allocation_pct |
| Rebalancing Proposal | proposal_id (PROP-YYYYMMDD-NNNN), client_id, advisor_id, status, version, created_at, notes |
| Proposal Version | version_id, proposal_id, version_number, allocations_snapshot (JSON), saved_by, saved_at |
| Suitability Report | report_id, proposal_id, run_at, overall_result, violations (JSON) |
| Compliance Rule | rule_id, risk_profile_target, threshold_pct, severity (Critical/Warning), is_active |
| Audit Log Entry | log_id, timestamp_utc, user_id, role, action_type, entity_id, prev_state, new_state, source_ip, session_id |
| User Account ★ | user_id, full_name, email, role, is_active, sso_provider_id, mfa_enabled |

---

## 9. Integration Requirements ★

| ID | Integration | Protocol |
|---|---|---|
| INT-001 | Identity Provider (SSO) | SAML 2.0 / OAuth 2.0 + OIDC |
| INT-002 | Email Notification Service | SMTP / REST (SendGrid or AWS SES) |
| INT-003 | AI / LLM Service | HTTPS REST (Anthropic API or Azure OpenAI) |
| INT-004 | Document Storage | AWS S3 / Azure Blob with SSE-S3 |
| INT-005 | Mock Data Seed (MVP) | Internal seed script |

---

## 10. UX Screens

| Screen | Name |
|---|---|
| S-01 | Login / SSO Entry |
| S-02 | Advisor Dashboard |
| S-03 | Portfolio Detail View |
| S-04 | Proposal Creator |
| S-05 | Suitability Report Modal |
| S-06 | Compliance Review |
| S-07 ★ | Audit Trail Viewer |
| S-08 ★ | AI Summary Editor |
| S-09 ★ | Admin Panel |

---

## 11. Requirements Traceability Matrix

| FR Range | Epic | JIRA Story | UX Screen |
|---|---|---|---|
| FR-001–005 | EP-01 | As an Advisor, I want a dashboard showing all assigned clients | S-02 |
| FR-006–010 | EP-02 | As an Advisor, I want full portfolio detail and history | S-03 |
| FR-011–020 | EP-03 | As an Advisor, I want to create, version, and submit proposals | S-04 |
| FR-021–026 | EP-04 | As Compliance, I want proposals auto-validated on submission | S-05 |
| FR-027–033 | EP-05 | As Compliance, I want a structured approval workflow | S-06 |
| FR-034–038 | EP-07 | As an Advisor, I want AI-generated client summaries | S-08 |
| FR-039–043 | EP-06 | As Compliance, I want a searchable, exportable audit trail | S-07 |
| FR-044–048 | EP-08 | As Admin, I want SSO, RBAC, MFA, and user management | S-01, S-09 |

---

## 12. Risks

| ID | Risk | Probability | Impact | Mitigation |
|---|---|---|---|---|
| R-01 | Mock data insufficient for edge-case testing | Medium | High | Define representative mock data set |
| R-02 | Simplified rules engine misses regulatory nuances | High | High | Compliance sign-off on rule set before go-live |
| R-03 | AI summary quality inconsistent | Medium | Medium | Prompt engineering standards; track edit rate |
| R-04 ★ | SSO IdP integration delays | Medium | High | Local auth fallback for non-production |
| R-05 ★ | Scope creep: real-time market data requests | High | Medium | Firm out-of-scope list; formal change control |

---

## 13. Version History

| Version | Date | Changes |
|---|---|---|
| 1.0 | 20 May 2026 | Initial draft |
| 1.1 | 21 May 2026 | Added EP-08, notifications, SLA escalation, NFRs, data model, integration reqs, UX inventory, RTM |
| 1.2 | 21 May 2026 | Full re-push via Atos-Github MCP following CLAUDE.md versioning rules |
