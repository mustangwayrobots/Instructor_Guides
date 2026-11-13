# How to Create a New Repo (Step by Step)

This guide is for teachers who are new to GitHub. It shows how to add a new project or document collection to the Mustang Way Robots site using the club's **template repos**, so you don't have to copy files by hand. You only need a web browser.

When you finish, your new repo shows up automatically on the main page at **https://mustangwayrobots.github.io/**.

---

## Before you start

* You need a GitHub account that is a member of the **mustangwayrobots** organization, with permission to create repos. Ask the club advisor or another org owner to invite you (see the Advisor Handbook, "Accounts and ownership").
* Decide which **type** of repo you are making:

| Type | What it's for | Start from this template | Examples |
|---|---|---|---|
| **A. Document library** | Guides, rules, forms, PDFs, Word or PowerPoint files. Visitors see one card per file and click to read it. | `Template_Document_Library` | `Club-Info-and-Guides`, `Instructor_Guides` |
| **B. Firmware project** | Arduino code for an ESP32-C3 project, plus a **⚡ Flash** web page so students can load the firmware from Chrome without installing Arduino. | `Template_ESP32_Firmware` | `ESP_NOW_CAR`, `ESP_NOW_Controller` |

Not sure? If students will **flash** it, it's type B. If students will **read** it, it's type A.

---

## Step 1. Make the repo from a template

1. Go to **https://github.com/mustangwayrobots** and open the template repo for your type (`Template_Document_Library` or `Template_ESP32_Firmware`).
2. Click the green **Use this template** button → **Create a new repository**.
3. **Owner:** make sure it says **mustangwayrobots**, not your personal account.
4. **Repository name:** letters, numbers, dashes `-` or underscores `_`. **No spaces.**
   * Good: `Line-Follower`, `Sumo_Bot`, `Skittles_Sorter`, `Teacher-Forms`
   * The name becomes part of the web address, and **capital letters matter**: `Sumo_Bot` and `sumo_bot` are different links. Pick a name and stick with it.
   * For a firmware project, write the name down exactly. You need it in Part B.
5. **Description:** one short sentence for students. It shows on the project's card on the main page. Example: *"Sorts Skittles by color using a color sensor and a servo."*
6. Choose **Public**. The website part (GitHub Pages) is free only for public repos.
7. Click **Create repository**.

## Step 2. Add topics (tags)

Topics tell the main page how to show your repo. They are **not** copied from the template, so add them now.

1. On your new repo's page, find **About** on the right and click the ⚙️ gear next to it.
2. In **Topics**, type a topic and press Enter after each one:

| Topic | What it does on the main page |
|---|---|
| `firmware` | Card gets a **⚡ Flash firmware** button (type B only) |
| `admin` | Card goes in the collapsed **Instructor tools** section at the bottom, out of students' way |
| `hidden` | Repo is not shown at all. Use it while you're still building |
| anything else | e.g. `esp32`, `3d-printing`, `sensors`: shown as small tags and searchable |

3. Click **Save changes**.

> 💡 Add `hidden` now. Remove it at the end, when the repo is ready for students.

## Step 3. Know how to upload and edit files

You'll do this a lot, so here it is once:

* **Upload:** on the repo page click **Add file → Upload files**, drag files or folders in, type a short note (e.g. *"Add wiring diagram"*) and click **Commit changes**.
* **Replace:** upload a file with the exact same name.
* **Edit a text file** (`.md`, `.ino`, `.h`): open it and click the ✏️ pencil. Commit when done.
* **Rename:** open the file, click ✏️, and change the name in the box at the top. Commit.
* **Delete:** open the file, click **⋯** (top right) → **Delete file**, then commit.

---

## Part A: Document library

### A1. Turn on the website

1. In your repo click **Settings** (top tab) → **Pages** (left menu).
2. **Source:** **Deploy from a branch**. **Branch:** **main**, folder **/ (root)**. Click **Save**.
3. Wait 1–2 minutes and refresh. The page shows your site address, e.g. `https://mustangwayrobots.github.io/Teacher-Forms/`.

### A2. Add your documents

1. Delete the example file `01_example_guide.md`.
2. Upload your documents. Each of these becomes a card:

| File type | What happens when someone clicks it |
|---|---|
| `.md` (Markdown) | Opens right on the page, nicely formatted, with a **🖨️ Print** button |
| `.pdf` | Opens in the browser's PDF viewer |
| `.docx` `.pptx` `.xlsx` (and old `.doc` `.ppt` `.xls`) | Opens in Microsoft's free online viewer, plus a **Download** button |
| `.txt` `.csv` `.png` `.jpg` `.mp4` | Opens in the browser |

**Organizing:**
* **Folders become sections** on the page. A folder named `Forms` gives a "Forms" heading.
* **Set the order** by starting names with a number: `01_Safety`, `02_Schedules`, `01_battery_policy.md`. The number is hidden on the page.
* File names become card titles: `field_trip-permission.pdf` → "Field Trip Permission". Use clear names.
* Pictures **used inside** a Markdown guide go in a folder called `images`. Files there don't get their own cards.
* For `.md` files, the card shows the **first normal paragraph**, so start each guide with a one- or two-sentence summary.

### A3. Optional: custom title and notice

Without changes, the page title comes from the repo name (`Teacher-Forms` → "Teacher Forms"). To change the title or subtitle, or add a yellow notice box:

