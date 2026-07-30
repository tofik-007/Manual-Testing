# Test Plan — Sauce Demo E-Commerce App

## 1. Objective
Validate the core functionality of the Sauce Demo web application
(https://www.saucedemo.com), a demo e-commerce site, covering login,
product browsing/sorting, cart management, and checkout.

## 2. Scope

### In Scope
- Login (valid/invalid credentials, locked-out user)
- Product listing (sort, view details)
- Cart (add/remove items, cart badge count)
- Checkout (form validation, order completion)

### Out of Scope
- Payment gateway integration (Sauce Demo checkout is simulated, no real
  payment processing)
- Performance/load testing
- Mobile responsiveness

## 3. Test Approach
- **Manual, black-box scripted testing** for core flows (login, cart,
  checkout) using written test cases.
- **Exploratory testing** (time-boxed session) to catch issues scripted
  cases might miss.
- Test case design techniques applied: **Equivalence Partitioning (EP)**
  and **Boundary Value Analysis (BVA)** on the checkout form fields
  (Zip/Postal Code and First Name).

## 4. Test Environment
- **URL:** https://www.saucedemo.com
- **Browser(s):** Chrome (latest), Firefox (latest)
- **Test accounts provided by the app:**
  - `standard_user` — normal login
  - `locked_out_user` — should be blocked
  - `problem_user` — known to have UI bugs (useful for finding real issues)
  - `performance_glitch_user` — slow-loading, but should still function
  - Password for all: `secret_sauce`

## 5. Entry Criteria
- Site is accessible and loading correctly.
- Known test accounts are confirmed working (at least `standard_user`).
- Test cases have been written and reviewed.

## 6. Exit Criteria
- All planned test cases executed.
- No unresolved **Critical** or **High** severity defects.
- Exploratory session completed and logged.
- Test Summary Report completed.

## 7. Risks & Assumptions
- Sauce Demo is a public demo app maintained for testing practice; it may
  contain **intentional bugs** (that's expected and part of the exercise).
- No real backend/database exists — data does not persist across sessions
  in the way a production app would.

## 8. Deliverables
1. This Test Plan
2. Test Case spreadsheet (40–60 cases)
3. Exploratory Testing Session Log
4. Bug Reports (one per confirmed issue)
5. Test Summary Report
