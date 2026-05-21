# Business Requirements Document
## Advisor Portfolio Rebalancing & Suitability Review Platform

| Field | Value |
|---|---|
| **Version** | 1.3 |
| **Status** | Approved |
| **Date** | 21 May 2026 |
| **Classification** | Confidential — Internal Use Only |
| **Document Owner** | Product Manager – Wealth Advisory |
| **Business Sponsor** | Head of Wealth Advisory |

> ★ Requirements marked **AI-Added** were inferred to ensure completeness and must be reviewed before sign-off.

---

## 1. Executive Summary

This BRD defines the end-to-end functional, non-functional, and compliance requirements for a web-based Advisor Portfolio Rebalancing & Suitability Review Platform. The Platform digitises the full rebalancing lifecycle — portfolio drift detection, proposal authoring, suitability validation, compliance approval, AI-assisted client summary generation, and full audit trail.

**Targets:** 30–40% advisor productivity improvement · 40–50% compliance effort reduction · 8 epics · 49 FRs · 14 NFRs · 80 JIRA issues.

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
| EP-08 ★ | Authentication & Access Control | AI-Added |

---

## 6. Functional Requirements

### EP-01 · Advisor Dashboard

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-001 | Display dashboard: client name, risk profile, drift %, last review date, proposal status | Loads ≤3s; all fields visible | Source Docs |
| FR-002 | Colour-coded drift: Green ≤5%, Amber 5–10%, Red >10% | Colours match thresholds; legend visible | Source Docs |
| FR-003 | Sort and filter: name, risk profile, drift band, date range | All combinations work; updates <1s | Source Docs |
| FR-004 | Show current proposal status per client | Badge reflects latest state | Source Docs |
| FR-005 ★ | Manual refresh with last-updated timestamp | Timestamp updates; no stale data >24h | AI-Added |

### EP-02 · Portfolio Detail View

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-006 | Display holdings: asset class, ticker, quantity, value, current %, target % | All 7 fields; loads ≤3s | Source Docs |
| FR-007 | Visual chart: current vs target allocation | ARIA accessible; 1280×800 | Source Docs |
| FR-008 | Client risk profile, goals, horizon | All 3 visible without extra navigation | Source Docs |
| FR-009 ★ | Proposal history: ID, date, status, advisor | All listed; click → read-only | AI-Added |
| FR-010 ★ | Download holdings as CSV or Excel | In-page; all fields included | AI-Added |

### EP-03 · Rebalancing Proposal

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-011 | Initiate from dashboard or detail view | Draft with PROP-YYYYMMDD-NNNN ID | Source Docs |
| FR-012 | Adjust target allocations per asset class | Inputs and sliders synchronised | Source Docs |
| FR-013 | Validate total = 100%; block submit otherwise | Submit disabled; inline error | Source Docs |
| FR-014 | Current vs proposed comparison with delta | Updates within 500ms | Source Docs |
| FR-015 ★ | Auto-save every 2 min; last-saved timestamp | No data lost on tab close | AI-Added |
| FR-016 ★ | Unique ID: PROP-YYYYMMDD-NNNN | Displayed; unique at DB layer | AI-Added |
| FR-017 | Immutable version snapshot on every save | Version increments; prior read-only | Source Docs |
| FR-018 | Free-text notes up to 2,000 chars | Live char count; saved with version | Source Docs |
| FR-019 ★ | Attach up to 5 PDFs, max 10 MB each | Type, size, count limits enforced | AI-Added |
| FR-020 | Discard Draft with confirmation | Confirmation required; logged | Source Docs |

### EP-04 · Suitability Validation Engine

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-021 | Auto-trigger on submission | Triggers; progress shown; ≤5s P95 | Source Docs |
| FR-022 | Evaluate against risk profile rules | Conservative, Moderate, Aggressive | Source Docs |
| FR-023 | Structured report: result, violations, severity | All violations listed | Source Docs |
| FR-024 ★ | Block on Critical violations | Submit blocked; all critical listed | AI-Added |
| FR-025 ★ | Allow with acknowledged Warnings | All warning checkboxes required | AI-Added |
| FR-026 ★ | Admin rule configuration panel | Changes effective next submission; logged | AI-Added |

### EP-05 · Approval Workflow

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-027 | Multi-stage: Draft → Review → Approved/Rejected | Defined sequence only; all logged | Source Docs |
| FR-028 ★ | In-app + email to Compliance on submission | In-app ≤30s; email ≤5min | AI-Added |
| FR-029 | Approve/reject with mandatory comment (≥10 chars) | Reject blocked without comment | Source Docs |
| FR-030 ★ | Notify advisor on decision with comment | In-app ≤30s | AI-Added |
| FR-031 | Rejected → Draft; resubmittable | New version on resubmit | Source Docs |
| FR-032 ★ | Auto-escalate after 5 business days | Fires at threshold; logged | AI-Added |
| FR-033 ★ | Delegation with start/end date | Both officers in audit trail | AI-Added |

### EP-06 · Audit Trail & Reporting

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-039 | Log all user and system actions | All event types produce entry | Source Docs |
| FR-040 ★ | 10-field entry: timestamp, user ID, role, action, entity type/ID, prev/new state, IP, session | All 10 fields on every entry | AI-Added |
| FR-041 | Read-only immutable trail | No edit/delete for any role | Source Docs |
| FR-042 ★ | 7-year retention | Policy enforced; no premature deletion | AI-Added |
| FR-043 ★ | Search 5 dims; CSV export ≤10s/10k records | All filters work | AI-Added |

