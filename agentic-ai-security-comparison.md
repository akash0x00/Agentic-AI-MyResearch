# Agentic AI Security Platforms: Comparison and Scoring

| Item | Detail |
|---|---|
| Vendors | Armadin, XBOW, Terra Security, Tenzai, CyCognito, CodeAnt AI, HackerOne (H1) |
| Date | 10 November 2026 |
| Revision | 4 (restructured for slide reuse and reference) |

## INFO

- Part A : slide-ready blocks, one slide each, copy them straight across
- Part B : the detailed reference behind Part A, with a score justification for every cell and all the links
- Evidence IDs : codes like `TZ1` or `HO5`, drop them in as slide footnotes, each one links out in section B1
- Source types : **O** the vendor's own page, **P** a partner or investor, **I** an independent source
- Official : means the vendor said it, not that anyone checked it

---

# Part A: Slide-Ready Blocks

## A1. Executive Summary

**Key message:** Tenzai and HackerOne lead on public evidence. XBOW is close behind but tests web and API only.

| Rank | Vendor | Score (of 40) | Coverage-weighted (of 45) |
|---|---|---|---|
| 1 | Tenzai | 35 | 40 |
| 1 | HackerOne (H1) | 35 | 39 |
| 3 | XBOW | 34 | 36 |
| 4 | Terra Security | 33 | 37 |
| 5 | CodeAnt AI | 29 | 33 |
| 6 | Armadin | 27 | 31 |
| 7 | CyCognito | 23 | 26 |

Footnote: Coverage-weighted counts surface coverage twice. Scores are judgment based on public sources.

## A2. One-Line Positioning

**Key message:** The seven vendors solve different problems. Only five are direct agentic pentest competitors.

| Vendor | Positioning | Best fit |
|---|---|---|
| Tenzai | Autonomous AI hacker | Apps, APIs, AI apps and networks with built-in mitigation |
| HackerOne (H1) | Agentic platform plus human researchers | Accredited, auditor-accepted testing at scale |
| XBOW | Autonomous offensive security | Deep web and API testing with proven exploits |
| Terra Security | Agentic pentest with Human-on-the-Loop | Governed continuous testing across web, AI, network |
| Armadin | Agentic attacker swarm | Large attack campaigns across perimeter and internal network |
| CodeAnt AI | Code review plus agentic pentest | Developer workflow, code-aware testing |
| CyCognito | External exposure management | Unknown external assets; AI pentest not GA |

## A3. Evaluation Method

**Key message:** Eight criteria, scored 1 to 5, equal weights, maximum 40.

| Code | Criterion | High score means |
|---|---|---|
| C1 | Surface coverage | Web, API, cloud, network and AI apps tested |
| C2 | Agentic depth | Autonomous planning, chaining, continuous runs |
| C3 | Finding validation | Exploit proof, low false positives |
| C4 | Safety and governance | Scope controls, oversight, audit trail |
| C5 | Remediation loop | Fix guidance, ticketing, retest, mitigation |
| C6 | Compliance readiness | Certifications, auditor-accepted reports |
| C7 | Maturity | GA status, customers, ecosystem |
| C8 | Public evidence | Benchmarks, white papers, independent checks |

## A4. Scoring Matrix

**Key message:** No vendor leads on every criterion. Strengths differ by coverage, governance and proof.

| Vendor | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | Total |
|---|---|---|---|---|---|---|---|---|---|
| Tenzai | 5 | 5 | 4 | 5 | 5 | 4 | 3 | 4 | **35** |
| HackerOne (H1) | 4 | 4 | 5 | 4 | 4 | 5 | 5 | 4 | **35** |
| XBOW | 2 | 5 | 5 | 4 | 4 | 4 | 5 | 5 | **34** |
| Terra Security | 4 | 4 | 4 | 5 | 5 | 5 | 3 | 3 | **33** |
| CodeAnt AI | 4 | 4 | 4 | 2 | 4 | 4 | 4 | 3 | **29** |
| Armadin | 4 | 5 | 4 | 3 | 3 | 2 | 3 | 3 | **27** |
| CyCognito | 3 | 3 | 4 | 2 | 3 | 3 | 2 | 3 | **23** |

Footnote: Justification for every cell is in section B2.

## A5. Attack Surface Coverage

**Key message:** Tenzai and HackerOne list the widest coverage. XBOW is web and API only.

