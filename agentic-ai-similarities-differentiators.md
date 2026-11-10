# Agentic AI Security Platforms: Similarities and Key Differentiators

| Item | Detail |
|---|---|
| Vendors | Tenzai, HackerOne (H1), XBOW, Terra Security, Armadin, CodeAnt AI, CyCognito |
| Date | 10 November 2026 |
| Companion file | `agentic-ai-security-comparison.md` (scores and evidence register) |

**INFO**

- Section 1 : what these products have in common
- Section 2 : what makes each one different, one block per product
- Section 3 : the whole lot in a single table
- Section 4 : links to the official datasheets, white papers and briefs
- Strengths : taken from the vendors' own pages, so "official" means they said it, not that anyone checked it
- Gaps : my own read, each with the reasoning, how sure I am, and a way to check it yourself
- (I) : a gap the independent Doyensec study backs up

---

## 1. Similarities

### 1.1 Shared by All Seven

- **AI agents act as the attacker.** Each product uses specialised AI agents that plan and adapt, instead of fixed scanner signatures.
- **Exploitability over volume.** Each aims to show what can really be exploited, not a long list of theoretical issues.
- **Continuous, not point-in-time.** Each positions itself against the annual or quarterly pentest.
- **Web applications are in scope.** Every product tests internet-facing web applications.
- **Human expertise is built in.** The role differs: training the agents, supervising them, or validating findings.
- **Delivered as a cloud service.** None requires the customer to build its own agent stack.

### 1.2 Shared by Most

| Trait | Vendors that state it | Exceptions |
|---|---|---|
| API testing | Tenzai, HackerOne, XBOW, Terra, CodeAnt AI, CyCognito | Armadin does not state it |
| Proof with each finding (exploit steps or validated attack path) | Tenzai, HackerOne, XBOW, Terra, CodeAnt AI, Armadin | CyCognito validates mainly through deterministic tests |
| Retest after a fix | Tenzai, HackerOne, XBOW, Terra, CodeAnt AI | Armadin and CyCognito: not officially documented |
| Testing triggered by change (code or release) | Tenzai, HackerOne, XBOW, Terra, CodeAnt AI | Armadin, CyCognito |
| Ticketing integration (Jira, ServiceNow or GitHub) | Tenzai, HackerOne, XBOW, CodeAnt AI | Terra, Armadin: not named on official pages |
| Code-aware or white-box mode | Tenzai, HackerOne, Terra, CodeAnt AI | XBOW, Armadin, CyCognito |
| AI and LLM application testing | Tenzai, HackerOne, Terra, CyCognito (exposed AI assets) | XBOW, Armadin, CodeAnt AI: not stated |
| Network testing beyond web | Tenzai, HackerOne, Terra (preview), Armadin, CodeAnt AI (limited internal), CyCognito (external) | XBOW |
| SOC 2 Type II stated for the vendor itself | Tenzai, Terra, CodeAnt AI | Others: confirm through trust centers |
| Safety controls for production testing described | Tenzai, HackerOne, XBOW, Terra, Armadin | CodeAnt AI, CyCognito |

### 1.3 Shared Gaps (analyst assessment)

Vendors do not publish their weaknesses. These points are my reasoning from design trade-offs and from what is missing in public material.

