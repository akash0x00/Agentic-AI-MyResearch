# Agentic AI Security Platforms: Major Learnings and How to Build a Basic Replica

| Item | Detail |
|---|---|
| Based on | Tenzai, HackerOne (H1), XBOW, Terra, Armadin, CodeAnt AI, CyCognito |
| Date | 10 November 2026 |
| Companion files | `agentic-ai-security-comparison.md`, `agentic-ai-similarities-differentiators.md` |
| Nature | Learnings and a build blueprint. Architecture is my own analysis, not any vendor's internal design |

**INFO**

- Section 1 : the main lessons these seven products teach
- Sections 2-3 : what you'd actually need to build a basic version, and which models fit
- Section 4 : the question you raised, how these tools do "visual" work with GUI tools like Burp when the LLM only reads text
- Section 5 : the whole build drawn as one ASCII diagram
- Sections 6-7 : how far a basic build really gets you, and a note on the model names

---

## 1. Top Learnings

These are the patterns that show up again and again once you look past the marketing.

1. **The LLM is the brain, not the hands.** None of these tools ask a model to "hack." The model plans, picks the next step, and reads results. Real tools (scanners, proxies, exploit scripts) do the actual work. Get that split right and the rest follows.

2. **A finding without a working exploit is noise.** Every serious vendor sells proof, not a list. The thing that separates them from a scanner is that they try the exploit and show it worked. This is also what keeps false positives low.

3. **Validation is a separate step from discovery.** The better designs have one agent find a candidate and a different path confirm it. XBOW's independent validators and HackerOne's exploit agents are the same idea: never trust the finder to also grade itself.

4. **Chaining is the real value.** A single low-severity bug is boring. The money is in linking three weak things into one path to admin or data. This is why "attack path" and "kill chain" appear everywhere, and why pure scanners cannot compete.

5. **Continuous beats point-in-time, but only with a trigger.** The whole category is built against the annual pentest. In practice "continuous" means "re-test when code or the attack surface changes," not "run forever."

6. **Safety is a feature you sell, not an afterthought.** Scope limits, rate control, a command checker, an action log, a pause button. Autonomous attack in production scares buyers, so the vendors that document guardrails win trust.

7. **The human never fully leaves.** Even the most autonomous tools keep a human somewhere: training the models, approving the first run, or signing the report for auditors. "No humans" is a slogan, not a design.

8. **Coverage is the main axis of competition.** Web is table stakes. The fight is over API, cloud, internal network and AI apps. Breadth is also where the youngest vendors over-claim, so it is the first thing to test.

9. **Context makes the agent smarter and cheaper.** Feeding the agent source code, prior findings or asset context (CodeAnt, HackerOne, CyCognito) means fewer wasted tokens and deeper bugs. Starting cold is expensive.

