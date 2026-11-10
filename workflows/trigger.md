# ResearchPilot Trigger — Telegram Topic Selection

## Purpose
Receive a Telegram reply, validate it, and store the corresponding suggested topic.

## Intended sequence
1. Telegram Bot — Watch Updates.
2. Retrieve the current selection state from Supabase.
3. If selection is closed, send a closed-selection message.
4. If open, match a single digit from 1 to 5.
5. Route valid and invalid replies separately.
6. For a valid reply, retrieve the corresponding topic from the current batch.
7. Insert the topic into `selected_topics`.
8. Close selection only after successful insertion.

## Input validation
```regex
^[1-5]$
```
This accepts only `1`, `2`, `3`, `4`, or `5`. Inputs such as `hello`, `0`, `6`, `I choose 3`, and `2 and 4` should be rejected.

The Text Parser capture group can be checked using Exists / Does not exist filters.

## Suggested messages
Invalid input: “Please reply with a valid number between 1–5.”

Closed selection: “Topic selection is currently closed. Please wait until the next selection round.”

## State transition
```text
awaiting_selection = false
        |
        | New batch published
        v
awaiting_selection = true
        |
        | Valid reply saved
        v
awaiting_selection = false
```

Invalid input must not close the selection window.

## Safeguards
- Map the incoming Telegram chat ID dynamically if supporting multiple users.
- Associate each selection with the current batch.
- Reject stale replies from previous batches.
- Close selection only after the selected topic is saved.
- Consider duplicate-update handling.

## To confirm
- Exact deployed regex and parser settings.
- Whether state is checked before parsing.
- Whether chat ID, prompt message ID, batch ID, and expiry are validated.
- Whether duplicate Telegram updates are deduplicated.