| Vendor | Web | API | Cloud | Ext. network | Int. network | AI apps |
|---|---|---|---|---|---|---|
| Tenzai | Yes | Yes | Not listed | Yes | Yes | Yes |
| HackerOne (H1) | Yes | Yes | Yes | Yes | Yes | Yes |
| XBOW | Yes | Yes | No | No | No | No |
| Terra Security | Yes | Named | Named | Preview | Preview | Yes |
| Armadin | Yes | Not stated | Partial | Yes | Yes | Not stated |
| CodeAnt AI | Yes | Yes | Yes | Yes | Limited | Not stated |
| CyCognito | External | External | External | Yes | No | Exposed assets |

Footnote: Sources TZ1, HO4, XB1, TE1, TE6, AR4, CA1, CA6, CY3. HackerOne coverage includes human researchers. Tenzai also tests mobile apps.

## A6. Operating Model and Status

**Key message:** Autonomy and maturity trade off. The most autonomous vendors are the youngest.

| Vendor | Human role | Product status |
|---|---|---|
| Tenzai | Sets rules of engagement, can steer tests | Enterprise subscription; launched Nov 2025 |
| HackerOne (H1) | Researchers validate and handle complex chains | H1 Platform live since June 2026; about 1,300 organisations |
| XBOW | Optional approval on first run | Available direct and via four cloud marketplaces |
| Terra Security | Human-on-the-Loop at decision points | Web and AI live; network modules in preview |
| Armadin | Safety model trained with expert feedback | In production for unnamed large customers |
| CodeAnt AI | Researcher vetting per engagement | Available; free first pentest |
| CyCognito | Not described for AI layer | AI pentest with design partners; no GA date |

Footnote: Sources TZ2, TZ14, HO1, HO3, XB3, XB7, TE1, TE6, AR5, AR2, CA1, CA6, CY4.

## A7. Vendor Card: Tenzai (35)

**Key message:** Broadest autonomous coverage with a full find-to-mitigate loop. Youngest track record.

Strengths
- Tests web, mobile, API, AI and MCP, external and internal network (TZ1)
- Network-level scope enforcement and per-action checks (TZ2)
- WAF rules, fix guidance, tickets and retest in one loop (TZ4, TZ5)
- SOC 2 Type 1 and 2; zero data retention on LLM calls; audit trail (TZ6, TZ7)
- #1 among AI security companies on HackerOne in Q2 2026 (TZ10)

Gaps
- Launched from stealth in November 2025 (TZ14)
- Model providers not fully named on official pages (TZ15)
- No CREST accreditation listed; no public REST API yet (TZ15)

## A8. Vendor Card: HackerOne H1 (35)

**Key message:** Strongest trust and compliance position. Agents plus humans, not agents alone.

Strengths
- Agentic platform across discovery, validation and remediation (HO1)
- Coverage across web, mobile, API, cloud, network, AI/LLM (HO4)
- CREST-accredited; reports for SOC 2, ISO 27001, PCI DSS, DORA (HO5)
- 88% fix-verified accuracy on its benchmark suite (HO6)
- 35+ integrations; retest verifies closure (HO9)

Gaps
- Complex chains still rely on human researchers (HO4)
- Benchmark published without sample sizes (HO6)
- No temporary mitigation such as WAF rules described

## A9. Vendor Card: XBOW (34)

**Key message:** Best public proof for web and API. Scope stops there.

Strengths
- Every finding validated by independent validators before release (XB2)
- Detailed safety controls: scope, impact level, safety judge, action log (XB3)
- #1 on HackerOne with 1,500+ reproducible exploits (XB6)
- Independent study: 31 true positives, 1 false positive (XB11)
- Microsoft and Accenture partnerships (XB8, XB9)

Gaps
- No network, cloud, mobile or AI-system testing listed (XB1)
- Independent study recorded one scan that disabled authentication and deleted a test account (XB12)
- Quote-only pricing (XB7)

## A10. Vendor Card: Terra Security (33)

**Key message:** Best governance design. Network coverage still maturing.

Strengths
- Human-on-the-Loop with per-action logging (TE2, TE4)
- SOC 2 Type II and CREST member; human-signed reports (TE2)
- Remediation with pull requests and temporary firewall rules (TE3)
- Reports accepted by SOC 2, ISO 27001, PCI DSS, HIPAA auditors (TE7)

