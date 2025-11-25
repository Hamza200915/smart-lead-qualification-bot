# Smart Lead Qualification & Auto Follow‑Up

AI-powered automation that reads new leads from a Google Form, scores them with OpenAI, sends a personalized email reply, and alerts the business owner when a lead is hot.

---

## 🔍 What this project does

This project is a **smart lead qualification bot** built with:

- **Google Forms + Google Sheets** – collect and store leads
- **Make.com** – automation / workflow engine
- **OpenAI (ChatGPT)** – extract info, score the lead, write emails
- **Gmail** – send replies and owner alerts

**Flow in plain English:**

1. A person fills out a **Google Form** (name, email, what they need, budget, timeline).
2. The response is saved as a new row in a **Google Sheet**.
3. **Make.com** watches the sheet and triggers when a new row appears.
4. The row is sent to **OpenAI**, which:
   - extracts the key details
   - gives the lead a **score (0–100)**
   - labels it as **hot / warm / cold**
   - generates a **personalized reply email** text
5. The reply text is sent to the lead via **Gmail**.
6. The **AI Score** and **AI Label** are written back into the Google Sheet.
7. If the label is **hot**, a second Gmail step sends a **“HOT lead” alert email** to the business owner with all the details.

---

## ✨ Features

- ✅ Automatic intake from Google Form → Google Sheet  
- ✅ AI-powered extraction of:
  - what the lead needs
  - budget
  - timeline
- ✅ Lead scoring (0–100) using OpenAI
- ✅ Lead classification:
  - **hot** – clear need, real budget, urgent
  - **warm** – interested but less clear/urgent
  - **cold** – just exploring, low budget, no real timeline
- ✅ Personalized follow-up email for every lead
- ✅ Instant **HOT lead alert** to the owner
- ✅ Lead score + label stored in the sheet for later analysis

---

## 🧱 Tech Stack

- **Automation:** Make.com
- **LLM:** OpenAI Chat Completions API (e.g. `gpt-4.1-mini`)
- **Input:** Google Forms
- **Data store:** Google Sheets
- **Email:** Gmail

---

## 🧠 Lead scoring logic (concept)

The exact scoring is done by the LLM using a prompt, but the idea is:

- High score / **hot**
  - Clear, specific project
  - Defined budget (e.g. $1000+)
  - Short timeline (days / 1–2 weeks)
- Medium score / **warm**
  - Somewhat clear idea
  - Some budget
  - Flexible timeline (weeks / 1 month)
- Low score / **cold**
  - “Just exploring” / very vague
  - No real budget
  - No real timeline (“someday”, “no rush”)

Example JSON returned by OpenAI:

```json
{
  "score": 88,
  "label": "hot",
  "reply_email": "Hi Aisha, ..."
}