10. **Token cost shapes the product.** Deep AI testing of every asset is costly, so vendors ration it: run cheap deterministic tests first, save the expensive model for the hard parts (CyCognito's model literally does this).

11. **Benchmarks are mostly self-graded.** Almost every number is vendor-reported. One independent study exists in this set, and a competitor paid for it. Treat all claims as hypotheses to test in your own proof of concept.

12. **The report is the product.** Buyers do not consume exploits, they consume evidence: reproduction steps, a fix, and a retest that proves closure. The platforms that map this to SOC 2 or ISO win the enterprise.

13. **MCP is becoming the plumbing.** Tenzai ships as an MCP server that plugs into Claude Code, Cursor and Devin. The tool is not a website you log into, it is a capability your own agents call. Worth noting for how the market is heading.

14. **The model is becoming a commodity; the harness is the moat.** Vendors swap models freely (some use several at once). The durable value is the orchestration, the tool library, the safety layer and the validation loop around the model, not the model itself.

---

## 2. What You Need to Build a Basic Replica

You can build a working, basic version. It will not match a funded product, but the architecture is not a secret. Here are the parts.

### 2.1 The Required Pieces

- **A reasoning model.** The brain that decides the next action and interprets output. One good frontier model is enough to start (for example Claude via an Anthropic API key).
- **An agent loop.** The cycle of: look at state, decide a step, run a tool, read the result, update state, repeat. This is the orchestrator.
- **A tool layer.** The actual offensive tools, wrapped so the agent can call them and get clean text back (recon, scanning, exploitation, a browser).
- **A sandbox.** An isolated Kali or Ubuntu container where tools run and nothing can reach the wider network. This is both a safety boundary and the execution environment.
- **A validator.** A second step that re-runs a candidate finding and only keeps it if the exploit actually works.
- **Memory and state.** A store of what was found, what was tried, credentials, endpoints and the current goal, so the agent does not loop or forget.
- **A safety layer.** Scope allow-list, a traffic proxy, rate limits, a blocked-command list, a full action log, and a kill switch.
- **A reporter.** Turns the validated findings and logs into a readable report with reproduction steps.

### 2.2 Single Agent or Sub-Agents

- **Start single-agent.** One model in one loop with a toolbox is enough to prove the idea and to pentest one simple web app.
- **Move to sub-agents when scope grows.** A common split: an orchestrator that plans, plus specialists for recon, for web, for exploitation, each with its own narrow toolset. HackerOne and Armadin both describe this shape.
- **Why split at all.** Smaller, focused agents keep the prompt short, limit what each one can touch (safety), and let you run many in parallel. The cost is coordination: they need shared state and a manager.

### 2.3 The Honest Minimum (a basic but real build)

A believable starter, roughly in order:

- One frontier model with tool use, driven by an agent loop.
- A Kali container as the sandbox.
- A handful of CLI tools wrapped as callable functions: a port and service mapper, an HTTP prober, a web fuzzer, a vulnerability template engine, and a request proxy.
- A headless browser for anything that needs a rendered page.
- A validator step and a simple state file.
- A scope check and a kill switch before anything runs.
- A report generator.

That gets you an agent that can recon a target, probe a web app, try a few vulnerability classes, confirm hits, and write them up. It will be slow and narrow, but it is the same skeleton the real products are built on.

---

## 3. Which Models You Can Use

The model is swappable. Pick by three things: reasoning quality, cost per run, and whether you must keep data in-house.

### 3.1 Frontier Models via API (easiest, strongest reasoning)

- **Anthropic Claude.** Strong tool use and long-horizon reasoning, and it has vision for the screenshot path in section 4. An Anthropic API key plus Claude is the simplest capable starting point. Independent and vendor benchmarks in this space repeatedly use Claude Sonnet as the reference model, which tells you it is a sensible default.
- **OpenAI GPT.** Comparable reasoning and tool use; also has vision. Tenzai is reported to use both Anthropic and OpenAI models depending on the task.
- **Google Gemini.** Large context and vision, a reasonable third option.

Trade-off: best reasoning and no infrastructure to run, but your target data leaves your network and cost scales with tokens.

### 3.2 Open-Weight Frontier Models (run them yourself)

Use these when data cannot leave your environment, or to cut cost at scale. They are strong enough for agentic security work today, though usually a step behind the top closed models on the hardest reasoning.

- **DeepSeek** (V3 and R1 reasoning line). Strong reasoning, popular for self-hosted agents. Notably, the open-directory "Operation Snowball" attack harness in the wild ran on a DeepSeek model, which shows these are capable enough for real offensive loops.
- **Qwen** (Alibaba). Broad range of sizes, good tool-calling, easy to fine-tune.
- **GLM** (Z.ai). Reported in this market: Tenzai's HackerOne contest work was linked to Z.ai models, and GLM has been used for offensive and forensic agent work.
- **Llama** (Meta). The common baseline for self-hosting, widely supported by agent frameworks.
- **Mistral** and **gpt-oss** (OpenAI's open-weight line). Lighter options for the cheaper, narrow sub-agents.

Trade-off: full data control and lower marginal cost, but you run the GPUs, you handle scaling, and reasoning depth is usually a notch below frontier API models.

### 3.3 A Sensible Mix

The mature move, and what several vendors do, is to blend them:

- A **strong frontier model** for planning and for the hard chaining decisions.
- A **cheaper or open-weight model** for the high-volume, simple sub-tasks (parsing output, routine recon triage).
- A **vision-capable model** only when you need the screenshot path.

This keeps the smart, expensive model for the few decisions that need it.

---

## 4. The GUI Question: How Agents Work With Tools Like Burp

This is the sharp question you raised, so it gets its own section.

### 4.1 Your Intuition Is Right, and It Has a Twist

You pictured an agent in Kali: give a command, read the text output, let the LLM decide the next command. That is exactly how the CLI side works, and it is most of what these tools do. Tools like a port scanner, a fuzzer or a vulnerability engine all speak plain text, so the loop is clean.

The twist is this: **the serious tools almost never "look at" a GUI.** Driving Burp Suite by clicking buttons would be slow, fragile and expensive. So instead of using the GUI, they reach the same engine a different way. There are three ways to do that, from best to last resort.

### 4.2 Way 1: Use the API, Not the Window (the real answer)

Most GUI security tools also expose a non-visual interface. The agent uses that and never opens the window.

- **Burp specifically.** Burp can run headless (no GUI) and exposes a REST API, and it has an extension interface (the Montoya API) for driving it programmatically. An agent tells Burp to scan a target or pull the HTTP history through the API and reads structured results back as text or JSON. No clicking.
- **The general rule.** Before assuming an agent needs to "see" a tool, check if that tool has a CLI, a REST API, or a headless mode. Almost all of them do. The GUI is for humans; the API is for agents.

This is why "how does it click around Burp" usually has the answer: it does not. It calls Burp's engine directly.

### 4.3 Way 2: Sit in the Traffic, Read It as Text

A lot of what Burp's GUI shows you is just HTTP requests and responses. You do not need the window to get those.

- Route the target traffic through a proxy (Burp headless, or a lightweight proxy like mitmproxy).
- The proxy records every request and response.
- The agent reads that traffic as text and reasons over it: parameters, headers, auth tokens, responses.

So the "visual" history panel a human stares at becomes a text stream the model reads. Same information, no pixels.

### 4.4 Way 3: Actually Look at the Screen (last resort, for true visual work)

Some things are genuinely visual: a rendered web page, a canvas, a legacy desktop app with no API, or a bug you can only see when the page draws (some DOM-based XSS, UI redressing). For those, you give the agent eyes. Two sub-options:

- **DOM and accessibility tree (preferred).** Drive a headless browser (Playwright or Puppeteer). Instead of a screenshot, hand the model the page's DOM or its accessibility tree as text. It is structured, cheap, and tells the model what elements exist and where. This covers most "visual" web work without a single image.
- **Screenshots to a vision model (true computer use).** When text is not enough, take a screenshot, send it to a vision-capable model, and let it say where to click or type. The model returns coordinates or an element, your code performs the click, you screenshot again, and repeat. This is the "computer use" pattern. It is how you would drive an actual GUI like the Burp window if you truly had no other choice.

### 4.5 Why Way 3 Is the Last Resort

The screenshot loop is real but painful: every step is an image (expensive tokens), vision models still misread coordinates, GUIs change and break the flow, and it is slow. So the production tools push everything they can to Way 1 and Way 2, and use Way 3 only for the narrow slice that is truly visual. Your instinct that it "reads output and decides" is correct; the craft is in choosing the cheapest interface that still works for each tool.

### 4.6 How You Would Build the Visual Path, Basically

- For web apps: use a headless browser, feed the DOM or accessibility tree to the model first, and only fall back to screenshots and a vision model when a bug is genuinely visual.
- For a tool like Burp: run it headless and call its REST or extension API; never automate its window.
- Keep a hard rule: prefer API, then proxy and text, then DOM, then screenshots, in that order. Drop down a level only when the one above cannot answer.

---

## 5. Architecture at a Glance

A basic replica, drawn as the control loop plus the three ways of reaching tools from section 4.

```
                         +--------------------------+
                         |     REASONING MODEL      |
                         |  (plans, decides, reads) |
                         |  Claude / GPT / open LLM |
                         +------------+-------------+
                                      |
                        decide next step | read result
                                      v
        +-----------------------------+------------------------------+
        |                   AGENT LOOP / ORCHESTRATOR                |
        |     single agent, or manager + recon/web/exploit subs     |
        +--+----------------+----------------+---------------------+-+
           |                |                |                     |
   reads & |         writes |          calls |              checks |
   updates v                v                v                     v
     +-----------+   +--------------+   +-----------------+   +-----------+
     |  MEMORY   |   |   REPORTER   |   |   TOOL LAYER    |   |  SAFETY   |
     | & STATE   |   | evidence +   |   | (see 3 ways)    |   |  LAYER    |
     | findings, |   | repro steps  |   |                 |   | scope,    |
     | endpoints,|   | + retest     |   |                 |   | proxy,    |
     | creds     |   +--------------+   |                 |   | rate cap, |
     +-----------+                      |                 |   | kill sw., |
                                        |                 |   | full log  |
                                        |                 |   +-----------+
          THREE WAYS TO REACH A TOOL    |                 |
          (prefer top, fall down only   |                 |
           when it cannot answer)       |                 |
                                        |                 |
        Way 1  API / headless  ---------+--> Burp headless REST, CLI tools
               (best)                   |     (scanner, fuzzer, templates)
                                        |
        Way 2  proxy, read as text -----+--> mitmproxy / Burp proxy history
                                        |
        Way 3  look at screen ----------+--> headless browser
               (last resort)            |       |
                                        |       +--> DOM / a11y tree (text, preferred)
                                        |       +--> screenshot -> vision model -> click
                                        v
                              +------------------------+
                              |   SANDBOX (Kali/Ubuntu |
                              |   container, isolated) |
                              +-----------+------------+
                                          |
                                          v
                                   +-------------+
                                   |   TARGET    |
                                   | scoped only |
                                   +-------------+

   VALIDATOR: before a finding is kept, re-run the exploit in the sandbox.
   No working exploit, no finding.
```

---

## 6. A Realistic View of the Gap

So you set expectations if this ever becomes a project:

- **A basic replica is a weekend-to-weeks effort.** One model, a loop, five or six wrapped tools, a sandbox and a report. It will find real bugs on simple targets.
- **The hard 80% is everything around the model.** Reliable validation, low false positives, safe behaviour in production, broad coverage, and reporting auditors accept. That is where the funded teams spend their money.
- **Determinism is the quiet problem.** The same run twice can differ, because the model is not deterministic. Taming that (fixed tool contracts, validation, replay from state) is most of what "production grade" means here.
- **Coverage is a long tail.** Web is quick. API, internal network, cloud and AI-app testing each take their own tools and their own tuning. The breadth the vendors advertise is years of work, not a feature flag.

---

## 7. Note on Models and Claims

- Model names and version numbers in this space change fast. Treat the names in section 3 as current families and categories, and check the latest versions when you build.
- The architecture here is my own synthesis from how agentic systems work and from what the vendors describe publicly. No vendor has published its full internal design, so this is a reasonable blueprint, not a copy of any one product.
- Where I cite a vendor behaviour (for example Tenzai shipping as an MCP server, or CyCognito running deterministic tests before AI), the detail is from their official material referenced in the companion files.
