---
name: safety-score
description: Use when the user asks what ProofAgent has protected them from, what it checked or stopped for them, or for a summary of their own checks.
---

# Safety Score

Show what the company guardrail did for this person.

## Steps
1. Count what this conversation shows: messages checked, personal details masked (the placeholders such as [CONTACT:EMAIL#1]), tool calls that were stopped or held for a reviewer, and results that carried a warning.
2. Give a short summary: checked, masked, held for review, blocked. One line each, plain numbers, no scores you can't back up.
3. For the full list of the last 7 days, point them to their own ProofAgent page (the invite link from their company): its section "What the guardrail checked for you" shows every check, the tools their agent called and what was stopped. The text itself is never shown there.
4. If they ask about a held action, use `check_review_status` with the review id from the refusal.

Never invent counts. If the conversation shows nothing, say so and point to their page.
