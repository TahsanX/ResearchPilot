# ResearchPilot Prompt Documentation

This section contains the system prompts used by the two Gemini-powered stages of ResearchPilot.

## 1. Frontend — Topic Discovery

File: [`prompts/frontend-topic-discovery.md`](prompts/frontend-topic-discovery.md)

Used by **ResearchPilot Front** to analyze recent research context and generate exactly five topic suggestions:
- Topics 1–3 deepen recent research directions.
- Topics 4–5 explore related but different domains.
- Output is one JSON array containing exactly five non-empty strings.
- Make.com must still parse and validate the result before saving it; prompt instructions alone cannot guarantee complete output.

## 2. Backend — Paper Analysis and Email Reporting

File: [`prompts/backend-paper-analysis.md`](prompts/backend-paper-analysis.md)

Used by **ResearchPilot Back** to:
- Extract each paper's existing XML `<summary>` without rewriting it.
- Verify methodology against the actual paper whenever accessible.
- Separate author-acknowledged limitations from analyst-identified drawbacks.
- Propose evidence-grounded improvements and research opportunities.
- Generate a detailed email report with paper-by-paper analysis and comparative insights.
- Return exactly two top-level output sections: `EMAIL_SUBJECT` and `EMAIL_BODY`.

## Deployment notes

- Copy the relevant prompt into the corresponding Gemini module's System Instructions.
- Keep the Frontend's JSON output contract separate from the Backend's email-report output contract.
- Validate structured model output in Make.com before writing to Supabase.
- Do not commit API keys, bot tokens, Supabase secret keys, private chat IDs, or personal data.
- Keep a dated copy of each deployed prompt version when making changes.
