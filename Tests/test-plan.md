# Test Plan: Book Store App

## 🎯 Objective and Scope

### Objective
Ensure the React Book Store application provides a seamless, accessible, and secure shopping experience across all user journeys—from book discovery to purchase completion—while meeting  performance benchmarks.

### Scope
This test cycle will focus on validating the core bookstore functionality including catalog browsing, cart management, checkout flow, and administrative features. Testing will cover functional, accessibility, performance  and compatibility.

## ✅ In-Scope Features (Mapped to FR Codes)

### Catalog & Discovery
- **FR-CAT-01**: Catalog browsing at `/catalog`
- **FR-CAT-02**: Search functionality across title/author/description
- **FR-CAT-03**: Responsive book grid with lazy-loaded images
- **FR-CAT-04**: "Buy Now" functionality with cart routing

### Cart Management  
- **FR-CART-01**: Cart page at `/cart` with quantity updates
- **FR-CART-02**: Subtotal calculations and persistence
- **FR-CART-03**: localStorage persistence for cart data
- **FR-CART-04**: Cart item management (add/remove/update)

### Checkout & Payments
- **FR-PAY-01**: Checkout scaffolding at `/checkout`
- **FR-PAY-02**: Paystack integration with configurable currency
- **FR-PAY-03**: Payment verification stub
- **FR-PAY-04**: Order persistence in localStorage

### User & Admin Features
- **FR-ADMIN-01**: Admin page stub with route guarding at `/admin`
- **FR-ADMIN-02**: Role-based access control (admin role check)
- **FR-USER-01**: localStorage user session management

### Technical Requirements
- **FR-TECH-01**: React Router navigation
- **FR-TECH-02**: localStorage quota-safe handling
- **FR-TECH-03**: Responsive Tailwind CSS design
- **FR-TECH-04**: Accessibility compliance (Navbar a11y, labels)

## 🚫 Out-of-Scope

### Excluded Features
- Inventory management backend systems
- Publisher portal functionality  
- Advanced analytics dashboard
- Mobile application testing (web responsive only)
- International shipping calculations
- Real payment processing 
- Email notification delivery systems

### Justification
Focus remains on customer-facing functionality and core technical implementation as outlined in the "Prioritized Backlog P1" requirements.

## 🌍 Environments

### Browser Matrix (Priority 1 - Must Test)
- **Chrome**  on Windows 11 
- **Firefox**  on Windows 11
- **Edge**  on Windows 11

### Device Testing
- **Desktop**: DESKTOP-VKRMBR2
- **Mobile**: Itel A80

### Network Conditions
- **Broadband**: 50Mbps down/10Mbps up
- **Throttled**: Fast 3G (1.6Mbps/0.8Mbps)


## 🛠️ Tools

### Testing Tools
- **Test Management**: GitHub Projects for test case tracking
- **Accessibility**: axe DevTools, WAVE, NVDA screen reader
- **Performance**:  Chrome DevTools
- **API Testing**: Browser DevTools for network monitoring
- **Cross-browser**: BrowserStack for compatibility testing


### Browser Extensions
- axe DevTools for accessibility testing
- WAVE Evaluation Tool for a11y audit
- React Developer Tools for component inspection
- LocalStorage Manager for data persistence testing

### Screen Readers
- NVDA on Windows
- VoiceOver on macOS
- JAWS for critical path verification

## ⚠️ Risks and Mitigations

| Risk | Impact | Probability | Mitigation Strategy |
|------|--------|-------------|---------------------|
| **Payment Gateway Sandbox Instability** | High | Medium | Maintain multiple test accounts; document workarounds |
| **localStorage Quota Limitations** | Medium | High | Test with large cart datasets; validate error handling |
| **Cross-browser CSS Rendering Issues** | Medium | High | Early compatibility testing; use progressive enhancement |
| **Accessibility Compliance Gaps** | High | High | Integrate a11y testing throughout development sprints |
| **Performance Regression from Lazy Loading** | Medium | Medium | Establish performance budgets; monitor Core Web Vitals |
| **React Router Navigation Bugs** | High | Low | Comprehensive route testing with various user journeys |

### Risk-Based Testing Focus
Priority will be given to:
1. Checkout and payment flow (high business impact)
2. Accessibility compliance (legal requirement) 
3. Cross-browser functionality (user experience)
4. Data persistence (data integrity)

## 🧪 Test Types

### Functional Testing
- **Happy Path**: Complete user journeys from catalog to order confirmation
- **Edge Cases**: Empty states, out-of-stock scenarios, payment failures
- **Error Handling**: Invalid inputs, network failures, storage quota exceeded
- **Integration**: Component interactions and data flow validation

### Accessibility Testing (WCAG 2.1 AA)
- **Keyboard Navigation**: Full tab order, focus management, ESC key functionality
- **Screen Reader Compatibility**: NVDA/VoiceOver with meaningful announcements
- **Color Contrast**: Text and interactive elements meet 4.5:1 ratio
- **ARIA Labels**: Form inputs, modal dialogs, dynamic content updates
- **Mobile Accessibility**: Touch target sizes, zoom compatibility

### Performance Testing
- **Lighthouse Metrics**: LCP ≤ 2.5s, TTI ≤ 1s, CLS ≤ 0.1
- **Image Optimization**: Lazy loading effectiveness, appropriate sizing
- **Bundle Analysis**: React component loading efficiency
- **Storage Performance**: localStorage operations under load

### Compatibility Testing
- **Browser Matrix**: Latest 2 versions of major browsers
- **Responsive Design**: Breakpoint validation across devices
- **JavaScript Features**: ES6+ compatibility fallbacks
- **CSS Support**: Flexbox/Grid layout consistency

### Hygiene & Security Testing
- **XSS Prevention**: Input sanitization, safe content rendering
- **Data Validation**: Form inputs, URL parameters, localStorage data
- **Authentication**: Route guarding, role-based access controls
- **Error Handling**: Graceful degradation, informative messages

## 🚪 Entry/Exit Criteria

### Entry Criteria (Prerequisites for Testing)
- ✅ Development build deployed to test environment
- ✅ Paystack sandbox credentials configured and validated
- ✅ Test dataset with 50+ books available in catalog
- ✅ Accessibility testing tools installed and configured
- ✅ Test cases reviewed and approved by team
- ✅ Performance benchmarking baseline established

### Exit Criteria (Completion Requirements)
- ✅ All critical and major severity defects resolved
- ✅ 100% of P1 test cases executed with 95% pass rate
- ✅ WCAG 2.1 AA compliance achieved for all user journeys
- ✅ Performance budgets met across all measured metrics
- ✅ Cross-browser testing completed on Priority 1 browsers
- ✅ Checkout flow successfully processes test transactions
- ✅ Team consensus on production readiness
- ✅ Final test report approved by Test Manager

### Team Roles and communication plan

| Role | Name | Email |
|------|------|-------|
| Test Manager | Wamahiga Ng'anga | wmahiganganga@gmail.com |
| Risk Analyst | Lodrick Kibochi | kibochilodrick@gmail.com |
| Test Executor | Vianne Ndagire | karmaviann@gmail.com |

### Communication plan
Communication among the team members will be held via Whatsapp and zoom for meetings and screensharing as we collaborate to work on the project testing.


**Test Manager:** Wamahiga Ng'ang'a
**Date:** 11/03/2025
