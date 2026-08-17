# All prompts, single file

Copy the lot if you'd rather not click through.


## Alert Triage & Enrichment

### First-Pass Alert Triage Workflow

*A fresh alert lands and you need a structured starting point before digging in.*

```text
You are a SOC tier-1 analyst. Environment context: [ENVIRONMENT_CONTEXT — stack, asset criticality, known admin tooling, current projects]. Triage this alert and return: (1) one-line plain-English summary of what it claims happened, (2) the genuinely distinct benign explanations, ranked by likelihood — as many as the evidence supports, not a fixed number, (3) the genuinely distinct malicious explanations, ranked, (4) for each leading hypothesis, the specific evidence that would confirm or kill it, (5) the exact data sources to pull next, (6) a provisional verdict (benign / suspicious / malicious / insufficient data) with confidence stated as High/Medium/Low and what that means here. Do not pad to reach a count. State every assumption explicitly, invent no organisational facts you were not given, and flag anything that must be confirmed with raw logs before acting. Alert: [PASTE_ALERT_JSON_OR_TEXT].
```

Tip: Chain the "exact data sources to pull next" output straight into your SIEM query builder.

### IP Address Enrichment Summary

*An alert references an external IP and you need fast context without ten browser tabs.*

```text
You are a threat-intel analyst. For the IP [IP_ADDRESS], produce a structured enrichment brief: likely ASN/owner and hosting type (residential / cloud / VPS / Tor / CDN), typical legitimate uses of that hosting, what would make traffic to it suspicious in my environment, and the specific reputation checks I should run (with what a "bad" result looks like). Do not invent reputation scores or geolocation you cannot derive — clearly separate inference from verified fact and list what I must confirm in a TI source.
```

### Domain Reputation Triage

*A domain shows up in proxy, DNS, or email logs and you need to judge it.*

```text
You are a DNS and threat-intel analyst. Assess the domain [DOMAIN]. Return: registrable domain vs subdomain breakdown, signals of risk to check (registration age, registrar, entropy/DGA-likeness of the label, lookalike/typosquat of [KNOWN_BRAND], wildcard or fast-flux hints), legitimate reasons it might appear, and a prioritised checklist to confirm verdict. Mark each risk signal as "observable from data I have" vs "requires external lookup." Flag clearly if this looks like a typosquat and why.
```

### File Hash Verdict Helper

*You have a hash from an EDR detection and want a structured reputation workflow.*

```text
You are a malware triage analyst. For file hash [HASH] (type: [MD5/SHA1/SHA256]) seen as [FILENAME] at path [PATH], outline a verdict workflow: what each reputation source can and cannot tell me, how to interpret detection-ratio (e.g. 3/70 vs 45/70), how to distinguish a packer/installer false positive from real malware, and the host-side artefacts to correlate. Do not assert the file is malicious or clean — give me the decision tree and tell me which step is authoritative. List ATT&CK techniques to consider if it executed.
```

### URL Deconstruction & Risk Read

*A suspicious URL appears in an email or proxy log and you need to read it safely.*

```text
You are a phishing-analysis specialist. Deconstruct this URL without advising me to visit it: [URL]. Break out scheme, host, path, query parameters, and any encoding. Identify redirect/obfuscation tricks (URL shorteners, @-tricks, punycode/homoglyphs, embedded second URLs, base64 params), what each parameter likely does, and the brand it may be impersonating. Output a table of components plus a risk read and the sandbox/detonation checks to run. Flag any decoded content that itself needs analysis.
```

Tip: Pair with the base64 decoder prompt if a query parameter contains encoded content. Decode it as a separate step.

### Raw Log Line Interpreter

*You're staring at an unfamiliar log line and need it explained field by field.*

```text
You are a log-analysis expert. Interpret this raw log line and tell me the source product/format if identifiable: [PASTE_LOG_LINE]. Return a field-by-field table (field name, value, meaning), a one-sentence plain-English summary of the event, which fields matter most for triage, and 3 follow-up queries to run. If a field is ambiguous or format-dependent, say so rather than guessing. Note any value that looks anomalous and why.
```

