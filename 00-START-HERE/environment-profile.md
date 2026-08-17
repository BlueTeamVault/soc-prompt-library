## Prompt #0 — your environment profile (build this once)

Every prompt here gets sharper when the model knows your environment. Fill this in once on a quiet shift, save it somewhere you can paste from, and put it at the top of any session.

```
ENVIRONMENT PROFILE

Sector / region: [VALUE]
SIEM / query surface: [e.g. Sentinel + Defender XDR advanced hunting / Splunk ES]
EDR: [VALUE]          Identity: [e.g. Entra ID, on-prem AD, Okta]
Email security: [VALUE]   Network/NDR: [VALUE]   Cloud: [AWS / Azure / GCP / none]

Asset tiers that matter: [Tier-0 systems, crown-jewel data stores, regulated systems]
Business-critical hours / change windows: [VALUE]
Known-noisy legitimate tooling: [backup jobs, vuln scanners, RMM, CI/CD, admin scripts]
Service accounts with unusual-looking-but-normal behaviour: [VALUE]
Current projects that generate odd telemetry: [migrations, pen-tests, rollouts]

Escalation model: [tiers, who decides, out-of-hours]
Our AI-use policy in one line: [what I may and may not paste]
```

Twenty minutes to build. It turns generic output into output that knows your jump box does that every Tuesday. Update it quarterly, or whenever your stack changes.