1. Open `index.html` and click the ✏️ pencil.
2. Find `const PAGE = {` near the bottom. Copy one entry and change it. The first line must be your repo name **in lower case**:
   ```
   'teacher-forms': {
     kicker: 'Instructors',
     title: 'Teacher Forms',
     subtitle: 'Permission slips, rosters and purchase forms.',
     notice: ''
   },
   ```
3. Commit. Don't change anything else in `index.html`.

### A4. Finish

Open your site link and check every card opens. Then remove the `hidden` topic. Go to **Finish (both types)**.

---

## Part B: Firmware project

The template already contains the starter sketch, the **Flash page** (`flash/index.html`) and the **automatic build** (`.github/workflows/build.yml`). Every time you change the code on GitHub, it builds the firmware and updates the Flash page by itself.

### B1. Rename the sketch (most important step)

The build only works if the main sketch file has **exactly the same name as the repo**, capital letters included.

1. Open `Template_ESP32_Firmware.ino` and click the ✏️ pencil.
2. In the file-name box at the top, change it to your repo name: repo `Sumo_Bot` → `Sumo_Bot.ino`.
3. Commit.

> A red ✗ build from before you renamed it is normal. Only the build after the rename matters.

### B2. Watch the build

1. Click the **Actions** tab.
2. **Compile and Deploy Firmware** runs (yellow dot) for a few minutes.
3. **Green ✓** = success. **Red ✗** = click it, open the failed step and read the error. See **Troubleshooting** below.

### B3. Turn on the website

A successful build creates a branch called **gh-pages** that holds the website.

1. **Settings → Pages**.
2. **Source:** **Deploy from a branch**. **Branch:** **gh-pages**, folder **/ (root)**. **Save**.
3. After 1–2 minutes the Flash page is live at `https://mustangwayrobots.github.io/Sumo_Bot/flash/`.

### B4. Test the Flash page

1. Open the Flash page in **Chrome or Edge** on a laptop.
2. Plug in an ESP32-C3 board with a USB-C cable that carries data.
3. Flash it. The starter sketch blinks the board's LED and prints to the Serial Monitor. If that works, the whole system works.

### B5. Put your project code in

Work in **Arduino IDE on your own computer** first, then upload to GitHub. **Whatever is on GitHub is what students flash**, so only upload code you've tested.

1. On the repo page click **Code → Download ZIP** and unzip it into your Arduino sketch folder. Rename the folder to match the `.ino` name (e.g. `Sumo_Bot`).
   *(Or use GitHub Desktop: **Code → Open with GitHub Desktop**.)*
2. In Arduino IDE choose board **MakerGO ESP32 C3 SuperMini**, using the same ESP32 core version as `CORE_VERSION` in `build.yml`.
3. Write your code. Put pins in `HardwareConfig.h`.
4. **Libraries:** make a `libraries` folder next to the `.ino` and copy in every library folder the sketch uses (from `Documents/Arduino/libraries`). The GitHub build uses only these.
5. **More than one board version?** Add a `HARDWARE_V2`, `HARDWARE_V3`… block in `HardwareConfig.h` (the file explains how). The build makes one firmware per version, and students pick theirs on the Flash page.
6. Upload your changed files to GitHub (Step 3), or **Commit** and **Push** in GitHub Desktop.
7. Check the Actions build goes green, then re-test the Flash page.
8. Write a line in `CHANGELOG.md` every time you change what students flash.

### B6. Finish

Edit the `README.md`: replace the setup checklist with a description, parts list and photos (`docs/images`). Make sure the `firmware` topic is set, then remove `hidden`.

---

## Finish (both types)

* Open **https://mustangwayrobots.github.io/** and press **Ctrl+Shift+R**. The main page saves its project list for 15 minutes, so a new repo can take up to 15 minutes to appear.
* Check the card shows your description and the right buttons.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Build error **"no sketch found"** | The `.ino` name doesn't match the repo name exactly. Check capitals and dashes vs underscores. |
| Build error about a **missing library** or "No such file" | Copy that library's folder into the repo's `libraries` folder. |
| Build fails at **Deploy** with "permission denied" or 403 | **Settings → Actions → General → Workflow permissions →** Read and write permissions → Save. Then **Actions → Compile and Deploy Firmware → Run workflow**. |
| Site shows **404** | Pages isn't on yet, it's set to the wrong branch, or the link has the wrong capital letters. Firmware = **gh-pages**, documents = **main**. |
| Repo **not on the main page** | Wait 15 minutes and press Ctrl+Shift+R. Check it's Public, not archived, and doesn't have the `hidden` topic. |
| No **⚡ Flash** button on the card | Add the `firmware` topic. |
| Card shows in the wrong section | `admin` topic = Instructor tools; no `admin` = student projects. |
| Main page says **"GitHub is busy"** | GitHub allows about 60 list requests per hour per network. The school shares one, so it can run out. Wait and refresh. |

---

## Quick checklist

**Every repo**
- [ ] Made with **Use this template**, owner **mustangwayrobots**, Public, no spaces in the name
- [ ] Description written for students
- [ ] Topics added (`hidden` while building)
- [ ] Pages turned on and site link checked
- [ ] `hidden` removed when ready

**Document library (A)**
- [ ] Pages source: **main / root**
- [ ] Example guide deleted, documents uploaded and numbered for order

**Firmware project (B)**
- [ ] `.ino` renamed to match the repo exactly
- [ ] Actions build is green
- [ ] Pages source: **gh-pages / root**
- [ ] `firmware` topic added
- [ ] Test flash done in Chrome or Edge
- [ ] `libraries/` folder holds every library used
- [ ] README and CHANGELOG updated
