# Alert Triage & Enrichment

A complete triage loop: alert in, verdict and case note out.

| # | Prompt | Use it when |
|---|---|---|
| 01 | [First-Pass Alert Triage Workflow](01-first-pass-alert-triage-workflow.md) | A fresh alert lands and you need a structured starting point before digging in. |
| 02 | [IP Address Enrichment Summary](02-ip-address-enrichment-summary.md) | An alert references an external IP and you need fast context without ten browser tabs. |
| 03 | [Domain Reputation Triage](03-domain-reputation-triage.md) | A domain shows up in proxy, DNS, or email logs and you need to judge it. |
| 04 | [File Hash Verdict Helper](04-file-hash-verdict-helper.md) | You have a hash from an EDR detection and want a structured reputation workflow. |
| 05 | [URL Deconstruction & Risk Read](05-url-deconstruction-risk-read.md) | A suspicious URL appears in an email or proxy log and you need to read it safely. |
| 06 | [Raw Log Line Interpreter](06-raw-log-line-interpreter.md) | You're staring at an unfamiliar log line and need it explained field by field. |
| 07 | [Multi-Line Log Sequence Storyline](07-multi-line-log-sequence-storyline.md) | You have a cluster of related log entries and need the narrative they tell. |
| 08 | [Severity & Priority Scoring](08-severity-priority-scoring.md) | You must assign or sanity-check a severity rating before queue ordering. |
| 09 | [False-Positive Hypothesis Test](09-false-positive-hypothesis-test.md) | An alert smells like noise but you need to justify closing it. |
| 10 | [EDR Process Alert Triage](10-edr-process-alert-triage.md) | Your EDR flags a suspicious process and you need to judge the execution. |
| 11 | [Decode Encoded PowerShell / Base64 Command](11-decode-encoded-powershell-base64-command.md) | A command line contains base64 or an encoded PowerShell payload. |
| 12 | [Azure / Entra Sign-In Anomaly Triage](12-azure-entra-sign-in-anomaly-triage.md) | An Azure AD / Entra ID risky sign-in or conditional-access alert fires. |
| 13 | [Impossible-Travel Investigation](13-impossible-travel-investigation.md) | An identity tool flags two logins too far apart to be physically possible. |
| 14 | [Network IDS/IPS Alert Triage](14-network-ids-ips-alert-triage.md) | A Suricata/Snort/Zeek or NDR signature fires and you need to read it. |
| 15 | [C2 Beaconing Analysis](15-c2-beaconing-analysis.md) | A host shows repetitive outbound connections that may be command-and-control. |
| 16 | [ATT&CK Technique Mapping of an Alert](16-att-ck-technique-mapping-of-an-alert.md) | You need to map an alert's observed behaviour to MITRE ATT&CK cleanly. |
| 17 | [Escalation Decision Support](17-escalation-decision-support.md) | You're unsure whether to escalate to tier-2/IR or close it yourself. |
| 18 | [Business & Asset Context Questions](18-business-asset-context-questions.md) | An alert's severity depends on context only the business or asset owner has. |
| 19 | [Ready-to-Paste Case Note](19-ready-to-paste-case-note.md) | You've finished triage and need a clean, defensible ticket note. |
| 20 | [End-of-Shift Triage Summary & Handover](20-end-of-shift-triage-summary-handover.md) | You're closing a shift and need to hand the queue over cleanly. |
