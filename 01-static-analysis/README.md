# 01 — 🔍 Static Analysis

> Reading the app without running it: structure, manifest, decompiled code, secrets.
>
> [⬅ Back to Android Hacking Dashboard](../README.md)

## Modules

| Module | MASVS | Status | Notes |
|--------|:-----:|:------:|:-----:|
| [APK Structure & Manifest Analysis](./apk-structure-manifest.md) | MASVS-CODE | ⬜ | [📖](./apk-structure-manifest.md) |
| [Decompilation (jadx, apktool)](./decompilation.md) | Technique | ⬜ | [📖](./decompilation.md) |
| [Secrets & Code Review](./secrets-code-review.md) | MASVS-STORAGE | ⬜ | [📖](./secrets-code-review.md) |

## 🎯 Domain Goal

```text
APK File
      ↓
Manifest & Components
      ↓
Decompiled Code
      ↓
Secrets & Flaws
```

## Readiness Checklist

- [ ] Explain the underlying concepts
- [ ] Identify attack opportunities
- [ ] Execute the relevant techniques
- [ ] Troubleshoot when the obvious approach fails
- [ ] Document commands and evidence
- [ ] Apply the technique in an unfamiliar environment
- [ ] Combine it with other skills

---

[⬅ Back to Android Hacking Dashboard](../README.md)
