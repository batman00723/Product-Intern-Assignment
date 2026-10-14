# AI Prompt Log & Iteration History
**Candidate:** Aman Mishra (`batmanmishra23@gmail.com`)  
**Assignment:** Cheerio Product Intern Assignment — Assignment A  
**Primary AI Tool Used:** Antigravity  

---

## My Approach to Using AI

I treated Antigravity as a fast, technical sparring partner rather than an auto-pilot. Whenever I asked it broad questions, it gave me textbook SaaS corporate fluff (like "write help center articles" or "hire account managers"). But when I treated it like a junior developer or a research assistant—giving it tight constraints, specific Indian business personas, and strict layout requirements—it saved me hours of manual coding and helped me dig up real edge cases.

Below is the honest log of the prompts I ran, what worked, what failed, and how I iterated.

---

## Prompt 1: Grounding the Persona & Finding Real Setup Blockers

### The Prompt:
> *"I am working on a product assignment for Cheerio (https://cheerio.in). The user is Aman Mishra, who runs GATESprint Academy, an online coaching institute for GATE exam aspirants in India. He is non technical and gets leads from Instagram ads. List the 5 most common setup issues he will run into on Cheerio, in the order he would face them."*

### What Antigravity Generated:
It broke down the setup journey chronologically:
1. Connecting the phone number and getting WhatsApp Business API approval.
2. Meta rejecting broadcast templates for promotional wording.
3. Designing the chatbot flow to qualify students without knowing logic trees.
4. Pushing leads to Google Sheets and routing them to human counsellors.
5. Diagnosing delivery failures during live marketing campaigns.

### What Was Missing & What I Changed:
The initial response used generic American coaching terms (like "SAT prep" and "advisors"). I refined the context manually:
* Changed exam streams to real GATE engineering branches (`CSE`, `Data Science & AI`, `Mechanical`, `Electrical`, `Electronics`).
* Added the real operational reality: coaching owners in Lucknow or Jaipur do not care about API endpoints; they care about admissions counsellors (like Priya Sharma) getting callbacks before students join a rival institute.

---

## Prompt 2: The Broad Question That Completely Failed

### The Initial Prompt:
> *"How can Cheerio scale customer support for non technical users?"*

### Why It Failed:
This was way too broad. Antigravity gave me five pages of generic B2B boilerplate:
* *"Build an extensive Intercom help center with searchable FAQs."*
* *"Create 5-minute Loom onboarding video tutorials."*
* *"Hire outsourced Level-1 support reps in different time zones."*

None of this actually solves the problem. A non technical founder under pressure 2 hours before a weekend webinar is not going to read a 12-page help doc or watch a video. They want the software to just work.

### How I Iterated:
I threw out the help center idea completely. I realized the solution had to live **inside the setup screen itself**. 

I ran this targeted follow-up prompt:
> *"Forget external help docs and videos. If the product interface itself had an AI assistant that auto-fills form fields on the screen as the user speaks in plain language, how would the interaction work? Give me a split-screen concept."*

This shift directly produced the core thesis of my submission: **The Setup Copilot (Chat × Form Workspace)**.

---

## Prompt 3: Uncovering WhatsApp Template Rejection Edge Cases

### The Prompt:
> *"Write a WhatsApp broadcast template for an online coaching institute announcing a free GATE strategy session. Also tell me what phrases Meta usually rejects during template review for education businesses."*

### What Antigravity Generated:
It wrote a sample broadcast message and highlighted Meta's strict rules around unprovable academic claims. It pointed out that phrases like *"get a winning plan"* or *"guaranteed rank boost"* trigger automated spam rejections under Meta Policy 4.2.

### What I Changed & How I Used It:
I took this exact edge case and built it into the heart of the interactive prototype:
* In Card 3 of the prototype, the broadcast message intentionally contains the high-risk phrase *"get a winning plan"*.
* The Copilot flags an amber alert: *"Meta Policy Pre-Flight Warning: 82% rejection risk under promotional guidelines."*
* It provides a 1-click button to rewrite it to compliant copy: *"get a study plan and session details."*

This demonstrates real domain knowledge of the WhatsApp Business API rather than just a generic chatbot demo.

---

## Prompt 4: Building the HTML/JS Interactive Prototype