### Multi-Line Log Sequence Storyline

*You have a cluster of related log entries and need the narrative they tell.*

```text
You are an incident analyst. Below are related log lines in time order: [PASTE_LOG_LINES]. Reconstruct the storyline as a numbered timeline (timestamp, actor, action, target, outcome). Identify the likely root event, what happened next, and whether the sequence is consistent with normal activity or an attack chain. Map plausible steps to MITRE ATT&CK technique IDs. Separate what the logs prove from what you're inferring, and list the gaps where I need more data.
```

### Severity & Priority Scoring

*You must assign or sanity-check a severity rating before queue ordering.*

```text
You are a SOC triage lead. Score this alert for severity and priority. Inputs — alert: [ALERT_SUMMARY]; affected asset: [ASSET_ROLE_AND_CRITICALITY]; data sensitivity: [DATA]; exposure: [INTERNET_FACING_YES/NO]; exploitability/confidence: [NOTES]. Return: severity (1–5) and priority (P1–P4) with one-line justification each, the single biggest factor driving the score, what would raise or lower it by one level, and a recommended SLA. State assumptions and flag any input that materially changes the score if wrong.
```

Tip: Standardise the asset-criticality wording across the team so scores stay comparable.

### False-Positive Hypothesis Test

*An alert smells like noise but you need to justify closing it.*

```text
You are a detection-tuning analyst. Treat this alert as a possible false positive: [ALERT_DETAILS]. List the top benign root causes (admin tooling, scanners, backup jobs, software updates, legitimate automation), the specific evidence that would confirm each, and the evidence that would rule out benign and force escalation. Conclude with a defensible recommendation (close as FP / monitor / escalate) and the exact note I should leave. Be explicit about what you cannot confirm from the data given.
```

### EDR Process Alert Triage

*Your EDR flags a suspicious process and you need to judge the execution.*

```text
You are an EDR triage analyst. Triage this endpoint detection: process [PROCESS_NAME], command line [CMDLINE], parent [PARENT_PROCESS], user [USER], host [HOST], signer [SIGNED?]. Assess: is the parent-child relationship normal, is the command line suspicious and why, what ATT&CK techniques fit (give IDs), and what the process likely did. Return a verdict with confidence, the host artefacts to pull next (files, network, registry, child processes), and the containment options. If the command line is encoded or obfuscated, decode only what you can do deterministically and say so — never infer or invent the payload contents. Flag living-off-the-land patterns and anything needing human confirmation before isolation. End with the single piece of evidence that would most change this verdict.
```

Tip: If the command line is encoded, decode it with the encoded-PowerShell prompt before assessing.

### Decode Encoded PowerShell / Base64 Command

*A command line contains base64 or an encoded PowerShell payload.*

