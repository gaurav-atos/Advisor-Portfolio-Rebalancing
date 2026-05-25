# Business Requirements Document
## Advisor Portfolio Rebalancing & Suitability Review Platform
**Version:** 1.3 | **Status:** Approved | **Date:** 21 May 2026 | **Classification:** Confidential

> Requirements marked **AI-Added** were inferred to ensure completeness and must be reviewed before sign-off.

---

## 1. Executive Summary

This BRD defines functional, non-functional, and compliance requirements for a web-based Advisor Portfolio Rebalancing & Suitability Review Platform covering the full rebalancing lifecycle: drift detection, proposal authoring, suitability validation, compliance approval, AI-assisted client summary, and audit trail.

**Key targets:** 30-40% advisor productivity gain · 40-50% compliance effort reduction · 8 epics · 49 FRs · 14 NFRs · 80 JIRA issues.

---

## 2. Problem Statement

| Problem | Impact |
|---|---|
| Manual spreadsheet workflows | 3-5 day delays per proposal |
| Ad-hoc suitability checks | Violations may go undetected |
| No audit trail | Regulatory exposure |
| Email-based proposals | No version control |
| Admin overhead | Limits advisor client capacity |

---

## 3. Success Metrics

| Metric | Target |
|---|---|
| Proposal creation time | Less than 1 business day |
| Compliance review cycles | 1 or fewer iterations |
| Suitability escape rate | 0% critical violations |
| Audit completeness | 100% actions logged |
| Compliance effort | 40-50% reduction |

---

## 4. Stakeholders

| Role | R | A |
|---|---|---|
| Head of Wealth Advisory | - | A |
| Compliance Officer | R | A |
| Product Manager | R | A |
| Financial Advisor | R | - |
| Technology Lead | R | - |
| Operations Lead | R | - |

---

## 5. Epics

| Epic | Name | Source |
|---|---|---|
| EP-01 | Advisor Dashboard | Source Docs |
| EP-02 | Portfolio Detail View | Source Docs |
| EP-03 | Rebalancing Proposal | Source Docs |
| EP-04 | Suitability Validation Engine | Source Docs |
| EP-05 | Approval Workflow | Source Docs |
| EP-06 | Audit Trail and Reporting | Source Docs |
| EP-07 | AI Summary Generation | Source Docs |
| EP-08 | Authentication and Access Control | AI-Added |

---

## 6. Functional Requirements

### EP-01 Advisor Dashboard

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-001 | Dashboard: client name, risk profile, drift %, last review date, proposal status | Loads in 3s; all fields visible | Source Docs |
| FR-002 | Colour-coded drift: Green 5% or below, Amber 5-10%, Red above 10% | Colours match thresholds | Source Docs |
| FR-003 | Sort and filter by name, risk profile, drift band, date range | All combinations work; updates in 1s | Source Docs |
| FR-004 | Current proposal status per client | Badge reflects latest state | Source Docs |
| FR-005 | Manual refresh with last-updated timestamp | Timestamp updates; no stale data beyond 24h | AI-Added |

### EP-02 Portfolio Detail View

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-006 | Holdings: asset class, ticker, quantity, value, current %, target % | All 7 fields; loads in 3s | Source Docs |
| FR-007 | Visual chart comparing current vs target allocation | ARIA accessible | Source Docs |
| FR-008 | Client risk profile, goals, horizon | All 3 visible without extra navigation | Source Docs |
| FR-009 | Proposal history: ID, date, status, advisor | All listed; click opens read-only | AI-Added |
| FR-010 | Download holdings as CSV or Excel | In-page download; all fields included | AI-Added |

