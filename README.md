# Agentic AI Security Platforms: Research Notes

Independent research on AI platforms that run penetration tests on their own.

It compares seven vendors, sets out what they share and where they differ, and covers what it takes to build a basic version yourself.

| | |
|---|---|
| **Vendors** | Tenzai, HackerOne (H1), XBOW, Terra Security, CodeAnt AI, Armadin, CyCognito |
| **As of** | 10 November 2026 |
| **Sources** | Public only: vendor pages, partner and investor news, independent studies |

---

## Repository Map

```text
Agentic-AI-MyResearch/
│
├── agentic-ai-security-comparison.md             Who scores how, and why
│     ├── Part A: slide-ready blocks              Summary, scoring, vendor cards, selection guide
│     └── Part B: detailed reference              Evidence register, per-cell score justification
│
├── agentic-ai-similarities-differentiators.md    What they share, what sets each apart
│     ├── Similarities
│     ├── Key differentiators (per vendor)
│     └── Official reference library
│
└── agentic-ai-security-learnings-and-replica.md  What I learned, and how to build a basic one
      ├── Top learnings
      ├── Building blocks and model choices
      ├── Working with GUI tools like Burp Suite
      └── Architecture and the gap to commercial products
```

## Suggested Reading Order

```text
 ┌──────────────────────┐     ┌──────────────────────┐     ┌──────────────────────┐
 │  1. Comparison       │ ──> │  2. Similarities and │ ──> │  3. Learnings and    │
 │     Who leads        │     │     Differentiators  │     │     Replica          │
 │     and why          │     │     How they differ  │     │     How to build one │
 └──────────────────────┘     └──────────────────────┘     └──────────────────────┘
```

## Scores at a Glance

Eight criteria, each scored 1 to 5, equal weights, maximum 40.

```text
 Vendor            Score   0        10        20        30        40
                           |---------|---------|---------|---------|
 Tenzai              35    ███████████████████████████████████░░░░░
 HackerOne (H1)      35    ███████████████████████████████████░░░░░
 XBOW                34    ██████████████████████████████████░░░░░░
 Terra Security      33    █████████████████████████████████░░░░░░░
 CodeAnt AI          29    █████████████████████████████░░░░░░░░░░░
 Armadin             27    ███████████████████████████░░░░░░░░░░░░░
 CyCognito           23    ███████████████████████░░░░░░░░░░░░░░░░░
```

| Code | Criterion | A high score means |
|---|---|---|
| C1 | Surface coverage | Web, API, cloud, network and AI apps tested |
| C2 | Agentic depth | Autonomous planning, chaining, continuous runs |
| C3 | Finding validation | Exploit proof, low false positives |
| C4 | Safety and governance | Scope controls, oversight, audit trail |
| C5 | Remediation loop | Fix guidance, ticketing, retest, mitigation |
| C6 | Compliance readiness | Certifications, auditor-accepted reports |
| C7 | Maturity | GA status, customers, ecosystem |
| C8 | Public evidence | Benchmarks, white papers, independent checks |

The full breakdown, including a coverage-weighted score, is in [the comparison file](agentic-ai-security-comparison.md).

## How to Read the Evidence

- Every claim carries an evidence ID such as `TZ1` or `XB9`, listed with its link in section B1 of the comparison
- **O** means the vendor's own page, **P** a partner or investor, **I** an independent source
- "Official" means the vendor said it, not that anyone verified it
