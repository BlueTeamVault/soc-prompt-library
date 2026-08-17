# Decode Encoded PowerShell / Base64 Command

**Use it when:** A command line contains base64 or an encoded PowerShell payload.

## The prompt

```text
You are a malware command-line analyst. Decode and explain this encoded command for defensive analysis only — do not improve, repair, or weaponise it. Input: [ENCODED_STRING] (context: [WHERE_SEEN]). Note that PowerShell `-EncodedCommand` is Base64 over **UTF-16LE**; state which encoding you applied. Decode iteratively through each layer. **If any layer cannot be deterministically decoded, stop and say so explicitly — do NOT infer, reconstruct, or guess the payload, and do not invent URLs, IPs, or filenames that are not literally present in the decoded bytes.** Then: show the decoded content, explain step by step what it does, identify download URLs, IPs, registry keys, scheduled tasks, or files it touches, and map behaviour to ATT&CK techniques (e.g. T1059.001, T1140). List every IOC to extract, **defanged** (`hxxp://`, `[.]`). Flag any destructive action and clearly mark what needs human verification before response.
```

**Tip:** Works for `-enc`/`-EncodedCommand`, certutil, and base64 in JScript/VBScript loaders too.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).