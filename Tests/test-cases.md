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

| **Test Case ID** | **Title** | **FR Code(s)** | **Pre-Conditions** | **Steps** | **Expected Result** | **Post-Conditions** | **Severity** | **Priority** | **Evidence** |
|------------------|------------|----------------|--------------------|------------|---------------------|---------------------|--------------|--------------|---------------|
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
| TC-RVW-01 | Review without purchase | FR-U01 | Logged in user | 1. Open book 2. Submit review | Error “Purchase required” | No review saved | Minor | Medium | evidence/TC-RVW-01.png |
| TC-RVW-02 | Safe markdown sanitization | FR-U03 | Reviewer form | 1. Add `[Click](javascript:alert(1))` | Script blocked | Sanitized text only | Critical | High | evidence/TC-RVW-02.png |
| TC-ADM-01 | Access admin page unauthorized | FR-M01 | Non-admin user | 1. Go to /admin | Unauthorized message displayed | No access | Major | High | evidence/TC-ADM-01.png |
| TC-NOT-01 | Mark all notifications read | FR-N02 | Notifications exist | 1. Click “Mark all read” | Badge resets to 0 (intentional defect) | Defect observable | Minor | Medium | evidence/TC-NOT-01.gif |

---

##  Notes
- All evidence is stored in `tests/evidence/` following the naming convention `TC-<area>-<id>.<ext>`.  
- Severity levels: **Critical**, **Major**, **Minor**, **Cosmetic**.  
- Priority levels: **High**, **Medium**, **Low**.  
- Intentional defects (e.g., FR-N02 badge update) are logged in the corresponding `defect-log.md`.  
- Linked to Github Projects for traceability (FR–TC–Bug mapping).  

---

