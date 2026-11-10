# ResearchPilot Front — Topic Generation

## Purpose
Generate five personalized research-topic suggestions from recent research context, store them, and send the choices through Telegram.

## Intended sequence
1. Scheduler at 9:00 PM.
2. HTTP request retrieves recent research context from Supabase.
3. Gemini generates exactly five topic strings.
4. Parse and validate the JSON response.
5. Insert the five suggestions into `suggested_topics`.
6. Send the numbered choices through Telegram.

## Topic distribution
- Topics 1–3: deeper exploration of recent research activities.
- Topics 4–5: related but different research directions.

The prompt instructs Gemini to avoid duplicates, broad topics, fabricated history, and unsupported novelty claims.

## Output contract
```json
[
  "Research topic 1",
  "Research topic 2",
  "Research topic 3",
  "Research topic 4",
  "Research topic 5"
]
```

Validate that the parsed output is an array of exactly five non-empty strings before inserting anything.

## Reliability
Send the Telegram message only after all five suggestions have been stored successfully.

## To confirm
- Exact Supabase source table, query, sort order, and limit.
- Whether JSON parsing and five-item validation are deployed.
- Whether all five rows are inserted before Telegram notification.
- How batch IDs, active flags, and expiry are assigned.