Gaps
- External and internal network testing in preview (TE5, TE6)
- Initial findings take 1 to 2 weeks (TE7)
- No independent benchmark found

## A11. Vendor Card: Armadin (27)

**Key message:** Largest demonstrated scale of agentic attack. Least official documentation.

Strengths
- Agentic attacker swarm with custom models (AR1)
- 26,000 agents, 17 million actions, 38 validated attack paths in one exercise (AR3)
- Perimeter, internal network and web apps, with no privileged credentials (AR4)
- Every action passes a control layer with a safety model (AR5)

Gaps
- No official source for certifications, pricing, integrations or retest
- Customers and exercise institution unnamed (AR2, AR3)
- No white papers found

## A12. Vendor Card: CodeAnt AI (29)

**Key message:** Code-aware pentesting with transparent pricing. Light on safety documentation.

Strengths
- Code review, SAST, cloud and pentest in one platform (CA1)
- 500+ attack agents; black, gray and white box (CA4)
- From $4,000; no charge without high or critical findings; unlimited retests (CA5)
- SOC 2 Type II and HIPAA (CA2)

Gaps
- Internal network and AD coverage limited (CA6)
- Production safety controls not described
- Comparative evidence is self-published

## A13. Vendor Card: CyCognito (23)

**Key message:** Strong external discovery. Agentic pentest is not generally available.

Strengths
- Continuous AI pentesting across the full external surface (CY1)
- 100,000+ deterministic tests feed the AI layer (CY2)
- Finds exposed AI assets such as MCP servers and LLM endpoints (CY3)
- GigaOm ASM Radar Leader and Outperformer (CY6)

Gaps
- External only; no internal network (CY3)
- Design-partner stage, no GA date (CY4)
- No safety controls or accuracy metrics published for the AI layer

## A14. Selection Guide

**Key message:** Match the vendor to the scope and the governance bar.

| Priority | Shortlist |
|---|---|
| Web and API depth with proven exploits | XBOW, Tenzai |
| Web, API, cloud and network in one platform | Tenzai, HackerOne, Terra Security, Armadin |
| AI governance approval and audit sign-off | HackerOne, Terra Security, Tenzai |
| Fastest path from finding to mitigation | Tenzai, Terra Security |
| Shift-left and developer workflow | CodeAnt AI, HackerOne |
| Unknown external assets and shadow AI | CyCognito |
| Transparent, low entry cost | CodeAnt AI |

## A15. Questions for Every Vendor

**Key message:** Six answers decide the proof of concept.

1. Which surfaces are GA today, and which are preview?
2. What is the measured false-positive rate on customer environments?
3. What approval gates, rate limits and kill switch exist for production testing?
4. Which LLM providers process our data, and what is the retention policy?
5. Are reports accepted by our auditors, and who signs them?
6. What is the time from scan start to first validated finding, and to retest after a fix?

## A16. Limits of This Review

**Key message:** Public-source scoring supports, but does not replace, hands-on evaluation.

- Scores reflect public information on 10 November 2026 and analyst judgment
- Official sources are vendor statements, not independent verification
- Only one independent study exists (Doyensec), and a competitor of XBOW sponsored it
- armadin.com and CyCognito's product page could not be opened from the research environment
- A hands-on internal evaluation carries more weight than this scoring

---

# Part B: Detailed Reference

## B1. Evidence Register

### Tenzai

