# Android Offensive Security & Reverse Engineering Roadmap

> [⬅ Domain](./README.md) | [🏠 Dashboard](../README.md)

**Status:** 🔄 In Progress

A staged path from your first APK to hard native and protected apps. Every link below appeared in my searches. For each challenge I give a Files link (the download or repo) when I found one, and otherwise the event or platform site; I have not downloaded every file, so check each APK link before planning around it. Anything I could not verify is marked as such.

---

## How to use this roadmap

- You already program, so skip language study. Your learning curve is Android concepts and tooling, not syntax.
- For every challenge: open it in JADX, spend 60 to 90 minutes alone, write down a hypothesis, try to solve it, and only then read a writeup. Re-solve it yourself and write 2 or 3 sentences on why the solution worked.
- Keep a GitHub repo with one folder per challenge: notes.md, screenshots, solution.md.
- Map each finding to an OWASP MASTG test case.
- Add Frida early as a small tool (hook one method, print arguments, change a return value). Add Ghidra and ARM64 only when you reach native code.
- Put Burp or mitmproxy in before Stage 3, because most real mobile pentesting is network and API testing.

---

## Stage 0: Tooling (1 to 2 days)

Set up a rooted emulator (Android Studio AVD) or a spare test phone, plus ADB, JADX, apktool, Burp Suite, and later Frida and Ghidra. No language study; just get the setup working.

---

## Stage 1: Reading APKs with JADX (week 1)

**Goal:** find entry points, hardcoded secrets, validation logic and weak crypto without running anything.

- **CTFlearn: Basic Android RE 1** (easy, 5,350 solves). Files: ctflearn.com/challenge/962. Writeup: RemusDBD (finds an MD5 check in JADX).
- **picoGym: droids0 and droids1.** Site: picoGym (search for droids0 and droids1; I did not get a direct URL). Guide with both solved: NUS Greyhats, Introduction to Android App Reversing.
- **DroidDump** (beginner: resources and static analysis). Site: Learn SecByte CTF, the platform behind this walkthrough.
- **Silent Data Exfiltration: WayneSecure, GothamConnect, SystemMonitor (2026).** Files: no direct link found. Writeup (names the three APKs): rehutalwar.com.
- **GDG CTF 2026: Food.** Files: no direct link found. Writeup: GDG CTF 2026 writeup.
- **OWASP UnCrackable L1.** Files: mas.owasp.org/crackmes/Android. Do it with JADX only first, then read these, which each use a different method:
  - tksec: JADX, smali patching and Frida
  - cygnus: smali patching and objection
  - pentest.co.uk: Frida root-detection bypass
  - HackerNoon walkthrough
- **Hacky Holidays CTF: Pizza Pazzi 1 to 4** (medium). Files: no direct link found; the challenge came from the Hacky Holidays CTF. Writeup: CTFtime writeup 34706 (apktool, grep, base64 hunting).

**Skills you should have by the end:** manifest reading, finding MainActivity, following method calls, spotting string and hash checks, using apktool and grep.

---

## Stage 2: App pentesting fundamentals (weeks 2 to 3)

**Goal:** move from "where is the password" to "how does this app actually work". Cover exported components, intents, insecure storage, WebViews, logcat leaks, and traffic interception with Burp. Do one apktool patch, rebuild, sign and install exercise, and write one short pentest report.

