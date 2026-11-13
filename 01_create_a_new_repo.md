# How to Create a New Repo (Step by Step)

This guide is for teachers who are new to GitHub. It walks you through adding a new project or document collection to the Mustang Way Robots site. You only need a web browser. No software to install.

When you finish, your new repo will show up automatically on the main page at **https://mustangwayrobots.github.io/**.

---

## Before you start

* You need a GitHub account that is a member of the **mustangwayrobots** organization. Ask the club advisor to invite you if you aren't.
* Decide which **type** of repo you are making:

| Type | What it's for | Examples |
|---|---|---|
| **A. Document library** | A collection of guides, rules, forms, PDFs, Word or PowerPoint files. Visitors see one card per file and click to read it. | `Club-Info-and-Guides`, `Instructor_Guides` |
| **B. Firmware project** | Arduino code for a robot, plus a **⚡ Flash** web page so students can load the firmware from Chrome without installing Arduino. | `ESP_NOW_CAR`, `ESP_NOW_Controller` |

Steps 1–3 are the same for both types. Then follow **Part A** or **Part B**.

---

## Step 1. Create the repo

1. Go to **https://github.com/mustangwayrobots**.
2. Click the green **New** button (or **Repositories → New repository**).
3. Make sure **Owner** says **mustangwayrobots**, not your personal account.
4. **Repository name:** use letters, numbers, dashes `-` or underscores `_`. **No spaces.**
   * Good: `Line-Follower`, `Sumo_Bot`, `Teacher-Forms`
   * The name becomes part of the web address, and **capital letters matter**: `Sumo_Bot` and `sumo_bot` are different links. Pick a name and stick with it.
   * For a firmware project, write the name down exactly. You'll need it again in Part B.
5. **Description:** one short sentence. It appears on the project's card on the main page, so write it for students. Example: *"Two-wheel line-following robot with an IR sensor bar."*
6. Choose **Public**. GitHub Pages (the website part) is free only for public repos.
7. Tick **Add a README file**.
8. Click **Create repository**.

## Step 2. Add topics (tags)

Topics tell the main page how to show your repo.

1. On your repo's page, find **About** on the right side and click the ⚙️ gear next to it.
2. In **Topics**, type a topic and press Enter after each one:

