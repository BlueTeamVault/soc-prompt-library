# URL Deconstruction & Risk Read

**Use it when:** A suspicious URL appears in an email or proxy log and you need to read it safely.

## The prompt

```text
You are a phishing-analysis specialist. Deconstruct this URL without advising me to visit it: [URL]. Break out scheme, host, path, query parameters, and any encoding. Identify redirect/obfuscation tricks (URL shorteners, @-tricks, punycode/homoglyphs, embedded second URLs, base64 params), what each parameter likely does, and the brand it may be impersonating. Output a table of components plus a risk read and the sandbox/detonation checks to run. Flag any decoded content that itself needs analysis.
```

**Tip:** Pair with the base64 decoder prompt if a query parameter contains encoded content. Decode it as a separate step.

---

Before running this, paste the [version block](../00-START-HERE/version-block.md) once per session, 
and read [data handling](../00-START-HERE/data-handling.md) before pasting anything real.

Part of the free subset of [The Blue Team Prompt Vault](../README.md).