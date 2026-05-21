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

**Key targets:** 30–40% advisor productivity improvement · 40–50% compliance effort reduction · 8 core epics · 49 functional requirements.

---

## 2. Business Context & Problem Statement

### 2.1 Current State

| Problem Area | Description |
|---|---|
| Process Inefficiency | Manual workflows create 3–5 day delays per proposal |
| Compliance Risk | Suitability validation is ad-hoc; violations may go undetected |
| Audit Deficiency | No centralised, immutable audit trail |
| Collaboration Gaps | Email-based proposals with no version control |
| Advisor Capacity | Admin tasks limit client capacity |

---

## 3. Objectives & Success Metrics

| Metric | Current State | Target | Measurement |
|---|---|---|---|
| Proposal creation time | 3–5 business days | < 1 business day | Platform analytics |
| Compliance review cycles | 2–3 iterations | ≤ 1 iteration | Avg revision count |
| Suitability escape rate | Not measured | 0% critical | Audit log |
| Audit completeness | 0% | 100% | Coverage report |
| Compliance effort | Baseline TBD | −40–50% | Time tracking |

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

## 5. Scope

### In Scope (MVP)

| Epic | Name |
|---|---|
| EP-01 | Advisor Dashboard |
| EP-02 | Portfolio Detail View |
| EP-03 | Rebalancing Proposal |
| EP-04 | Suitability Validation Engine |
| EP-05 | Approval Workflow |
| EP-06 | Audit Trail & Reporting |
| EP-07 | AI Summary Generation |
| EP-08 ★ | Authentication & Access Control |

---

## 6. Functional Requirements

### EP-01 · Advisor Dashboard

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-001 | Display dashboard with all assigned clients: name, risk profile, drift %, last review date | Loads ≤3s; all 5 fields visible | Source Docs |
| FR-002 | Colour-coded drift indicators: Green ≤5%, Amber 5–10%, Red >10% | Colours match thresholds; legend visible | Source Docs |
| FR-003 | Sort and filter by client name, risk profile, drift band, date range | All filter/sort combinations work; updates <1s | Source Docs |
| FR-004 | Show current proposal status per client | Status badge reflects latest state | Source Docs |
| FR-005 ★ | Manual refresh button with last-updated timestamp | Refresh updates timestamp; no stale data >24h | AI-Added |

### EP-02 · Portfolio Detail View

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-006 | Display all holdings: asset class, ticker, quantity, value, current %, target % | All 7 fields rendered; loads ≤3s | Source Docs |
| FR-007 | Visual chart comparing current vs target allocation | Chart ARIA accessible; readable at 1280×800 | Source Docs |
| FR-008 | Display client risk profile, goals, and horizon | All 3 visible without extra navigation | Source Docs |
| FR-009 ★ | Proposal history list: ID, date, status, advisor name | All proposals listed; click navigates to read-only | AI-Added |
| FR-010 ★ | Download holdings as CSV or Excel | Download triggers in-page; all fields included | AI-Added |

### EP-03 · Rebalancing Proposal

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-011 | Initiate proposal from dashboard or portfolio detail | New proposal in Draft state with unique ID | Source Docs |
| FR-012 | Adjust target allocations per asset class | Inputs and sliders synchronised in real time | Source Docs |
| FR-013 | Validate total allocations = 100% in real time | Submit disabled when total ≠ 100% | Source Docs |
| FR-014 | Side-by-side current vs proposed comparison with delta | Panel updates within 500ms | Source Docs |
| FR-015 ★ | Auto-save every 2 minutes with last-saved timestamp | Auto-save without user action; no data lost | AI-Added |
| FR-016 ★ | Unique proposal ID: PROP-YYYYMMDD-NNNN | ID displayed; no duplicates | AI-Added |
| FR-017 | Immutable version snapshots on every save | Version increments; prior versions read-only | Source Docs |
| FR-018 | Free-text notes up to 2,000 characters | Live char count; saved with each version | Source Docs |
| FR-019 ★ | Attach up to 5 PDFs, max 10 MB each | Type, size, count limits enforced | AI-Added |
| FR-020 | Discard Draft with confirmation | Confirmation required; logged in audit trail | Source Docs |

### EP-04 · Suitability Validation Engine

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-021 | Auto-trigger validation on submission | Triggers on submit; progress shown; ≤5s P95 | Source Docs |
| FR-022 | Evaluate against risk profile rules | Validates Conservative, Moderate, Aggressive | Source Docs |
| FR-023 | Return structured report: result, violations, severity | All violations listed with rule ID and description | Source Docs |
| FR-024 ★ | Block submission on Critical violations | Submit blocked; error lists all critical violations | AI-Added |
| FR-025 ★ | Allow submission with acknowledged Warnings | Warning modal; all checkboxes checked required | AI-Added |
| FR-026 ★ | Admin panel for rule configuration | Rule changes effective on next submission; logged | AI-Added |

