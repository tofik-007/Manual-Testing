# Exploratory Testing Session Log

**Charter:** Explore the checkout flow and cart behavior for edge cases and
unexpected states not covered by scripted test cases, with a focus on
Sauce Demo's built-in non-standard accounts (`problem_user`,
`visual_user`, `error_user`, `performance_glitch_user`).

**Tester:** Taufik Sumara
**Date:** July 29, 2026
**Duration:** ~45 minutes (extended beyond the original 30-min charter
after multiple account-specific issues surfaced)
**Environment:** Chrome, https://www.saucedemo.com

---

## Session Notes

| Account | Action Taken | Observation |
|---|---|---|
| standard_user | Increased quantity of an item in cart | Quantity field is static, not editable — no stepper/input control (design limitation, not a bug) |
| standard_user | Checked footer links | "Terms of Service" and "Privacy Policy" links are not clickable (BUG-011... wait see bug list) |
| problem_user | Attempted to add items to cart | Add to Cart does not work at all — items never get added |
| problem_user | Changed sort dropdown | Product order does not change regardless of option selected |
| problem_user | Product images | Images are mismatched across products |
| visual_user | Reviewed product images | Sauce Labs Backpack image is swapped with an unrelated (dog) image |
| visual_user | Reviewed navigation bar layout | Nav bar appears tilted; cart icon overlaps the sort dropdown position |
| error_user | Attempted full checkout | Checkout cannot be completed |
| performance_glitch_user | Logged in and browsed | Noticeably slow — appears to be intentional simulated latency rather than a defect; confirmed it eventually loads |
| Cross-account | Logged in as User A, added items, logged out, logged in as User B | Cart items from User A persist into User B's session — cart does not reset on login as a different user |
| Checkout form | Entered invalid data in First Name, Last Name, Zip fields | All three fields accept invalid/unformatted input with no validation |
| Checkout overview | Compared payment/shipping info across multiple orders/users | Payment and shipping info is static/hardcoded — expected behavior for a demo app with no real backend |

## Bugs Found This Session
See `bug-reports/` for full write-ups.

- BUG-001 — First Name field accepts invalid input, no validation
- BUG-002 — Last Name field accepts invalid input, no validation
- BUG-003 — Zip/Postal Code field accepts invalid input, no validation
- BUG-004 — Add to Cart fails entirely for problem_user
- BUG-005 — Product images mismatched under problem_user
- BUG-006 — Sort dropdown has no effect under problem_user
- BUG-007 — Cart contents persist across logout/login as a different user
- BUG-008 — Sauce Labs Backpack image swapped under visual_user
- BUG-009 — Navigation bar tilted / cart icon overlaps sort dropdown under visual_user
- BUG-010 — Footer Terms of Service / Privacy Policy links not clickable
- BUG-011 — Checkout cannot be completed for error_user

## Non-Bug Observations
_Evaluated and excluded as defects — logged here for completeness._

- Cart quantity field is not editable (design limitation, not a bug)
- `performance_glitch_user` login/browsing is slow — appears to be
  intentional simulated latency, not a defect
- Payment/Shipping info on checkout overview is static regardless of
  user or order — expected for a demo app with no real backend

## Areas Covered
- [x] Standard flow (login, cart, checkout)
- [x] problem_user across multiple features
- [x] visual_user across multiple features
- [x] error_user checkout
- [x] performance_glitch_user
- [x] Cross-user session/cart persistence
- [x] Footer/navigation links

## Follow-Up / Out of Time
- Confirm whether BUG-007 (cart persistence) also survives a hard
  browser refresh, not just logout/login
- Retest "Reset App State" specifically under problem_user to confirm
  whether it's affected by the same root cause as Add to Cart/Sort
- Cross-browser check in Firefox (this session was Chrome-only)
