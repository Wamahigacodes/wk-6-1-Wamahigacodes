# Phase 2 – Defect Log  
**Project:** Online Bookstore Management System  
**Prepared by:** QA Team  
**Date:** November 2025  
**Version:** 1.0  

---

## Overview  
This document logs all defects identified during Phase 2 testing. Each entry corresponds directly to a failed or problematic test case listed in `test-cases.md`.  
The goal is to document the issue details, traceability, and resolution progress for continuous quality assurance.

---

## Defect Log Table  

| Defect ID | Related TC ID | Functional Requirement | Description | Steps to Reproduce | Expected Result | Actual Result | Severity | Status | Assigned To | Date Logged | Resolution |
|------------|----------------|------------------------|--------------|--------------------|-----------------|----------------|-----------|----------|---------------|--------------|-------------|
| D01 | TC05 | FR3 – View Books | Only 6 books visible despite DB having more entries | 1. Login as user<br>2. Open catalog | All available books displayed | Only six books are displayed even though the database contains more entries| High | Open | Dev Team | 2025-11-05 | Pending fix |
| D02 | TC06 | FR4 – Search Book | Search not case-insensitive | 1. Search “react” vs “React” | Should show same results | Search is case sensitive;searching "react"returns no results | Medium | Open | Dev Team | 2025-11-05 | To be fixed in API |
| D03 | TC08 | FR6 – Checkout | Payment confirmation slow | 1. Add to cart<br>2. Checkout | Payment processed instantly | Payment confirmation takes 5-7 seconds| Medium | In Progress | Backend | 2025-11-06 | Optimization ongoing |
| D04 | TC09 | FR7 – Admin Login | Admin role not recognized after session refresh | 1. Login as admin<br>2. Refresh page | Should stay logged in | Admin session not retained;refresh redirects to login page | High | Open | Auth Team | 2025-11-06 | Cookie issue under review |
| D05 | TC10 | FR8 – Unauthorized Access | Unauthorized message lacks redirect | 1. Login as normal user<br>2. Go to /admin | Should redirect to home | Unauthorised users remain on error page instead of being redirected | Low | Open | Frontend | 2025-11-06 | UI redirect planned |
| D06 | TC11 | FR9 – Update Inventory | Stock count doesn’t update instantly | 1. Update stock<br>2. Save | New value visible immediately | Stock updates require a page refresh to appear | Medium | Open | Frontend | 2025-11-06 | Trigger state refresh |
| D07 | TC12 | FR10 – Manage Orders | Orders table doesn’t auto-refresh after update | 1. Complete new order<br>2. Open admin orders | New order appears instantly |Orders table doesnot autorefresh after updates;manual reload needed| Medium | In Progress | Dev Team | 2025-11-06 | Refresh event pending |
| D08 | TC13 | FR11 – Edit Catalog | Add-book form allows blank price field | 1. Add new book<br>2. Leave price empty | Validation error shown |Add-bookform allowsblank pric;book saved with null value | High | Open | Backend | 2025-11-07 | Validation fix needed |
| D09 | TC14 | FR11 – Edit Catalog | Delete action has no confirmation dialog | 1. Click Delete | Confirmation prompt expected | Delete action has no confirmation dialog;book deleted immediately | Low | Open | Frontend | 2025-11-07 | UX improvement planned |
| D10 | TC15 | FR12 – Error Handling | Server errors not logged in console | 1. Simulate API error | Error logged in console |Server errors are not logged in the console | Medium | Open | Backend | 2025-11-07 | Log middleware pending |
| D11 | TC03 | FR2 – User Login | “Remember me” checkbox not functional | 1. Tick “Remember me”<br>2. Login<br>3. Refresh page | Session should persist |"Remember me"checkbox doesnot persist session after refresh| Medium | Open | Auth Team | 2025-11-07 | LocalStorage logic fix |
| D12 | TC01 | FR1 – User Registration | Password strength not validated | 1. Register weak password | Should reject weak passwords |Password strength not validated;weak passwords are accepted| Medium | Open | Backend | 2025-11-07 | Validation rule to be added |

---

## Notes  
- All defects are tracked in alignment with their respective **Test Case IDs** for traceability.  
- Screenshots, console logs, and videos are stored under `/tests/evidence/defects/`.  
- Severity levels follow standard QA classification: **Low**, **Medium**, **High**, **Critical**.  
- Status values used: **Open**, **In Progress**, **Resolved**, **Closed**.  
- Fix verification will be re-tested and documented in **Phase 3 Regression Tests**.

---

