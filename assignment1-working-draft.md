# Cheerio Product Intern Assignment — Working Draft

## Assignment A: Make customer support scale for non-technical users

### Working case

This is a fictional case used to make the assignment concrete.

**Business:** GATESprint Academy, an online coaching institute for multiple GATE papers.

**Primary user:** Aman Mishra, founder of GATESprint Academy.

GATESprint gets student enquiries through Instagram and Facebook ads, its website, and WhatsApp. Aman’s small admissions team answers questions about different GATE papers, course batches, fees, demo classes, test series, and admission.

Aman uses Cheerio to capture enquiries, send WhatsApp follow-ups, and automate routine messages. He is not technical, and he often needs support to set up or fix these workflows.

**Aman’s job to be done**

> When a GATE aspirant shows interest in a course, help me capture the enquiry, send the right information, and route serious leads to my counsellors quickly, without needing technical help for routine setup.

## 1. User and the top five issues to solve first

We do not have Cheerio’s support-ticket data. The five issues below are a working hypothesis. Cheerio should validate them with ticket volume, time to resolution, and customer-satisfaction data.

### 1. Connect and set up a WhatsApp Business number

**Aman’s question:** “How do I connect and set up my WhatsApp Business number on Cheerio?”

**Why it comes first:** This is a dependency. If the number is not connected or verified correctly, Aman cannot run WhatsApp campaigns, automations, or enquiry flows. It blocks value completely.

### 2. Create an approved WhatsApp template

**Aman’s question:** “How do I create a template for a course announcement or demo-class reminder, and why was it rejected?”

**Why it comes second:** Aman needs templates for messages such as a free GATE strategy session, a new-batch announcement, or an enrolment reminder. A rejected template can delay a time-sensitive admissions campaign, and a non-technical user may not know how to fix it.

### 3. Create a WhatsApp enquiry flow for GATE aspirants

**Aman’s question:** “How do I create a flow that collects a student’s GATE paper, target year, graduation status, and course interest?”

**Why it comes third:** This replaces repeated back-and-forth between the admissions team and prospective students. Building forms, branches, and follow-up rules can feel difficult for a founder who has not used workflow tools before.

### 4. Send leads to a Google Sheet or CRM and assign a counsellor

**Aman’s question:** “How do I send new leads to my Google Sheet or CRM and assign them to the right counsellor?”

**Why it comes fourth:** If hand-off is unreliable, leads can be missed, duplicated, or contacted too late. That creates extra work for the admissions team and can hurt enrolments.

### 5. Diagnose a campaign that did not send as expected

**Aman’s question:** “Why did my WhatsApp campaign not send, remain pending, or reach fewer people than expected?”

**Why it comes fifth:** These issues are urgent. Aman may be promoting a batch with a fixed start date and needs a clear next step instead of waiting for a support agent.

### Why these issues are the initial priority

I prioritised these issues using four checks: how often they are likely to occur, whether they affect admissions, whether a product can guide the user through standard steps, and how risky it is to handle them without a human.

They sit on the main admissions path: set up WhatsApp, create an approved message, capture a student lead, pass the lead to a counsellor, and troubleshoot a campaign.

The first version will not try to solve custom API or webhook problems, billing disputes, or account-policy appeals. These cases can need deeper investigation, sensitive account information, or a human decision.

## 2. Possible solutions and why I picked the Setup Copilot

To solve setup issues for non-technical users like Aman, I considered four possible approaches:

### Solution 1: Better help-centre articles and video tutorials
Cheerio could create step-by-step guides and short screen recordings, such as “Create a GATE lead flow in 10 minutes” or “How to fix a rejected template.”
* **The upside:** It is cheap and quick to produce.
* **Why it falls short:** Aman still has to search for the right article, read through technical instructions, follow each step manually, and fix errors himself. When a busy founder is stuck right before an admissions campaign, they usually don't want to read documentation—they just open a support ticket.

### Solution 2: A setup checklist / onboarding wizard
Cheerio could show a fixed 5-step checklist inside the app: (1) Connect WhatsApp number → (2) Create template → (3) Build enquiry flow → (4) Connect Google Sheet → (5) Publish.
* **The upside:** It gives clear structure and shows users what step comes next.
* **Why it falls short:** The checklist is the same for every business. It cannot write message copy for Aman, adapt to his specific GATE course questions, or diagnose why he is stuck when something fails.

