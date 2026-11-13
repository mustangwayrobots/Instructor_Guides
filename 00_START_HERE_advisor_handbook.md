# Advisor Handbook: Start Here

Everything a new club advisor needs to take over Mustang Way Robots: who owns what, what to do each month of the school year, how the safety program works, and how the website and firmware fit together. Read this first, then use the other Instructor Guides as you need them.

| Document info | |
|---|---|
| **Last updated** | _(date and name of whoever updated it)_ |
| **Written by** | _(founding advisor's name)_ |

---

## 1. The club in one page

* **What we do:** students design, build and program projects: custom PCBs (EasyEDA Pro), 3D-printed parts and ESP32-C3 firmware (Arduino IDE). Projects include an ESP-NOW RC car and controller, with a color sorter, robot arm and lightsaber planned.
* **Where everything lives:**

| What | Where |
|---|---|
| Club website (students start here) | https://mustangwayrobots.github.io/ |
| GitHub organization (all code and documents) | https://github.com/mustangwayrobots |
| Club rules, safety SOPs and the sign-off form | Club-Info-and-Guides repo (the yellow box on the main page) |
| Teacher guides (this document) | Instructor_Guides repo (Instructor tools, bottom of the main page) |
| Templates for new repos | Template_Document_Library, Template_ESP32_Firmware |
| **Signed forms, incident log, roster** | **Never on GitHub.** _(fill in: e.g. locked cabinet in room ___, school Google Drive folder ___)_ |
| Batteries, quarantine container, charging station | _(fill in: room and cabinet)_ |
| Tools, soldering stations, 3D printers | _(fill in)_ |
| Parts inventory and ordering | _(fill in: e.g. spreadsheet link, purchasing process, budget code)_ |

* **Key people:**

| Role | Name | Contact |
|---|---|---|
| Club advisor | _(fill in)_ | _(school email)_ |
| Backup / co-advisor | _(fill in)_ | |
| Department chair / administrator who approves SOPs | _(fill in)_ | |
| School nurse | _(fill in)_ | |
| Building safety contact | _(fill in)_ | |

---

## 2. Accounts and ownership (do this first)

The GitHub organization is the club's most important asset. **If nobody who is still at the school is an owner, the club can lose control of the website.**

### Rules

* The **mustangwayrobots** organization must always have **at least two owners who work at the school** (e.g. the advisor and a co-advisor or department chair).
* Use accounts tied to people, ideally signed up with a **school email**, not a shared password.
* Turn on **two-factor authentication** for every owner (GitHub: your picture → **Settings → Password and authentication**).
* Students don't need GitHub accounts to flash firmware. If students contribute code, give them **Member** access only, never Owner. Remove them when they graduate.

### Handing over to a new advisor

1. New advisor creates a GitHub account (school email recommended).
2. Current owner: **github.com/mustangwayrobots → People → Invite member**, enter the new account, set role **Owner**.
3. New advisor accepts the email invite.
4. New advisor checks they can open **Settings** on the organization page.
5. Only **after** that, remove the departing advisor (or downgrade them to Member if they'll keep helping).
6. Update the "Key people" table above and the advisor name in **01_code_of_conduct.md** in Club-Info-and-Guides.

> ⚠️ Never delete or transfer the organization itself, and never rename repos without checking: renaming changes the web addresses students use.

---

## 3. The school year, month by month

### August (before students arrive)
- [ ] Read every document in **Club-Info-and-Guides**. Update anything that has changed (room, schedule, equipment).
- [ ] In every safety SOP, update **Version**, **Effective date** and **Reviewed / approved by**, then get the approval signature from your administrator. Keep the signed copy with the club records.
- [ ] Fill in the meeting info in **01_code_of_conduct.md**.
- [ ] Check equipment against each SOP's **Advisor checklist** (battery quarantine can with sand, metal tongs, charging station, fume extractors, safety glasses, first-aid kit, sharps container).
- [ ] Inspect stored batteries. Swollen or damaged ones go to quarantine, then recycling.
- [ ] Start a new **incident log** and **training/sign-off record** for the year (Section 4). Keep last year's.
- [ ] Check the website works: open the main page, Club Info, and every Flash page.

### First meetings
- [ ] Safety briefing for all members: walk through the Code of Conduct and each SOP. Record attendance.
- [ ] Send home the **Safety Acknowledgment Form** (Club Info → print). Nothing with batteries, irons, printers or power tools until it comes back signed.
- [ ] Hands-on training for each piece of equipment before first use. Record who was trained on what.
- [ ] Show everyone where the fire extinguisher, alarm pull station, exits, eyewash and first-aid kit are.

### During the year
- [ ] Keep the incident log up to date. Report injuries, fires and damage to administration the same day, using the school's process.
- [ ] Spot-check batteries and charging habits.
- [ ] Before changing firmware students use, test it on your own board first (Section 6).
- [ ] New project? Follow **01_create_a_new_repo.md**.
- [ ] Late joiners get the same briefing and form before using equipment.

### End of year
- [ ] Collect club batteries and projects that aren't going home for the summer. Store batteries per the Battery Safety Policy.
- [ ] Take quarantined and dead batteries to recycling.
- [ ] Inventory tools and parts; list what to order.
- [ ] File the year's signed forms, training record and incident log as the district requires.
- [ ] Remove graduating students from the GitHub organization.
- [ ] Hide (topic `hidden`) or archive repos for projects that are finished or abandoned.
- [ ] **Update this handbook** with anything you learned, and set the "Last updated" line.

---

## 4. The safety program

The safety documents are written so that a reasonable person can see the club gave clear rules, trained students, collected sign-offs and responded to problems. They only protect you if they're **actually used**.

### What's in Club-Info-and-Guides

| File | What it is |
|---|---|
| 01_code_of_conduct.md | Behavior rules, meeting info, consequences |
| 02_battery_safety_policy.md | LiPo / Li-ion handling, charging, storage, emergencies, disposal |
| 03_soldering_safety.md | Irons, fumes, lead, burns |
| 04_3d_printer_rules.md | Printer safety, fair use, print approval |
| 05_tool_safety.md | Hand tools, power tools, hot glue |
| 10_safety_acknowledgment_form.md | One form covering all of the above, signed by student and parent |

### The four records to keep (NOT on GitHub)

The GitHub site is public. **Never upload signed forms, student names, the roster, the incident log or photos of students** (unless the district's media permission allows it).

| Record | What to write | Keep it |
|---|---|---|
| **Signed acknowledgment forms** | One per student per year | _(fill in where)_ |
| **Training record** | Date, student, what they were trained on (batteries, soldering, printer, power tools), trainer | _(fill in where)_ |
| **Incident log** | Date, time, student(s), project, what happened, injuries, what was done, who was told (nurse, admin, parents) | _(fill in where)_ |
| **SOP approvals** | Signed copy of each SOP version with the approval date | _(fill in where)_ |

### Changing a safety document

1. Edit the file in Club-Info-and-Guides (open it, click ✏️).
2. Raise the **Version** number and update the **Effective date**.
3. Get it re-approved.
4. If the change matters (a new rule, not a typo), tell students at the next meeting and note it in the training record.
5. If it affects what parents agreed to, consider a new signed form.

> Before relying on these documents, have your administrator or district review them. They were written by teachers, not lawyers.

---

## 5. How the website works

You don't need to know HTML to run the site. Here's what's going on.

* **GitHub Pages** turns repos into websites. The main page lives in the repo **mustangwayrobots.github.io**.
* **The main page builds itself.** Each time it loads, it asks GitHub for the list of club repos and makes a card for each one. It saves the list in the browser for **15 minutes**, so changes can take that long to show (Ctrl+Shift+R to refresh sooner).
* **You control the cards from GitHub, not by editing the page:**

| To do this | Do this on the repo (⚙️ gear next to About) |
|---|---|
| Change a card's text | Edit the **Description** |
| Add a ⚡ Flash button | Add topic `firmware` (repo needs a working `flash/` page) |
| Move a card to Instructor tools | Add topic `admin` |
| Hide a card | Add topic `hidden` |
| Add an **Open** button | Turn on GitHub Pages for that repo |

* **The Featured project** is the one place you edit the page itself: in `index.html` of the mustangwayrobots.github.io repo, find `const FEATURED = {` near the top of the script and change the title, description, picture and repo names. Commit.
* **Club-Info-and-Guides and Instructor_Guides** use the same document-library page (`index.html`). It shows a card for every document in the repo. To add a document, just upload it.
* **"GitHub is busy right now"** on the page means the school network used up GitHub's limit of about 60 list requests per hour. The page shows the last saved list; it fixes itself within the hour.

---

## 6. How firmware gets to students

```
Your PC (Arduino IDE) → test on a real board → upload to GitHub
   → GitHub Actions builds it automatically (Actions tab, ~3 min)
   → Flash page updates → students flash in Chrome/Edge
```

* **GitHub is "production".** As soon as you upload code, students flash it. **Always test on your own board in Arduino IDE first.**
* **Every project carries its own libraries** in its `libraries/` folder. The build uses only those, so a library update on someone's PC can't break the build.
* **Board versions:** projects with several PCB versions list them in `HardwareConfig.h` (`HARDWARE_V2`, `HARDWARE_V3`…). The build makes one firmware per version and students pick theirs.
* **"Erase device?"** on the Flash page: students should leave it **unchecked** so saved settings (like car/controller pairing) are kept. Check it only to fix a board that's acting strangely.
* **The Flash page and build file are shared.** `flash/index.html` and `.github/workflows/build.yml` are identical in every firmware repo. If you improve them, copy the new versions to **every** firmware repo **and** to Template_ESP32_Firmware.
* **Matching projects** (like the RC car and its controller) talk using a shared protocol. Update and flash both together.

### Students can't flash: quick fixes

| Symptom | Try |
|---|---|
| No port appears in the list | Different USB-C cable (many only charge). Different USB port. Chrome or Edge only (not Safari/Firefox). |
| Still nothing | Hold the board's **BOOT** button while plugging it in, then try again. |
| Flashes but doesn't work right | Wrong board version picked. Re-flash with the right one. |
| Car and controller won't talk | Flash both from the same day's firmware, then re-pair. |
| Weird behavior after many flashes | Re-flash with **Erase device?** checked (this clears saved pairing/settings). |
| Phone or tablet | Not supported. Use a laptop. |

---

## 7. Templates

New repos start from a template so nobody has to copy files by hand (see **01_create_a_new_repo.md**).

| Template | Makes |
|---|---|
| **Template_Document_Library** | A document repo with the card page, like Club Info |
| **Template_ESP32_Firmware** | An ESP32-C3 project with starter sketch, Flash page and automatic build |

Both have the `admin` topic so they show only under Instructor tools. A repo becomes a template under **Settings → General → Template repository** (tick the box). **Keep templates current**: when the shared Flash page, build file or document page improves, update the template too.

---

## 8. Getting help

* **Instructor Guides** (this repo) for step-by-step guides.
* **GitHub's help:** https://docs.github.com
* **AI assistants** (like Claude) are good at explaining GitHub errors and Arduino code. Paste the exact error message from the Actions log.
* _(fill in: colleagues, former advisor's contact, district tech support)_

---

## 9. Handover checklist (outgoing advisor)

- [ ] New advisor is an **Owner** of the GitHub organization and has confirmed access (Section 2).
- [ ] At least two school staff are owners. Two-factor authentication on for both.
- [ ] "Key people" and "Where everything lives" tables in this handbook are filled in and current.
- [ ] Advisor name updated in the Code of Conduct.
- [ ] New advisor knows where the signed forms, training record and incident log are, and has access.
- [ ] Walked the new advisor through the battery storage, quarantine container, charging station, tools and printers.
- [ ] Walked through flashing a board and making a small firmware change end to end.
- [ ] Open problems and planned projects listed below.

### Open problems and plans

_(Outgoing advisor: list unfinished projects, known bugs, parts on order, ideas for next year.)_
