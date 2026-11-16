---
name: safety-score
description: Shows what ProofAgent caught in this conversation, and the checks and credits left. Use when the user asks what ProofAgent protected them from, their usage, or a weekly or monthly summary.
---

# 🏅 Safety Score

Show the value ProofAgent delivered.

## Steps
1. Call `get_usage` (free, uses no check).
2. Count what earlier ProofAgent results in this conversation caught: details masked, scams flagged, actions held or blocked.

## Answer format
**🏅 Safety Score**
- Free checks left this month, and credits.
- What was caught in this conversation.
- One tip for next week.

## Rules
- If the ProofAgent tools are not available, say so and stop: in Claude Code run `/mcp`, choose proofagent, then Authenticate (on claude.ai: Settings > Connectors > ProofAgent > Connect). Keys are at https://app.proofagent.ai. Don't guess a result.
- Use plain words, no security jargon.
