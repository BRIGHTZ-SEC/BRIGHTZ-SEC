<div align="center">

# Bima Ramadhan Kartika

**`BRIGHTZ-SEC`**

Software Engineering student focused on **malware analysis, reverse engineering, and applied security research**.

[![Website](https://img.shields.io/badge/Website-bimaramadhankartika.web.id-2563eb?style=flat-square&logo=googlechrome&logoColor=white)](https://bimaramadhankartika.web.id)
[![Location](https://img.shields.io/badge/Location-Surabaya%2C%20Indonesia-2563eb?style=flat-square&logo=googlemaps&logoColor=white)](https://www.google.com/maps/place/Surabaya)
[![Discord](https://img.shields.io/badge/Discord-brightz33-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.com/users/brightz33)

</div>

---

## About

I'm a vocational high school student at **SMKS KRIAN 1**, majoring in **Software Engineering (RPL)**.

My interest is in the gap between *how code looks* and *how it actually behaves*. I like taking things apart — decompiling an APK, tracing where a string came from, working out why an obfuscator did it that way, then automating the process so the next sample takes minutes instead of hours.

Most of my work is **defensive**: understanding malware well enough to write about it, document indicators, and explain mitigation steps to non-technical people.

---

## Featured Work

### Android Malware Analysis & Automated Deobfuscation

[![View Report](https://img.shields.io/badge/View%20Report-2563eb?style=flat-square)](https://github.com/BRIGHTZ-SEC/APK-MALWARE-ANALISIS)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)](https://nodejs.org)

Static analysis of a trojanized APK disguised as a wedding invitation, paired with a **Node.js deobfuscator** that resolves the sample automatically.

**What the malware does**
- Intercepts incoming SMS (including bank OTPs and 2FA codes) and exfiltrates them to an attacker-controlled Telegram bot
- Abuses `NotificationListenerService` to capture notifications from banking and messaging apps
- Sends SMS remotely on command, functioning as an SMS relay/spam node
- Harvests device fingerprint data (brand, manufacturer, model, SDK version)

**Obfuscation layers that were broken**

| Layer | Technique | How it was defeated |
|---|---|---|
| String encryption | XOR-encoded `short[]` arrays holding all sensitive strings | `& 0xFFFF` masking to correctly emulate Java's unsigned 16-bit `char` conversion, so negative `short` values decrypt without corruption |
| Control flow | Android API calls wrapped in renamed utility classes (`C0001`–`C0005`) with dead-branch opaque predicates | Recursive paren-matching parser that resolves each wrapper and annotates the call site with the real API (`/* -> Log.d(tag, msg) */`) |
| Runtime arithmetic | Offsets, lengths, and XOR keys computed at runtime instead of written as literals | Expression evaluator that parses and evaluates the runtime XOR arithmetic against the dynamic `Object[]` constant pool |

**Engineering details worth noting**
- **Collision-free constant resolution** — replacements sorted by length descending, so substituting `RESULT_ENABLE` doesn't corrupt `MainActivity.RESULT_ENABLE`
- Cross-file constant dependency resolution, so decrypting a folder correctly handles globals shared between classes
- Emits both a readable report and annotated `_deobfuscated.java` files

> Scope is limited to a single-file sample (one `MainActivity.java`). Handling multi-DEX archives and native `.so` payloads is the next step.

📄 [Full technical write-up & IoC list](https://github.com/BRIGHTZ-SEC/APK-MALWARE-ANALISIS)

---

### BeatQuiz — Single-File Web Game

[![Live Demo](https://img.shields.io/badge/Live%20Demo-2563eb?style=flat-square)](https://brightz-sec.github.io/BeatQuiz/BeatQuiz.html)
[![Source](https://img.shields.io/badge/Source-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/BRIGHTZ-SEC/BeatQuiz)

A music quiz game — guess the artist from the track title — built as a **single HTML file with zero dependencies**.

- Three difficulty modes (Normal / Rush / Chill) with distinct timers and life counts
- Streak multiplier scoring (×2 and ×3), per-question score breakdown, and letter grades
- 22 tracks across 8 artists, randomising 12 questions per session
- Persistent stats via `localStorage`, canvas particle background, confetti on streak
- No build step, no framework — download and play

Built as a practical exercise in state management, CSS responsive scaling with `clamp()`, and shipping a complete product without tooling overhead.

---

## Toolset

**Offensive / Analysis**

![Kali Linux](https://img.shields.io/badge/Kali%20Linux-367BF2?style=flat-square&logo=kalilinux&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp%20Suite-F26726?style=flat-square&logo=burpsuite&logoColor=white)
![JADX](https://img.shields.io/badge/JADX-3DDC84?style=flat-square)
![Ghidra](https://img.shields.io/badge/Ghidra-3F5F8A?style=flat-square)

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)

**Platform**

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-159957?style=flat-square&logo=githubpages&logoColor=white)

---

## GitHub Activity

<div align="center">

![Stats](https://github-readme-stats.vercel.app/api?username=BRIGHTZ-SEC&show_icons=true&theme=default&hide_border=true&include_all_commits=true)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs?username=BRIGHTZ-SEC&layout=compact&theme=default&hide_border=true)

</div>

<div align="center">

![Streak](https://streak-stats.demolab.com/?user=BRIGHTZ-SEC&hide_border=true&theme=default)

</div>

---

## Currently Learning

- Reverse engineering beyond the Java layer — native code, JNI, and multi-DEX handling
- Practical web application security and vulnerability assessment methodology
- Writing findings clearly enough that non-technical readers can act on them

---

## Contact

Open to collaborating on malware analysis, security research, or tooling projects.

[![Website](https://img.shields.io/badge/bimaramadhankartika.web.id-2563eb?style=for-the-badge&logo=googlechrome&logoColor=white)](https://bimaramadhankartika.web.id)
[![Discord](https://img.shields.io/badge/Discord-brightz33-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/brightz33)

---

## Contribution Graph

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/BRIGHTZ-SEC/BRIGHTZ-SEC/gh-pages/snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/BRIGHTZ-SEC/BRIGHTZ-SEC/gh-pages/snake.svg">
  <img src="https://raw.githubusercontent.com/BRIGHTZ-SEC/BRIGHTZ-SEC/gh-pages/snake.svg" alt="Contribution graph rendered as a snake animation">
</picture>

---

## Notes

All security research published here is for **educational purposes and defensive analysis only**. Any sample, indicator, or technique documented is presented to explain how attacks work and how to detect and mitigate them.

---

<div align="center">

[![Visitors](https://komarev.com/ghpvc/?username=BRIGHTZ-SEC&label=Profile%20Views&color=0e75b6&style=flat)](https://github.com/BRIGHTZ-SEC)

</div>