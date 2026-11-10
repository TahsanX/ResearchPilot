# Screenshots and Execution Evidence

This page is the visual evidence index for the ResearchPilot implementation. The screenshots are stored in the repository-level `screenshots/` directory and are embedded below so readers can follow the actual Make.com scenarios and user-facing outputs.

> **Image path convention:** keep the image filenames exactly as shown below. From this document (`docs/screenshots.md`), the images are referenced using `../screenshots/<filename>`.

## 1. Make.com scenario overview

### Integration Telegram Bot — Reply handling and selection workflow

![Integration Telegram Bot scenario](../screenshots/Integration_Telegram_Bot.png)

This scenario receives Telegram updates, checks the selection state, processes the reply, and routes valid and invalid input. A valid selection is resolved against the available topic options and saved to Supabase. Invalid input receives a corrective Telegram message.

### ResearchPilot Front — Daily topic generation

![ResearchPilot Front scenario](../screenshots/ResearchPilot_front.png)

The Front scenario runs on its daily schedule. It retrieves recent research context, asks Gemini to generate five research-topic recommendations, stores the suggestions in Supabase, and sends the numbered choices to Telegram.

### ResearchPilot Backend — Paper retrieval and analysis

![ResearchPilot Backend scenario](../screenshots/ResearchPilot_Backend.png)

The Back scenario retrieves the selected topic, searches arXiv, parses the XML response, processes paper entries, and uses Gemini to analyze the research. The workflow branches to Gmail for report delivery and Supabase for structured persistence.

## 2. Telegram interaction

### Daily recommendations and input validation

![Telegram topic selection conversation](../screenshots/telegram_chat.png)

The Telegram conversation demonstrates the user-facing topic-selection experience:

- The bot sends five numbered research-topic recommendations.
- A message such as `56` is rejected because it is outside the allowed range.
- A non-numeric message such as `Rrrr` is rejected.
- The bot asks the user to enter a valid number from 1 to 5.
- A valid reply such as `2` is accepted and the bot confirms the response.

The intended parser can also extract a single unambiguous choice from natural-language replies (for example, `I like 4`). Messages containing multiple possible choices should be treated as ambiguous and rejected. After a successful selection is saved, the selection window closes; further messages must not alter the selected topic for that batch.

## 3. Research email output

### Individual paper analysis

![Research analysis email — individual paper review](../screenshots/email1.png)

This screenshot demonstrates the individual-paper section of the generated research email, including the paper title, link, research objective, methodology, findings, limitations, drawbacks, improvements, and future research directions.

### Comparative research summary

![Research analysis email — comparative insights](../screenshots/summary_email.png)

This screenshot demonstrates the comparative section of the email report. It brings together common limitations, methodological differences, and possible directions for further investigation across the analyzed papers.

## 4. Evidence notes

- These screenshots document one observed workflow layout and example execution. They do not prove that every future run will succeed.
- Scenario screenshots show the Make.com module arrangement; individual module settings and API mappings are documented separately.
- The Telegram screenshot is an example interaction, not a full test suite.
- Email content should be checked against the original papers before being used as academic evidence.
- Replace or supplement these screenshots when the workflow changes materially.

## 5. Suggested repository layout

```text
ResearchPilot/
├── docs/
│   └── screenshots.md
└── screenshots/
    ├── email1.png
    ├── Integration_Telegram_Bot.png
    ├── ResearchPilot_Backend.png
    ├── ResearchPilot_front.png
    ├── summary_email.png
    └── telegram_chat.png
```