### EP-03 Rebalancing Proposal

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-011 | Initiate from dashboard or detail view | Draft with PROP-YYYYMMDD-NNNN ID | Source Docs |
| FR-012 | Adjust target allocations per asset class | Inputs and sliders synchronised | Source Docs |
| FR-013 | Validate total equals 100% and block submit otherwise | Submit disabled with inline error | Source Docs |
| FR-014 | Current vs proposed comparison with delta | Updates within 500ms | Source Docs |
| FR-015 | Auto-save every 2 minutes with last-saved timestamp | No data lost on tab close | AI-Added |
| FR-016 | Unique ID in PROP-YYYYMMDD-NNNN format | Displayed; unique at DB layer | AI-Added |
| FR-017 | Immutable version snapshot on every save | Version increments; prior read-only | Source Docs |
| FR-018 | Free-text notes up to 2000 characters | Live character count; saved with version | Source Docs |
| FR-019 | Attach up to 5 PDFs max 10 MB each | Type, size, and count limits enforced | AI-Added |
| FR-020 | Discard Draft with confirmation | Confirmation required; logged in audit | Source Docs |

### EP-04 Suitability Validation Engine

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-021 | Auto-trigger on submission | Triggers; progress shown; 5s P95 | Source Docs |
| FR-022 | Evaluate against risk profile rules | Conservative, Moderate, Aggressive | Source Docs |
| FR-023 | Structured report: result, violations, severity | All violations listed | Source Docs |
| FR-024 | Block submission on Critical violations | Submit blocked; all critical violations listed | AI-Added |
| FR-025 | Allow submission with acknowledged Warnings | All warning checkboxes required | AI-Added |
| FR-026 | Admin rule configuration panel | Changes effective on next submission; logged | AI-Added |

### EP-05 Approval Workflow

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-027 | Multi-stage: Draft to Review to Approved or Rejected | Defined sequence only; all logged | Source Docs |
| FR-028 | In-app and email notification to Compliance on submission | In-app within 30s; email within 5min | AI-Added |
| FR-029 | Approve or reject with mandatory comment at least 10 characters | Reject blocked without comment | Source Docs |
| FR-030 | Notify advisor on decision including comment | In-app within 30s | AI-Added |
| FR-031 | Rejected proposal returns to Draft and is resubmittable | New version on resubmit | Source Docs |
| FR-032 | Auto-escalate after 5 business days | Fires at threshold; logged | AI-Added |
| FR-033 | Delegation with start and end date | Both officers attributed in audit trail | AI-Added |

### EP-06 Audit Trail and Reporting

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-039 | Log all user and system actions | All event types produce an entry | Source Docs |
| FR-040 | 10-field entry: timestamp, user ID, role, action, entity type, entity ID, previous state, new state, IP, session | All 10 fields on every entry | AI-Added |
| FR-041 | Read-only immutable trail | No edit or delete for any role | Source Docs |
| FR-042 | 7-year retention | Policy enforced; no premature deletion | AI-Added |
| FR-043 | Search by 5 dimensions; CSV export within 10s for 10000 records | All filters work | AI-Added |

### EP-07 AI Summary Generation

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-034 | Plain-language client summary | No jargon or return projections | Source Docs |
| FR-035 | Reference client goals, horizon, or risk profile | At least one referenced | Source Docs |
| FR-036 | Advisor editable; original AI output preserved | Versioned snapshot on save | AI-Added |
| FR-037 | Export as branded PDF with logo, advisor, client, proposal ID | All 4 fields present | AI-Added |
| FR-038 | Generation within 30s P95; progress indicator shown | Timeout error if exceeded | AI-Added |

### EP-08 Authentication and Access Control

| FR | Requirement | AC | Source |
|---|---|---|---|
| FR-044 | SSO via SAML 2.0 or OAuth 2.0 OIDC | Successful SSO; failed auth blocks | AI-Added |
| FR-045 | RBAC with 4 roles; cross-role attempts return HTTP 403 | All roles restricted to permitted features | AI-Added |
| FR-046 | Session timeout at 30 min; 2-minute warning modal | Warning at 28 min; extendable | AI-Added |
| FR-047 | MFA for Compliance Officer and Admin | Login blocked without MFA | AI-Added |
| FR-048 | Admin operations: create, deactivate, assign roles, reset credentials | All 4 succeed; changes logged | AI-Added |

---

## 7. Non-Functional Requirements

