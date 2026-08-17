# SOC Prompt Library

Structured prompts for security operations work: alert triage, detection writing, phishing analysis, threat intel, incident response. Built for people who have to check the output, not people who want a magic button.

**25 prompts, free, MIT licensed.** The alert-triage workflow here is complete and usable on its own.

---

## Why these are different from a generic prompt list

Four design choices you'll see repeated throughout:

1. **Benign explanations get ranked before malicious ones.** Otherwise you anchor the model, and yourself, on the scary answer.
2. **Every hypothesis needs disconfirming evidence.** The prompts ask what would *kill* an idea, not only what supports it. That is the difference between analysis and a confident guess.
3. **"Insufficient data" is an allowed verdict.** Most prompts force a call. These don't.
4. **The model is told not to invent things.** No event IDs, field names, table names, GUIDs or ATT&CK mappings it wasn't given. When it can't determine something, the right answer is saying so.

---

## Start here

| File | Why |
|---|---|
| [Data handling](00-START-HERE/data-handling.md) | What to strip from alert data before it leaves your tenancy. Read first. |
| [Version block](00-START-HERE/version-block.md) | Paste once per session. The single best defence against a model inventing identifiers. |
| [Environment profile](00-START-HERE/environment-profile.md) | Fill in once. Every prompt afterwards gets sharper. |

## The prompts

| Workflow | Count | |
|---|---|---|
| [Alert triage & enrichment](triage/) | 20 | Complete loop: alert in, verdict and case note out |
| [Detection engineering](detection/) | 1 | LSASS credential access |
| [Phishing & email analysis](phishing/) | 1 | SPF / DKIM / DMARC / ARC interpretation |
| [Threat intelligence](threat-intel/) | 2 | ATT&CK mapping, CVE triage |
| [Incident response](incident-response/) | 1 | Forensic timeline from raw events |

Prefer one file? [ALL-PROMPTS.md](ALL-PROMPTS.md).

## How to use them

1. Paste the [version block](00-START-HERE/version-block.md) at the top of your session.
2. Paste your [environment profile](00-START-HERE/environment-profile.md) if you've built one.
3. Copy the prompt, replace the `[BRACKETED_PLACEHOLDERS]`, paste your data.
4. Read the output critically. Verify before you act.

Works with ChatGPT, Claude, Copilot, Gemini or a local model. Output quality and instruction-following vary by model and plan. Smaller local models will drop some of the longer multi-part instructions.

## A caution worth repeating

An LLM-invented field name that silently returns zero rows beats no detection in exactly one way: it lets you believe you have coverage you don't have. Nothing generated here goes live until you validate it against your own schema.

These prompts assist a trained analyst. They are not security, legal or compliance advice, and they don't replace your judgement.

## The full library

This repo is the alert-triage workflow plus four samples. The complete library covers six workflows end to end:

- 200 prompts: triage, detection writing, phishing, threat intel, IR comms, exec and board reporting
- An advanced pack: 30 detection-engineering prompts (AD CS, Kerberos delegation, Golden SAML, OAuth consent abuse, Kubernetes, EDR/ETW tampering, detection-as-code), 18 fill-in IR comms templates, 6 chaining playbooks

[**See all 200 prompt titles**](Blue-Team-Prompt-Vault-CONTENTS.pdf) — the full contents list, free and ungated, no email.

[**Get the Vault**](https://blueteamvault.gumroad.com/l/blueteampromptvault) — PDF and copy-paste Markdown, lifetime v1.x updates, 7-day money-back guarantee.

## Contributing

Found something wrong, or something that could be sharper? Open an issue. Corrections ship to everyone.

Maintained by **BlueTeamVault**. Built by a working security practitioner. The prompts are the CV: read them and judge.

## Licence

MIT. See [LICENSE](LICENSE). Use these at work, on client engagements, in your own tooling.