- **Run-to-run variation.** LLM agents are not deterministic, so two runs on the same target can return different findings.
- **No proof of coverage.** Reports show what was found, not what was tested and passed.
- **The testing agent can be manipulated.** Content on the target can inject instructions into the agent.
- **Customer data reaches third-party LLMs.** Requests, responses and sometimes source code are processed by model providers.
- **Auditor acceptance is unsettled.** Not every auditor accepts an AI-generated report as a penetration test.
- **Production impact is a real risk.** Autonomous exploitation can change data or lock accounts.
- **Cost is tied to tokens.** Deep testing of every asset is expensive, so vendors limit depth or scope.
- **Results are mostly self-reported.** Only one independent study exists, and it covers XBOW only [(I) Doyensec](https://doyensec.com/resources/ComparingAIApplicationSecurityTestingPlatforms_Doyensec.pdf).
- **Complex authentication is hard.** SSO, MFA and multi-role flows often need manual setup.

---

## 2. Key Differentiators

### 2.1 Tenzai

**In one line:** The widest autonomous coverage, with mitigation built into the same loop.

- **Broadest surface list from one agent:** web, mobile, API, AI and MCP, external and internal network. [Product](https://www.tenzai.com/product)
- **Find, mitigate and fix in one flow:** validated WAF rules, fix guidance, tickets and retest. [Product](https://www.tenzai.com/product), [Press release](https://www.newswire.com/news/tenzais-ai-hacker-can-now-autonomously-mitigate-what-it-finds)
- **Guardrails at network level:** scope is enforced on the network, and every action is checked against the rules of engagement. [Product](https://www.tenzai.com/product)
- **Transparent reasoning:** the agent's reasoning trace is queryable; zero data retention on LLM calls. [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws)
- **AI application depth:** tests actors, tools, credentials and guardrails together with web and API in one run. [Press release](https://www.tenzai.com/press-releases/tenzai-expands-its-ai-hacker-to-ai-applications)
- **Works inside coding agents:** delivered as an MCP server for Claude Code, Cursor and Devin. [AWS listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws)
- **Exposure management tie-in:** integration with Palo Alto Networks Cortex Exposure Management. [Press release](https://www.newswire.com/view/content/tenzai-integrates-with-palo-alto-networks-to-help-enterprises-validate-22860775)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Newer surfaces are shallower than the web and API core | Six surfaces from a company one year old. Network was announced in July 2026, AI apps in June 2026 | Medium | Test internal network and mobile against a lab with known flaws, not only web |
| AI-only reports may not satisfy every auditor | No accredited body or human signature behind the report | Medium | Ask your PCI or ISO auditor before purchase |
| Auto-generated WAF rules can block real users | Any generated blocking rule carries false-block risk; only Akamai is named | Medium | Run rules in monitor mode first; confirm your WAF is supported |
| Customer data flows to third-party LLMs | Uses frontier and open-weight models; providers not fully named | High | Request the full model and subprocessor list and data regions |
| Integration effort is higher than it looks | MCP server only, no public REST API yet | High | Map how findings reach your SIEM, GRC and ticketing tools |
| Leaderboard results do not prove enterprise depth | CTF and bug bounty reward known bug classes on public targets, not SSO-heavy internal apps | Medium | Include one complex app with SSO, MFA and several roles |
| Vendor capacity for large rollouts | Small, young company with fast product expansion | Low | Ask for reference customers of similar size and for support SLAs |

### 2.2 HackerOne (H1)

**In one line:** Agents plus the largest researcher community, with accredited reports.

- **Hybrid by design:** AI agents handle scale; human researchers handle complex chains and business logic. [Solution page](https://www.hackerone.com/solutions/autonomous-pentesting)
- **Accreditation:** CREST-accredited and CSA-licensed in Singapore; reports for SOC 2, ISO 27001, PCI DSS, DORA, GDPR. [Solution page](https://www.hackerone.com/solutions/autonomous-pentesting)
- **One platform for bounty, pentest and agentic findings:** Hai orchestrates every stage. [H1 Platform](https://www.hackerone.com/platform)
- **Learns from history:** testing is informed by prior bug bounty findings and program data. [H1 Continuous Testing](https://www.hackerone.com/product/h1-continuous-testing)
- **Published benchmark method:** five pillars, with 88% fix-verified accuracy reported. [Engineering blog](https://www.hackerone.com/blog/agentic-ptaas-security-architecture)
- **Scale of adoption:** about 1,300 organisations. [Press release](https://www.hackerone.com/press-release/h1-platform-delivers-continuous-threat-exposure-management-ai-scale-validated)
- **Eats its own cooking:** Hai is in scope of HackerOne's own bug bounty. [Hai Security and Trust](https://docs.hackerone.com/en/articles/10908081-hai-security-trust)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Agentic part is newer than the brand suggests | Agentic PTaaS launched January 2026 and the H1 Platform in June 2026 | High | Ask which findings in the PoC came from agents and which from humans |
| Continuous coverage is mainly for web applications | Continuous Testing is described for applications; network, cloud and mobile lean on human pentests | Medium | Confirm what runs continuously per surface |
| Depth and speed depend on the assigned researchers | Complex chains are routed to humans, so quality and turnaround vary | Medium | Check tester selection, continuity and response times |
| Cost grows with scope | Human effort plus separate products (Bounty, Pentest, Continuous Testing, Validation, Code) | Medium | Get a three-year price for your full scope |
| External researchers touch your systems | The crowd model widens who sees targets and data | Medium | Review vetting, NDA and data-handling terms |
| Best results need platform history | Hai is tuned by prior bounty and program data, so new customers start cold | Low | Ask what a first-year customer should expect |
| No stop-gap protection | No WAF or firewall rule generation described | High | Plan mitigation through your own tooling |

### 2.3 XBOW

**In one line:** The deepest proof for autonomous web and API testing.

- **Every finding is a working exploit:** independent validators confirm it before release. [Platform](https://xbow.com/platform)
- **Most detailed safety controls on paper:** impact levels, safety judge, command checker, testing windows, pause. [Platform](https://xbow.com/platform)
- **Public track record:** #1 on HackerOne with 1,500+ reproducible exploits. [Overview brief](https://xbow.com/briefs/xbow-overview)
- **Only vendor with an independent study:** 31 true positives and 1 false positive. [(I) Doyensec](https://doyensec.com/resources/ComparingAIApplicationSecurityTestingPlatforms_Doyensec.pdf)
- **Ecosystem reach:** Microsoft Security Copilot and Sentinel integration; four cloud marketplaces. [News](https://xbow.com/news/xbow-penetration-testing-microsoft-security-ecosystem), [Pricing](https://xbow.com/pricing)
- **Accenture investment** and integration into Cyber.AI. [(P) Accenture](https://newsroom.accenture.com/news/2026/accenture-invests-in-xbow-to-advance-continuous-offensive-security-testing-and-exposure-management)
- **AI governance framework listed:** ISO 42001 appears alongside SOC 2 and ISO 27001. [Platform](https://xbow.com/platform)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| A second vendor is needed for network and cloud | Only web and API are listed | High | Budget and integrate another tool for the remaining scope |
| No attack chains across layers | A web-only tool cannot show web to network to cloud movement | High | Decide whether cross-layer paths matter for your risk model |
| Results vary strongly by application | Independent study: 24 findings on one app, 7 on the other (I) | High | Test at least two different tech stacks |
| Weaker on multi-role authorisation testing | Independent study ran with one admin account and no multi-user support (I) | Medium | Test IDOR and privilege flaws with several roles |
| Production safety needs proof | One scan disabled authentication and deleted a test account (I) | Medium | Start in staging; confirm impact-level settings |
| Onboarding and delivery can be slow | Independent study: manual sales approval, multi-day scan, report five days later (I) | Medium | Measure time from request to report in the PoC |
| Usage-based cost is hard to forecast | Quote-only, usage-based pricing | Medium | Ask for a cap or fixed price per application |

### 2.4 Terra Security

**In one line:** Governance first: a human on the loop at every critical decision.

- **Human-on-the-Loop model:** agents execute, pentesters keep control at decision points. [Home](https://www.terra.security/)
- **TORCH workspace:** humans and agents work in the same tool during live production tests. [Press release](https://www.terra.security/blog/pr-terra-security-redefines-penetration-testing-for-the-ai-era-with-terra-portal)
- **Audit-ready by default:** per-action logging and reports signed by certified pentesters. [Home](https://www.terra.security/)
- **SOC 2 Type II and CREST member.** [Home](https://www.terra.security/)
- **Fixes shipped as pull requests,** plus temporary firewall rules that block proven exploits. [Home](https://www.terra.security/)
- **Validation Hub:** checks whether findings from scanners and bug bounty are really exploitable. [Home](https://www.terra.security/)
- **Built for service providers too:** MSSPs can deliver it as their own continuous service. [Platform](https://www.terra.security/terra-platform)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Human checkpoints limit speed and scale | Initial findings take 1 to 2 weeks; reviewers are a bottleneck | High | Measure time to first finding and to retest |
| Price behaves like a service, not software | Certified pentesters sign reports and supervise agents | Medium | Compare cost per application with pure-agent vendors |
| Network modules are immature | External network in public preview, internal network in limited preview | High | Do not score network coverage until it is GA |
| Fewer machine-scale discoveries | More human gating usually means fewer parallel attack attempts | Low | Compare finding counts on the same target |
| Thin public proof | No leaderboard result or independent benchmark | Medium | Ask for customer references and sample reports |
| Broad roadmap for a small company | Web, AI, external and internal network within about one year | Medium | Ask for the roadmap and team size per module |

### 2.5 Armadin

**In one line:** The largest demonstrated agentic attack campaign, red-team style.

- **Swarm scale:** 26,000 agents and 17 million offensive actions in one three-day exercise. [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html)
- **Kill chains, not findings:** chains low-severity weaknesses into validated attack paths with blast radius. [Press release](https://www.prnewswire.com/news-releases/armadin-raises-255-5-million-series-b-to-scale-effective-autonomous-security-302895278.html)
- **Zero-knowledge start:** no privileged credentials, no whitelisting, no source access. [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html)
- **Custom models:** agents use models trained on elite operator tradecraft. [Press release](https://www.prnewswire.com/news-releases/armadin-secures-record-breaking-189-9m-in-seed-and-series-a-funding-to-combat-the-era-of-ai-driven-hyperattacks-302709318.html)
- **Tests the defence as well:** the exercise ran against live WAFs, endpoint security and a SOC. [Press release](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html)
- **Largest funding in the group:** $445M total. [Press release](https://www.prnewswire.com/news-releases/armadin-raises-255-5-million-series-b-to-scale-effective-autonomous-security-302895278.html)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Hard to pass procurement and AI governance | No public documentation, certifications or pricing | High | Request the security pack under NDA early |
| Campaigns are noisy | One exercise produced 17 million actions and over 100,000 alerts | High | Agree change windows and SOC readiness before testing |
| Weaker on application logic and APIs | Red-team style: perimeter to lateral movement. API and authenticated app testing not stated | Medium | Include an authenticated business-logic test case |
| Remediation loop is early | No official detail on retest, ticketing or fix validation | Medium | Ask for a demo from finding to closed ticket |
| Custom models are a black box | Proprietary models make reasoning harder to explain to auditors | Medium | Ask for action logs and decision evidence |
| High price and high-touch delivery | Positioned at Fortune 500 and government buyers | Medium | Confirm minimum contract size |
| Short track record | Public launch in March 2026 | High | Ask for references in production over six months |

### 2.6 CodeAnt AI

**In one line:** Pentesting that starts from the code, with public outcome-based pricing.

- **Defence and offence on shared context:** code review, SAST, cloud posture and pentest in one platform. [Home](https://codeant.ai/)
- **Code-aware attack paths:** reads source, IaC, dependencies and secrets, then attacks the running app. [Blog](https://codeant.ai/blogs/automated-penetration-testing-2026)
- **Pay for outcomes:** from $4,000, no charge without high or critical findings. [Blog](https://codeant.ai/blogs/best-ai-penetration-testing-platforms)
- **Fast report:** within 48 hours, with unlimited retests. [Blog](https://codeant.ai/blogs/best-ai-penetration-testing-platforms)
- **Pentest in the pipeline:** PR-level runs from CI. [Blog](https://codeant.ai/blogs/automated-penetration-testing-2026)
- **Research output:** 200+ CVEs disclosed. [Home](https://codeant.ai/)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Offensive depth is unproven | Core product is code review; pentesting is the newer line | Medium | Compare findings with a specialist on the same app |
| Best results need source code access | Code-aware testing means sharing repositories with the vendor | High | Check IP and data-handling terms |
| Pricing can reward severity inflation | The vendor is paid only for high and critical findings | Medium | Validate severity ratings independently |
| Closer to fast engagements than continuous testing | 48-hour reports and per-test pricing suggest point-in-time runs | Medium | Ask how continuous runs are priced and triggered |
| Production safety is undocumented | No scope, rate or kill-switch controls described | High | Start in staging; ask for the safety design |
| Marketing claims need checking | Comparisons are self-published and favour the vendor | High | Rely on PoC results, not the comparison pages |
| Limited enterprise footprint | Smaller vendor; limited internal network coverage | Medium | Ask for references at your scale |

### 2.7 CyCognito

**In one line:** Starts from discovery: finds the assets nobody listed, then tests them.

- **Outside-in discovery:** maps the external surface with no agents or network access. [Solution page](https://www.cycognito.com/solutions/external-exposure-management/)
- **Deterministic first, AI second:** 100,000+ deterministic tests, with AI agents reserved for complex chains. [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/)
- **Self-improving test library:** each validated AI attack chain becomes a new deterministic test. [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/)
- **Target Graph:** decides where AI testing runs and how deep, to control cost. [Blog](https://www.cycognito.com/blog/new-continuous-ai-pentesting/)
- **Shadow AI coverage:** finds exposed MCP servers, LLM endpoints and AI agents. [Solution page](https://www.cycognito.com/solutions/external-exposure-management/)
- **Analyst recognition:** GigaOm ASM Radar Leader and Outperformer. [Home](https://www.cycognito.com/)

**Likely gaps (analyst assessment, not vendor-stated)**

| Likely gap | Why I think so | Confidence | How to check |
|---|---|---|---|
| Not a pentest replacement | External and largely unauthenticated testing cannot reach logic behind login | High | Keep a separate vendor for authenticated testing |
| AI pentest is not a buyable product yet | Design-partner stage with no GA date | High | Ask for a GA date and a contract commitment |
| Shallower proof of exploitation | Tests built to be safe at scale stop short of full exploitation | Medium | Review sample findings for real exploit evidence |
| Asset attribution errors | Outside-in discovery can assign assets to the wrong owner | Medium | Check the accuracy of the discovered inventory |
| High finding volume | Whole-surface testing produces many low-value items | Medium | Check prioritisation quality in the PoC |
| No internal or code view | External position only | High | Combine with internal testing tools |

---

## 3. Differentiators at a Glance

| Vendor | Core differentiator | Autonomy | Human role | Unique asset |
|---|---|---|---|---|
| Tenzai | Widest coverage plus mitigation loop | High | Sets rules, can steer | WAF rule generation |
| HackerOne (H1) | Agents plus researcher community | Medium | Validates, handles complex chains | CREST accreditation, bounty data |
| XBOW | Proven web and API exploitation | High | Optional first-run approval | Independent study, HackerOne #1 |
| Terra Security | Human-on-the-Loop governance | Medium | Controls decision points | TORCH workspace, signed reports |
| Armadin | Swarm-scale attack campaigns | High | Trains the safety model | 26,000-agent exercise |
| CodeAnt AI | Code-aware, outcome pricing | Medium to high | Vets per engagement | Public pricing |
| CyCognito | Discovery-led exposure testing | Low to medium | Not described for AI layer | External asset discovery |

---

## 4. Official Reference Library

### 4.1 Tenzai
- [Product page](https://www.tenzai.com/product)
- [Trust Center](https://trust.tenzai.com/)
- [AWS Marketplace listing](https://aws.amazon.com/marketplace/pp/prodview-xxf5kvredpvws)
- [Blog: #1 on HackerOne in under 90 days](https://www.tenzai.com/blog/tenzai-hits-1-on-hackerone-in-under-90-days)
- [Press release: Autonomous mitigation](https://www.newswire.com/news/tenzais-ai-hacker-can-now-autonomously-mitigate-what-it-finds)
- [Press release: AI applications](https://www.tenzai.com/press-releases/tenzai-expands-its-ai-hacker-to-ai-applications)
- [Press release: Top 1% in CTF competitions](https://www.newswire.com/news/tenzais-ai-hacker-is-the-first-autonomous-system-to-rank-in-the-top-1-of-global)
- [Press release: Cortex Exposure Management integration](https://www.newswire.com/view/content/tenzai-integrates-with-palo-alto-networks-to-help-enterprises-validate-22860775)
- Datasheet or white paper: none found

### 4.2 HackerOne (H1)
- [Solution brief: Agentic PTaaS](https://www.hackerone.com/resources/pentest/agentic-ptaas-solution-brief)
- [Solution brief: H1 Continuous Testing, How It Works](https://www.hackerone.com/resources/pf/col/home/h1-continuous-testin?pflpid=62888&pfsid=D6FVvZWbt9)
- [H1 Platform (brief download on page)](https://www.hackerone.com/platform)
- [H1 Continuous Testing](https://www.hackerone.com/product/h1-continuous-testing)
- [H1 Agentic Pentest and H1 Pentest](https://www.hackerone.com/product/pentest)
- [Engineering blog: architecture and benchmarks](https://www.hackerone.com/blog/agentic-ptaas-security-architecture)
- [Docs: Hai Security and Trust](https://docs.hackerone.com/en/articles/10908081-hai-security-trust)
- [Press release: Agentic PTaaS](https://www.hackerone.com/press-release/hackerone-introduces-agentic-ptaas-deliver-continuous-expert-verified-pentesting)
- [Press release: H1 Platform](https://www.hackerone.com/press-release/h1-platform-delivers-continuous-threat-exposure-management-ai-scale-validated)
- [Report: Hacker-Powered Security](https://www.hackerone.com/report/hacker-powered-security)

### 4.3 XBOW
- [White paper: How to Scale Offensive Security Across Your Application Portfolio](https://xbow.com/whitepapers/how-to-scale-offensive-security-across-your-application-portfolio)
- [White paper: PHP2shell, Prove It, Don't Assume It](https://xbow.com/whitepapers/php2shell-prove-it-dont-assume-it)
- [Brief: XBOW Overview](https://xbow.com/briefs/xbow-overview)
- [Brief: PHP2shell Checklist](https://xbow.com/briefs/php2shell-checklist)
- [Platform](https://xbow.com/platform)
- [Resource Center](https://xbow.com/resource-center)
- [Trust Center](https://trust.xbow.com/)

### 4.4 Terra Security
- [Agentic Pentesting Buyer's Guide (PDF download)](https://www.terra.security/blog/buyers-guide)
- [White papers index](https://www.terra.security/category/whitepapers)
- [Terra Platform](https://www.terra.security/terra-platform)
- [Web app testing](https://www.terra.security/terra-platform/web-app-testing)
- [Network testing](https://www.terra.security/terra-platform/network-testing)
- [Trust Center](https://terra.security/trust-center)
- [Press release: TORCH](https://www.terra.security/blog/pr-terra-security-redefines-penetration-testing-for-the-ai-era-with-terra-portal)
- [Press release: Internal network pentesting](https://www.terra.security/blog/pr-terra-security-announces-internal-network-pentesting)

### 4.5 Armadin
- [Press release: Platform launch, Seed and Series A](https://www.prnewswire.com/news-releases/armadin-secures-record-breaking-189-9m-in-seed-and-series-a-funding-to-combat-the-era-of-ai-driven-hyperattacks-302709318.html)
- [Press release: Armadin and TENEX.ai exercise](https://www.prnewswire.com/news-releases/armadin-and-tenexai-run-the-largest-controlled-live-ai-cyberattack-on-record-302841653.html)
- [Press release: Series B](https://www.prnewswire.com/news-releases/armadin-raises-255-5-million-series-b-to-scale-effective-autonomous-security-302895278.html)
- [Trust Center](https://trust.armadin.com/)
- [(P) a16z: Investing in Armadin](https://a16z.com/announcement/investing-in-armadin/)
- Datasheet or white paper: none found

### 4.6 CodeAnt AI
- [White paper](https://codeant.ai/white-paper)
- [Benchmark](https://codeant.ai/benchmark)
- [Security research](https://codeant.ai/security-research)
- [Trust Center](https://codeantai.trust.site/)
- [Home and platform](https://codeant.ai/)

### 4.7 CyCognito
- [Datasheets hub](https://www.cycognito.com/resources/datasheets/)
- [Datasheet: Active Security Testing](https://www.cycognito.com/resources/data-sheet/active-security-testing)
- [Datasheet: Platform Overview (PDF)](https://cycognito.com/documents/datasheets/CyCognito_Platform_Overview.pdf)
- [Datasheet: Automated Security Testing (PDF)](https://www.cycognito.com/documents/datasheets/CyCognito-DS-Automated-Security-Testing-Oct-2024.pdf)
- [White paper: Rethinking Penetration Testing](https://www.cycognito.com/resources/white-papers/rethinking-penetration-testing/)
- [Blog: Continuous AI Pentesting](https://www.cycognito.com/blog/new-continuous-ai-pentesting/)
- [Solution briefs](https://www.cycognito.com/resources/briefs/)
