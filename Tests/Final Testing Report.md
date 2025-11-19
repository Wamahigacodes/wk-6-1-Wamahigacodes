# Software Test Report

## Online Bookstore  System "Bookstore app"

**Document ID:** TR-BOOKSTORE-2025-001

**Date of Report:** November 19, 2025

**Prepared by:** Wamahiga Nganga (Team Manager)

**Version:** 1.0

---

## Executive Summary

This report presents the results of comprehensive testing conducted on the  Online Bookstore web application version 1.0 from October 24 to November 19, 2025. The testing focused on validating core e-commerce functionality, ensuring accessibility compliance, verifying security hygiene, and assessing performance across different browsers and conditions.

### Key Findings:

- All critical and high-severity functional issues have been addressed except for one high-severity session persistence issue for admin users.
- Core user journeys (browse, search, cart, checkout) perform well with a 94.6% test case pass rate.
- The Paystack payment gateway integration functions correctly for supported currencies.
- Minor performance and accessibility concerns were identified and documented.

### Recommendation:
The QA team recommends proceeding with release, contingent on the immediate resolution of the admin session issue and a phased rollout plan to monitor performance.

Show Image

---

## 1. Test Objective

The primary objective of this testing cycle was to evaluate the quality, functionality, performance, and usability of the Bookworm Online Bookstore version 1.0 before its release to production. Specifically, our testing aimed to:

1. Validate that all core e-commerce features function according to the requirements specifications, particularly the catalog, cart, checkout, and payment processing.
2. Ensure the application is accessible and complies with WCAG 2.1 AA guidelines.
3. Verify the application's performance against defined budgets (LCP ≤ 2.5s, TTI ≤ 1s).
4. Assess the application's compatibility across different web browsers and devices.
5. Validate security measures, including input sanitization and role-based access control.

This round of testing was conducted over a three-week period from October 24, 2025, to November 19, 2025.

Show Image

---

## 2. Areas Covered

### 2.1 Functional Testing

The following functional areas were thoroughly tested:

- **User Authentication & Account Management**
  - User registration and login
  - Logout functionality and session clearance
  - Role-based access control (User vs. Admin)

- **Product Catalog & Search**
  - Product browsing
  - Search functionality (text-based)
  - Product filtering and sorting
  - Product details display

- **Shopping Cart & Checkout**
  - Add/remove items functionality
  - Quantity modification with stock enforcement
  - Coupon application and validation
  - Shipping information form
  - Payment processing via Paystack
  - Order confirmation

- **Order Management & Admin Features**
  - Order history and details view
  - Order status lifecycle transitions
  - Admin catalog CRUD operations
  - Inventory management and low-stock alerts
  - Review and Q&A moderation

- **Reviews & Community**
  - Review submission (purchasers only)
  - Review flagging and moderation
  - Safe markdown sanitization in Q&A

Show Image

### 2.2 Non-Functional Testing

The following non-functional areas were tested:

- **Performance Testing**
  - Largest Contentful Paint (LCP) and Time to Interactive (TTI)
  - Application behavior under various network conditions (Throttled 3G, 4G, Wi-Fi)

- **Compatibility Testing**
  - Testing across latest versions of Chrome, Firefox, Safari, and Edge
  - Responsive design validation across different screen sizes

- **Security Testing**
  - Input validation and sanitization (XSS attempts)
  - Authentication and authorization mechanisms
  - Secure storage of user data in localStorage

- **Usability & Accessibility Testing**
  - Keyboard navigation
  - Focus visibility
  - Screen reader compatibility (basic checks)
  - Error message clarity and guidance

Show Image

## 3. Areas Not Covered

The following areas were not included in this testing cycle:

- **Full Penetration Testing**
  - Reason: Scope limited to security hygiene checks. A comprehensive penetration test is recommended for a future cycle.

- **Extended Performance Load Testing**
  - Reason: The current user base is small. Load testing will be considered as the user base grows.