- **OneList** (10 flags, beginner to expert). Files: github.com/cywr/android-re-ctfs. The repo accepts community writeups, so check it for existing ones.
- **DIVA (Damn Insecure and Vulnerable App).** Files: payatu/diva-android (source; the README also points to a debug APK download). A prebuilt APK copy is at 0xArab/diva-apk-file.
- **MASTG Hacking Playground.** Files: OWASP/MASTG-Hacking-Playground (Java and Kotlin apps). Other MASTG reference apps are on the index page.
- **InsecureShop.** Files: hax0rgb/InsecureShop.
- **AndroGoat, InjuredAndroid, Damn Vulnerable Bank, OVAA, Vuldroid, InsecureBankv2.** I did not get direct download pages; find all of them in the awesome-vulnerable-apps list.
- **KGB Messenger** (Alerts, Login, Social Engineering; solve in order). Files: tlamb96/kgb_messenger. Its README links the APK download, a video lecture from George Mason University's MasonCC club and a video walkthrough with timestamps.
- **MobileReversing walkthrough repo** with a suggested order (RagingRock, DIVA, InjuredAndroid, InsecureShop, Frida Labs, hpAndro): sam-mg/MobileReversing.
- **Mobile Hacking Lab.** Site: Corellium training page for Mobile Hacking Lab (a free Android userland exploitation teaser lab; registration required). Writeups to check your work: mehmetfarisacar/Mobile-Hacking-Lab-Writeups.
- **8kSec free mobile labs** (2025, includes 10 Android challenges). Site: 8ksec.io/battle. I have not found writeups for them.
- **HacktivityCon CTF Mobile (MobileOne, Pinocchio).** Files: mobile_one.apk. Writeup: goggleheadedhacker.com. Pinocchio uses mitmproxy, so it doubles as a first traffic-interception exercise.
- **BdSecCTF 2025: Hacker App.** Files: no direct link found. Writeup: 0x0meowsec (custom encoding chain: XOR, TEA, byte table, Base64).
- **Securinets Friendly CTF 2025, mobile folder.** Files: securinets-insat/Friendly-CTF-2025. I found no mobile writeups yet. I could not verify a 2026 edition or a count of 17 mobile challenges.

---

## Stage 3: Frida, in small steps

**Goal:** hook methods, bypass root and Frida detection, dump keys at runtime, and call hidden methods.

- Redo **UnCrackable L1 with Frida** using the tksec and pentest.co.uk writeups from Stage 1.
- **UnCrackable L2** (Java plus a small native part). Files: mas.owasp.org/crackmes/Android.
- **PwnSec CTF 2025: CuteFrida, RudeFrida, FreakyFrida.** All three are designed for Frida; RudeFrida needs library reversing plus root and Frida detection bypass. Event site: pwnsec.ctf.ae and CTFtime event 2906. I found no direct file links, so check those two pages. Writeups:
  - bi0s: RudeFrida
  - Handoumeh: RudeFrida
  - zeroflag: RudeFrida
- **PwnSec CTF 2024 mobile: FireStorm and Snake** (hard). FireStorm needs Frida to force a hidden Password() method and then a Firebase login; Snake combines anti-root, anti-Frida and anti-ptrace checks with a SnakeYAML issue. Same event sites as above. Writeups: FireStorm, Snake (writeup 1) and Snake (writeup 2). These are written partly in French.
- **bi0s writeup index.** The same blog lists writeups for Squirrel CTF (DROID), Shakti CTF (nowyouseeme), ByuCTF (baby-android-2) and Cyberchaze CTF (Capture Me, Firmware). Start from the RudeFrida page and follow its sidebar.
- **Frida debugging case study** (recent): why a hook on the java.lang.String constructor installed but never fired. Article.
- **Frida techniques overview** (hooks, root and SSL pinning bypass, key dumping). Article.
- **Frida CodeShare scripts** to study and adapt: multiple bypass and fridantiroot. Read them before running them.

---

## Stage 4: Native reversing (ARM64, JNI, Ghidra)

Prepare first: learn JNI and ELF basics and practice Ghidra on small binaries. Learn ARM64 instructions as Ghidra shows them to you, starting with function calls, loops, and XOR.

- **MASTG chapter: Reverse Engineering and Tampering** (native libraries, JNIEnv, disassembly). Read it.
- **UMassCTF 2024: Free Delivery** (medium; malware obfuscation, static and dynamic analysis, native library). Event site: umasscybersec.org; I found no direct file link. Writeups: powalll on GitHub and a short solution on CTFtime (base64 plus XOR in Java, then a XOR-0x55 string in libfreedelivery.so).
- **IntechCTF Android category** (flag, JNI, OAT, reflection, sign). Files: the writeup credits aimardcr as problem setter and says the challenges are on a repository; I found only his profile, github.com/aimardcr, so look there. Writeups: Part 1 and Part 2: Game. Medium may paywall these.
- **UMass CTF 2026: Android ARM64** (medium-hard; stripped ARM64 library liblegocore.so, dynamic JNI registration, a custom VM, red herrings). Files: the pwn.college CTF archive for UMassCTF 2026 lists the challenge zips (for example lego-clicker.zip); I did not confirm which one is the Android challenge. Writeup: Wa3r on Medium.
- **Nullcon Goa 2023 workshop: ARM-ing for Android.** An intro to ARM assembly plus four Android apps. This is the workshop description, not a download: nullcon.net.
- **CTFlearn: Android, run!** (hard, 140 points). Files: challenge page. The APK is on a mega.nz link there that may have expired.

