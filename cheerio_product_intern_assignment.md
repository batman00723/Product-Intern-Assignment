# Cheerio Product Intern Assignment — Assignment A
**Scaling Customer Support for Non Technical Users** | Candidate Submission

---

## Part 1: Solution

### 1. User Persona & The Top 5 Setup Blockers
* **Target User:** Aman Mishra, founder of **GATESprint Academy**, an online coaching institute in India preparing students for GATE exams (CSE, DA, ME, EE, EC). Aman captures student enquiries via Instagram/Facebook ads and converts them over WhatsApp. He is non technical and gets anxious about routine setup failures right before admissions deadlines.
* **Top 5 Setup Blockers (in chronological order of friction):**
  1. **Connecting WhatsApp Business Number:** WABA registration, two-factor authentication, and Meta display name verification. Without this, no campaigns can run.
  2. **Meta Template Rejections:** Automated rejections by Meta's compliance filters due to perceived promotional hype (e.g., "guaranteed rank boost").
  3. **Building the Student Qualification Flow:** Structuring interactive questionnaires (GATE stream, exam year, prep status) without complex workflow logic.
  4. **Google Sheets Sync & Counsellor Routing:** Mapping student responses to spreadsheets and alerting counsellor Priya Sharma without broken webhooks.
  5. **Campaign Delivery Troubleshooting:** Diagnosing why broadcast messages show as "Pending" or "Failed" before time-sensitive weekend webinars.

### 2. Solution Prioritization
To scale support, I evaluated 4 potential approaches against non technical user realities:

| Solution Option | Easy for Non Technical? | Creates the Setup? | Fixes Root Cause? | Verdict |
| :--- | :--- | :--- | :--- | :--- |
| **1. Help Docs & Videos** | Low (requires reading) | No (manual work) | Partial | **Rejected:** Users under deadline stress skip docs and open tickets. |
| **2. Static Checklist Wizard** | Medium (step-by-step) | Partial (rigid steps) | No (generic) | **Rejected:** Too generic; cannot write copy or adapt to GATE streams. |
| **3. Rule-Based Troubleshooter**| Medium (decision tree) | No (reactive only) | Yes (for known bugs) | **Rejected:** Purely reactive; only triggers after something breaks. |
| **4. AI Setup Copilot** | **High (natural language)**| **Yes (drafts copy/forms)**| **Yes (pre-flight checks)**| **Selected: Solves both creation and real-time error prevention.** |

### 3. Chosen Solution: Cheerio Setup Copilot
An in-product assistant that translates everyday language (*"I want to run a free GATE strategy session"*) into live, verified WhatsApp workflows.
* **What It Does:** Interprets campaign goals, auto-populates configuration fields, drafts Meta-compliant templates, structures qualification questions, connects Google Sheets, and pre-screens for errors.
* **What It Will Not Do in V1:** It will not auto-publish without human review, handle high-risk Meta policy appeals, manage billing disputes, or resolve custom backend webhooks.

### 4. Human-in-the-Loop Safeguards & Escalation
1. **User Sign-Off Gate:** The Copilot drafts the setup on a live canvas, but the live broadcast button remains disabled until Aman reviews the diff and checks an explicit confirmation box.
2. **Support Handover (for the 40% edge cases):** If an issue cannot be resolved within 3 turns, Cheerio packages the full canvas state, error codes, and transcript for instant human agent takeover without repeating information.

### 5. Metrics & North Star Target
* **Metric 1: Setup Completion Rate** (% of started setups successfully published).
* **Metric 2: Time-to-First-Broadcast** (reduction in onboarding friction from 48h to <15 mins).
* **Metric 3: CSAT Micro-Score** (1-click thumbs up/down post-session helpfulness).
* **North Star Metric:** **60% Self-Serve Resolution Rate within 3 months** (60 out of 100 setup blockers resolved completely without human agent intervention).

---

## Part 2: Design Prototype

### Prototype Architecture: Split-Screen "Chat × Form" Workspace
Rather than a disconnected floating chatbot popup, the prototype uses an integrated split-screen workspace:
* **Left Panel (Conversational Copilot):** Aman chats in plain English, receives contextual questions, inspects pre-flight warnings, and uses quick-action chips.
* **Right Panel (Live Dynamic Canvas):** Renders real interactive form inputs (`<input>`, `<select>`, `<textarea>`) that update in real time as the conversation unfolds. Aman can directly edit any field.
* **Review & Sign-Off Bar:** Sticky footer enforcing human verification before publishing.

