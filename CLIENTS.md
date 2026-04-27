# Client Strategy — Selling AI to Local Businesses in Norrbotten

> This file goes in any project related to client outreach, demos, or sales.
> It gives Claude Code full context on who I'm selling to, what I'm selling, and how.

---

## Who I Am (Sales Context)

I'm Yahya — a solo AI developer in Norrbotten, Sweden. I build AI tools for small local businesses. I have no paying clients yet, but I have four real working demos. I'm pricing low on purpose to land my first clients and build a portfolio.

**All outreach is in Swedish.**

---

## What I Sell

### 1. RAG Chatbot (Kunskapsbot)
A chatbot trained on the client's own documents. Customers ask questions, the bot answers from the business's actual content — menus, FAQs, service info, manuals.

- **Best for:** Restaurants, clinics, gyms, construction companies, property managers
- **Delivered as:** Embeddable widget or standalone page
- **Stack:** Python/FastAPI + Claude API + Supabase pgvector + HTML frontend. Deployed on Render/Netlify/Cloudflare.
- **Price:** 1 500 – 2 500 SEK

### 2. AI Customer Service Bot (Svarbot)
Handles common customer questions automatically, 24/7 without staff involvement.

- **Best for:** Any business that gets repetitive questions via phone, email, or social
- **Price:** 1 000 – 1 500 SEK

### 3. AI Automation
Automates repetitive tasks — classifying emails, summarizing documents, extracting structured data, connecting tools.

- **Examples:** Auto-respond to form submissions, summarize reports, push data to Google Sheets
- **Price:** 1 000 – 2 000 SEK

### 4. Custom AI Solutions
Anything that doesn't fit the above. Built to spec.

- **Price:** Offert (quote on request)

---

## Demos I've Already Built

These are real, deployed projects I can show prospects:

| Demo | Business | What it does |
|---|---|---|
| **FriluftsByn** | Nature retreat, Höga Kusten | RAG chatbot on Netlify answering questions about the venue, events, and nature activities |
| **TandAkutenNorr** | Dental emergency clinic, Luleå | RAG chatbot answering questions about opening hours, services, costs. Cloudflare Workers deployment. |
| **LS Bygg & Snickeri** | Construction company, Piteå | "Lars" — RAG chatbot answering questions about services, ROT-avdrag, pricing. Render deployment. |
| **The Unit** | Gym/fight center, Luleå | RAG chatbot answering questions about classes, memberships, and schedule. The base template. |

When approaching a new prospect, build a custom demo for their business before reaching out — or at minimum reference the most relevant existing demo.

---

## Who to Target

Small and medium businesses in Norrbotten that:
- Get repetitive customer questions (öppettider, priser, tjänster, meny)
- Rely on manual processes that could be automated
- Have little to no existing AI tools
- Would benefit from 24/7 availability without hiring more staff

**Best-fit industries in the region:**
- Restauranger & caféer
- Tandläkare / vårdcentraler / kliniker
- Fastighetsbolag / mäklare
- Butiker & e-handel
- Hantverkare (städ, bygg, el, VVS)
- Gym & friskvård

**Priority targets:** Businesses that already have a decent website with content — easier to build a RAG KB from their existing material.

---

## Pricing

Intentionally low. I'm building a portfolio, not maximizing margin yet.

| Tjänst | Pris (SEK) |
|---|---|
| Enkel chatbot / svarbot | 1 000 – 1 500 |
| RAG-chatbot med dokument | 1 500 – 2 500 |
| AI-automation (enklare) | 1 000 – 2 000 |
| Anpassad lösning | Offert |

No monthly fees unless the client wants ongoing maintenance or updates.

---

## Outreach Approach

**Goal of first message: get a reply, not a sale.**

- Messages in Swedish, informal but professional
- 3–5 sentences max for first contact
- Lead with a specific problem the business likely has
- Reference a live demo or offer to show one
- No pressure, no jargon — speak like a person

**Template structure (adapt per business):**
1. Hej [namn], jag heter Yahya och bygger AI-lösningar för lokala företag i Norrbotten.
2. Jag la märke till att [specific observation about their business / problem they likely have].
3. Jag har byggt en AI-assistent som kan [konkret nytta] — [reference demo or offer to show].
4. Inga kostnader förrän du sett hur det fungerar. Intresserad av en snabb demo?

---

## Constraints & Honest Limits

- No client testimonials yet — lead with demos instead
- I build and hand off. No ongoing maintenance unless explicitly agreed and priced.
- I don't do website design from scratch or traditional software dev — I focus on AI features and automations
- If a project is out of scope, I say so rather than overpromise
- I'm in Älvsbyn — most client contact will be remote (video call / email / phone). That's fine for this type of work.

---

## How to Find New Prospects

The **Approach Local Businesses** project handles this:
- Scrapes businesses by category and city
- Scores and deduplicates
- Pushes to Google Sheets for review and outreach

Run that pipeline to build the prospect list. Never collect or use Facebook/Instagram data — phone and email only.
