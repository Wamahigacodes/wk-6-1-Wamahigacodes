# Test Cases — Book Store App (Phase 2)

**Project:** Book Store App QA  
**Phase:** 2 — Test Design & Early Execution  
**Date:** November 8, 2025  
**Execution Mode:** Manual  
**Evidence Folder:** `tests/evidence/`  
**Prepared by:** Risk Analyst  

---

## Overview
This document contains the detailed manual test cases designed for Phase 2 of the Book Store App QA project.  
Each case is traceable to its corresponding **Functional Requirement (FR)** and covers core functional, accessibility, and performance aspects defined in the FR document.  

---

## Assumptions
- Test data is seeded with **6 books** in the catalog.  
- The app runs locally using `npm start`.  
- Admin access is managed via `localStorage.user.role = 'admin'`.  
- No real payment or backend integration is used.  
- Browser under test: Firefox on Kali Linux.

---

##  Test Cases Table
> Each test case includes preconditions, detailed steps, expected and post-conditions, mapped FR codes, and severity/priority indicators.  
> Evidence paths refer to screenshots, GIFs, or logs captured in the `tests/evidence` directory.

| **Test Case ID** | **Title**                                    | **FR Code(s)** | **Pre-Conditions**        | **Steps**                                              | **Expected Result**                   | **Post-Conditions**                | **Severity** | **Priority** | **Evidence** |
|------------------|---------------------------------------------|----------------|---------------------------|------------------------------------------------------|-------------------------------------|----------------------------------|--------------|--------------|---------------|
| TC-CAT-01 | Search for book by title | FR-O01 | App loaded with seeded data | 1. Open home page  2. Type “harry” in search 3. Press Enter | Matching titles appear | Results visible | Minor | High | evidence/TC-CAT-01.png |
| TC-CAT-02 | Filter by genre | FR-O01 | Same as above | 1. Open filter panel 2. Select “Fiction” | Only Fiction books displayed | Filter retained on refresh | Minor | Medium | evidence/TC-CAT-02.png |
| TC-CAT-03 | Sort by rating | FR-O01 | Filter cleared | 1. Choose “Sort by rating desc” | Books reorder by rating | Sort indicator active | Minor | Medium | evidence/TC-CAT-03.png |
| TC-CHK-01 | Add to cart | FR-O01 | User on catalog page | 1. Click Add to Cart on a book | Cart count increases | Item stored | Major | High | evidence/TC-CHK-01.gif |
| TC-CHK-02 | Exceed stock quantity | FR-O01 | Item added | 1. Increase qty past stock limit | Error shown; qty unchanged | Stock unchanged | Major | High | evidence/TC-CHK-02.png |
| TC-CHK-03 | Apply valid coupon | FR-O02 | Cart > ₦500 | 1. Enter “SAVE10” 2. Apply | 10% discount shown | Discount persisted | Major | High | evidence/TC-CHK-03.png |
| TC-CHK-04 | Apply expired coupon | FR-O02 | Cart ready | 1. Enter “OLD20” 2. Apply | Coupon rejected | None | Minor | Medium | evidence/TC-CHK-04.png |
| TC-PAY-01 | Pay with Paystack | FR-O03 | Valid cart | 1. Proceed checkout 2. Fill form 3. Select Paystack | Payment modal opens | Pending→Paid | Critical | High | evidence/TC-PAY-01.gif |
| TC-PAY-02 | Cancel payment | FR-O03 | Payment modal open | 1. Close gateway | Message shown “Payment cancelled” | Order = Pending | Major | Medium | evidence/TC-PAY-02.png |
| TC-ORD-01 | View order history | FR-O04 | User completed purchase | 1. Navigate Orders | Orders listed with statuses | Viewable | Minor | Low | evidence/TC-ORD-01.png |
| TC-ORD-02 | Order filter by status | FR-O04 | Orders available | 1. Filter “Completed” | Only completed shown | Filter persists | Minor | Medium | evidence/TC-ORD-02.png |
| TC-ORD-03 | Verify order lifecycle transitions | FR-O05 | Order placed successfully | 1. Mark Paid → Fulfilled → Delivered 2. Attempt refund | Status transitions logged | Order audit trail updated | Major | High | evidence/TC-ORD-03.png |
| TC-RET-01 | Validate 7-day return window | FR-R01 | Delivered order | 1. Submit return request on day 8 | Request accepted (defect) | Logged in audit | Major | Medium | evidence/TC-RET-01.png |
| TC-REF-01 | Verify refund with audit entry | FR-R02 | Returned order | 1. Admin initiates refund | Status changes to Refunded | Refund audit recorded | Major | High | evidence/TC-REF-01.png |
| TC-ADM-02 | Check admin approval required for refunds | FR-R03 | Logged in as admin | 1. Attempt refund as user 2. Attempt as admin | User blocked, admin succeeds | Audit entry recorded | Major | Medium | evidence/TC-ADM-02.png |
| TC-RVW-01 | Review without purchase | FR-U01 | Logged in user | 1. Open book 2. Submit review | Error “Purchase required” | No review saved | Minor | Medium | evidence/TC-RVW-01.png |
| TC-RVW-03 | Flag and moderate review | FR-U02 | Logged in user/admin | 1. Flag review 2. Check admin queue | Review visible to admin | Moderation state updated | Minor | Medium | evidence/TC-RVW-03.png |
| TC-RVW-02 | Safe markdown sanitization | FR-U03 | Reviewer form | 1. Add `[Click](javascript:alert(1))` | Script blocked | Sanitized text only | Critical | High | evidence/TC-RVW-02.png |
| TC-ADM-01 | Access admin page unauthorized | FR-M01 | Non-admin user | 1. Go to /admin | Unauthorized message displayed | No access | Major | High | evidence/TC-ADM-01.png |
| TC-ADM-03 | Verify low-stock alerts | FR-M02 | Admin logged in | 1. Reduce stock below threshold | Low-stock warning appears | Alert visible in dashboard | Minor | Medium | evidence/TC-ADM-03.png |
| TC-ADM-04 | Update orders dashboard as admin | FR-M03 | Admin logged in | 1. Change order status | Dashboard updated | Status reflected | Minor | Medium | evidence/TC-ADM-04.png |
| TC-ADM-05 | Moderate flagged reviews | FR-M04 | Admin logged in | 1. Check flagged reviews 2. Approve/reject | Status updated | Audit logged | Minor | Medium | evidence/TC-ADM-05.png |
| TC-NOT-01 | Mark all notifications read | FR-N02 | Notifications exist | 1. Click “Mark all read” | Badge resets to 0 (intentional defect) | Defect observable | Minor | Medium | evidence/TC-NOT-01.gif |
| TC-NOT-02 | Verify notification badge increment | FR-N01 | New notifications | 1. Generate new notification | Badge count increases | Badge visible | Minor | Medium | evidence/TC-NOT-02.png |
| TC-A11Y-01 | Keyboard navigation of catalog | FR-X01 | Keyboard only | 1. Tab through items | Focus visible on elements | Navigation successful | Minor | Medium | evidence/TC-A11Y-01.gif |
| TC-PERF-01 | Catalog load time < 3s | FR-X02 | Fresh reload | 1. Open homepage | Catalog renders under 3 sec | Timer recorded | Major | High | evidence/TC-PERF-01.png |
| TC-COMP-01 | Test browser compatibility | FR-X03 | App deployed locally | 1. Open app on Chrome, Firefox, Edge | Layouts render consistently | Compatible across browsers | Minor | Low | evidence/TC-COMP-01.png |
| TC-SEC-01 | Block admin access via manual role edit | FR-X04 | User logged | 1. Change role in DevTools to “admin” | Unauthorized remains | Secure | Critical | High | evidence/TC-SEC-01.png |
| TC-SEC-02 | Coupon input validation (script injection) | FR-X04 | Cart loaded | 1. Insert `<script>alert(1)</script>` | Script removed | Safe | Critical | High | evidence/TC-SEC-02.png |
| TC-ERR-01 | Simulate JSON / quota errors | FR-S01–S03 | System loaded | 1. Trigger storage limits or invalid JSON | Proper error handled | Logged error | Major | Medium | evidence/TC-ERR-01.png |
| TC-UAC-01 | Logout clears user session | FR-UAC01 | Logged in | 1. Logout | localStorage cleared | User = guest | Major | High | evidence/TC-UAC-01.png |

##  Notes
- All evidence is stored in `tests/evidence/` following the naming convention `TC-<area>-<id>.<ext>`.  
- Severity levels: **Critical**, **Major**, **Minor**, **Cosmetic**.  
- Priority levels: **High**, **Medium**, **Low**.  
- Intentional defects (e.g., FR-N02 badge update) are logged in the corresponding `defect-log.md`.  
- Linked to Github Projects for traceability (FR–TC–Bug mapping).  

---

