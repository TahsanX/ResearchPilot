# ResearchPilot Back — Paper Retrieval and Analysis

## Purpose
Retrieve the selected topic, discover arXiv papers, analyze them with Gemini, email a report, and store structured results in Supabase.

## Intended sequence
1. Scheduler at 9:00 AM.
2. Retrieve the selected topic from Supabase.
3. Send an arXiv API request.
4. Parse the Atom/XML feed.
5. Iterate through paper entries and collect metadata.
6. Prepare paper content for Gemini.
7. Ask Gemini to analyze the paper or papers.
8. Send a readable report through Gmail.
9. Store structured analysis in Supabase.

## Paper information to capture
Potential fields include title, abstract, authors, published date, updated date, arXiv identifier, and paper URL.

**To confirm:** exact extracted fields and whether the workflow downloads full-text PDFs or analyzes metadata/abstracts only.

## Analysis dimensions
- Research objective
- Methodology
- Main findings
- Limitations / shortcomings
- Potential research gaps
- Future research directions
- Source paper URL

Distinguish limitations stated by the paper from model-inferred observations. Do not present an unverified gap as proven novelty.

## To confirm
- Exact arXiv endpoint and query construction.
- Maximum papers retrieved per topic.
- Whether papers are analyzed individually or in a batch.
- Exact Gemini analysis prompt and output structure.
- Whether Gmail sends before or after database persistence.
- Error handling for zero results, malformed XML, Gemini failures, and email failures.