- **Real Payment Capture**
  - Reason: The Paystack integration was tested in sandbox mode only.

- **Multi-Currency Catalog & Complex Tax Logic**
  - Reason: Defined as out of scope for this release.

Show Image

## 4. Testing Approach

### 4.1 Test Strategy

Our testing approach combined various testing methodologies to ensure comprehensive coverage:

1. **Risk-Based Testing**
   - We identified high-risk areas such as payment processing, user authentication, and admin access control for additional testing focus.

2. **Test Case Design**
   - Test cases were designed using black-box techniques.
   - Boundary value analysis and equivalence partitioning were applied to input fields.
   - Scenarios were directly traced to Functional Requirement (FR) codes.

3. **Automation & Manual Testing Balance**
   - Testing was conducted manually due to project constraints and timeline.
   - Exploratory testing sessions were conducted to supplement scripted test cases.

Show Image

### 4.2 Testing Process

The testing process followed these phases:

1. **Test Planning (Oct 24-31, 2025)**
   - Test plan creation and resource allocation
   - Test environment setup and data preparation (seeded book data)
   - Test case review and prioritization

2. **Test Execution (Nov 1-14, 2025)**
   - Smoke testing on each new build
   - Feature-specific testing for all core functionality
   - Non-functional testing (performance, security, compatibility)

3. **Defect Management (Ongoing)**
   - Defects logged in GitHub Projects with severity and priority assignments
   - Weekly defect review meetings

Show Image

### 4.3 Testing Tools

The following tools were utilized during the testing process:

- **Test Management**: GitHub Projects
- **Defect Tracking**: GitHub Issues
- **Performance Testing**: Lighthouse, Browser DevTools
- **Compatibility Testing**: BrowserStack (for cross-browser checks)
- **Security Testing**: Manual penetration testing techniques, OWASP ZAP (basic)
- **Accessibility Testing**: axe DevTools, WAVE

### 4.4 Sample Key Test Cases

Below are examples of critical test cases that helped validate core functionality:

**Test Case ID: TC-PAY-01**

- **Title**: Pay with Paystack
- **Preconditions**: User logged in, items added to cart, checkout initiated
- **Steps**:
  1. Proceed through checkout steps
  2. Fill in shipping form
  3. Select Paystack as payment method
  4. Complete payment in sandbox mode
- **Expected Results**: Order status updates from Pending to Paid, payment reference stored.
- **Actual Results**: As expected
- **Status**: PASS

**Test Case ID: TC-SEC-01**

- **Title**: Block Admin Access via Manual Role Edit
- **Preconditions**: User logged in as standard user
- **Steps**:
  1. Open browser DevTools
  2. Manually change `localStorage.user.role` to 'admin'
  3. Navigate to `/admin` page
- **Expected Results**: Unauthorized access message is displayed, access is blocked.
- **Actual Results**: As expected
- **Status**: PASS

Show Image

## 5. Defect Report

### 5.1 Defect Summary

A total of 12 defects were identified during the testing cycle, categorized by severity as follows:

| Severity    | Count    | Closed    | Open    |
|---|---|---|---|
| Critical    | 0        | 0         | 0        |
| High        | 4        | 3         | 1        |
| Medium      | 6        | 4         | 2        |
| Low         | 2        | 2         | 0        |
| **Total**   | **12**   | **9**     | **3**    |

Show Image

### 5.2 Critical Defects (All Resolved)

*No Critical defects remained open at the time of report closure.*

### 5.3 Open High-Severity Defect

1. **Admin Role Not Recognized After Session Refresh** (D04)

- **Description**: After logging in as an admin, refreshing the page causes the session to be lost and redirects to the login page.
- **Current Status**: Open and assigned to Auth Team.
- **Root Cause**: Suspected issue with session cookie or localStorage persistence logic.
- **Mitigation Plan**: A hotfix is required before production release. Users must avoid refreshing the admin page.