### End-to-End User Journey (Aman's Scenario)
1. **Goal Input:** Aman types: *"I want to run a free GATE strategy session for 2027/28 aspirants."*
2. **Auto-Configuration:** Copilot structures eligible GATE streams and session time (Sunday 7 PM) into the right-hand canvas.
3. **Qualification Flow:** Copilot structures a 4-question WhatsApp flow (Paper, Year, Prep Level, Callback preference).
4. **Edge Case Handled (Meta Compliance Warning):** Copilot drafts message copy but catches a policy risk: *"The phrase 'get a winning plan' has an 82% rejection risk under Meta rules."* Suggests replacing with *"get a study plan and session details."* Aman applies fix with one click.
5. **CRM Routing & Launch:** Copilot links registrations to Google Sheet `GATESprint Leads` and assigns counsellor Priya Sharma. Aman reviews, checks verification, and hits **Publish Funnel Live**.

* **Live Prototype Link:** `https://batman00723.github.io/Product-Intern-Assignment/`
* **GitHub Repository:** `https://github.com/batman00723/Product-Intern-Assignment`
* **File Reference:** `cheerio-copilot-workspace.html` / `index.html` (Standalone clickable prototype).

---

## Part 3: How I Used AI

### Tools Used
I used **Antigravity** as an agentic partner to brainstorm technical edge cases, test prompt iterations, and write the initial interactive HTML/CSS/JS prototype code.

### Prompt Log: 3 Effective Prompts & 1 Failed Prompt
1. **Persona & Blockers (Worked Well):** *"I am working on a product assignment for Cheerio (https://cheerio.in). The user is Aman Mishra, who runs GATESprint Academy... List the 5 most common setup issues he will run into in order."*  
   *Outcome:* Grounded output in Indian coaching realities; generated the 5 chronological blockers.
2. **Compliance & Edge Cases (Worked Well):** *"Write a WhatsApp broadcast template for an online coaching institute... tell me what phrases Meta usually rejects during review for education businesses."*  
   *Outcome:* Surfaced Meta's ban on promotional hype phrases, providing the exact edge case used in the prototype.
3. **Prototype Layout (Worked Well):** *"Create a single HTML file with two columns. On left, chat assistant. On right, form with inputs for campaign name, date, student questions, and sheet routing..."*  
   *Outcome:* Generated clean split-screen layout with real interactive form fields.
4. **Support Scaling (Failed & Refined):** *"How can Cheerio scale customer support for non technical users?"*  
   *Why it failed:* Yielded textbook SaaS advice (build Intercom docs, hire CSMs).  
   *Refinement:* Narrowed prompt to in-product natural language guidance and auto-filled forms so users never have to leave the screen to read docs.

### Weaknesses Caught & What I Did Without AI
* **Weaknesses Caught:** (1) AI initially proposed auto-publishing campaigns without human review; I killed this and added the mandatory verification sign-off bar. (2) AI wrapped cards in a flex container that squished into thin unreadable strips at 100% zoom; I fixed this by switching to natural block scrolling with visible inputs.
* **Authored Without AI:** GATESprint case context, Indian admissions counselling workflows, solution trade-off evaluation matrix, human escalation packaging, and the entire unit economics and freemium pricing strategy.

---

## Part 4: Numbers — Cost, Billing, Audit & Savings

### 1. Volume Guesstimate & Resolution Rate
* **Cheerio Active Businesses:** 5,000 businesses (given).
* **Monthly Support Query Volume:** Blended rate of **1.0 query/business/month** across active campaign creators and maintenance accounts = **5,000 queries/month**.
* **Copilot AI Resolution (60% North Star Target):** **3,000 queries/month** resolved self-serve.
* **Escalated to Human Support (40% Edge Cases):** **2,000 queries/month**.

### 2. Running Cost & Groq Token Economics
* **Model Selected:** Llama 3 70B Enterprise hosted on **Groq** (chosen for sub-second inference speed to eliminate UI latency).
* **Pricing & Benchmark:** $0.00059 / 1k input tokens, $0.00079 / 1k output tokens (Groq Enterprise). Live rate: **1 USD ≈ ₹95.76**.
* **Token Usage per Session:** 3,000 input tokens (concise system prompt, account state, pruned history) + 250 output tokens (structured suggestions and JSON updates).
* **Cost per Query:** $\frac{3000}{1000} \times \$0.00059 + \frac{250}{1000} \times \$0.00079 = \mathbf{\$0.0019675}$ (~**₹0.19 per query**).
* **Total Monthly AI Running Cost:** $5,000 \times \$0.0019675 = \mathbf{\$9.84 / \text{month}}\quad (\mathbf{₹942 / \text{month}}$ total company bill).

### 3. Billing Strategy: Freemium Activation Engine
* **Activation Hook:** **First 5 campaign setups 100% FREE** for all accounts. In India, charging non technical users for setup assistance creates instant hesitation, onboarding drop-offs, and negative reviews.
* **Monetization (Campaign 6 Onward):** Once an account demonstrates power usage, offer a **Pro Copilot Add-On (₹499/month)** or bundle it into Cheerio's **Growth Plan (₹2,499/month)**.
* **Margin:** At ~₹0.19/query, 15 campaigns cost Cheerio ₹2.85 against a ₹499 fee, delivering a **99.4% gross margin**.

