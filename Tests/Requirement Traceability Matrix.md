# 📊 **Requirement Traceability Matrix (RTM) — Book Store App**

**Project:** Book Store App QA
**Phase:** 2 — Requirement Coverage and Traceability
**Date:** November 13, 2025
**Prepared by:** QA Team Manager (Wamahiga Nganga)
**Purpose:** To ensure all Functional Requirements (FRs) defined in the specification are covered by corresponding Test Cases (TCs), and to identify any missing or pending coverage areas.



## ✅ **Traceability Coverage Summary**

* [x] Functional Requirements (FRs) fully covered by executed Test Cases
* [x] Partial coverage for admin & returns workflows (Phase 3 continuation)
* [x] Additional 10 test cases proposed below for uncovered FRs
* [ ] Phase 3 verification pending (final report next week)

---

## 🧩 **Requirement-to-Test Case Mapping Table**

| **FR Code**    | **Requirement Description**                            | **Mapped Test Case ID(s)** | **Coverage Status**  | **Remarks / Evidence**                |
| -------------- | ------------------------------------------------------ | -------------------------- | -------------------- | ------------------------------------- |
| **FR-O01**     | Cart operations (add/update/remove, stock enforcement) | TC-CHK-01, TC-CHK-02       | ✅ Covered            | Stock enforcement validated           |
| **FR-O02**     | Checkout wizard & coupon validation                    | TC-CHK-03, TC-CHK-04       | ✅ Covered            | Coupons & checkout flow tested        |
| **FR-O03**     | Payments with Paystack                                 | TC-PAY-01, TC-PAY-02       | ✅ Covered            | Payment success/cancel validated      |
| **FR-O04**     | Orders history & CSV export                            | TC-ORD-01                  | ⚠️ Partially Covered | CSV export to be tested (Phase 3)     |
| **FR-O05**     | Order lifecycle transitions                            | ➕ **TC-ORD-02 (NEW)**      | ⏳ Pending            | To test Pending→Delivered→Refund flow |
| **FR-R01**     | Returns within 7-day window                            | ➕ **TC-RET-01 (NEW)**      | ⏳ Pending            | Return rule (day 8 accepted defect)   |
| **FR-R02**     | Refunds audit trail                                    | ➕ **TC-REF-01 (NEW)**      | ⏳ Pending            | Verify refund status update           |
| **FR-R03**     | Admin approval required for refunds                    | ➕ **TC-ADM-02 (NEW)**      | ⏳ Pending            | Admin-only return approval            |
| **FR-U01**     | Reviews limited to purchasers                          | TC-RVW-01                  | ✅ Covered            | Review without purchase blocked       |
| **FR-U02**     | Moderation of flagged reviews                          | ➕ **TC-RVW-03 (NEW)**      | ⏳ Pending            | Admin moderation queue check          |
| **FR-U03**     | Safe markdown sanitation                               | TC-RVW-02                  | ✅ Covered            | JavaScript links blocked              |
| **FR-M01**     | Admin page authorization                               | TC-ADM-01                  | ✅ Covered            | Non-admin restricted                  |
| **FR-M02**     | Inventory adjustment triggers alerts                   | ➕ **TC-ADM-03 (NEW)**      | ⏳ Pending            | Low-stock alert verification          |
| **FR-M03**     | Orders dashboard (status update)                       | ➕ **TC-ADM-04 (NEW)**      | ⏳ Pending            | Update order status as Admin          |
| **FR-M04**     | Moderation — manage flags                              | ➕ **TC-ADM-05 (NEW)**      | ⏳ Pending            | Admin manages review reports          |
| **FR-N01**     | Notification badge update                              | ➕ **TC-NOT-02 (NEW)**      | ⏳ Pending            | Badge count increment check           |
| **FR-N02**     | Mark-all-read (intentional defect)                     | TC-NOT-01                  | ✅ Covered            | Badge not updated defect captured     |
| **FR-X01**     | Accessibility — labels & focus                         | ➕ **TC-A11Y-01 (NEW)**     | ⏳ Pending            | Keyboard navigation test              |
| **FR-X02**     | Performance — lazy images, LCP                         | ➕ **TC-PERF-01 (NEW)**     | ⏳ Pending            | Lazy-loading check                    |
| **FR-X03**     | Compatibility — browser support                        | ➕ **TC-COMP-01 (NEW)**     | ⏳ Pending            | Test Chrome/Firefox/Edge              |
| **FR-X04**     | Security hygiene & sanitization                        | ➕ **TC-SEC-01 (NEW)**      | ⏳ Pending            | Verify blocked unsafe URLs            |
| **FR-S01–S03** | Sanitization & storage error handling                  | ➕ **TC-ERR-01 (NEW)**      | ⏳ Pending            | Simulate JSON/Quota error handling    |

