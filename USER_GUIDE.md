# Office Time Logger — User Guide

## What is this app?

Office Time Logger is a **browser-based time tracking app** that runs entirely on your device — no account, no server, no internet required after the first load. It records when you clock in and out each day, tracks your 6.5-hour daily goal, and lets you export your attendance as an Excel file.

---

## How to Open / Install

### Option A — Open as a web page (simplest)

1. Double-click `index.html` to open it in your browser.
2. The app works immediately. All data is saved in the browser's local storage on that device.

> **Note:** Always open the same browser on the same device. Local storage is browser- and device-specific — switching browsers or devices gives you a fresh, empty app.

### Option B — Install as a desktop/mobile app (recommended)

The app is a **Progressive Web App (PWA)**, meaning you can install it like a native app so it opens from your taskbar, Start menu, or home screen.

**On Chrome / Edge (Windows/Android):**

1. Open `index.html` in the browser.
2. Look for the **Install** icon (⊕ or screen icon) in the address bar, or open the browser menu (⋮) and choose **Install app** / **Add to Home screen**.
3. Click **Install**. The app will appear in your Start menu or as a desktop shortcut.

**On iPhone / iPad (Safari):**

1. Open `index.html` in Safari.
2. The app shows a blue banner at the top: *"Install: tap Share → Add to Home Screen"*.
3. Tap the **Share** button (box with arrow pointing up), then **Add to Home Screen**, then **Add**.
4. The app icon appears on your home screen and opens full-screen, like a native app.

### Option C — Host it on a local server or shared folder

If you want to access it from multiple devices on the same network:

1. Place all files (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`) in the same folder on a web server or a shared network path.
2. Open the URL in any browser. For a quick local server you can run:
   ```
   npx serve .
   ```
   or use VS Code's **Live Server** extension.

---

## What the App Does

The app has two main sections, switched via the **Today** and **History** tabs at the top.

---

### Today Tab

This is the main screen you use every day.

| Element | What it shows |
|---|---|
| **Header** | Today's date and your name |
| **Live Clock** | Current time, updating every second |
| **Status Pill** | Green **IN** when you are clocked in, red **OUT** when not |
| **Ring + Button** | A circular progress ring that fills as you approach 6.5 hours |
| **Elapsed Timer** | How long the current session has been running |
| **Today's Hours** | Total hours worked so far today (across all sessions) |
| **6.5h Goal** | Percentage progress toward the 6.5-hour target |
| **Today's Sessions** | A list of each in/out session recorded for today |
| **Recent Days** | A compact table of the last 14 days (excluding today) |

---

### History Tab

A full log of every day you have recorded, grouped by month.

Each month shows:
- Number of **days attended**
- Number of days where you **met the 6.5-hour goal**
- **Average** daily hours for completed days

Each day card shows the first in-time, last out-time, total duration, and a badge (✓ met / ✗ not met / open session).

---

## What You Can Do

### Clock In / Clock Out

Tap the large circular button on the Today tab.

- When you are **OUT**, the button is green and pressing it opens a **Clock In** sheet.
- When you are **IN**, the button is red and pressing it opens a **Clock Out** sheet.
- The sheet pre-fills the current time. You can adjust it to an earlier time (e.g., if you forgot to clock in when you arrived). A note appears confirming the backdated time.
- Tap **Clock In** or **Clock Out** to confirm.

### Add an Entry for Any Date (Past or Today)

Tap the **+** button (floating, bottom-right corner) on either tab, or tap **+ Add Entry** in the History tab header.

- Pick any date (today or in the past).
- Enter an in-time and an out-time (out is optional — leave blank for an open session).
- Tap **Save Entry**.

This is useful for adding a day you forgot to log.

### Edit an Existing Entry

In the **History** tab, each day card has an **Edit** button for each session recorded that day.

- Tap **Edit** to open a sheet with the in and out times pre-filled.
- Adjust either time and tap **Save Changes**.

### Change Your Name

Tap your **name / avatar chip** in the top-right corner of any screen.

- A sheet opens with a text field.
- Type your name and tap **Save**.
- Your initial and name in the header update immediately.

### Export to Excel

Tap **Export Excel** (available in the Today tab's Recent Days card, or in any month header in the History tab).

- Downloads a file called `Office_Attendance.xlsx` to your Downloads folder.
- The file has **one sheet per month**, each containing: Sr. No., Date, In Time, Out Time, Total Hours, 6.5 Hours Done?, and a summary section at the bottom.
- Re-export at any time to get the latest data.

### Auto-Save Excel (Chrome / Edge on Windows)

If your browser supports the **File System Access API** (Chrome or Edge on desktop), an **Auto-Save** button appears next to Export Excel.

- Tap **Auto-Save** and choose where to save the file (e.g., your OneDrive or Desktop).
- From that point on, the Excel file is **automatically overwritten every time you clock in or out** — you always have an up-to-date file without manually clicking export.
- The button turns green (**Auto-Save ON**) to confirm it is active.

---

## Data Storage

- All time entries are stored in your browser's **local storage** under the key `office_time_logger_v1`.
- Data is **never sent anywhere** — it stays entirely on your device.
- Clearing your browser's site data or switching browsers will lose the data. Use **Export Excel** regularly as a backup.

---

## Tips

- You can clock in and out **multiple times in one day** (e.g., if you go out for lunch). Each session is recorded separately and all durations are summed for the total.
- The **progress ring** fills blue as you work toward 6.5 hours, then switches to green once the goal is reached.
- The **Recent Days** table uses colour coding: green = goal met, amber = close (over 5.5h), red = below target.
- The app works **offline** after the first visit thanks to the service worker (`sw.js`).