Show Image

### 5.4 Defect Trend Analysis

The defect discovery rate decreased significantly in the final week of testing, indicating stabilizing quality:

- Week 1: 7 defects discovered (58%)
- Week 2: 4 defects discovered (33%)
- Week 3: 1 defect discovered (8%)

The declining trend in defect discovery suggests the application is maturing and reaching a stable state for release.

Show Image

## 6. Platform Details

### 6.1 Test Environment

**Server Environment:**
- Frontend: React 18, deployed locally via `npm start`
- Storage: Browser localStorage
- Payment Gateway: Paystack Sandbox

**Client Environments:**

| Browser       | OS Version    | Screen Resolution    |
|---|---|---|
| Firefox       | Kali Linux    | 1920 x 1080          |
| Chrome        | Windows 11    | 1920 x 1080          |
| Safari        | macOS Sonoma  | 1728 x 1117          |
| Edge          | Windows 11    | 1920 x 1080          |

Show Image

### 6.2 Network Conditions Tested

- **High-Performance**: Wi-Fi (100+ Mbps)
- **Average Mobile**: Throttled 4G (10-20 Mbps)
- **Poor Connection**: Throttled 3G (1-2 Mbps)

### 6.3 Tools and Frameworks

- **Manual Testing**: Primary method for all test cases.
- **Performance Monitoring**: Lighthouse, Chrome DevTools
- **Accessibility Testing**: axe DevTools, WAVE
- **Device Farm**: BrowserStack for cross-browser compatibility checks

Show Image

## 7. Overall Status

### 7.1 Testing Summary

- **Test Cases Executed**: 37 out of 37 planned (100%)
- **Test Case Pass Rate**: 35 passed (94.6%)
- **Automation Coverage**: 0% (All testing was manual)
- **Critical User Journeys**: 100% passing (All 5 critical user journeys verified)

Show Image

### 7.2 Quality Assessment

Based on our testing results, the Bookstore v1.0 application has reached a satisfactory level of quality with the following observations:

**Strengths:**

- The core shopping and checkout functionality is stable and performs as expected.
- Payment integration with Paystack works correctly in the sandbox environment.
- Security hygiene for input sanitization and role-based access is effectively implemented.
- The application is generally responsive across modern browsers.

**Areas of Concern:**

- The admin session persistence issue (D04) is a significant blocker for admin users.
- Performance on throttled 3G networks occasionally exceeds the LCP budget.
- The "Mark all as read" notification badge does not update (intentional defect).

Show Image

### 7.3 Risk Assessment

The remaining risks associated with releasing the application are:

1. **Admin Session Issue**: HIGH RISK
   - Impact: High (Renders admin dashboard unusable after refresh)
   - Mitigation: Must be fixed prior to release.

2. **Performance on Slow Networks**: LOW RISK
   - Impact: Low (Affects users with very poor connectivity)
   - Mitigation: Performance optimizations planned for v1.1.

3. **Payment Gateway Integration**: LOW RISK
   - Impact: Potentially high (could affect checkout process)
   - Mitigation: Extensive sandbox testing completed; monitoring plan in place for production.

Show Image

### 7.4 Release Recommendation

Based on our comprehensive testing and the current status of the application, the QA team **CONDITIONALLY RECOMMENDS PROCEEDING WITH THE RELEASE** of Bookstore v1.0 to production, with the following **mandatory** condition:

1. **Fix the high-severity admin session persistence issue (D04) before release.**

If the above condition is met, we further recommend:

2. Enabling enhanced monitoring for the Paystack payment integration for the first 48 hours after release.
3. Implementing a phased rollout plan (starting with 15% of users) to allow for early detection of any unforeseen issues.

### 7.5 Post-Release Activities

The following activities are recommended after release:

