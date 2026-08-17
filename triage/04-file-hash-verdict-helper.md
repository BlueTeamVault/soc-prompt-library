# File Hash Verdict Helper

**Use it when:** You have a hash from an EDR detection and want a structured reputation workflow.

## The prompt

```text
You are a malware triage analyst. For file hash [HASH] (type: [MD5/SHA1/SHA256]) seen as [FILENAME] at path [PATH], outline a verdict workflow: what each reputation source can and cannot tell me, how to interpret detection-ratio (e.g. 3/70 vs 45/70), how to distinguish a packer/installer false positive from real malware, and the host-side artefacts to correlate. Do not assert the file is malicious or clean — give me the decision tree and tell me which step is authoritative. List ATT&CK techniques to consider if it executed.
```

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).