### EP-05 · Approval Workflow

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-027 | Multi-stage workflow: Draft → Review → Approved/Rejected | Transitions only in defined sequence; all logged | Source Docs |
| FR-028 ★ | In-app and email notification to Compliance on submission | In-app ≤30s; email ≤5min | AI-Added |
| FR-029 | Approve or reject with mandatory comment (min 10 chars) | Reject blocked without comment | Source Docs |
| FR-030 ★ | Notify advisor on approval/rejection | In-app ≤30s; includes compliance comment | AI-Added |
| FR-031 | Rejected proposal returns to Draft; resubmittable | Creates new version on resubmit | Source Docs |
| FR-032 ★ | Auto-escalate after 5 business days in review | Fires at 5-business-day threshold; logged | AI-Added |
| FR-033 ★ | Compliance officer delegation with date range | Both officers shown in audit trail | AI-Added |

### EP-06 · Audit Trail & Reporting

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-039 | Log all user and system actions | All event types produce a log entry | Source Docs |
| FR-040 ★ | 10-field log entry: timestamp, user ID, role, action, entity type/ID, prev/new state, IP, session ID | All 10 fields on every entry | AI-Added |
| FR-041 | Read-only immutable audit trail | No edit/delete in UI or API | Source Docs |
| FR-042 ★ | 7-year audit log retention | Retention policy enforced | AI-Added |
| FR-043 ★ | Search/filter (5 dims) and CSV export | CSV export ≤10s for 10,000 records | AI-Added |

### EP-07 · AI Summary Generation

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-034 | Generate plain-language client summary | Plain English; no jargon | Source Docs |
| FR-035 | Reference client goals, horizon, or risk profile | At least one referenced | Source Docs |
| FR-036 ★ | Advisor editable; original AI output preserved | Versioned snapshot; original in read-only toggle | AI-Added |
| FR-037 ★ | Export as branded PDF | Firm logo, advisor name, client name, proposal ID | AI-Added |
| FR-038 ★ | Generation ≤30s P95 with progress indicator | Timeout error shown if exceeded | AI-Added |

### EP-08 · Authentication & Access Control ★

| FR ID | Requirement | Acceptance Criteria | Source |
|---|---|---|---|
| FR-044 ★ | SSO via SAML 2.0 or OAuth 2.0 / OIDC | Successful SSO; failed auth blocks access | AI-Added |
| FR-045 ★ | RBAC with 4 roles; cross-role attempts return HTTP 403 | All roles restricted to permitted features | AI-Added |
| FR-046 ★ | Session timeout at 30 min; 2-min warning modal | Warning at 28 min; user can extend | AI-Added |
| FR-047 ★ | MFA enforced for Compliance Officer and Admin | Login blocked without MFA for these roles | AI-Added |
| FR-048 ★ | Admin: create, deactivate, assign roles, reset credentials | All 4 operations succeed; logged in audit trail | AI-Added |

---

## 7. Non-Functional Requirements

| NFR ID | Category | Requirement | Target | Source |
|---|---|---|---|---|
| NFR-001 | Performance | Page load time | P95 ≤3s / 100 concurrent users | Source Docs |
| NFR-002 | Performance | Suitability validation | P95 ≤5s | Source Docs |
| NFR-003 ★ | Performance | Non-AI API response | P95 ≤500ms | AI-Added |
| NFR-004 | Availability | Uptime business hours | ≥99.5% rolling 30 days | Source Docs |
| NFR-005 ★ | Scalability | Concurrent users | 500 without degradation | AI-Added |
| NFR-006 | Security | Data in transit | TLS 1.2+; SSL Labs A/A+ | Source Docs |
| NFR-007 ★ | Security | Data at rest | AES-256 | AI-Added |
| NFR-008 ★ | Accessibility | WCAG | 2.1 Level AA | AI-Added |
| NFR-009 ★ | Browser | Compatibility | Latest 2: Chrome, Firefox, Edge, Safari | AI-Added |
| NFR-010 ★ | Responsiveness | Viewport | Functional at 768px | AI-Added |
| NFR-011 ★ | Data Retention | Audit / Proposals | 7 years / 5 years | AI-Added |

---

## 8. Version History

| Version | Date | Changes |
|---|---|---|
| 1.0 | 20 May 2026 | Initial draft |
| 1.1 | 21 May 2026 | Added EP-08, notifications, SLA escalation, attachment support, extended NFRs, data model, integration requirements, UX inventory, RTM |
