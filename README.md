# ProofAgent Guardrail Enterprise for Claude Code

This branch (`enterprise`) is for companies running **ProofAgent Guardrail Enterprise** on their own servers.
Every prompt, tool call and tool result is checked by **your company's guardrail**, under your company's policies.
Nothing is sent to ProofAgent's cloud, and there is no fallback to it.

**Employees:** open your ProofAgent invite link, choose Claude Code, and run the one command it shows.
It adds this plugin and connects it to your company's server with your personal key.

**What you get**
- Personal data is masked before Claude sees it; the real values are filled back in on your machine only.
- Risky actions your company's policy blocks, or holds for a reviewer, are stopped (mode `strict`, the default).
- `/proofagent` shows the status; if the plugin isn't connected yet, it tells you what to do.

The cloud edition of the plugin is on the `main` branch.

---

<p align="center">
  <img src="assets/logo.png" alt="ProofAgent" width="88" height="88">
</p>

<h1 align="center">ProofAgent for Claude Code</h1>

<p align="center"><b>Keep your private data private.</b> Personal data is masked before Claude sees it,<br>and AI risks are flagged as they happen.</p>

<p align="center"><a href="https://proofagent.ai">proofagent.ai</a> · <a href="https://app.proofagent.ai">Get a key</a> · <a href="https://proofagent.ai/privacy">Privacy</a></p>

---

## Install

**In the Claude desktop app:**

1. **Settings › Customize › Plugins › + Add**, add `ProofAgent-ai/proofagent-claude-plugin`, then install **ProofAgent**.
2. Sign in: open the **proofagent** connector and click **Connect** (in Claude Code: `/mcp` › proofagent › Authenticate).
3. Click **Approve** on the ProofAgent screen. Done: the status line shows `proofagent on (warn)`.

> Already added ProofAgent as a connector on claude.ai? Then you are already signed in: the plugin uses that connection, its own connector shows **Not added** with a greyed-out **Connect**, and there is nothing more to do.

No key to copy. **In Claude Code**, send these one at a time, then sign in as in step 2:

```
/plugin marketplace add ProofAgent-ai/proofagent-claude-plugin
```

```
/plugin install proofagent@proofagent
```

## What you get

- **Masked before Claude sees it.** Names, emails, phones, IDs, card numbers, health data and secrets become placeholders like `maria@acme.com`, in your messages and in what tools return.
- **Real values back, on your machine.** When Claude writes a file or runs a command, the real values are filled in. On your screen, replies show the real values too.
- **AI risks flagged.** Prompt injection, jailbreaks and data leaving, in one short notice.

## Workplace skills

Ask Claude in plain words, or run a skill directly with `/proofagent:<skill>`.

| Skill | Ask | For |
|---|---|---|
| **IP Guard** `ip-guard` | "What am I not allowed to share with AI?" · "Why was this blocked?" | Everyone |
| **Safe to Share** `safe-to-share` | "Make this safe to send" | Everyone |
| **Privacy X-Ray** `privacy-xray` | "What's sensitive in this file?" | Everyone |
| **Vendor Check** `vendor-check` | "Can I send this to our supplier?" | Everyone |
| **Meeting Cleaner** `meeting-cleaner` | "Clean these minutes so I can share them" | Everyone |
| **Scam Radar** `scam-radar` | "Is this email genuine?" | Everyone |
| **Code Share Check** `code-share-check` | "Can I post this code in a public issue?" | Developers |
| **Secret Sniffer** `secret-sniffer` | "Is this file safe to commit?" | Developers |
| **HR Hush** `hr-hush` | "Anonymise these CVs" | HR |
| **Client Cloak** `client-cloak` | "Anonymise my client's details" | Legal, consulting |
| **Patient Privacy** `patient-privacy` | "Remove patient details from this note" | Healthcare |
| **Invoice Shield** `invoice-shield` | "Is this invoice legitimate?" | Finance |
| **Pay Pause** `pay-pause` | Runs before any payment | Finance |
| **Safety Score** `safety-score` | "What did the guardrail check for me?" | Everyone |

The checks themselves are automatic: these skills add help on top (explaining a stop, preparing a safe version). What is confidential and which folders are restricted is set by your administrator in the console, under **Policies › Confidential projects and restricted folders**; a skill never loosens it.

ProofAgent helps you spot risks; it does not guarantee to catch everything, and it is not legal or compliance advice.

