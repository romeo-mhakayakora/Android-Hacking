# Android Reverse Engineering — Challenge Ladder

> [⬅ Domain](./README.md) | [🏠 Dashboard](../README.md)

**Status:** ⬜ Not Started

Use a **progressive challenge ladder** where each stage introduces one new skill. Do not jump between dozens of apps.

---

## 🟢 PHASE 1 — Learn to read APKs with JADX

**Goal:** Become comfortable opening an APK and understanding how the application works without tutorials.

| Order | Challenge | Main tool |
|---|---|---|
| 1 | **OWASP UnCrackable L1** | JADX |
| 2 | **BPVA Challenge 0** | JADX |
| 3 | **VulnDroid 1–3** | JADX + ADB |
| 4 | **Android CrackMe Challenge 5** | JADX |
| 5 | **OneList — beginner flags** | JADX |

**Do not use Frida yet.**

Learn to find:

- `MainActivity`
- interesting classes
- strings
- hardcoded secrets
- password checks
- flag validation
- `if` conditions
- cryptographic functions
- AndroidManifest
- resources
- SharedPreferences
- SQLite

Your basic workflow should become:

```text
APK
 ↓
JADX
 ↓
AndroidManifest
 ↓
MainActivity
 ↓
Follow method calls
 ↓
Find validation logic
 ↓
Understand condition
 ↓
Recover flag/secret
```

---

## 🟡 PHASE 2 — Android internals

Once you're comfortable with JADX:

### 6. Android CrackMe Challenges 1–4

Then:

### 7. DIVA

### 8. AndroGoat

### 9. InsecureBankv2

### 10. MASTG Hacking Playground

Now start learning:

```text
JADX
ADB
Logcat
AndroidManifest
Activities
Services
Broadcast Receivers
Content Providers
Intents
SharedPreferences
SQLite
External storage
```

The objective changes from:

> "Where is the password?"

to:

> **"How does this Android application actually work?"**

---

## 🟠 PHASE 3 — Dynamic analysis

Now introduce **Frida**.

### 11. OWASP UnCrackable L2

Don't immediately look at the solution.

Try:

```text
JADX
 ↓
understand Java/Kotlin
 ↓
identify native/JNI component
 ↓
ADB
 ↓
observe application
 ↓
Frida
 ↓
hook interesting function
 ↓
recover secret
```

Then:

### 12. OWASP UnCrackable L3

This is where you'll start encountering more serious anti-analysis.

Then:

### 13. BPVA advanced challenges

Now combine:

**JADX + Apktool + Frida + Burp**

---

## 🔴 PHASE 4 — Native Android reversing

Now you move beyond Java/Kotlin.

### 14. N4TIVE — Challenge 1

Learn:

- `.so` libraries
- JNI
- ELF
- ARM64
- strings
- XOR
- native functions

Then:

### 15. N4TIVE — Challenge 2

Then continue through:

### 16. N4TIVE 3–6

At this point your toolchain becomes:

```text
JADX
  ↓
APKTool
  ↓
Smali
  ↓
Ghidra
  ↓
ARM64
  ↓
Frida
```

---

## 🟣 PHASE 5 — Serious Android RE

Now attack:

### 17. CyberTruck Challenge 2019

Then:

### 18. HeroCTF — Freeda Native Hook

Then:

### 19. Google CTF Android

Then:

### 20. OneList — harder challenges

Then:

### 21. Securinets Friendly CTF 2026

**Do all 17 Mobile challenges.**

This should be one of your major milestones because it's a modern Android CTF rather than an old crackme.

---

## ⚫ PHASE 6 — Advanced protection

Finally:

### 22. OWASP UnCrackable L4

Study:

- obfuscation
- anti-debugging
- anti-tampering
- native code
- runtime protections
- cryptography
- Frida bypasses

At this point you're no longer simply learning "how to use JADX."

You're doing **actual Android reverse engineering**.

---

## Your complete sequence

```text
                 ANDROID RE
                     │
                     ▼
             ┌──────────────┐
             │  PHASE 1     │
             │     JADX      │
             └──────┬───────┘
                    │
      L1 → BPVA 0 → VulnDroid
                    │
                    ▼
             ┌──────────────┐
             │  PHASE 2     │
             │ Android RE    │
             └──────┬───────┘
                    │
       DIVA → AndroGoat → MASTG
                    │
                    ▼
             ┌──────────────┐
             │  PHASE 3     │
             │    Frida      │
             └──────┬───────┘
                    │
             L2 → L3 → BPVA
                    │
                    ▼
             ┌──────────────┐
             │  PHASE 4     │
             │ Native / ARM  │
             └──────┬───────┘
                    │
              N4TIVE 1 → 6
                    │
                    ▼
             ┌──────────────┐
             │  PHASE 5     │
             │ Advanced RE   │
             └──────┬───────┘
                    │
     CyberTruck → HeroCTF → Google CTF
                    │
                    ▼
             Securinets 2026
                    │
                    ▼
             ┌──────────────┐
             │  PHASE 6     │
             │ Hard Android  │
             └──────┬───────┘
                    │
             UnCrackable L4
```

## The most important rule

**Don't watch the solution first.**

For every challenge:

1. Download APK.
2. Open in JADX.
3. Spend **60–90 minutes** trying to understand it.
4. Write down your hypothesis.
5. Try to solve it.
6. If stuck, inspect the official writeup.
7. Reproduce the solution yourself.
8. Write your own notes.
9. Move on.

## Per-challenge notes layout (for later)

When you start solving, give each challenge its own folder:

```text
android-re/
│
├── 01-uncrackable-l1/
│   ├── notes.md
│   ├── screenshots/
│   └── solution.md
│
├── 02-bpva-0/
│   └── notes.md
│
├── 03-vulndroid/
│   ├── level-01/
│   ├── level-02/
│   └── level-03/
│
├── 04-diva/
│
├── 05-androgoat/
│
├── 06-uncrackable-l2/
│
├── 07-uncrackable-l3/
│
├── 08-n4tive/
│
└── 09-advanced/
```

**Your immediate starting point is just one thing: OWASP UnCrackable L1.** Don't install Frida, Ghidra, or 20 other tools yet. Learn to squeeze as much information as possible out of **JADX + the APK itself** first.

---

[⬅ Domain](./README.md) | [🏠 Dashboard](../README.md)