### EP-07 · AI Summary Generation

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-034 | Plain-language client summary | No jargon or return projections | Source Docs |
| FR-035 | Reference client goals, horizon, or risk profile | At least one referenced | Source Docs |
| FR-036 ★ | Advisor editable; original AI output preserved | Versioned snapshot | AI-Added |
| FR-037 ★ | Export as branded PDF | Logo, advisor, client, proposal ID | AI-Added |
| FR-038 ★ | Generation ≤30s P95; progress indicator | Timeout error if exceeded | AI-Added |

### EP-08 · Authentication & Access Control ★

| FR | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-044 ★ | SSO via SAML 2.0 or OAuth 2.0/OIDC | Successful SSO; failed auth blocks | AI-Added |
| FR-045 ★ | RBAC: 4 roles; cross-role → HTTP 403 | All roles restricted | AI-Added |
| FR-046 ★ | Session timeout 30 min; 2-min warning | Warning at 28 min; extendable | AI-Added |
| FR-047 ★ | MFA for Compliance Officer and Admin | Login blocked without MFA | AI-Added |
| FR-048 ★ | Admin: create, deactivate, assign roles, reset | All 4 ops succeed; logged | AI-Added |

---

## 7. Non-Functional Requirements

| NFR | Category | Requirement | Target | Source |
|---|---|---|---|---|
| NFR-001 | Performance | Page load | P95 ≤3s / 100 concurrent users | Source Docs |
| NFR-002 | Performance | Suitability validation | P95 ≤5s | Source Docs |
| NFR-003 ★ | Performance | Non-AI API | P95 ≤500ms | AI-Added |
| NFR-004 | Availability | Uptime business hours | ≥99.5% rolling 30 days | Source Docs |
| NFR-005 ★ | Scalability | Concurrent users | 500 without degradation | AI-Added |
| NFR-006 | Security | In transit | TLS 1.2+; SSL Labs A/A+ | Source Docs |
| NFR-007 ★ | Security | At rest | AES-256 | AI-Added |
| NFR-008 ★ | Accessibility | WCAG | 2.1 Level AA | AI-Added |
| NFR-009 ★ | Browser | Compatibility | Latest 2: Chrome, Firefox, Edge, Safari | AI-Added |
| NFR-010 ★ | Responsiveness | Viewport | Functional at 768px | AI-Added |
| NFR-011 ★ | Data Retention | Audit/Proposals | 7 years / 5 years | AI-Added |
| NFR-012 | Role Access | Cross-role | HTTP 403; denials logged | Source Docs |
| NFR-013 ★ | Localisation | Timestamps | UTC + local timezone | AI-Added |
| NFR-014 ★ | Error Handling | User-facing errors | No raw stack traces to non-Admin | AI-Added |

---

## 8. Data Requirements

| Entity | Key Attributes |
|---|---|
| Client Profile | client_id, full_name, risk_profile, investment_goals, time_horizon, assigned_advisor_id |
| Portfolio Holdings | holding_id, client_id, asset_class, ticker, quantity, current_value, allocations |
| Rebalancing Proposal | proposal_id (PROP-YYYYMMDD-NNNN), client_id, advisor_id, status, version, notes |
| Proposal Version | version_id, proposal_id, version_number, allocations_snapshot (JSON), saved_by |
| Suitability Report | report_id, proposal_id, overall_result, violations (JSON array) |
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

| Screen | Name | Key Elements |
|---|---|---|
| S-01 | Login / SSO Entry | SSO button, MFA challenge, error states |
| S-02 | Advisor Dashboard | Client table, drift indicators, proposal status badges |
| S-03 | Portfolio Detail | Holdings table, allocation chart, profile card, history |
| S-04 | Proposal Creator | Allocation editor, sum validator, comparison panel, notes, attachments |
| S-05 | Suitability Modal | Pass/fail banner, violation list, warning checkboxes |
| S-06 | Compliance Review | Proposal summary, comment thread, approve/reject panel |
| S-07 ★ | Audit Trail Viewer | Filterable log table, CSV export |
| S-08 ★ | AI Summary Editor | Rich-text field, original AI toggle, PDF export |
| S-09 ★ | Admin Panel | User management, role assignment, rule editor |

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
| FR-039–043 | EP-06 | As Compliance, I want a searchable audit trail | S-07 |
| FR-044–048 | EP-08 | As Admin, I want SSO, RBAC, MFA, and user management | S-01, S-09 |

---

## 12. Risks

| ID | Risk | Probability | Impact | Mitigation |
|---|---|---|---|---|
| R-01 | Mock data insufficient for edge cases | Medium | High | Representative mock data set |
| R-02 | Rules engine misses regulatory nuances | High | High | Compliance sign-off before go-live |
| R-03 | AI summary quality inconsistent | Medium | Medium | Prompt engineering standards |
| R-04 ★ | SSO IdP integration delays | Medium | High | Local auth fallback for non-production |
| R-05 ★ | Scope creep: real-time market data | High | Medium | Firm out-of-scope list; change control |

---

## 13. Version History

| Version | Date | Changes |
|---|---|---|
| 1.0 | 20 May 2026 | Initial draft |
| 1.1 | 21 May 2026 | Added EP-08, notifications, SLA escalation, NFRs, data model, integration, UX, RTM |
| 1.2 | 21 May 2026 | Full re-push via Atos-Github MCP following CLAUDE.md versioning rules |
| 1.3 | 21 May 2026 | Re-push via /push_brd command; VERSION.txt read live from repo (confirmed 1.2) |