1. Close monitoring of application performance metrics and error logs for the first week.
2. Targeted user feedback collection on the checkout and search experiences.
3. Analysis of any customer support tickets for patterns indicating undiscovered issues.



## 8. Requirements Traceability

The following table shows how key requirements were validated through testing:

| Requirement ID | Requirement Description | Test Case IDs | Status |
|---|---|---|---|
| FR-O03 | Payments – Paystack init with configured currency; success/error handling | TC-PAY-01, TC-PAY-02 | PASSED |
| FR-U03 | Q&A – Safe markdown subset; sanitation; scheme whitelist | TC-RVW-02 | PASSED |
| FR-X01 | Accessibility – Labels, focus, aria-live; keyboard nav | TC-A11Y-01 | PASSED |
| FR-X02 | Performance – LCP/TTI budgets met; lazy images | TC-PERF-01 | PASSED with NOTE* |
| FR-M01 | Admin access control – Unauthorized access blocked | TC-ADM-01, TC-SEC-01 | PASSED |
| FR-N02 | Notifications – Mark all read; badge updates | TC-NOT-01 | PASSED (Intended Defect) |

*Note: Performance budgets are generally met but can degrade on very slow networks.

Show Image

---

## 9. Testing Challenges & Lessons Learned

### 9.1 Challenges Encountered

1. **Test Data Limitation**: The seeded database contained only 6 books, which limited the realism of testing for search, filter, and pagination.
   - Solution: Used creative test case design to maximize coverage with available data.

2. **Environment Consistency**: Slight variations in behavior were observed between local development environments of team members.
   - Solution: Standardized on one primary testing environment (Firefox on Kali Linux) for consistent results.

3. **Session Management**: Complexities in testing session persistence and role-based access without a full backend.
   - Solution: Focused testing on localStorage mechanisms and manual role manipulation.

### 9.2 Lessons Learned

1. **Early FR Code Mapping**: Tracing test cases directly to Functional Requirement codes from the start improved traceability and coverage reporting.

2. **Evidence Organization**: Implementing a strict naming convention for screenshots and videos (`tests/evidence/`) saved significant time during report compilation.

3. **Collaborative Triage**: Weekly defect review meetings ensured all team members were aligned on issue priority and status.

4. **Risk-Based Focus**: Prioritizing tests for payment, security, and admin functions ensured that the most critical areas received the deepest scrutiny.

Show Image

## 10. Appendices

### 10.1 Test Case Execution Details

Detailed test case execution results are available in the project repository under `tests/test-cases.md`.

### 10.2 Performance Test Results

Detailed performance test results from Lighthouse are available in the separate Performance Test Log.

### 10.3 Traceability Matrix

The full Requirements Traceability Matrix linking requirements to test cases and their results is available in document `tests/traceability-matrix.md`.

### 10.4 Test Data Used

Description of test datasets used during testing is available in the Test Data Inventory.

### 10.5 Defect Details

Complete details of all defects, including screenshots and reproduction steps, are available in the GitHub Project board and `tests/defect-log.md`.

## 11. Approvals

The following stakeholders have reviewed this report and approve the release recommendation or have noted their concerns:

| Role             | Name              | Approval Date | Signature  | Notes                                           |
|---|---|---|---|---|
| QA Team Manager  | Wamahiga Nganga   | Nov 19, 2025  | [Approved] | Conditionally approves release pending fix for D04. |
| Risk Analyst     | Lodrick Kibochi   | Nov 19, 2025  | [Approved] | Confirms all risks have been assessed and documented. |
| Test Executor    | Vianney Ndagire   | Nov 19, 2025  | [Approved] | Confirms all tests were executed as planned.        |
| Product Owner    | Gerald Macherechedze   | Nov 19, 2025  | [Approved] | Accepts remaining risks and confirms educational value of release. |

By signing above, approvers acknowledge they have reviewed this report in its entirety and understand the current state of the application, including any limitations, risks, and mitigation plans.

**End of Test Report**