---

## 🧪 **New Test Cases (Uncovered Functional Requirements)**

> These **10 new test cases** extend coverage for areas not included in the Phase 2 document.
> Format follows existing table conventions.

| **Test Case ID** | **Title**                                    | **FR Code(s)** | **Pre-Conditions**        | **Steps**                                              | **Expected Result**                   | **Post-Conditions**                | **Severity** | **Priority** | **Evidence**            |
| ---------------- | -------------------------------------------- | -------------- | ------------------------- | ------------------------------------------------------ | ------------------------------------- | ---------------------------------- | ------------ | ------------ | ----------------------- |
| **TC-ORD-02**    | Verify order lifecycle transitions           | FR-O05         | Order placed successfully | 1. Mark Paid → Fulfilled → Delivered 2. Attempt refund | Status transitions logged             | Order audit trail updated          | Major        | High         | evidence/TC-ORD-02.png  |
| **TC-RET-01**    | Validate 7-day return window                 | FR-R01         | Delivered order           | 1. Submit return request on day 8                      | Request accepted (defect)             | Logged in audit                    | Major        | Medium       | evidence/TC-RET-01.png  |
| **TC-REF-01**    | Verify refund with audit entry               | FR-R02         | Returned order            | 1. Admin initiates refund                              | Status changes to Refunded            | Refund audit recorded              | Major        | High         | evidence/TC-REF-01.png  |
| **TC-ADM-02**    | Check admin approval required for refunds    | FR-R03         | Logged in as admin        | 1. Attempt refund as user 2. Attempt as admin          | User blocked, admin succeeds          | Audit entry recorded               | Major        | Medium       | evidence/TC-ADM-02.png  |
| **TC-RVW-03**    | Flag and moderate review                     | FR-U02         | Logged in user/admin      | 1. Flag review 2. Check admin queue                    | Review visible to admin               | Moderation state updated           | Minor        | Medium       | evidence/TC-RVW-03.png  |
| **TC-ADM-03**    | Verify low-stock alerts                      | FR-M02         | Admin logged in           | 1. Reduce stock below threshold                        | Low-stock warning appears             | Alert visible in dashboard         | Minor        | Medium       | evidence/TC-ADM-03.png  |
| **TC-A11Y-01**   | Validate accessibility (keyboard navigation) | FR-X01         | UI loaded                 | 1. Tab through elements 2. Use ESC                     | Focus order correct, ESC clears modal | All interactive elements reachable | Minor        | Medium       | evidence/TC-A11Y-01.gif |
| **TC-PERF-01**   | Verify lazy loading of images                | FR-X02         | Catalog page open         | 1. Scroll down slowly                                  | Off-screen images load lazily         | Performance improved               | Minor        | Medium       | evidence/TC-PERF-01.png |
| **TC-COMP-01**   | Test browser compatibility                   | FR-X03         | App deployed locally      | 1. Open app on Chrome, Firefox, Edge                   | Layouts render consistently           | Compatible across browsers         | Minor        | Low          | evidence/TC-COMP-01.png |
| **TC-SEC-01**    | Verify unsafe link blocking                  | FR-X04 / S01   | Reviewer form             | 1. Submit `[Test](javascript:alert())`                 | Script blocked, sanitized link        | Secure markdown only               | Critical     | High         | evidence/TC-SEC-01.png  |

---

## 📁 **Supporting Documents**

* **Functional Requirements:** `docs/functional-requirements.md`
* **Test Cases (Phase 2):** `tests/test-cases.md`
* **Defect Log:** `tests/defect-log.md`
* **Evidence Folder:** `tests/evidence/` (screenshots, logs, GIFs)

---

## 🧾 **Key**

* ✅ = Fully Covered
* ⚠️ = Partially Covered
* ⏳ = Pending (planned in Phase 3)
* ➕ = Newly added test case for uncovered FR

---

## 💬 **Summary**

This Requirement Traceability Matrix (RTM) provides **end-to-end visibility** between requirements and test coverage.
Phase 2 achieved strong alignment between **core functional areas (Cart, Checkout, Payment)** and their tests, while **Phase 3** will address **returns, refunds, accessibility, and performance** scenarios.

All newly added test cases have been outlined for execution in the next testing phase to ensure **100% FR-to-TC coverage** by project completion.

---

Would you like me to add a **color-coded version (with emojis for severity/priority and status indicators)** to make it more visually appealing for a presentation (like ✅🟡⏳🔴 indicators)?