### 4. Monthly Auditing & Profitability Controls
1. **Daily Token Spike Alert:** Automated ceiling alert at **$2.00/day** on Groq (~₹190/day) to catch runaway loops or DDoS attempts.
2. **15-Turn Session Throttling:** Cap conversations at 15 turns/hour; automatically trigger friendly human support handover before user frustration builds.
3. **Weekly Monday Escalation Audit:** Review the 40% escalated tickets weekly to identify recurring policy/integration blockers and patch Copilot prompts within 24 hours.

### 5. Human Support Cost vs. AI Savings
* **Human Support Baseline:** Tier-1 agent cost = **₹30,000/month**; capacity = **500 tickets/month** (₹60.00/ticket).
  * 5,000 queries require **10 agents** = **₹3,00,000 / month** (₹3.0 Lakhs).
* **With AI Copilot:** Human team handles only the 2,000 escalated queries = **4 agents** (₹1,20,000/month) + ₹942 Groq AI cost = **₹1,20,942 / month**.
* **Net Financial Impact:**
  * **Monthly Net Savings:** $₹3,00,000 - ₹1,20,942 = \mathbf{₹1,79,058 / \text{month}}$ (~**₹1.79 Lakhs/month**).
  * **Annual Net Savings:** $₹1,79,058 \times 12 = \mathbf{₹21,48,696 / \text{year}}$ (~**₹21.5 Lakhs/year**).
  * **Cost Reduction:** **59.7% reduction** in overall support expenditure.

### 6. Complete Unit Economics Model (Formulas & Assumptions)

| Metric / Parameter | Value / Formula | Unit | Notes / Benchmarks |
| :--- | :--- | :--- | :--- |
| **Active Cheerio Businesses** | `5,000` | Businesses | Given in assignment brief |
| **Monthly Queries per Business** | `1.0` | Queries/mo | Blended rate across active & passive accounts |
| **Total Monthly Queries** | `5,000` (5,000 × 1.0) | Queries/mo | Total incoming setup & delivery tickets |
| **AI Self-Serve Resolution Rate** | `60%` | % | 3-month North Star target |
| **Queries Resolved by AI** | `3,000` (5,000 × 60%) | Queries/mo | Resolved self-serve without human agent |
| **Queries Escalated to Human** | `2,000` (5,000 - 3,000) | Queries/mo | Complex edge cases & policy appeals |
| **Input Token Price per 1k** | `$0.00059` | USD ($) | Groq Enterprise Llama 3 70B ($0.59 / 1M) |
| **Output Token Price per 1k** | `$0.00079` | USD ($) | Groq Enterprise Llama 3 70B ($0.79 / 1M) |
| **Input Tokens per Query** | `3,000` | Tokens | Lean prompt: system + state + pruned history |
| **Output Tokens per Query** | `250` | Tokens | Concise suggestions & JSON form updates |
| **AI Cost per Query (USD)** | `$0.0019675` | USD ($) | Input cost ($0.00177) + Output cost ($0.0001975) |
| **Total Monthly AI Cost (USD)** | `$9.84` | USD ($) | 5,000 queries × $0.0019675 |
| **USD to INR Exchange Rate** | `95.76` | INR (₹) | Live mid-market exchange rate |
| **Monthly AI Cost (INR)** | **₹942 / month** | INR (₹) | Total company AI bill (office coffee budget) |
| **Support Agent Monthly Cost** | `₹30,000` | INR (₹) | Tier-1 support agent salary baseline |
| **Tickets / Agent / Month** | `500` | Tickets | ~22–23 tickets/day across 22 working days |
| **Cost per Human Ticket** | `₹60.00` | INR (₹) | ₹30,000 salary / 500 tickets |
| **Agents Needed (Baseline)** | `10 agents` | Agents | 5,000 tickets / 500 (without AI) |
| **Baseline Human Support Cost** | `₹3,00,000 / month` | INR (₹) | 10 agents × ₹30,000 (₹3.0 Lakhs) |
| **Agents Needed (With AI)** | `4 agents` | Agents | 2,000 escalated tickets / 500 (saves 6 FTEs) |
| **New Total Support Cost** | `₹1,20,942 / month` | INR (₹) | 4 agents (₹1.20L) + Groq AI cost (₹942) |
| **Net Monthly Savings** | **₹1,79,058 / month** | **INR (₹)** | **Baseline - New Cost (~₹1.79 Lakhs/mo)** |
| **Net Annual Savings** | **₹21,48,696 / year** | **INR (₹)** | **Monthly Savings × 12 (~₹21.5 Lakhs/yr)** |
| **Support Cost Reduction** | **59.7% reduction** | **%** | **Direct reduction in support expenditure** |

