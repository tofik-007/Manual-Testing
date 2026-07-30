# Test Summary Report — Sauce Demo E-Commerce App

**Date:** July 29, 2026
**Tester:** Taufik Sumara
**Build/Environment:** https://www.saucedemo.com, Chrome
**Session Duration:** 7:18 PM – 7:50 PM (32 minutes)

## 1. Summary of Testing
- Total test cases planned: 44
- Total test cases executed: 44 (plus additional exploratory coverage
  across `problem_user`, `visual_user`, `error_user`, and
  `performance_glitch_user` accounts, beyond the original scripted scope)
- Pass: 33   Fail: 11   Blocked: 0   Not Executed: 0
- Exploratory session completed: Yes — extended to ~45 minutes to cover
  account-specific behavior across 4 non-standard test accounts

## 2. Defect Summary

| Severity | Count | Open | Closed |
|----------|-------|------|--------|
| Critical | 0 | 0 | 0 |
| High | 3 | 3 | 0 |
| Medium | 7 | 7 | 0 |
| Low | 1 | 1 | 0 |

## 3. Notable Defects
- **BUG-001** — First Name field on checkout accepts invalid input with no validation (Medium/Low)
- **BUG-002** — Last Name field on checkout accepts invalid input with no validation (Medium/Low)
- **BUG-003** — Zip/Postal Code field on checkout accepts invalid input with no validation (Medium/Low)
- **BUG-004** — "Add to Cart" fails entirely for `problem_user` (High/High) — blocks core purchase flow for this account
- **BUG-005** — Product images mismatched under `problem_user` (High/High)
- **BUG-006** — Sort dropdown has no effect for `problem_user` (Medium/Medium)
- **BUG-007** — Cart contents persist across logout and login as a different user (High/High) — session isolation / data integrity issue
- **BUG-008** — Sauce Labs Backpack image swapped for an unrelated image under `visual_user` (Medium/Medium)
- **BUG-009** — Navigation bar tilted / cart icon overlaps sort dropdown under `visual_user` (Medium/Low)
- **BUG-010** — Footer Terms of Service / Privacy Policy links not clickable (Low/Low)
- **BUG-011** — Checkout cannot be completed for `error_user` (High/High) — blocks core purchase flow for this account

_Full write-ups for all 11 defects are in `bug-reports/`._

## 4. Exit Criteria Assessment
- [x] All planned test cases executed
- [ ] No unresolved Critical/High defects — **3 High-severity defects are still open**
- [x] Exploratory session completed and logged

**Exit criteria met?** No. Three High-severity defects remain open, each
blocking a core flow (Add to Cart, Checkout, or cross-user session
isolation). This build would not be release-ready until these are
triaged and resolved.

## 5. Risk Assessment / Recommendation
Testing surfaced three High-severity defects that each independently
block a core purchase flow: Add to Cart fails entirely under
`problem_user`, checkout cannot be completed under `error_user`, and —
most critically — cart contents persist across logout/login between
different users, which is a session-isolation issue rather than a
cosmetic one. In a production system, that last defect would be treated
as a data integrity and privacy risk, not just a functional bug, since it
implies one customer could see another customer's session data.

The remaining defects are concentrated around two patterns: (1)
non-standard test accounts (`problem_user`, `visual_user`) exhibiting
broken core interactions across multiple unrelated features — suggesting
a shared root cause tied to account/session state rather than
independent bugs — and (2) a checkout form with no input validation on
any text field, which is a systemic gap worth fixing holistically rather
than patching field-by-field.

Given the number and severity of blocking defects, I would not recommend
this build for release without further triage, particularly on the
cross-user cart persistence issue (BUG-007).

A few observations were deliberately excluded from the defect count
after evaluation confirmed they were expected demo-app behavior rather
than real bugs: the static cart quantity field, `performance_glitch_user`'s
simulated slowness, and the static payment/shipping info on the checkout
overview page.

## 6. What I'd Test Next With More Time
- Confirm whether cart persistence (BUG-007) also occurs on a hard
  browser refresh, not just logout/login
- Retest "Reset App State" specifically to isolate whether it's broken
  universally or only under `problem_user`
- Cross-browser check in Firefox (this session was Chrome-only)
- Deeper investigation into whether `visual_user`'s layout issue
  (BUG-009) blocks clickability or is purely cosmetic
