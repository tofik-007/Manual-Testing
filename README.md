<div align="center">

# 🧪 Manual & Exploratory QA Testing — Sauce Demo

### End-to-end manual QA project covering test planning, scripted test cases, exploratory testing, and defect reporting on a live e-commerce demo application.

[![Test Cases](https://img.shields.io/badge/Test%20Cases-44-blue?style=for-the-badge)](./02_Test_Cases.csv)
[![Bugs Found](https://img.shields.io/badge/Bugs%20Found-11-red?style=for-the-badge)](./bug-reports)
[![High Severity](https://img.shields.io/badge/High%20Severity-3-critical?style=for-the-badge)](./bug-reports)
[![Status](https://img.shields.io/badge/Status-Complete-success?style=for-the-badge)]()

[![Manual Testing](https://img.shields.io/badge/Manual%20Testing-black?style=flat-square)]()
[![Exploratory Testing](https://img.shields.io/badge/Exploratory%20Testing-black?style=flat-square)]()
[![Bug Reporting](https://img.shields.io/badge/Bug%20Reporting-black?style=flat-square)]()
[![EP%2FBVA](https://img.shields.io/badge/EP%20%2F%20BVA-black?style=flat-square)]()
[![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown&logoColor=white)]()

</div>

---

## 📌 Overview

This project demonstrates a complete manual QA process against
[**Sauce Demo**](https://www.saucedemo.com), a public e-commerce demo
site built for QA practice. It covers the full testing lifecycle: test
planning → scripted test case design → exploratory testing → defect
reporting → release recommendation — the same workflow expected in a
real QA role.

Testing intentionally went beyond the standard login, and dug into
Sauce Demo's built-in "problem" accounts (`problem_user`, `visual_user`,
`error_user`, `performance_glitch_user`) to surface deeper functional,
visual, and data-integrity defects.

> 🔍 **Headline finding:** Cart contents persist across logout and
> login as a *different user* — a session-isolation / data-integrity
> issue, not just a cosmetic bug. See [`BUG-007`](./bug-reports/BUG-007.md).

---

## 🗂️ Repository Structure

```
qa-repo/
├── README.md                          → you are here
├── 01_Test_Plan.md                    → scope, approach, entry/exit criteria
├── 02_Test_Cases.csv                  → 44 test cases (login, cart, checkout, sort)
├── 03_Exploratory_Session_Log.md      → charter-based exploratory session
├── 05_Test_Summary_Report.md          → final results, risk & release recommendation
├── Test_Summary_Report.pdf            → formatted, shareable version
└── bug-reports/
    ├── BUG-001.md ... BUG-011.md      → individual defect reports
    └── _TEMPLATE.md                   → reusable bug report format
```

---

## 🧭 Approach

| Phase | What I Did |
|---|---|
| **1. Test Planning** | Defined scope, approach, and entry/exit criteria before touching the app |
| **2. Test Case Design** | Wrote 44 test cases covering login, product sort, cart, and checkout — applied **Equivalence Partitioning** and **Boundary Value Analysis** explicitly on checkout form fields |
| **3. Scripted Execution** | Ran all 44 cases against the standard flow |
| **4. Exploratory Testing** | Time-boxed session extended across 4 non-standard Sauce Demo accounts to surface deeper issues |
| **5. Defect Triage** | Evaluated every anomaly for *real bug vs. expected demo behavior* before logging it |
| **6. Reporting** | Wrote individual bug reports + a full Test Summary Report with a release-readiness call |

---

## 🐞 Defect Summary

| Severity | Count | Open |
|:---:|:---:|:---:|
| 🔴 Critical | 0 | 0 |
| 🟠 High | 3 | 3 |
| 🟡 Medium | 7 | 7 |
| 🟢 Low | 1 | 1 |

**Top 3 defects:**

| ID | Title | Severity |
|---|---|:---:|
| [BUG-007](./bug-reports/BUG-007.md) | Cart persists across logout/login as a different user | 🟠 High |
| [BUG-004](./bug-reports/BUG-004.md) | "Add to Cart" fails entirely for `problem_user` | 🟠 High |
| [BUG-011](./bug-reports/BUG-011.md) | Checkout cannot be completed for `error_user` | 🟠 High |

Full breakdown of all 11 defects: [`bug-reports/`](./bug-reports)

---

## 🎯 Key Skills Demonstrated

- ✅ Test Plan authoring (scope, entry/exit criteria)
- ✅ Test case design techniques — **Equivalence Partitioning**, **Boundary Value Analysis**
- ✅ Charter-based exploratory testing
- ✅ Standardized bug reporting (severity vs. priority, repro steps, evidence)
- ✅ Root-cause pattern recognition across accounts (not just isolated bug-filing)
- ✅ Risk-based release recommendation

---

## 📄 Reports

- 📋 [Test Plan](./01_Test_Plan.md)
- 📊 [Test Cases (CSV)](./02_Test_Cases.csv)
- 🔎 [Exploratory Session Log](./03_Exploratory_Session_Log.md)
- 📈 [Test Summary Report (Markdown)](./05_Test_Summary_Report.md)
- 📄 [Test Summary Report (PDF)](./Test_Summary_Report.pdf)

---

## 🚀 What's Next

- Automate the smoke-path flow (login → add to cart → checkout) with **Selenium + Python**
- Investigate whether `problem_user` / `visual_user` failures share a
  single root cause rather than being independent defects
- Add visual regression screenshots for the image/layout defects

---

<div align="center">

**Tester:** Taufik Sumara &nbsp;|&nbsp; **Date:** July 29, 2026

⭐ *If this project is useful as a QA portfolio reference, feel free to star it.*

</div>