| Topic | What it does on the main page |
|---|---|
| `firmware` | Card gets a **⚡ Flash firmware** button (Type B only) |
| `admin` | Card is moved to the collapsed **Instructor tools** section at the bottom, out of students' way |
| `hidden` | Repo is not shown at all (good while you're still building it) |
| anything else | e.g. `esp32`, `3d-printing`, `sensors`: shown as small tags and searchable |

3. Click **Save changes**.

> 💡 Tip: add `hidden` while you set things up, then remove it when the repo is ready for students.

## Step 3. Know how to upload files

You'll do this a lot, so here it is once:

1. On the repo page click **Add file → Upload files**.
2. Drag files or folders from your computer into the browser window.
3. Scroll down, type a short note in the box (e.g. *"Add battery policy"*), and click **Commit changes**.

To **replace** a file, upload a file with the exact same name. To **delete** one, open it, click the **⋯** menu (top right) and choose **Delete file**, then commit.

---

## Part A: Document library repo

### A1. Copy the library page

Every document repo uses the **same** `index.html`. It works out by itself which repo it's in.

1. Open **https://github.com/mustangwayrobots/Club-Info-and-Guides/blob/main/index.html**.
2. Click the **Download raw file** button (⬇ icon, top right of the file).
3. Upload that `index.html` to the top level of your new repo (Step 3).

**Optional: custom title.** Without any changes, the page title is made from the repo name (`Teacher-Forms` → "Teacher Forms"). To give it a better title, subtitle or a yellow notice box:

1. Open `index.html` in your repo and click the ✏️ pencil to edit.
2. Find the `const PAGE = {` block near the bottom.
3. Copy one of the existing entries and change it. The first line must be your repo name **in lower case**:
   ```
   'teacher-forms': {
     kicker: 'Instructors',
     title: 'Teacher Forms',
     subtitle: 'Permission slips, rosters and purchase forms.',
     notice: ''
   },
   ```
4. Click **Commit changes**.

### A2. Add your documents

Upload any of these and each one becomes a card:

| File type | What happens when someone clicks it |
|---|---|
| `.md` (Markdown) | Opens right on the page, nicely formatted, with a **🖨️ Print** button |
| `.pdf` | Opens in the browser's PDF viewer |
| `.docx` `.pptx` `.xlsx` (and old `.doc` `.ppt` `.xls`) | Opens in Microsoft's free online viewer, plus a **Download** button |
| `.txt` `.csv` `.png` `.jpg` `.mp4` | Opens in the browser |

**Organizing:**
* **Folders become sections** on the page. A folder named `Forms` gives a "Forms" heading.
* **Control the order** by starting names with a number: `01_Safety`, `02_Schedules`, `01_battery_policy.md`. The number is hidden on the page.
* File names become card titles: `field_trip-permission.pdf` → "Field Trip Permission". Use clear names.
* Pictures **used inside** a Markdown guide go in a folder called `images`. Files there don't get their own cards.
* `index.html`, `README.md` and `LICENSE` are never shown as cards.

**Card descriptions:** for `.md` files, the card shows the first normal paragraph of the document. Start each guide with a one- or two-sentence summary. Other file types just show their type.

### A3. Turn on the website

1. In your repo click **Settings** (top tab) → **Pages** (left menu).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Set **Branch** to **main** and the folder to **/ (root)**. Click **Save**.
4. Wait 1–2 minutes, then refresh. The page shows your site address, e.g. `https://mustangwayrobots.github.io/Teacher-Forms/`.

Done. The repo appears on the main page within about 15 minutes. The main page caches the list, so press **Ctrl+Shift+R** to refresh sooner.

---

## Part B: Firmware project repo

These repos build the firmware **automatically** on GitHub every time you upload new code, and publish a Flash page for students. Two files make that happen, and they are copied **unchanged** from an existing project.

### B1. Prepare the code on your computer (Arduino IDE)

The build is picky about names. Check these before uploading:

1. The **main sketch file** must have **exactly the same name as the repo**, including capital letters.
   Repo `Sumo_Bot` → main file `Sumo_Bot.ino`.
   (Arduino IDE already expects the sketch folder and main `.ino` to have the same name, so name the folder `Sumo_Bot` too.)
2. Make sure it compiles in Arduino IDE with board **MakerGO ESP32 C3 SuperMini** and the same ESP32 core version the club uses (see `CORE_VERSION` in `build.yml`, e.g. 3.3.12).
3. **Libraries:** the project must carry its own. Make a folder called `libraries` next to the `.ino` files and copy in each library folder the sketch uses (from `Documents/Arduino/libraries`). Nothing is downloaded from elsewhere.
4. **Multiple board versions (optional):** if the code supports more than one board, put the pin choices in `HardwareConfig.h` using `#if defined(HARDWARE_V2)` / `#elif defined(HARDWARE_V4)` and so on. The build finds every `HARDWARE_Vx` and makes one firmware for each, and students pick their version on the Flash page. With no `HardwareConfig.h`, you get one firmware.

### B2. Copy the two build files

From **https://github.com/mustangwayrobots/ESP_NOW_CAR** download (⬇ **Download raw file**):

* `flash/index.html`: the Flash page
* `.github/workflows/build.yml`: the automatic build

Put them in the same places in your project folder:

```
Sumo_Bot/
├── Sumo_Bot.ino          ← same name as the repo
├── (other .ino / .h files)
├── HardwareConfig.h      ← optional
├── libraries/            ← the libraries this project needs
├── flash/
│   └── index.html        ← copied unchanged
├── .github/
│   └── workflows/
│       └── build.yml     ← copied unchanged
├── docs/
│   └── images/           ← photos, schematic (optional)
└── README.md
```

> ⚠️ Folders starting with a dot (`.github`) are hidden on Mac and sometimes Windows.
> On Mac press **Cmd+Shift+.** in Finder to show them. On Windows tick **View → Hidden items** in File Explorer.

### B3. Upload everything

Upload the **contents** of the project folder (not the folder itself) to the repo (Step 3). Check on GitHub that `Sumo_Bot.ino` sits at the top level, next to `README.md`, and that `.github/workflows/build.yml` is there.

### B4. Watch the build

1. Click the **Actions** tab in your repo.
2. You'll see **Compile and Deploy Firmware** running (yellow dot). It takes a few minutes.
3. **Green ✓** = success. **Red ✗** = click it, open the failed step, and read the error. Most common causes:
   * *"no sketch found"*: the main `.ino` name doesn't match the repo name exactly.
   * *Missing library / "No such file"*: a library isn't in the `libraries` folder.
   * *Permission denied on deploy*: go to **Settings → Actions → General → Workflow permissions**, choose **Read and write permissions**, Save, then re-run from the Actions tab (**Run workflow**).

### B5. Turn on the website

A successful build creates a branch called **gh-pages** that holds the website.

1. **Settings → Pages**.
2. **Source:** **Deploy from a branch**. **Branch:** **gh-pages**, folder **/ (root)**. **Save**.
3. After 1–2 minutes the Flash page is live at `https://mustangwayrobots.github.io/Sumo_Bot/flash/`.

### B6. Finish up

* Add the topic `firmware` (Step 2) so the main page shows the **⚡ Flash firmware** button.
* Test it yourself: open the Flash page in **Chrome or Edge** on a laptop, plug in a board with a USB-C cable, and flash it.
* From now on, **every upload to the repo rebuilds the firmware automatically**. Test changes in Arduino IDE on your own PC first: students flash whatever is on GitHub.

---

## Quick checklist

**Every repo**
- [ ] Created under **mustangwayrobots**, Public, no spaces in the name
- [ ] Description written for students
- [ ] Topics added (`hidden` while building)
- [ ] Pages turned on
- [ ] Opened the site link and checked it works
- [ ] `hidden` topic removed when ready

**Document library (A)**
- [ ] `index.html` copied from Club-Info-and-Guides
- [ ] Documents uploaded, numbered for order if needed
- [ ] Pages source: **main / root**

**Firmware project (B)**
- [ ] Main `.ino` named exactly like the repo
- [ ] `libraries/` folder included
- [ ] `flash/index.html` and `.github/workflows/build.yml` copied unchanged
- [ ] Actions build is green
- [ ] Pages source: **gh-pages / root**
- [ ] `firmware` topic added
- [ ] Test flash done in Chrome or Edge
