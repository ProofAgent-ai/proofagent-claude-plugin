<p align="center">
  <img src=".claude-plugin/icon.png" alt="ProofAgent" width="96" height="96">
</p>

<h1 align="center">ProofAgent for Claude Code</h1>

<p align="center"><b>Keep your private data private.</b><br>
Personal data is masked before Claude sees it, risks are flagged as they happen,<br>
and the real values are filled back in on your machine, only where they are needed.</p>

<p align="center">
  <a href="https://proofagent.ai">proofagent.ai</a> ·
  <a href="https://app.proofagent.ai/connect">Get a key</a> ·
  <a href="https://proofagent.ai/privacy">Privacy</a>
</p>

---

## Install

In Claude Code:

```
/plugin marketplace add ProofAgent-ai/proofagent-claude-plugin
/plugin install proofagent@proofagent
```

Claude Code asks for your **ProofAgent guardrail key** (from [app.proofagent.ai](https://app.proofagent.ai) › API keys). It is kept in your system's secure storage. The status line then shows `proofagent on (warn)`.

## What it does

| | |
|---|---|
| **Masks personal data before Claude sees it** | Names, emails, phone numbers, IDs, card and bank numbers, health data and secrets in your messages and in tool results are replaced by placeholders such as `[CONTACT:EMAIL#1]`. Claude only ever sees the placeholders. |
| **Puts the real values back, on your machine** | When Claude runs a tool (writes a file, runs a command, calls an API), the placeholders are filled in with the real values just before it runs. Claude's replies are drawn on your screen with the real values too, while the conversation Claude reads keeps the placeholders. |
| **Flags risks as they happen** | Prompt injection, jailbreaks and system prompt extraction (**AI risk**), and data leaving (**Data risk**), in your messages, Claude's actions and what tools return, in one short notice. |
| **Applies your organization's policy** | Every check uses the policy of your ProofAgent workspace: what to mask, which terms are off limits, which actions need a person. |

Notices look like this:

```
ProofAgent (your message): masked email, first name · ⚠ AI risk: Direct prompt injection
ProofAgent (Bash): ⚠ Data risk: Data exfiltration
```

## How it works

```
 you type ──► ProofAgent masks + checks ──► Claude (placeholders only)
                                               │
                  real values filled in  ◄─────┘ tool call
                  on your machine
                         │
 tool result ──► ProofAgent masks + checks ──► Claude (placeholders only)
```

1. **Your message** is sent to ProofAgent Nano, which finds personal data and risks. The plugin replaces each value with a numbered placeholder. The same value always gets the same placeholder for the whole session.
2. **The lookup table** (placeholder → real value) lives **only in your Claude Code session's memory**. It is never written to disk and never sent to Claude or to ProofAgent.
3. **Before a tool runs**, the action is checked against your policy (ProofAgent sees the placeholders, not the real values), then the plugin fills in the real values.
4. **What the tool returns** is checked and masked again before Claude reads it.

Your messages are never blocked. Risky ones go on to Claude with a notice, and Claude is told not to follow instructions that override its rules or send data out.

## Modes and commands

| | |
|---|---|
| `warn` (default) | Mask and notify. Risky actions run with a notice. |
| `strict` | Also stops risky actions (deletes, sends, payments, outside recipients) before they run. |
| `/proofagent` | Status and how many values were masked this session |
| `/proofagent off` · `/proofagent on` | Pause and resume for this session |

Settings (`/plugin` › proofagent): key, mode, **show real values on my screen** (on by default; turn it off when sharing your screen), endpoint (for on-premises installs), and a key file instead of a pasted key.

## Plugin or connector?

| | Claude Code plugin (this repo) | Claude connector |
|---|---|---|
| Where | Claude Code | Claude on the web, Desktop and Claude Code |
| When it checks | **Every** message, action and tool result, automatically | When Claude decides to call it, or when you ask |
| Masks before Claude sees the data | Yes, with real values restored on your machine | No: Claude sees the text, then calls ProofAgent |
| Set up | `/plugin install` and a key | Add `https://nano.proofagent.ai/mcp` in Claude › Settings › Connectors and approve |

The plugin also adds the connector's tools (`check_user_message`, `check_before_execute`, `scan_text` and more), signed in through the same ProofAgent approval screen.

## Privacy

- Claude sees placeholders only. The real values stay in your session's memory and on your screen.
- The text being checked is sent to your ProofAgent endpoint over HTTPS, processed in memory and **not stored**. Only usage counts and decisions are kept, for your workspace's Usage page.
- If ProofAgent cannot be reached, the plugin steps aside (your work is never stuck).

Known limits: images and screenshots are not masked; text typed after a slash command is not rewritten.

## Requirements

A recent Claude Code (plugins with hooks modules) and a ProofAgent account. Free accounts include monthly checks.

## Development

```
claude plugin validate plugins/proofagent
claude plugin test plugins/proofagent
```

## License

Apache-2.0. © ProofAgent.
