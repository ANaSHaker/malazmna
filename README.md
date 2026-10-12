<p align="center"><img src="assets/banner.png" alt="Malazmna" width="100%"></p>
<h1 align="center">Malazmna</h1>
<p align="center"><b>Every book, study booklet and ministerial exam an Iraqi student needs, in one Arabic app.</b></p>
<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Android">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white" alt="Flutter">
  <img src="https://img.shields.io/badge/UI-Arabic%20RTL-6C6CF5?style=flat-square" alt="Arabic RTL">
  <img src="https://img.shields.io/badge/Theme-Light%20%2B%20Dark-111827?style=flat-square" alt="Light and dark">
  <a href="https://youtu.be/QEL1GZai3H8"><img src="https://img.shields.io/badge/Demo-YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white" alt="YouTube demo"></a>
  <img src="https://img.shields.io/badge/Case%20Study-2022-6C6CF5?style=flat-square" alt="Case Study">
</p>

> ℹ️ Case study. The source code of this freelance project is not included (it is not in the author's archive), so this page documents only what the released app shows.

## Overview

**Malazmna** (ملازمنا, "our study booklets") is an Arabic education app for school students in **Iraq**.
It collects the material students look for during the school year in one place: official textbooks,
*malazem* (teacher-written study booklets), ministerial past papers, schedules, holiday dates and exam results.

| | |
|---|---|
| **Audience** | Iraqi intermediate (متوسط) and preparatory (اعدادي) students |
| **My role** | Freelance Flutter developer: built the Android app end to end |
| **Timeline** | Released in 2022 (demo shared in March 2022) |
| **Language** | Arabic, right to left, with light and dark themes |

## The challenge

- Study material was **spread across Telegram channels and websites**, so finding the right file for a specific grade and subject took time.
- A single download link is not always reachable, so students needed **more than one way to get each file**.
- During exam season students check the same things every day: **how many days are left until a holiday, and whether results are out**.

## Highlights

**📚 Study materials**
- Six sections on the home screen: books (الكتب), booklets (الملازم), schedules (الجداول), ministerial exams (الوزاريات), timings (التوقيتات) and holidays (العطل)
- Content is organised by grade, then by subject (for example *First Intermediate → Arabic textbook*)
- Every file offers **two download sources**: a direct link (مباشر) or a Telegram mirror (تليجرام)
- Ministerial past papers are grouped per subject, for example Arabic papers from 2011 to 2021

**⏳ Exam season tools**
- Holidays screen with a live countdown (days, hours, minutes, seconds) to each upcoming holiday
- Results centre (مركز النتائج) with a link for each exam round, for example Third Intermediate and Sixth Primary 2022

**🎨 Experience**
- Fully Arabic RTL interface with a bottom navigation bar and a side menu
- Light and dark themes that you can switch from Settings
- Settings: dark mode, our website, contact us, about the app, rate the app, share the app

## Screens

<p align="center"><img src="assets/screens-study.png" alt="Study materials screens" width="100%"></p>
<p align="center"><sub>Home, categories, a grade's books, a book with direct and Telegram download, ministerial exams.</sub></p>

<p align="center"><img src="assets/screens-dark.png" alt="Dark mode screens" width="100%"></p>
<p align="center"><sub>The same flows in dark mode, plus the side menu and settings.</sub></p>

## Signature feature

<p align="center"><img src="assets/feature-downloads.png" alt="From category to PDF in two taps" width="100%"></p>

The main job of the app is to get the student to the right PDF fast. From the home grid the student picks a section
(books, booklets, ministerial exams), then a grade, then the file. Each file card has two buttons:

1. **مباشر (Direct)**: opens the file straight from its host.
2. **تليجرام (Telegram)**: opens the same file in the Telegram channel where it is mirrored. This helps when the direct host is slow or blocked.

<p align="center"><img src="assets/feature-calendar.png" alt="Holidays countdown and results centre" width="100%"></p>

## Demo video

<p align="center"><a href="https://youtu.be/QEL1GZai3H8"><img src="assets/demo-video.png" alt="Watch the demo on YouTube" width="100%"></a></p>

## Product architecture

The source code is not available, so this diagram shows the **navigation and feature structure** you can see in the
released app, not the internal code layers.

```mermaid
flowchart LR
  Splash([Launch]) --> Home[Home<br/>banner + section grid]
  Home --> Books[Books<br/>الكتب]
  Home --> Booklets[Booklets<br/>الملازم]
  Home --> Exams[Ministerial exams<br/>الوزاريات]
  Home --> Tables[Schedules<br/>الجداول]
  Home --> Timings[Timings<br/>التوقيتات]
  Drawer[Side menu] --> Holidays[Holidays countdown<br/>العطل]
  Drawer --> Results[Results centre<br/>مركز النتائج]
  Drawer --> Site[Malazmna website]
  Books & Booklets & Exams --> Grade[Grade / subject list]
  Grade --> File{File card}
  File -->|Direct| Host[(File host)]
  File -->|Telegram| TG[(Telegram mirror)]
  Settings[Settings] --> Theme[Light / dark theme]
  Settings --> Share[Rate · Share · Contact]
```

| Layer | What the released app shows |
|---|---|
| Client | Flutter app for Android, Material components |
| Navigation | Bottom navigation bar (5 tabs) and a side drawer |
| Theming | Light and dark themes, switched at runtime from Settings |
| Localisation | Arabic RTL layout |
| Content delivery | External links to PDF files, with a direct host and a Telegram mirror |
| Time-based UI | Countdown timers (days, hours, minutes, seconds) for holiday dates |

## Engineering notes

- **Two download sources per file.** Each file card has a direct link and a Telegram mirror, so students can use whichever source works on their network.
- **RTL first.** All screens, cards and the drawer are built for Arabic right-to-left reading. Two-button rows, back arrows and icons follow the RTL direction.
- **Theme parity.** The study flow, the side menu and settings all have matching light and dark versions (see the screenshots above).
- **Live countdown.** Each holiday card counts down to a fixed date, down to the second.

## Results

- Shipped as an Android app for Iraqi students in 2022, with a public demo video ([YouTube](https://youtu.be/QEL1GZai3H8)).
- No public store statistics are available for this project, so none are claimed here.

## بالعربي

**ملازمنا** تطبيق تعليمي عربي لطلاب المدارس في العراق. يجمع الكتب المنهجية والملازم والأسئلة الوزارية والجداول في مكان واحد.
كل ملف متاح بطريقتين: تحميل مباشر أو من قناة تليجرام، حتى يختار الطالب الأسرع على شبكته.
فيه كمان عدّاد تنازلي للعطل ومركز للنتائج، وواجهة عربية كاملة بوضع فاتح وداكن.
اشتغلت على المشروع كمطوّر Flutter مستقل، وبنيت تطبيق أندرويد من أوله لآخره سنة 2022.

## Links

- 🎬 Demo video: <https://youtu.be/QEL1GZai3H8>

---
<h3 align="center">Built by Mahmoud Shaker — Senior Flutter Engineer</h3>
<p align="center">
  <a href="https://wa.me/201140279111"><img src="https://img.shields.io/badge/WhatsApp-Chat-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp"></a>
  <a href="https://www.linkedin.com/in/anashaker/"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://anashaker.github.io/shaker_portfolio/"><img src="https://img.shields.io/badge/Portfolio-Visit-111827?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Portfolio"></a>
  <a href="mailto:mahmoudshaker382001@gmail.com"><img src="https://img.shields.io/badge/Email-Hire%20me-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://khamsat.com/user/sheko201566"><img src="https://img.shields.io/badge/Khamsat-Services-F39C12?style=for-the-badge" alt="Khamsat"></a>
  <a href="https://mostaql.com/u/ShekoShaker"><img src="https://img.shields.io/badge/Mostaql-Freelance-2386C8?style=for-the-badge" alt="Mostaql"></a>
  <a href="https://github.com/ANaSHaker"><img src="https://img.shields.io/badge/GitHub-More%20work-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
</p>