### The Prompt:
> *"Create a single standalone HTML file with zero dependencies. On the left, put a chat assistant. On the right, put real interactive form inputs for campaign title, exam year dropdown, date/time, 4 student qualifying questions, broadcast template textarea, and Google Sheet integration. When user clicks a chip in chat, auto-fill the form fields on the right."*

### The Bugs & Weaknesses I Caught:

1. **The Flexbox Card Squishing Bug:**  
   Antigravity initially wrapped the right-hand canvas inside a flex container with `overflow: hidden`. When I tested it on my 1080p monitor at 100% zoom, the cards collapsed into flat horizontal strips where you could barely see the headers. You had to zoom out to 30% to read anything.  
   *What I did:* I stripped out the flex constraints and changed the canvas to natural block scrolling (`display: block; overflow-y: auto;`) with proper padding.

2. **The Auto-Publish Safety Violation:**  
   In its first script version, the AI automatically published the campaign live the moment the chat ended. In real life, no business owner wants an AI blasting paid messages to their contact list without reviewing it first.  
   *What I did:* I killed the auto-publish script entirely. I added Card 5 with a mandatory human review table and a strict confirmation checkbox (`confirmChk`). The green **Publish Automation Live** button stays disabled until the human physically checks the box.

3. **The "Pre-Filled Form" Illusion:**  
   When I first tested the HTML file, all inputs were already filled with text on page load. When the user clicked *"I want to run a strategy session"*, the bot claimed it filled the form, but nothing visibly changed.  
   *What I did:* I reset all cards to clean draft states with grey placeholders, and wrote a JavaScript animation (`@keyframes fieldFlash`) that pulses the fields green as the AI fills them.

---

## Prompt 5: Killing the "Generic AI Blue" Palette

### The Prompt:
> *"The prototype currently uses generic royal blue (#2563eb). Drop all electric blue accents and redesign the color variables using Deep Pine Teal (#0f766e) and WhatsApp green. It should look like an authentic WhatsApp enterprise SaaS product, not an AI template."*

### Why This Mattered:
Almost every AI code generator defaults to the same electric royal blue (`#2563eb`) or purple gradient. It looks like a cookie-cutter template. 
* By switching to **Deep Pine Teal (`#0f766e`)**, slate-200 borders, and subtle mint backgrounds (`#f0fdfa`), the prototype looks bespoke, grounded, and native to Meta's Business Suite.

---

## Summary of Prompt Iterations

| # | Topic | Initial AI Output | Flaw / Weakness Caught | My Course Correction |
|---|---|---|---|---|
| 1 | **Persona & Problems** | Generic US college prep advice | Lacked Indian coaching reality | Added GATE streams, WhatsApp ad leads, and counsellor handoff. |
| 2 | **Support Scaling** | Suggested help articles & video tutorials | Nobody reads docs under deadline stress | Pivoted to in-product Setup Copilot (auto-filling live forms). |
| 3 | **Policy Edge Cases** | Generated broadcast copy | Needed a tangible failure mode | Identified Meta Policy 4.2 and built pre-flight warning banner. |
| 4 | **Prototype Layout** | Squished flexbox cards + auto-published | Hard to read; unsafe automation | Fixed block layout; enforced mandatory human sign-off checkbox. |
| 5 | **Visual Styling** | Defaulted to electric royal blue (`#2563eb`) | Looked like generic AI template | Replaced with authentic WhatsApp Deep Pine Teal (`#0f766e`). |

---

## What I Deliberately Did Without AI

1. **The Core Product Thesis:** AI wanted to build knowledge bases. I made the executive call that non technical users need **automated execution**, not more reading material.
2. **Indian Admissions Operations:** The specific dynamics of GATESprint Academy—lead qualification before calling, counselling distribution, and urgent weekend webinar timelines—came from my own understanding of the coaching sector.
3. **The Unit Economics Model:** While Antigravity helped retrieve per-token pricing for Llama 3 70B on Groq, the financial spreadsheet was structured entirely by me: modeling 5,000 businesses at 1.0 query/month, setting realistic agent capacity (500 tickets/month @ ₹30k salary), and demonstrating ₹1.79 Lakhs/month in net savings (59.7% reduction).
4. **The Freemium Strategy:** Deciding that the first 5 campaigns must be 100% free is a human product call. In India, charging users upfront for setup support kills activation.