### Solution 3: A rule-based troubleshooting wizard
Cheerio could provide an interactive troubleshooter that asks questions: *“Where are you stuck?”* → *“My template was rejected”* → shows 3 common reasons and fixes.
* **The upside:** It directly addresses common known errors without human help.
* **Why it falls short:** It is purely reactive—it only helps *after* something breaks. It also becomes hard to maintain decision trees across dozens of features, and it does not help Aman create his flow in the first place.

### Solution 4: In-product AI Setup Copilot (Chosen solution)
An in-app assistant where Aman simply describes what he wants in plain words (*“I want to run a free GATE strategy session”*). The copilot drafts the message template, structures the student questions, checks for missing links or common mistakes, and lets Aman review everything before publishing.

### How I prioritised these solutions

| Solution | Easy for non-technical users? | Helps create the setup? | Helps when stuck? | Verdict |
| :--- | :--- | :--- | :--- | :--- |
| **1. Help articles & videos** | No (requires reading & manual work) | No (user does it all) | Partial (if user finds right doc) | Rejected: Users skip docs and raise tickets. |
| **2. Fixed checklist wizard** | Medium (structured, but rigid) | Partial (gives steps, not content) | No (doesn't explain errors) | Rejected: Too generic for diverse businesses. |
| **3. Rule-based troubleshooter** | Medium (simple Q&A) | No (only fixes errors) | Yes (for known bugs) | Rejected: Reactive only; doesn't help build flows. |
| **4. AI Setup Copilot** | **Yes (natural language)** | **Yes (drafts flow & copy)** | **Yes (proactive checks)** | **Selected: Solves both creation and errors.** |

### Why I chose the Setup Copilot
Non-technical users struggle with two things: **creating** workflows from scratch and **troubleshooting** technical errors. The other three options only address one side of the problem (or push the work back onto the user). The Setup Copilot handles both: it takes Aman's goal in plain English, drafts the setup for him, catches errors before they happen, and lets him stay in control by reviewing before publishing.

## 3. Chosen solution: Cheerio Setup Copilot

Cheerio Setup Copilot is an in-product assistant that helps non-technical users set up common WhatsApp workflows. The user describes the outcome they want, and the copilot checks the account, asks for the missing details, and prepares the setup.

For Aman, the journey begins with: “I want to run a free GATE strategy session.” The copilot then asks for the target GATE papers, session details, lead questions, and counsellor-routing preference. It prepares a draft WhatsApp template and enquiry flow, checks for missing setup or likely errors, and lets Aman test the student journey.

Before anything is published, the copilot shows Aman a clear summary of the proposed setup. Aman must review it and click the final **Publish** button. Aman is the human in the loop; the copilot can publish the completed flow only after this approval.

### What the Setup Copilot will do

- Let Aman describe what he wants to set up in everyday language.
- Ask only the follow-up questions needed to create the setup.
- Check whether the WhatsApp number, template, and lead-routing destination are ready.
- Create a draft WhatsApp template and enquiry-flow structure for Aman to review.
- Explain common errors in plain language and suggest a fix.
- Let Aman test the student journey before publishing.
- Publish the completed flow only after Aman reviews the summary and gives final approval.
- Route Aman to a support person with the relevant account details and error context when it cannot safely resolve the issue.

### What it will not do in version one

- It will not publish a campaign or flow without Aman’s clear approval.
- It will not replace human support for unusual, high-risk, or repeated technical failures.
- It will not promise enrolments, campaign delivery, or conversion results.

## 4. When a human needs to step in

The copilot should help with normal setup steps. A support person should take over when the user is stuck or the suggested steps do not solve the problem.

There are two human roles in this experience:

- **Aman, the account owner:** reviews the proposed setup and gives final approval before the flow is published.
- **A Cheerio support specialist:** handles exceptions that the copilot cannot safely resolve.

Human help is needed in these cases:

- Aman reviews the template, student questions, and lead-routing details before clicking **Publish**; the copilot only makes the flow live after his approval.
- Aman cannot connect his WhatsApp number even after following the copilot’s steps; the copilot creates a support request so a person can check what is blocking it.
- Aman corrects a rejected WhatsApp template with the copilot’s help, but it is rejected again; the copilot sends the template details to support so a person can tell Aman what to change before he tries again.
- A student fills the WhatsApp enquiry flow, but their details still do not reach Aman’s Google Sheet or counsellor after the copilot checks the setup; the copilot creates a support request so a person can fix the lead-routing problem.
- Aman sees an error that the copilot does not understand; the copilot offers a human hand-off so a support person can investigate it.
- Aman clicks **Talk to support**; the copilot passes the earlier conversation to the support person so Aman does not have to explain everything again.

The goal is simple: Aman should solve normal setup problems himself, but he should be able to reach a person quickly when the product cannot help.

## 5. How success will be measured

1. **Self-serve resolution rate:** The percentage of users who start the copilot and solve their setup problem without contacting support.

2. **Setup completion rate:** The percentage of users who start a setup and successfully publish their flow.

3. **Copilot helpfulness score:** At the end of each copilot session, Cheerio asks, “Did this help you solve your problem?” with **Yes** and **No** buttons. The helpfulness score is the percentage of respondents who select Yes. If a user selects No, Cheerio can ask what was missing: “I am still stuck,” “I needed human support,” “The answer was unclear,” or “Other.”

## 6. North Star metric and three-month target

**North Star metric: Self-serve resolution rate**

This is the percentage of users who start the Setup Copilot and solve their setup problem without contacting support. It captures the main value of the product: Aman completes routine setup work himself, while Cheerio receives fewer avoidable support requests.

**Three-month target: Reach a 60% self-serve resolution rate within three months of launch.**

For example, if 100 users start the copilot, 60 should finish their setup without raising a support request. This is an assignment assumption because Cheerio’s current self-service baseline is not available.

Cheerio can work towards this target by:

- Starting with the five common issues identified above instead of trying to solve every support problem at once.
- Using the feedback prompt to identify where users are getting stuck or finding answers unclear.
- Reviewing support requests created by the copilot each week and turning repeated questions into better guidance or product checks.
- Improving the copilot’s suggested templates and setup steps using successful flows already created by users.

## 7. Design Prototype (Part 2)

### Prototype Architecture: Chatbot × Form Hybrid Workspace
Rather than a rigid multi-page wizard or a disconnected chatbot popup, the prototype uses an **integrated split-view workspace** (built with warm ivory/parchment surfaces, hairline borders, and clay action accents):
- **Left Panel (Conversational AI Copilot):** Aman chats in plain English, receives contextual questions, inspects pre-flight warnings, and uses quick-action chips.
- **Right Panel (Dynamic Live Setup Canvas):** Updates automatically as the conversation unfolds. Aman can inspect the live configuration cards (Channel status, Session details, 4-step student qualifying questions, WhatsApp template preview with diff highlights, and Google Sheet / Counsellor routing).
- **Bottom Bar (Human-in-the-Loop Safeguard):** A dedicated sign-off checkpoint where Aman must explicitly confirm the setup before the **Publish Funnel Live** action activates.

### End-to-End User Scenario: Aman’s Journey
1. **Initial Goal (Turn 1):** Aman opens Cheerio and enters: *“I want to run a free GATE strategy session for 2027/28 aspirants.”*
2. **Auto-Configuration (Turn 2):** Copilot interprets the intent and fills the right canvas with eligible GATE papers (CSE, DA, ME, EE, EC), exam year, and timing (Sunday 7 PM).
3. **Qualifying Flow Generation (Turn 3):** Copilot structures a 4-question WhatsApp conversational form (GATE paper, exam year, current prep level, callback preference) so counsellors receive high-intent, pre-qualified leads.
4. **Template Generation & Edge Case Warning (Turn 4):**
   * *The Edge Case:* Copilot drafts the broadcast message but flags a Meta policy risk: *“The phrase 'get a winning plan' has an 82% rejection risk under Meta's promotional guidelines.”*
   * *The Resolution:* Copilot suggests replacing it with *“get a study plan and session details.”* Aman clicks **Apply Fix**, and the right canvas updates the template with an accepted diff tag.
5. **Lead Destination & Counsellor Routing (Turn 5):** Copilot connects new registrations to the Google Sheet `GATESprint - Strategy Session Leads` and assigns senior admissions counsellor `Priya Sharma`.
6. **Human Review & Launch (Turn 6):** Aman checks the verification box, hits **Publish Funnel Live**, and receives live status confirmation.
7. **Escalation Fallback:** If Aman gets stuck at any point, a **Handover to Cheerio Human Support** button packages the exact canvas state and transcript for immediate agent takeover without repeating information.

### 4 Key Screenshots Included in Submission
* **Screenshot 1 — Split-View Setup Workspace:** Showing the conversational Copilot on the left and auto-filled session details on the right canvas.
* **Screenshot 2 — Generated 4-Question Qualifying Form:** Showing the student questionnaire drafted without manual form-building.
* **Screenshot 3 (Edge Case) — Meta Compliance Warning & Diff:** Highlighting the flagged promotional phrase and the one-click suggested fix.
* **Screenshot 4 — Human Approval & Published Confirmation:** Demonstrating the human-in-the-loop review bar and successful launch modal.

**Prototype File:** [`cheerio-copilot-workspace.html`](file:///C:/Users/batma/Desktop/Cheerio%20Assignemtn/cheerio-copilot-workspace.html) *(Standalone clickable prototype, styled with Anthropic design language).*

## 8. How I used AI (Part 3)

### Which AI tools I used and for what
I used Antigravity for this assignment.
- I used Antigravity as a sounding board to map out where non technical founders usually get stuck with WhatsApp setup, probe Meta policy edge cases, and draft copy for WhatsApp templates.
- I used Antigravity to write and iterate on the prototype code (HTML, CSS, JS) so I could test the interaction and catch layout issues without spending days building it from scratch.

### Prompts log: 3 that worked well and 1 that failed

#### 1. Persona and bottleneck prompt (Worked well)
> "I am working on a product assignment for Cheerio (https://cheerio.in). The user is Aman Mishra, who runs GATESprint Academy, an online coaching institute for GATE exam aspirants in India. He is non technical and gets leads from Instagram ads. List the 5 most common setup issues he will run into on Cheerio, in the order he would face them."

* **Why it worked:** Giving Antigravity the link and a specific Indian SMB persona stopped it from giving me generic SaaS advice. It helped me map out the natural order of problems: connecting the phone number, waiting for Meta template approval, collecting student info, pushing leads to a spreadsheet, and figuring out why a campaign didn't send.

#### 2. WhatsApp template compliance prompt (Worked well)
> "Write a WhatsApp broadcast template for an online coaching institute announcing a free GATE strategy session. Also tell me what phrases Meta usually rejects during template review for education businesses."

* **Why it worked:** I didn't know all the quirks of Meta's template approval rules. Antigravity pointed out that lines like "get a winning plan" or "guaranteed rank improvement" often get rejected for promotional hype. That gave me a great real-world edge case for the prototype: catching the bad wording and suggesting a compliant fix before the user submits.

#### 3. Prototype layout prompt (Worked well)
> "Create a single HTML file with two columns. On the left, put a chat assistant. On the right, put a form with inputs for campaign name, date, exam year, student questions, a message textarea, and Google Sheet routing. When the user clicks a suggestion in the chat, fill in the form fields on the right."

* **Why it worked:** Being very clear about the layout (two columns, chat on left, real form inputs on right) meant the code worked right away in my browser without needing any backend setup.

#### 4. General support scaling prompt (Failed)
> "How can Cheerio scale customer support for non technical users?"

* **Why it failed:** Way too broad. It gave me textbook answers like "build an Intercom knowledge base", "write more help articles", and "hire account managers". None of that actually helps a stressed founder who is stuck right inside the app trying to launch a campaign.
* **What I changed:** I narrowed it down completely. I asked how the product itself could walk someone through setup using plain conversational prompts and auto-filled forms, so they never have to stop and read help articles.

### Where AI gave a wrong or weak answer, and how I caught it
1. **Auto-publishing without human sign-off:**  
   Early on, the AI suggested that the copilot should automatically create and publish the entire WhatsApp flow as soon as the user finishes chatting. That's a terrible idea in real life. No business owner wants an AI blasting messages to paid leads without looking at it first. I caught this and added a review screen with an explicit confirmation checkbox before the publish button even unlocks.

2. **CSS flexbox squishing the form cards:**  
   In the first version of the prototype code, the AI wrapped the form cards in a flex container with overflow hidden. When I opened it in Chrome at 100% zoom, the cards squished down into flat bars where you could only see the titles. You literally had to zoom out to 30% to read anything. I caught it while testing, scrapped the flex layout, and made it a normal scrolling page with proper input fields.

### Which parts I did myself, without AI

- **User psychology and persona context:**  
  I came up with GATESprint Academy because I know how Indian coaching businesses work around admissions season. Aman does not care about API endpoints, webhooks, or learning how to configure a workflow builder. He cares about leads from his Instagram ads getting answered before students pick a rival institute. AI gave generic SaaS startup advice, so I defined the persona, the 5 sequential blockers, the specific GATE streams (CSE, DA, ME, EE, EC), and the routing to admissions counsellor Priya Sharma.

- **The split-screen interaction model (Chat × Form):**  
  When I prompted AI for interface ideas, it suggested a standard chatbot widget in the bottom-right corner. I rejected that immediately. Chat-only tools leave users blind to what is actually happening in their account. I chose a split-screen layout where the chat sits on the left and real form controls sit on the right. When Aman chats, the form updates in real time so he can see, verify, or directly type into any field.

- **Human-in-the-loop review gate:**  
  AI wanted to auto-publish campaigns as soon as the chat conversation finished. I killed that idea. A platform should never fire broadcast messages or push student leads into live databases without user confirmation. I designed the review bar at the bottom with a mandatory sign-off checkbox before the "Publish Funnel Live" button activates.

- **Solution trade-off evaluation:**  
  I evaluated the four alternatives (help articles, onboarding checklists, rule-based troubleshooters, and the setup copilot) and built the comparison matrix. I wrote the reasoning for why docs fail (nobody reads them under deadline stress) and why rule-based wizards fall short (they only trigger after something breaks).

- **Support escalation design:**  
  I designed the fallback mechanism for the 40% of queries AI cannot solve. Instead of showing an error or telling the user to "email support," the prototype packages the chat history and form state so Cheerio’s human support team can take over immediately without asking Aman to explain everything again.

- **Financial model, rep capacity, and monetization decision:**  
  AI helped look up current per-token API pricing, but the business logic is mine. I modeled the support load for 5,000 businesses, set a realistic agent capacity (500 tickets a month at ₹30,000 salary), and calculated the net savings. I also made the product call to keep the copilot free on paid plans rather than charging per query, because charging for setup support creates hesitation, slows down activation, and increases churn.

## 9. Numbers: Cost, Billing, Audit & Savings (Part 4)

### 1. Guesstimate: Volume & Resolution Rate
* **Cheerio Active Businesses:** 5,000 businesses (given).
* **Monthly Support Query Volume:**
  * In a B2B marketing platform, ~40% of businesses actively launch or modify campaigns in a given month, generating multiple setup queries, while 60% are in a steady state.
  * Blended average query rate: **1.0 support query per business per month** relating to WhatsApp setup, templates, bot flows, CRM routing, or campaign delivery.
  * **Total Support Query Volume:** $5,000 \times 1.0 = \mathbf{5,000\text{ queries/month}}$.
* **Queries Resolved by Setup Copilot:**
  * Targets the top 5 routine blockers with our North Star target **60% Self-Serve Resolution Rate**.
  * **Copilot Resolved Queries:** $5,000 \times 60\% = \mathbf{3,000\text{ queries/month}}$.
  * **Escalated to Human Support (40%):** $5,000 \times 40\% = \mathbf{2,000\text{ queries/month}}$ (complex API bugs, billing disputes, account policy appeals).

### 2. Running Cost & Token Economics
* **Model Selected:** Llama 3 70B Enterprise, hosted on **Groq**.
  * *Why Groq:* Ultra-fast inference (~300+ tokens/second) gives non technical users instant, sub-second responses without frustrating UI lag.
* **Pricing Benchmark & Source:**
  * Official Groq Enterprise pricing: **\$0.00059 per 1k input tokens** (\$0.59 / 1M) and **\$0.00079 per 1k output tokens** (\$0.79 / 1M).
  * Current live exchange rate: **1 USD ≈ ₹95.76**.
* **Token Usage per Copilot Session (Avg. 4 conversational turns):**
  * **Input Tokens:** **3,000 tokens** (optimized prompt: ~800 tokens for system rules, ~700 tokens for account state, and ~1,500 tokens for recent chat history).
  * **Output Tokens:** **250 tokens** (concise suggestions and structured form updates, ~180-200 words).
* **Cost Calculations:**
  * Input token cost per query = $\frac{3,000}{1,000} \times \$0.00059 = \mathbf{\$0.001770}$
  * Output token cost per query = $\frac{250}{1,000} \times \$0.00079 = \mathbf{\$0.0001975}$
  * **Total Running Cost per Query:** **\$0.0019675** (~**₹0.188**, or **~₹0.19**).
  * **Total Monthly AI Running Cost (5,000 queries):**
    * In USD: $5,000 \times \$0.0019675 = \mathbf{\$9.84 / \text{month}}$
    * In INR: $\$9.84 \times ₹95.76 = \mathbf{₹942 / \text{month}}$ (practically office coffee budget for the company).

### 3. Billing & Monetization Strategy
* **Recommendation: Freemium Model (First 5 Campaigns Free, Then Paid Add-On)**
  * **Activation Hook (First 5 Campaigns 100% Free):**  
    In India, charging non technical business owners for basic setup help creates immediate friction. If a founder like Aman is asked to pay ₹20 just to connect his phone number, he hesitates, drops off, searches YouTube for free tutorials, and complains that Cheerio lacks setup support. Making the first 5 campaign setups free eliminates fear and gets users broadcasting immediately.
  * **Monetization (Campaign 6 Onward):**  
    Once an owner has successfully launched 5 campaigns, they have experienced clear value. For power users, Cheerio introduces two monetization paths:
    1. **Pro Copilot Add-on:** **₹499 / month** for unlimited copilot setups and automated template checks (accessible impulse pricing for active businesses).
    2. **Growth Plan Upgrade:** Gated as an inclusion in Cheerio's **Growth Tier (₹2,499 / month)** to drive annual expansion revenue.
  * **Gross Margin Impact:**  
    At an AI running cost of ~₹0.19 per session, even an active account creating 15 campaigns a month costs Cheerio just ₹2.85. Against a ₹499 monthly fee, the **gross margin is 99.4%**.

### 4. Monthly Auditing & Profitability Controls
To maintain reliability, stop bugs early, and prevent runaway costs, we establish 3 operational checks:
1. **Daily Token Spike Alert (Budget Ceiling):** Set an automated daily ceiling (\$2.00/day on Groq, ~₹190/day). If an unexpected bug or bot loop fires excessive API calls on any single day, ping the on-call engineering Slack channel immediately.
2. **Session Loop Throttling (Turn Cap):** A normal setup session takes 3 to 5 turns. If any single user chat exceeds **15 turns within an hour**, throttle the AI and show a friendly fallback: *"Looks like this needs a closer look—let me connect you directly to Cheerio human support."* This stops users from getting trapped in loops and eliminates token abuse.
3. **Weekly Monday Audit (Reviewing Escalations):** Every Monday, review the 40% of queries that got escalated to human agents and group them by error tag (e.g. Meta policy rejection, phone OTP failure, Google Sheet permission). If a specific error code spikes, update the copilot's prompt or Cheerio's UI to solve it automatically next time.

### 5. Human Support Cost vs. AI Savings Comparison
* **Human Support Economics (India SaaS Benchmarks):**
  * Fully loaded monthly cost of 1 Tier-1 Customer Support Specialist: **₹30,000 / month** (~$313).
  * Support agent resolution capacity: ~22-23 tickets/day $\times$ 22 working days = **500 tickets / agent / month**.
  * **Cost per Human Ticket:** $\frac{₹30,000}{500} = \mathbf{₹60.00\text{ per ticket}}$.
* **Before Copilot (100% Human Support for 5,000 queries):**
  * Support agents needed: $\frac{5,000}{500} = \mathbf{10\text{ agents}}$.
  * Monthly support payroll: $10 \times ₹30,000 = \mathbf{₹3,00,000 / \text{month}}$ (~₹3.00 Lakhs/month).
* **After Copilot (60% resolved by AI, 40% escalated to humans):**
  * Human tickets remaining: $2,000\text{ queries}$.
  * Support agents needed: $\frac{2,000}{500} = \mathbf{4\text{ agents}}$ (saving 6 FTEs).
  * New human support payroll: $4 \times ₹30,000 = ₹1,20,000 / \text{month}$.
  * AI Copilot running cost: ₹942 / month.
  * **Total New Monthly Support Cost:** **₹1,20,942 / month** (~₹1.21 Lakhs/month).
* **Net Financial Impact:**
  * **Monthly Net Savings:** $₹3,00,000 - ₹1,20,942 = \mathbf{₹1,79,058 / \text{month}}$ (~**₹1.79 Lakhs / month**).
  * **Annual Net Savings:** $₹1,79,058 \times 12 = \mathbf{₹21,48,696 / \text{year}}$ (~**₹21.5 Lakhs / year**).
  * **Net Cost Reduction:** **59.7% reduction in overall support expenditure**.

---

### Google Sheet Formula Template Reference
To copy this model directly into Google Sheets, format the cells as follows:

| Row / Item | Label | Value / Formula | Note |
| :--- | :--- | :--- | :--- |
| **B1** | Active Businesses | `5000` | Cheerio active business base |
| **B2** | Monthly Queries / Business | `1.0` | Average monthly setup query volume |
| **B3** | Total Monthly Queries | `=B1*B2` | Total monthly tickets (5,000) |
| **B4** | Self-Serve Resolution Rate | `60%` | North Star 3-month target |
| **B5** | Queries Resolved by AI | `=B3*B4` | Deflected queries (3,000) |
| **B6** | Queries Escalated to Human | `=B3-B5` | Human tickets remaining (2,000) |
| **B7** | Input Token Price per 1k | `$0.00059` | Groq Enterprise Llama 3 70B |
| **B8** | Output Token Price per 1k | `$0.00079` | Groq Enterprise Llama 3 70B |
| **B9** | Input Tokens per Query | `3000` | Optimized 4-turn prompt |
| **B10** | Output Tokens per Query | `250` | Concise suggestions & JSON |
| **B11** | Cost per Query ($) | `=(B9/1000)*B7 + (B10/1000)*B8` | Fully loaded query cost ($0.0019675) |
| **B12** | Total Monthly AI Cost ($) | `=B3*B11` | Monthly LLM bill ($9.84) |
| **B13** | USD to INR Exchange Rate | `95.76` | Live market exchange rate |
| **B14** | Monthly AI Cost (INR) | `=B12*B13` | At ₹95.76/USD (~₹942) |
| **B15** | Human Agent Monthly Cost (INR) | `30000` | Fully loaded salary + tooling per FTE |
| **B16** | Tickets per Human Agent / Month | `500` | ~23 tickets/day capacity |
| **B17** | Human Agents Needed (Baseline) | `=ROUNDUP(B3/B16, 0)` | 10 agents without AI |
| **B18** | Baseline Human Support Cost | `=B17*B15` | ₹3,00,000 / month |
| **B19** | Human Agents Needed (With AI) | `=ROUNDUP(B6/B16, 0)` | 4 agents with AI |
| **B20** | New Total Support Cost | `=(B19*B15)+B14` | ₹1,20,942 / month |
| **B21** | **Net Monthly Savings (INR)** | `=B18-B20` | **₹1,79,058 / month** |
| **B22** | **Annual Savings (INR)** | `=B21*12` | **₹21,48,696 / year (~₹21.5 Lakhs)** |