---

## Stage 5: Real CTF-level and modern targets

- **CyberTruck Challenge 2019** (NowSecure; keyless car app; Jadx, Frida, APKTool and Ghidra across Java and native layers). Files: nowsecure/cybertruckchallenge19. Background: NowSecure page. Writeup: user1342 on GitHub.
- **Google CTF 2020: Android.** Files: google/google-ctf, 2020 quals reversing-android. Writeup: luker983.
- **Google CTF 2017: Food** (native code in libcook.so; old and hard for its era). Files and writeup together: CTFtime writeup 6870 (its folder lists food.apk).
- **FamPay CTF 2026** (APK plus web target; native library, Firebase, cloud instance). Site: ctf.fampay.co, which may be offline. Writeup: bhatsupshubham on Medium. I found no standalone APK link.
- **SECCON 2015: Reverse-Engineering Android APK 2** (hard; includes a server-side SQL injection part, so it may not run today). Writeup: CTFtime writeup 3394. Optional.
- More classic challenge files, from the awesome-mobile-ctf lists: Trend Micro CTF 2020 Keybox.apk, DEF CON 2019 quals Matryoshka-style challenge, THC CTF 2018 Android serial and a collection of Android reversing challenges.

---

## Stage 6: Hard protections

- **OWASP UnCrackable L3** ("the crackme from hell"): MASTG page.
- **OWASP UnCrackable L4 (r2Pay).** Start with v0.9 (source available, softened); v1.0 is the R2con CTF 2020 version with no source and many extra protections. MASTG page.
- Study obfuscation, anti-debugging, anti-tampering, anti-Frida techniques and white-box cryptography here.

---

## Videos and courses

I could not get verified direct YouTube video URLs from my searches, because they returned only video titles. Rather than guess links that may be dead, here is what to search for, taken from the curated list Awesome-Android-Reverse-Engineering:

- Maddie Stone's Android Reverse Engineering training (marked a top pick on that list). Search her name plus the course title.
- Kristina Balaam: a video series on RE basics and Android malware.
- LaurieWired: a YouTube channel on Android reverse engineering.
- "Using Frida To Modify Android Games | Mobile Dynamic Instrumentation".
- Blue Fox: Arm Assembly Internals and Reverse Engineering: ARM foundations for Stage 4.

Search YouTube for: "OWASP UnCrackable Level 1 walkthrough", "OWASP UnCrackable Level 2 walkthrough", "Frida hooking Android basics".

One verified video route: the KGB Messenger repo links a video lecture from George Mason University's MasonCC club and a video walkthrough with spoiler-free timestamps. Open the README for the links.

Once you give me a stage, I can search for videos for that stage specifically.

---

## More lists to mine

- awesome-mobile-ctf: Google CTF 2020 and 2021, HacktivityCon, STACK the Flags 2020, BSidesSF 2018, SharifCTF and more.
- awesome-android-security: Hacker101 Android, Rednaga challenges and crackme collections.
- The Mobile CTF Lab: updated 2024 list of CTFs, writeups and vulnerable apps.
- pentest-bi0s/Mobile-CTFs on GitHub: described as Android and iOS mobile CTF challenges and writeups from 2025 onwards. I saw the repo name but not a direct URL, so search GitHub for it.

---

## Caveats

- Older writeups use older Frida and Android versions. Expect to adapt scripts (the RudeFrida author used Frida 16).
- Newer CTFs usually host files in the organizers' GitHub or on CTFtime, not in the writeup. If a download link is missing, search the CTF name there.
- Some beginner CTF items are solvable with strings and grep. Use them as warm-up, not as proof of skill.
- N4TIVE and a Securinets "2026, 17 challenges" item from the first draft of this roadmap did not show up in my searches, so I left them out.
- Medium pages sometimes hit a paywall; try a private window.

---

[⬅ Domain](./README.md) | [🏠 Dashboard](../README.md)