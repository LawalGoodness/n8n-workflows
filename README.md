# n8n-workflows
Here's the updated explanation with the APIs included:

This is an **n8n automation workflow** that runs every 20 minutes to generate and deliver a daily AI-written short story digest. Here's the flow:

1. **Schedule Trigger** — Kicks off the workflow every 20 minutes.
2. **Tales Maker** — Uses the **OpenAI API (GPT-5.2)** acting as a "master storyteller" to generate a completely random short story with full creative freedom on genre, characters, and plot.
3. **The Dust-Sweeper** — Uses the **OpenAI API (GPT-5-mini)** to compare the new story against a **Google Sheets API** log of past stories, removing duplicates even if worded differently. If everything is a duplicate, it outputs *"No new AI stories in the past 24 hours."*
4. **The Postmaster** — Uses the **Gmail API** to email the cleaned-up story digest to `mrgoodness2005@gmail.com` with the subject *"Daily Stories Digest."*
5. **Append Row in Sheet** — Uses the **Google Sheets API** again to log the new story headline and today's date for future duplicate-checking.

**APIs used at a glance:**
- **OpenAI API** (GPT-5.2 & GPT-5-mini)
- **Google Sheets API**
- **Gmail API**