```text
You are a malware command-line analyst. Decode and explain this encoded command for defensive analysis only — do not improve, repair, or weaponise it. Input: [ENCODED_STRING] (context: [WHERE_SEEN]). Note that PowerShell `-EncodedCommand` is Base64 over **UTF-16LE**; state which encoding you applied. Decode iteratively through each layer. **If any layer cannot be deterministically decoded, stop and say so explicitly — do NOT infer, reconstruct, or guess the payload, and do not invent URLs, IPs, or filenames that are not literally present in the decoded bytes.** Then: show the decoded content, explain step by step what it does, identify download URLs, IPs, registry keys, scheduled tasks, or files it touches, and map behaviour to ATT&CK techniques (e.g. T1059.001, T1140). List every IOC to extract, **defanged** (`hxxp://`, `[.]`). Flag any destructive action and clearly mark what needs human verification before response.
```

Tip: Works for `-enc`/`-EncodedCommand`, certutil, and base64 in JScript/VBScript loaders too.

### Azure / Entra Sign-In Anomaly Triage

*An Azure AD / Entra ID risky sign-in or conditional-access alert fires.*

```text
You are an identity security analyst. Triage this Entra ID sign-in alert: user [UPN], result [SUCCESS/FAILURE], IP/location [VALUE], device [VALUE], app [VALUE], risk detections [VALUE], MFA result [VALUE]. Assess whether this fits the user's baseline, whether it indicates token theft, password spray, or legitimate travel/VPN, and the matching ATT&CK techniques (e.g. T1078, T1110). Give a verdict, the sign-in/audit logs to pull next, and the containment steps (revoke sessions, require re-MFA). Flag what to confirm with the user before disabling the account.
```

### Impossible-Travel Investigation

*An identity tool flags two logins too far apart to be physically possible.*

```text
You are an identity threat analyst. Investigate this impossible-travel alert: user [USER]; login A [TIME, IP, GEO]; login B [TIME, IP, GEO]; implied speed [VALUE]. Work through the benign explanations first (VPN/proxy exit, mobile carrier-grade NAT, cloud-hosted client, geo-IP error, roaming) and the evidence that confirms or rejects each. Then assess the compromise case and matching ATT&CK techniques. Give a verdict, the exact corroborating data to pull (device, MFA, user-agent, session tokens), and what to ask the user. Separate fact from inference.
```

Tip: Geo-IP error and VPN/proxy exits are common benign causes. Check both before raising an incident.

### Network IDS/IPS Alert Triage

*A Suricata/Snort/Zeek or NDR signature fires and you need to read it.*

```text
You are a network security analyst. Triage this network alert: signature/detection [NAME_AND_ID], src [IP:PORT], dst [IP:PORT], protocol [VALUE], direction [INBOUND/OUTBOUND], payload/flow notes [VALUE]. Explain what the signature detects, whether this flow genuinely matches the threat or is a known noisy trigger, the direction's significance (e.g. outbound = possible compromise), and matching ATT&CK techniques. Give a verdict, the PCAP/flow data to pull, and the asset context to gather. Note any signature known for false positives on benign traffic.
```

### C2 Beaconing Analysis

*A host shows repetitive outbound connections that may be command-and-control.*

```text
You are a C2-detection analyst. Analyse possible beaconing from host [HOST] to [DEST]. Data: connection timestamps/intervals [PASTE], bytes per connection [VALUE], destination [IP/DOMAIN], user-agent/JA3 if known [VALUE]. Assess regularity (interval, jitter), data-volume symmetry, and destination reputation to judge whether this is C2 (T1071) vs benign polling (telemetry, updates, monitoring, sync). Give a beaconing-likelihood verdict with reasoning, the destinations to enrich, and the host-side checks. List the benign apps that mimic this pattern, and flag what needs PCAP confirmation.
```

Tip: Low jitter plus a long-lived, low-reputation destination is the strongest single tell. But confirm against software-update traffic.

### ATT&CK Technique Mapping of an Alert

*You need to map an alert's observed behaviour to MITRE ATT&CK cleanly.*

```text
You are a threat-intel analyst fluent in MITRE ATT&CK. Map this alert's behaviour to ATT&CK: [ALERT_DETAILS]. Output a table: observed behaviour → tactic → technique/sub-technique ID and name → confidence (high/medium/low) → the specific evidence justifying it. Only map what the evidence supports; do not over-attribute. Note techniques that are plausible-but-unconfirmed separately. Finish with the likely position in the kill chain and the next techniques an attacker would attempt, so I know what to hunt for next.
```

Tip: Feed the "next techniques" list into a hunt query to get ahead of the actor.

### Escalation Decision Support

*You're unsure whether to escalate to tier-2/IR or close it yourself.*

```text
You are a SOC shift lead advising on escalation. Alert and findings so far: [SUMMARY_AND_EVIDENCE]. Decide: escalate now, gather more first, or close — with clear reasoning. List the specific facts that justify escalation, the facts that argue against, the single most important unknown, and what to gather to resolve it. If escalating, state target tier (T2/IR/threat-hunt) and urgency. Give the one-paragraph handoff summary. Be explicit about the risk of both over- and under-escalating this case.
```

### Business & Asset Context Questions

*An alert's severity depends on context only the business or asset owner has.*

```text
You are a SOC analyst gathering context to finalise triage. For this alert: [ALERT_SUMMARY] on asset [ASSET]/user [USER], generate the precise questions I should ask to resolve severity — covering asset criticality and data classification, whether the activity was authorised/expected, change-window or maintenance overlap, account ownership and role, and any known projects (pen-test, migration, new software) that could explain it. Group questions by who to ask (asset owner, IT, user, management). Flag which answers would most change the verdict.
```

Tip: A scheduled pen-test or migration explains a surprising share of "scary" alerts. Always ask.

### Ready-to-Paste Case Note

*You've finished triage and need a clean, defensible ticket note.*

```text
You are a SOC analyst documenting a case. From these findings: [PASTE_FINDINGS], write a structured case note with: Summary (2 sentences), Affected entities (host/user/IP), Timeline (UTC), Observations (bullet facts), Assessment (verdict + confidence + reasoning), MITRE ATT&CK techniques, Actions taken, Recommendation/Next steps. Use neutral, factual language suitable for audit and possible legal review. Clearly separate confirmed facts from analyst inference, and mark any item still pending verification. Keep it copy-paste ready for our ticketing system.
```

### End-of-Shift Triage Summary & Handover

*You're closing a shift and need to hand the queue over cleanly.*

```text
You are a SOC analyst writing a shift-handover. From my worked alerts and notes: [PASTE_ALERTS_AND_STATUSES], produce a handover with: items still open and their current state, what's been done on each, the next action and owner, anything time-sensitive or awaiting a response, escalations in flight, and a "watch list" of low-confidence items that may resurface. Keep it scannable with clear priority ordering. Flag any item where dropping the thread risks missing an active threat, and list the single most important thing for the next shift to pick up first.
```

Tip: Put the one must-do item at the very top. Handover notes get skimmed, not read.


## Detection Engineering

### Detect LSASS credential access (T1003.001)

*You want to detect credential dumping attempts against LSASS memory.*

```text
You are an EDR detection engineer. Write detection logic in [QUERY_LANGUAGE] for LSASS memory access (ATT&CK T1003.001). Base it on handle/access events to `lsass.exe` (e.g., Sysmon Event ID 10, or EDR equivalents) with suspicious access rights from any **non-allowlisted** process — do NOT scope to "non-SYSTEM" processes, since credential dumping is typically performed by a SYSTEM-integrity process after escalation. Use **bitmask** logic against the granted access rights, not equality matching on literal values, and include the fork-and-dump path (PROCESS_CREATE_PROCESS, 0x0080) alongside the common read/query combinations. Output: (1) the detection, (2) required fields (`SourceImage`, `GrantedAccess`, `TargetImage`, `CallTrace`), (3) the telemetry prerequisite — confirm Sysmon/EDR is configured to emit ProcessAccess events for lsass, or the rule silently returns nothing forever, (4) assumptions, (5) false positives (AV, EDR, legitimate security and backup tooling) and an allowlist strategy keyed on signer and path. Note known evasions (handle duplication, direct syscalls, fork-and-dump) and their detection limits, including where `CallTrace` is the only partial answer.
```

Tip: Ask it to include the common known-good `SourceImage` allowlist (AV/EDR agents) as a starter lookup.


## Phishing & Email Analysis

### Interpret SPF / DKIM / DMARC Results

*You need to translate `Authentication-Results` into a plain-English verdict.*

```text
You are an email-authentication specialist. From the `Authentication-Results` and related headers below, report the result (pass/fail/softfail/none) for SPF, DKIM, and DMARC separately. For each: explain what the result means, which domain was checked (e.g., RFC5321.MailFrom vs RFC5322.From alignment), and whether DMARC alignment was met. Where multiple DKIM signatures are present, evaluate each `d=` domain separately and state which, if any, aligns with the RFC5322.From. Report any ARC chain result and `cv=` status, noting ARC is only meaningful if the sealing intermediary is trusted. Interpret policy strength, not just the result (`~all` vs `-all`; `p=none` vs `p=quarantine` vs `p=reject`). Name which MTA added the `Authentication-Results` header and note that only your boundary MTA's header is trustworthy. Conclude whether the sender is plausibly authorised or likely spoofed, list caveats (e.g., forwarding can break SPF), and state explicitly that authentication passing does NOT mean the message is trustworthy. State what needs human verification. [PASTE_AUTH_RESULTS_AND_HEADERS]
```


## Threat Intelligence

### Map TTPs to MITRE ATT&CK

*You want a report's behaviours expressed as ATT&CK techniques for coverage and hunting.*

```text
You are an ATT&CK mapping specialist. Read the report and map each described adversary behaviour to MITRE ATT&CK (Enterprise). Output a table: **Tactic**, **Technique ID & name** (include sub-technique where stated), **Evidence** (quote/paraphrase from report), **Confidence** (HIGH if explicitly described, LOW if inferred). State which ATT&CK version you are mapping against and flag any ID affected by a recent merge or deprecation. Use a three-point confidence scale (HIGH / MEDIUM / LOW). Only assign IDs you can justify from the text; mark inferred mappings clearly and never guess a technique ID. If the text supports a parent technique but not a specific sub-technique, map to the parent and say so rather than over-specifying. Where two techniques compete, list both and state your preference with reasoning. List behaviours you could not confidently map separately, and add a short section naming tactics with no supported mapping. Every ID should be verified against the live matrix before operational use. Report: [PASTE_REPORT]
```

Tip: Request output as an ATT&CK Navigator JSON layer to visualise coverage instantly.

### CVE Triage for Your Environment

*A batch of new CVEs drops and you must rank them for your actual estate, not in the abstract.*

```text
You are a vulnerability-prioritisation analyst. Triage the CVEs below for my environment. For each: **CVE**, **CVSS base**, **EPSS** (if provided), **KEV listed? (Y/N)**, **Affected product vs my stack** ([YOUR_STACK]), **Exposure** (internet-facing/internal/[ASSET_CONTEXT]), **Affected version range** and **Version in range? (Y/N/UNKNOWN)**, **Compensating controls in place** [WAF/IPS/segmentation/MFA], **Asset criticality**, **Priority** (P1–P4 with one-line rationale and target remediation window). Weight known-exploited (KEV) and high-EPSS above raw CVSS, and let compensating controls and asset criticality modify the result. Mark any CVE affecting a product not in my declared stack as OUT OF SCOPE and query it rather than assuming. Flag where patch availability is unknown or no patch exists. Clearly separate confirmed data I provided from your assessment, and flag where you lack data to judge (mark UNKNOWN rather than guessing). CVEs: [PASTE_CVES]
```

Tip: Feed it your asset inventory or CMDB extract so "affected vs my stack" is grounded, not assumed.


## Incident Response

### Incident Timeline From Raw Events

*You have scattered logs, alerts, and chat messages and need a clean chronological timeline.*

```text
You are an incident analyst constructing a forensic timeline. From the raw events in [EVENT_DATA] (logs, alerts, Slack messages, ticket entries), build a chronological table with columns: **Timestamp (UTC)**, **Event**, **Source**, **Evidence reference** (alert ID, event record ID, raw log line or file hash so any row can be re-derived), **Reliability** (machine telemetry vs human recollection), **Actor (if known)**, **Significance**. Normalise all times to UTC, flag timezone ambiguity, and separately flag suspected clock skew — mark any corrected timestamp as an estimate. Mark three anchors explicitly: first observed malicious activity, detection, and containment (so dwell time is stated, not implied). End with a section naming gaps in available telemetry. Where ordering is uncertain, note "[sequence unverified]." Do not infer events not present in the data. End with a one-line summary of the attack progression as evidenced.
```

Tip: Feed it raw and messy. Normalising timestamps to UTC is exactly where it saves you most.
