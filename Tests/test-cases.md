# 🧪 Test Cases — Book Store App

| ID | Feature Area | Title | Pre-conditions | Steps | Expected Result | Post-conditions | Priority | Severity | Evidence |
|----|--------------|-------|----------------|-------|----------------|-----------------|----------|----------|----------|
| TC-CAT-01 | Catalog & Discovery | Browse Catalog | App running; user on /catalog | 1. Open /catalog page<br>2. Scroll through book grid | All books load correctly; images visible; responsive layout | None | High | Major | tests/evidence/TC-CAT-01.png |
| TC-CAT-02 | Catalog & Discovery | Search by Title | App running; user on /catalog | 1. Enter book title in search<br>2. Press Enter | Only matching books appear; no errors | None | High | Major | tests/evidence/TC-CAT-02.png |
| TC-CART-01 | Cart Management | Add Item to Cart | User on /catalog | 1. Click "Buy Now" on a book | Book added to cart; cart count updated | Cart updated in localStorage | High | Critical | tests/evidence/TC-CART-01.png |
| TC-CART-02 | Cart Management | Update Quantity | Item in cart | 1. Go to /cart<br>2. Increase quantity | Subtotal updated correctly; cart persists | localStorage updated | Medium | Major | tests/evidence/TC-CART-02.png |
| TC-CART-03 | Cart Management | Remove Item | Item in cart | 1. Go to /cart<br>2. Remove item | Item disappears; subtotal updated | localStorage updated | Medium | Major | tests/evidence/TC-CART-03.png |
| TC-PAY-01 | Checkout & Payments | Checkout Flow | Items in cart; user logged in | 1. Go to /checkout<br>2. Complete form<br>3. Submit | Order confirmation shown; localStorage updated | Order saved in localStorage | High | Critical | tests/evidence/TC-PAY-01.png |
| TC-PAY-02 | Checkout & Payments | Paystack Payment | Items in cart; checkout page loaded | 1. Click "Pay"<br>2. Complete sandbox flow | Payment processed; confirmation visible | GatewayRef saved | High | Critical | tests/evidence/TC-PAY-02.png |
| TC-ADMIN-01 | Admin | Access Admin Page | User logged in as admin | 1. Go to /admin | Admin page loads | None | Medium | Major | tests/evidence/TC-ADMIN-01.png |
| TC-ADMIN-02 | Admin | Unauthorized Access | User logged in as non-admin | 1. Go to /admin | Access denied; redirect | None | High | Major | tests/evidence/TC-ADMIN-02.png |
| TC-USER-01 | User & Session | localStorage Persistence | User has active session | 1. Refresh page | Cart and session persist | Data unchanged in localStorage | Medium | Major | tests/evidence/TC-USER-01.png |
| TC-TECH-01 | Routing | Navigate Pages | App running | 1. Go to /catalog<br>2. Navigate to /cart<br>3. Navigate to /checkout | Correct pages load; URL updates | None | Medium | Minor | tests/evidence/TC-TECH-01.png |
| TC-A11Y-01 | Accessibility | Keyboard Navigation | App running | 1. Use Tab to navigate<br>2. Use Enter to activate buttons | Focus moves logically; interactive elements accessible | None | High | Critical | tests/evidence/TC-A11Y-01.png |
| TC-A11Y-02 | Accessibility | Screen Reader | App running | 1. Enable NVDA/VoiceOver<br>2. Navigate catalog and cart | All announcements meaningful; ARIA labels correct | None | High | Critical | tests/evidence/TC-A11Y-02.png |
| TC-PERF-01 | Performance | LCP Measurement | App running | 1. Load /catalog | LCP ≤ 2.5s on desktop | None | High | Major | tests/evidence/TC-PERF-01.png |
| TC-PERF-02 | Performance | Checkout TTI | App running; items in cart | 1. Go to /checkout | TTI ≤ 1s for critical interactions | None | High | Major | tests/evidence/TC-PERF-02.png |
