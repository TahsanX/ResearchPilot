# Setup and Reproduction

This guide is an initial outline. Exact SQL and screenshots will be added after the live configuration is confirmed.

## Prerequisites
- Make.com account
- Google Gemini API access
- Supabase project
- Telegram bot created through BotFather
- Gmail connection in Make.com

## Setup sequence
1. Create a Supabase project.
2. Create required tables and policies using the SQL in `database/`.
3. Create a Telegram bot and keep its token private.
4. Configure Gemini access.
5. Import the three Make.com blueprints from `workflows/`.
6. Reconnect imported modules to your own accounts.
7. Configure schedules and timezone.
8. Run manual tests.
9. Enable schedules after verifying the complete cycle.

## Secrets
Never commit Telegram bot tokens, Gemini API keys, Supabase service-role/secret keys, Gmail OAuth tokens, or private user data. Use Make.com connections and placeholders in examples.

## To confirm
- Required Make.com plan/features.
- Exact timezone.
- Final SQL schema and RLS policies.
- Blueprint import behavior in a fresh account.
- External API limits and configuration.
