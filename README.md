# Class 10 Command Centre (C10C)

> **A personal command centre for the Class 10 exam season.** Plan your study days, track chapter-level progress, keep revision notes, and see how far you've come — all in one place.

**Live app:** https://cxccomeback.vercel.app  
**Repository:** https://github.com/ElliotPatil/cxc_comeback

---

## What is C10C?

Class 10 Command Centre is a lightweight, mobile-friendly study dashboard built to make exam preparation easier to organise and easier to stick with.

Instead of jumping between a calendar, checklist, notes app, and progress spreadsheet, C10C brings the essentials into one workspace. It is designed around a simple idea:

**Know what needs to be done. Track what gets done. Keep moving.**

The project is currently configured around the **CBSE Class 10** subject structure.

## Features

### 📚 Study Tracker
- Browse subjects and their chapters.
- Track six milestones for every chapter:
  1. Studied
  2. Made notes
  3. Revised for prelims
  4. Studied after prelims
  5. Revised after prelims
  6. Board ready
- Keep a separate notepad for each chapter.
- View checklist progress as you work.

### 🗓️ Study Calendar
- View your plan by date.
- Add multiple subjects or study sessions to a single day.
- Add daily tasks and notes.
- Mark sessions and days as complete.
- Keep track of completed work over time.

### 📊 Syllabus Completion
- See progress across subjects and chapters.
- Identify chapters that still need attention.
- Review completion by subject and across the syllabus.

### 🎯 Exam Centre
- Keep exam-related information in one place.
- Track sample papers solved by subject.
- Record Mathematics question practice.
- Keep useful exam preparation details together.

### 🌱 Daily Reset & Motivation
- Use a guided breathing session with different durations.
- Review the work you've completed today.
- Compare your study activity with the previous day.
- Get a small daily motivational prompt.

### 🔥 Streaks & feedback
- Track consistency through study activity.
- Get lightweight feedback when milestones and tasks are completed.
- The goal is to encourage consistency, not punish missed days.

### 💾 Data & backups
- Save the workspace in the browser using IndexedDB, with a localStorage fallback.
- Export a JSON backup.
- Import a previous backup when needed.
- The app shell is cached by a service worker to support a more app-like experience.

### ☁️ Google connection (experimental)
- The app includes Google sign-in and a Firebase/Firestore integration for publishing a limited parent-progress snapshot.
- The parent view is available at the `/parents` route.

**Important:** This is not yet full account-isolated cloud sync. The complete workspace, including chapter notes and all study data, is not synchronised across devices. The current parent-progress implementation uses a shared Firestore document, so its access rules and suitability for multiple users must be reviewed before using it with other people's data. Do not treat this experimental feature as private multi-user storage.

---

## Getting started

### Use the live app

Open **https://cxccomeback.vercel.app** in a modern browser.

For the best mobile experience, open the site in Chrome. If your browser offers an install option, you can add C10C to your home screen.

### Run it locally

C10C is currently a static web app — there is no npm install or build step.

1. Clone or download this repository.
2. Start a local web server from the project folder. For example, with Python:

   ```bash
   python -m http.server 8000
   ```

3. Open **http://localhost:8000** in your browser.

Use a local server rather than opening `index.html` directly with `file://`, because the app uses JavaScript modules.

---

## Project structure

| File / folder | Purpose |
| --- | --- |
| `index.html` | Main application: layout, styles, study tools, and app logic |
| `manifest.json` | Progressive Web App metadata and install settings |
| `sw.js` | Service worker for app-shell caching and update handling |
| `icons/` | App icons used by the PWA manifest |

The application is intentionally kept lightweight and does not currently use a frontend framework or a package manager.

## Technology

- **HTML, CSS and JavaScript** — application structure, styling and behaviour.
- **IndexedDB** — primary browser-based workspace storage.
- **localStorage** — fallback and backup mirror for local data.
- **Firebase Authentication & Cloud Firestore** — experimental Google sign-in and parent-progress publishing.
- **Service Worker & Web App Manifest** — installable, app-like browser experience.
- **Vercel** — live deployment.

Firebase's JavaScript SDK is loaded as browser modules from Google's CDN, so an internet connection is required for those imports.

---

## Data, privacy & limitations

A few things worth knowing before using the app:

- **Local data belongs to the browser profile on that device.** It does not automatically follow you to another phone or browser.
- Export backups regularly. Clearing browser/site data, changing browser profiles, or losing access to the device can make local progress unavailable.
- Importing a backup replaces the current in-memory workspace with the imported data. Keep a copy of your current backup before importing.
- The current subject and chapter catalogue is configured for CBSE Class 10; it is not yet a general-purpose board/custom-syllabus editor.
- Google sign-in and parent-progress publishing are experimental. Full private, per-account cloud workspace sync has not been implemented.
- The app uses external Firebase modules and web fonts, so some features or styling may require an internet connection.

C10C is a work in progress. Backups are the safest way to protect important study data.

## Deployment

The repository is configured for a static-site deployment and is currently hosted on Vercel.

For your own deployment:
1. Fork or clone the repository.
2. Import the repository into your hosting provider as a static site.
3. Set the project root to the repository root; no build command is required.
4. If you intend to use Firebase features, configure your own Firebase project, authentication providers, authorised domains, and Firestore security rules. Review the current shared parent-dashboard data model before enabling it for real users.

Do not assume that changing the hosting URL alone makes the Firebase integration private or multi-user safe.

---

## Contributing

Suggestions, bug reports, and improvements are welcome. Before making a change, keep the project lightweight and mobile-friendly, and make sure existing local study data remains compatible.

For bug reports, include:
- What you were trying to do.
- What you expected to happen.
- What actually happened.
- Your browser and device, if the issue is visual or device-specific.

## Project philosophy

C10C isn't meant to be another complicated productivity system. It should make studying clearer, reduce the friction of getting started, and help turn small daily actions into steady progress.

**Plan clearly. Show up. Track the work. Repeat.**

---

*Built as a practical study companion for the Class 10 exam journey.*