| NFR | Category | Requirement | Target | Source |
|---|---|---|---|---|
| NFR-001 | Performance | Page load | P95 3s at 100 concurrent users | Source Docs |
| NFR-002 | Performance | Suitability validation | P95 5s | Source Docs |
| NFR-003 | Performance | Non-AI API response | P95 500ms | AI-Added |
| NFR-004 | Availability | Uptime business hours | 99.5% rolling 30 days | Source Docs |
| NFR-005 | Scalability | Concurrent users | 500 without degradation | AI-Added |
| NFR-006 | Security | Data in transit | TLS 1.2 or higher | Source Docs |
| NFR-007 | Security | Data at rest | AES-256 | AI-Added |
| NFR-008 | Accessibility | WCAG standard | 2.1 Level AA | AI-Added |
| NFR-009 | Browser | Compatibility | Latest 2 versions of Chrome, Firefox, Edge, Safari | AI-Added |
| NFR-010 | Responsiveness | Minimum viewport | Functional at 768px | AI-Added |
| NFR-011 | Data Retention | Audit and proposals | 7 years and 5 years respectively | AI-Added |
| NFR-012 | Role Access | Cross-role enforcement | HTTP 403 on all cross-role attempts; denials logged | Source Docs |
| NFR-013 | Localisation | Timestamps | UTC and local timezone on all timestamps | AI-Added |
| NFR-014 | Error Handling | User-facing errors | No raw stack traces shown to non-Admin users | AI-Added |

---

## 8. Data Entities

| Entity | Key Attributes |
|---|---|
| Client Profile | client_id, full_name, risk_profile, investment_goals, time_horizon, assigned_advisor_id |
| Portfolio Holdings | holding_id, client_id, asset_class, ticker, quantity, current_value, allocations |
| Rebalancing Proposal | proposal_id, client_id, advisor_id, status, version, notes |
| Proposal Version | version_id, proposal_id, version_number, allocations_snapshot, saved_by |
| Suitability Report | report_id, proposal_id, overall_result, violations |
| Compliance Rule | rule_id, risk_profile_target, threshold_pct, severity, is_active |
| Audit Log Entry | log_id, timestamp_utc, user_id, role, action_type, entity_id, prev_state, new_state, source_ip, session_id |
| User Account | user_id, full_name, email, role, is_active, sso_provider_id, mfa_enabled |

---

## 9. UX Screens

| Screen | Name |
|---|---|
| S-01 | Login and SSO Entry |
| S-02 | Advisor Dashboard |
| S-03 | Portfolio Detail View |
| S-04 | Proposal Creator |
| S-05 | Suitability Validation Modal |
| S-06 | Compliance Review |
| S-07 | Audit Trail Viewer |
| S-08 | AI Summary Editor |
| S-09 | Admin Panel |

---

## 10. Traceability Matrix

| FR Range | Epic | JIRA Story | Screen |
|---|---|---|---|
| FR-001 to FR-005 | EP-01 | As an Advisor I want a dashboard showing all assigned clients | S-02 |
| FR-006 to FR-010 | EP-02 | As an Advisor I want full portfolio detail and history | S-03 |
| FR-011 to FR-020 | EP-03 | As an Advisor I want to create version and submit proposals | S-04 |
| FR-021 to FR-026 | EP-04 | As Compliance I want proposals auto-validated on submission | S-05 |
| FR-027 to FR-033 | EP-05 | As Compliance I want a structured approval workflow | S-06 |
| FR-034 to FR-038 | EP-07 | As an Advisor I want AI-generated client summaries | S-08 |
| FR-039 to FR-043 | EP-06 | As Compliance I want a searchable audit trail | S-07 |
| FR-044 to FR-048 | EP-08 | As Admin I want SSO RBAC MFA and user management | S-01 and S-09 |

---

## 11. Version History

| Version | Date | Summary |
|---|---|---|
| 1.0 | 20 May 2026 | Initial draft |
| 1.1 | 21 May 2026 | Added EP-08, notifications, SLA escalation, NFRs, data model, integrations, UX, RTM |
| 1.2 | 21 May 2026 | Full re-push via Atos-Github MCP |
| 1.3 | 21 May 2026 | Re-push with live VERSION.txt verification; full CHANGELOG history restored |