| ID | Claim | Type | Source |
|---|---|---|---|
| TZ1 | Tests web apps, mobile apps (Android runtime, Android and iOS static), AI apps, agents and MCP tools, APIs, external network, internal network including assumed breach | O | [Product page](https://www.tenzai.com/product) |
| TZ2 | Guardrails: network-level scope enforcement; per-action checks against rules of engagement | O | [Product page](https://www.tenzai.com/product) |
| TZ3 | Black, gray and white box; autonomous, interactive and incremental runs | O | [Product page](https://www.tenzai.com/product) |
| TZ4 | Remediation: validated WAF rules, step-by-step fix guidance, ticket creation, retest | O | [Product page](https://www.tenzai.com/product) |
| TZ5 | WAF mitigation deployable through Akamai and other platforms | O | [Press release](https://www.newswire.com/news/tenzais-ai-hacker-can-now-autonomously-mitigate-what-it-finds) |
| TZ6 | SOC 2 Type 1 and Type 2 | O | [Trust Center](https://trust.tenzai.com/) |
| TZ7 | Zero data retention on LLM calls, tenant isolation, no training on customer data, full audit trail, reasoning trace via MCP | O | [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws) |
| TZ8 | Jira and ServiceNow tickets, OCSF JSON export, MCP server | O | [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws) |
| TZ9 | Hosted on AWS; customer-environment deployment on request | O | [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws) |
| TZ10 | Ranked #1 among AI security companies on HackerOne in Q2 2026; 100+ reports, nearly half high or critical. The linked leaderboard view is filtered, so the result is narrower than the headline | O | [Blog](https://www.tenzai.com/blog/tenzai-hits-1-on-hackerone-in-under-90-days) |
| TZ11 | Top 1% across six CTF platforms | O | [Press release](https://www.newswire.com/news/tenzais-ai-hacker-is-the-first-autonomous-system-to-rank-in-the-top-1-of-global) |
| TZ12 | Expansion into network security; purple-team research with Cortex XDR | P | [Palo Alto Networks](https://www.paloaltonetworks.com/blog/security-operations/fighting-ai-with-ai-palo-alto-networks-and-tenzai-collaborate-to-defeat-autonomous-threats.md/) |
| TZ13 | AI application testing: actors, tools, credentials, guardrails, in one run with web and API | O | [Press release](https://www.tenzai.com/press-releases/tenzai-expands-its-ai-hacker-to-ai-applications) |
| TZ14 | $75M seed; launched from stealth November 2025 | O | [Press release](https://www.tenzai.com/press-releases/tenzai-raises-75-million-in-record-seed-round-to-build-an-ai-hacker-that-secures-code-written-by-ai) |
| TZ15 | Models from Anthropic and OpenAI named; customer API docs on roadmap. Product page says only "frontier and open-weight models" | O | [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws), [Product page](https://www.tenzai.com/product) |

### HackerOne (H1)

| ID | Claim | Type | Source |
|---|---|---|---|
| HO1 | H1 Platform: agentic AI across discovery, validation, prioritisation, remediation, orchestrated by Hai; about 1,300 organisations | O | [Press release](https://www.hackerone.com/press-release/h1-platform-delivers-continuous-threat-exposure-management-ai-scale-validated) |
| HO2 | Always-on agentic testing; white, grey or black box access | O | [Platform](https://www.hackerone.com/platform) |
| HO3 | H1 Continuous Testing: recon, scanning and exploit agents; incremental tests on code changes; failed attempts logged for auditors | O | [Product](https://www.hackerone.com/product/h1-continuous-testing) |
| HO4 | Coverage with agents plus researchers: web, mobile, API, cloud, network, AI/LLM. Researchers handle complex chains | O | [Solution](https://www.hackerone.com/solutions/autonomous-pentesting) |
| HO5 | CREST-accredited; CSA-licensed in Singapore; reports for SOC 2, ISO 27001, PCI DSS, DORA, GDPR | O | [Solution](https://www.hackerone.com/solutions/autonomous-pentesting) |
| HO6 | 88% fix-verified accuracy on its benchmark suite; five-pillar benchmark framework | O | [Engineering blog](https://www.hackerone.com/blog/agentic-ptaas-security-architecture) |
| HO7 | Safety: per-agent tool limits, allowlists, rate controls, isolated containers, tenant-scoped audit trails | O | [Engineering blog](https://www.hackerone.com/blog/agentic-ptaas-security-architecture) |
| HO8 | Agents run against 100+ real-world web targets before launch | O | [Blog](https://www.hackerone.com/blog/agentic-pentesting-real-world-testing) |
| HO9 | 35+ integrations including Jira, ServiceNow, GitHub; retest verifies closure | O | [Solution](https://www.hackerone.com/solutions/autonomous-pentesting) |
| HO10 | Hai is free for all customers; admin on/off switch per agentic product | O | [Docs](https://docs.hackerone.com/en/articles/8887510-hai-ai-security-agent) |
| HO11 | Hai is in scope of HackerOne's own bug bounty; data boundaries described | O | [Docs](https://docs.hackerone.com/en/articles/10908081-hai-security-trust) |
| HO12 | Agentic PTaaS launched January 2026 | O | [Blog](https://www.hackerone.com/blog/agentic-penetration-testing-as-a-service) |

### XBOW

| ID | Claim | Type | Source |
|---|---|---|---|
| XB1 | Tests web applications and APIs, authenticated and unauthenticated, production or staging. No other surface listed | O | [Platform](https://xbow.com/platform) |
| XB2 | Independent validators confirm each exploit before a finding is shown | O | [Platform](https://xbow.com/platform) |
| XB3 | Safety: scope, impact level, rate limits, testing windows, safety judge, command checker, action log, pause, optional human approval on first run | O | [Platform](https://xbow.com/platform) |
| XB4 | Frameworks listed: SOC 2, ISO 27001, ISO 42001, PCI DSS, NIS 2, HIPAA, GDPR | O | [Platform](https://xbow.com/platform) |
| XB5 | Findings to Jira or GitHub with fix suggestion; retest confirms closure | O | [Brief](https://xbow.com/briefs/xbow-overview) |
| XB6 | #1 on HackerOne with 1,500+ reproducible exploits | O | [Brief](https://xbow.com/briefs/xbow-overview) |
| XB7 | Usage-based, quote-only pricing; sold via AWS, Google, Oracle, Microsoft marketplaces | O | [Pricing](https://xbow.com/pricing) |
| XB8 | Microsoft Security Copilot and Sentinel integration | O | [News](https://xbow.com/news/xbow-penetration-testing-microsoft-security-ecosystem) |
| XB9 | Accenture strategic investment; integration into Cyber.AI | P | [Accenture newsroom](https://newsroom.accenture.com/news/2026/accenture-invests-in-xbow-to-advance-continuous-offensive-security-testing-and-exposure-management) |
| XB10 | White papers on portfolio-scale testing and PHP2shell | O | [White paper 1](https://xbow.com/whitepapers/how-to-scale-offensive-security-across-your-application-portfolio), [White paper 2](https://xbow.com/whitepapers/php2shell-prove-it-dont-assume-it) |
| XB11 | Doyensec study: XBOW 31 true positives and 1 false positive; Aikido 49 and 2. XBOW led on Fider (24 vs 17), Aikido on Photoview (32 vs 7). Sponsored by Aikido | I | [Doyensec report](https://doyensec.com/resources/ComparingAIApplicationSecurityTestingPlatforms_Doyensec.pdf) |
| XB12 | Doyensec study: XBOW's Fider scan disabled authentication and deleted the test account; report came about five days after the scan | I | [Doyensec report](https://doyensec.com/resources/ComparingAIApplicationSecurityTestingPlatforms_Doyensec.pdf) |
| XB13 | $120M Series C at $1B+ valuation | O | [News](https://xbow.com/news/xbow-raises-120m-to-scale) |

### Terra Security

| ID | Claim | Type | Source |
|---|---|---|---|
| TE1 | Continuous agentic pentesting across AI systems, network and web apps with Human-on-the-Loop | O | [Home](https://www.terra.security/) |
| TE2 | SOC 2 Type II; CREST member; reports signed by certified pentesters; per-action logging | O | [Home](https://www.terra.security/) |
| TE3 | Validation Hub, white-box testing, remediation with pull requests, temporary firewall rules | O | [Home](https://www.terra.security/) |
| TE4 | TORCH: pentesters direct and oversee agents in production | O | [Press release](https://www.terra.security/blog/pr-terra-security-redefines-penetration-testing-for-the-ai-era-with-terra-portal) |
| TE5 | External network testing launched in the platform | O | [Blog](https://www.terra.security/blog/external-network-pentesting-with-terra-platform) |
| TE6 | Internal network testing in preview with design partners, July 2026 | O | [Press release](https://www.terra.security/blog/pr-terra-security-announces-internal-network-pentesting) |
| TE7 | Reports accepted by SOC 2, ISO 27001, PCI DSS, HIPAA auditors; initial findings in 1 to 2 weeks | O | [Use case](https://www.terra.security/use-cases/replace-legacy-pentests) |
| TE8 | Research output: CVE-2026-25724 | O | [Research](https://www.terra.security/blog/when-ai-becomes-the-attack-surface-lessons-from-discovering-cve-2026-25724) |
| TE9 | $30M Series A, September 2025 | O | [Blog](https://www.terra.security/blog/terra-security-raises-30m-series-a-to-redefine-penetration-testing-with-agentic-ai) |

### Armadin

| ID | Claim | Type | Source |
|---|---|---|---|
| AR1 | Specialised agents with custom models in an agentic attacker swarm | O | [Press release](https://www.prnewswire.com/news-releases/armadin-secures-record-breaking-189-9m-in-seed-and-series-a-funding-to-combat-the-era-of-ai-driven-hyperattacks-302709318.html) |
| AR2 | Chains low-severity weaknesses into validated kill chains with blast radius; in production for unnamed Fortune 500 and government customers; $445M total funding | O | [Press release](https://www.prnewswire.com/news-releases/armadin-raises-255-5-million-series-b-to-scale-effective-autonomous-security-302895278.html) |
| AR3 | August 2026 exercise: 26,000 agents, 1,300 attacks, 17 million actions, 25,000+ services, 238 findings, 38 validated attack paths. Institution unnamed | O | [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html) |
| AR4 | Exercise covered external perimeter, internal network and web applications, with no privileged credentials, whitelisting or source access | O | [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html) |
| AR5 | Every action runs through a control layer supervised by a safety model trained with expert human feedback | O | [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html) |
| AR6 | Coverage across external assets, cloud, identity, internal networks and applications | P | [a16z](https://a16z.com/announcement/investing-in-armadin/) |
| AR7 | Trust center exists; contents not readable in this review | O | [Trust Center](https://trust.armadin.com/) |

### CodeAnt AI

| ID | Claim | Type | Source |
|---|---|---|---|
| CA1 | AI code review, SAST, SCA, CSPM, IaC, attack surface management and black-box and white-box pentesting in one platform | O | [Home](https://codeant.ai/) |
| CA2 | SOC 2 Type II and HIPAA; trust center | O | [Home](https://codeant.ai/), [Trust Center](https://codeantai.trust.site/) |
| CA3 | 200+ CVEs disclosed; 12K+ pentests; free first pentest | O | [Home](https://codeant.ai/) |
| CA4 | 500+ attack agents; black, gray, white box; PR-level pentest; findings with working proof of concept | O | [Blog](https://codeant.ai/blogs/automated-penetration-testing-2026) |
| CA5 | From $4,000; no charge without high or critical findings; report in 48 hours; unlimited retests | O | [Blog](https://codeant.ai/blogs/best-ai-penetration-testing-platforms) |
| CA6 | Internal network and AD coverage limited; human validation per engagement | O | [Blog](https://codeant.ai/blogs/best-ai-penetration-testing-platforms) |
| CA7 | White paper and benchmark pages | O | [White paper](https://codeant.ai/white-paper), [Benchmark](https://codeant.ai/benchmark) |

### CyCognito

| ID | Claim | Type | Source |
|---|---|---|---|
| CY1 | Continuous AI pentesting across the external surface, fed by three modules and a Target Graph | O | [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/) |
| CY2 | 100,000+ deterministic tests; validated AI chains become new deterministic tests | O | [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/) |
| CY3 | Agents cover web apps, APIs, AI/LLM endpoints, cloud, VPNs, OT/IT on the external surface | O | [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/) |
| CY4 | Design-partner stage; no GA date | O | [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/) |
| CY5 | SaaS, no agents or network access required; prioritises by validated exploitability and business context | O | [Solution](https://www.cycognito.com/solutions/external-exposure-management/) |
| CY6 | Named Leader and Outperformer in GigaOm ASM Radar | O | [Home](https://www.cycognito.com/) |
| CY7 | White paper: Rethinking Penetration Testing | O | [White paper](https://www.cycognito.com/resources/white-papers/rethinking-penetration-testing/) |

## B2. Score Justification per Cell

### Tenzai (35)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 5 | Web, mobile, API, AI and MCP, external and internal network | TZ1 |
| C2 Agentic depth | 5 | Autonomous end to end, chains across layers, incremental runs | TZ3, TZ13 |
| C3 Validation | 4 | Reproducible exploits and accepted bounty reports; no false-positive rate published | TZ10, TZ7 |
| C4 Safety | 5 | Network-level scope enforcement, per-action checks, audit trail, zero retention | TZ2, TZ7 |
| C5 Remediation | 5 | WAF rules, fix guidance, tickets, retest | TZ4, TZ5, TZ8 |
| C6 Compliance | 4 | SOC 2 Type 1 and 2; no CREST accreditation | TZ6 |
| C7 Maturity | 3 | Launched November 2025; API docs on roadmap | TZ14, TZ15 |
| C8 Evidence | 4 | HackerOne and CTF results, partner research; all vendor-reported | TZ10, TZ11, TZ12 |

### HackerOne H1 (35)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 4 | All surfaces with humans; continuous agents focus on applications | HO4, HO3 |
| C2 Agentic depth | 4 | Agentic across the lifecycle; complex chains go to researchers | HO1, HO2, HO4 |
| C3 Validation | 5 | Exploit agents plus expert verification; 88% fix-verified accuracy | HO3, HO6 |
| C4 Safety | 4 | Allowlists, rate controls, isolation, audit trails; human review steps not detailed | HO7, HO11 |
| C5 Remediation | 4 | 35+ integrations, fix guidance, retest; no temporary mitigation | HO9 |
| C6 Compliance | 5 | CREST accreditation, CSA licence, reports for major frameworks | HO5 |
| C7 Maturity | 5 | About 1,300 organisations; platform GA | HO1, HO12 |
| C8 Evidence | 4 | Benchmark framework and 100+ real targets; no sample sizes | HO6, HO8 |

### XBOW (34)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 2 | Web applications and APIs only | XB1 |
| C2 Agentic depth | 5 | Fully autonomous assessment with chained exploits | XB1, XB2 |
| C3 Validation | 5 | Independent validators; independent study shows 1 false positive in 32 findings | XB2, XB11 |
| C4 Safety | 4 | Detailed controls; one destructive incident in the independent study | XB3, XB12 |
| C5 Remediation | 4 | Fix suggestions, ticketing, retest; no temporary mitigation | XB5 |
| C6 Compliance | 4 | Frameworks listed; own certificates to confirm via trust center | XB4 |
| C7 Maturity | 5 | Four cloud marketplaces, Microsoft and Accenture partnerships | XB7, XB8, XB9 |
| C8 Evidence | 5 | HackerOne ranking, white papers, independent study | XB6, XB10, XB11 |

### Terra Security (33)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 4 | Web and AI live; network in preview; API and cloud named only | TE1, TE5, TE6 |
| C2 Agentic depth | 4 | Agent swarm with human checkpoints | TE1, TE4 |
| C3 Validation | 4 | Human-verified findings and Validation Hub; no published metrics | TE2, TE3 |
| C4 Safety | 5 | Human-on-the-Loop, TORCH oversight, per-action logging | TE2, TE4 |
| C5 Remediation | 5 | Pull requests, proof of failed attack, temporary firewall rules | TE3 |
| C6 Compliance | 5 | SOC 2 Type II, CREST, auditor-accepted signed reports | TE2, TE7 |
| C7 Maturity | 3 | Network modules in preview | TE6 |
| C8 Evidence | 3 | CVE research; no independent benchmark | TE8 |

### CodeAnt AI (29)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 4 | Apps, APIs, cloud, code; internal network limited | CA1, CA6 |
| C2 Agentic depth | 4 | 500+ attack agents, three test modes | CA4 |
| C3 Validation | 4 | Working proof of concept per finding; self-reported | CA4 |
| C4 Safety | 2 | No production safety controls described | None found |
| C5 Remediation | 4 | Code-level fixes, unlimited retests | CA5 |
| C6 Compliance | 4 | SOC 2 Type II, HIPAA | CA2 |
| C7 Maturity | 4 | Available with public pricing and free first test | CA3, CA5 |
| C8 Evidence | 3 | CVE disclosures and white paper; comparisons self-published | CA3, CA7 |

### Armadin (27)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 4 | Perimeter, internal network, web apps official; cloud and identity via investor | AR4, AR6 |
| C2 Agentic depth | 5 | 26,000 agents and 17 million actions in one campaign | AR1, AR3 |
| C3 Validation | 4 | Validated kill chains; no false-positive data | AR2, AR3 |
| C4 Safety | 3 | Control layer with safety model; scope and audit controls not documented | AR5 |
| C5 Remediation | 3 | Attack paths and blast radius shown; no official retest or integration detail | AR2 |
| C6 Compliance | 2 | Trust center exists; certifications not visible | AR7 |
| C7 Maturity | 3 | In production; customers unnamed; launched March 2026 | AR2 |
| C8 Evidence | 3 | Detailed exercise data; self-reported, institution unnamed | AR3 |

### CyCognito (23)

| Criterion | Score | Why | Evidence |
|---|---|---|---|
| C1 Coverage | 3 | Broad but external only | CY3 |
| C2 Agentic depth | 3 | AI agents sit on top of deterministic tests | CY1, CY2 |
| C3 Validation | 4 | 100,000+ deterministic tests validate exploitability | CY2, CY5 |
| C4 Safety | 2 | No controls or human review described for the AI layer | None found |
| C5 Remediation | 3 | Prioritisation documented; no exploit-retest loop described | CY5 |
| C6 Compliance | 3 | Certifications not verified in this review | None found |
| C7 Maturity | 2 | AI pentest with design partners; no GA date | CY4 |
| C8 Evidence | 3 | Analyst recognition and white paper; no AI-layer metrics | CY6, CY7 |

## B3. Claims Not Officially Confirmed

Not used in scoring. Do not present these as facts.

| Vendor | Claim | Status |
|---|---|---|
| Armadin | One-click block through CrowdStrike Falcon MDR; Jira and ServiceNow ticketing | Executive interview in trade press. No official page found |
| Armadin | Automatic retest after a fix; sandboxed agents; no on-premise option; product name "Armadin Red" | Third-party directory only |
| Tenzai | AWS WAF integration | Third-party directory only. Official release names Akamai |
| Tenzai | Use of Z.ai models in a HackerOne contest | Press report only. Not confirmed by Tenzai |
| XBOW | No source code analysis; no automated remediation workflow | Competitor-authored comparison |
| HackerOne | High cost at enterprise scale | Competitor-authored comparison |

## B4. Revision History

| Revision | Change |
|---|---|
| 1 | First comparison and scoring |
| 2 | Tenzai 32 to 35 and HackerOne 34 to 35 after reading Tenzai's product page and the H1 Platform launch |
| 3 | Official-source audit. XBOW 35 to 34 (Doyensec primary report). Armadin 29 to 27 (claims without official source removed) |
| 4 | Restructured into slide-ready blocks and a detailed reference. No score changes |

## B5. Additional References

**Official**
- [XBOW Resource Center](https://xbow.com/resource-center)
- [XBOW Trust Center](https://trust.xbow.com/)
- [Terra white papers](https://www.terra.security/category/whitepapers)
- [Terra Trust Center](https://terra.security/trust-center)
- [Terra: Network pentesting](https://www.terra.security/terra-platform/network-testing)
- [Terra: Human oversight model](https://www.terra.security/blog/the-future-of-pentesting-is-human-judgment-and-agent-execution)
- [Tenzai Manifesto](https://www.tenzai.com/manifesto)
- [Tenzai press release: Palo Alto Networks collaboration](https://www.newswire.com/news/fighting-ai-with-ai-palo-alto-networks-and-tenzai-collaborate-to-defeat)
- [CyCognito press release: Continuous AI Pentesting](https://www.cycognito.com/news/press-releases/cycognito-extends-its-exposure-management-platform-with-continuous-ai-pentesting-across-every-exposed-asset.php)
- [CyCognito: AI pentesting guide](https://www.cycognito.com/learn/penetration-testing/ai-pentesting/)
- [CodeAnt AI security research](https://codeant.ai/security-research)
- [CodeAnt AI: AI pentesting and compliance](https://codeant.ai/blogs/ai-pentesting-compliance)
- [HackerOne press release: Hai agents and CTEM](https://www.hackerone.com/press-release/hackerone-launches-advanced-team-ai-agents-continuous-threat-exposure-management)
- [HackerOne press release: h1 Validation](https://www.businesswire.com/news/home/20260421791520/en/HackerOne-Introduces-h1-Validation-to-Help-Enterprises-Manage-Surge-in-AI-Discovered-Vulnerabilities)
- [HackerOne report: Hacker-Powered Security](https://www.hackerone.com/report/hacker-powered-security)

**Partner and investor**
- [Greylock: Introducing Tenzai](https://greylock.com/portfolio-news/introducing-tenzai-autonomous-ai-hackers/)

**Independent**
- [Doyensec: study announcement](https://blog.doyensec.com/2026/05/27/aikido-xbow.html)
