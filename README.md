# 💸 Naira Expense Tracker

A simple, mobile-first expense tracker that shows you where your money goes. Built with plain HTML, CSS and JavaScript in a single file. No backend, no API keys, no installs.

**Live demo:** `<add your link here>`

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Screenshots](#screenshots)
4. [Getting Started](#getting-started)
5. [How to Use](#how-to-use)
6. [Project Structure](#project-structure)
7. [How It Works](#how-it-works)
8. [Data Format](#data-format)
9. [Design Decisions](#design-decisions)
10. [Browser Support](#browser-support)
11. [Privacy and Data Storage](#privacy-and-data-storage)
12. [Troubleshooting](#troubleshooting)
13. [Roadmap](#roadmap)
14. [Contributing](#contributing)
15. [Author](#author)

---

## Overview

Most people don't know where their money goes until it's gone. This app makes tracking quick: type what you spent, pick a category, and see your totals update instantly. It's built for everyday Naira spending like food, transport, data and bills.

The whole app lives in one HTML file, so you can open it, host it anywhere, or edit it with no tooling.

## Features

**Core**
- Add expenses with a name, amount (₦), category and date
- Total spent displayed at the top, formatted like ₦12,500
- Category breakdown shown as chips (e.g. Food: ₦5,000)
- Expense list sorted newest first
- Edit or delete any expense
- Clear all with a confirmation popup

**Budgeting**
- Set a monthly budget in ₦
- Progress bar showing spent vs budget
- Turns orange at 80% and red when the limit is passed, with a warning message

**Views**
- All time, This month and This week

**Data**
- Auto-saves to your browser (localStorage)
- Export all expenses to CSV

**Design**
- Mobile-first layout, max width 480px
- Automatic dark mode
- Large tap-friendly inputs and buttons
- Safe-area support for phones with notches

## Screenshots

| Light mode | Dark mode |
|---|---|
| `<add screenshot>` | `<add screenshot>` |

## Getting Started

### Option 1: Open locally
1. Download `index.html`
2. Double-click it, or open it in your browser

### Option 2: Host it for free
- **GitHub Pages:** push the file to a repo, then go to Settings > Pages and select the main branch
- **Netlify:** drag and drop the file onto netlify.com/drop
- **Vercel:** import the repo and deploy

No build step and no environment variables needed.

## How to Use

1. **Add an expense:** type the name (e.g. "Jollof rice"), enter the amount, choose a category and date, then tap **Add expense**.
2. **Set a budget:** enter your monthly budget. The progress bar updates as you add expenses.
3. **Switch views:** use the tabs to see all time, this month or this week.
4. **Edit:** tap **Edit** on an expense. It loads into the form, then tap **Save changes**.
5. **Delete:** tap ✕ on an expense to remove it.
6. **Export:** tap **Export CSV** to download your data as a spreadsheet file.
7. **Reset:** tap **Clear all** and confirm to wipe everything.

## Project Structure

```
naira-expense-tracker/
├── index.html      # The entire app (HTML + CSS + JS)
└── README.md       # This file
```

Inside `index.html`:
- `<style>`: CSS variables, layout, dark mode
- `<body>`: form, budget bar, tabs, list
- `<script>`: state, rendering, storage, CSV export

## How It Works

1. **State:** all expenses live in a JavaScript array called `items`.
2. **Storage:** every change is saved to `localStorage` as JSON. On page load, the data is read back in. All storage calls are wrapped in `try/catch` so the app still works if storage is blocked.
3. **Rendering:** a `render()` function recalculates totals, category chips, the budget bar and the list from the current state, then updates the page.
4. **Money formatting:** amounts are formatted with `toLocaleString("en-NG")`.
5. **Safety:** user text is inserted with `textContent` instead of `innerHTML`, which prevents HTML injection.
6. **CSV export:** the app builds a CSV string, wraps it in a Blob, and triggers a download.

## Data Format

Expenses are stored under the localStorage key `exp` like this:

```json
[
  {
    "name": "Jollof rice",
    "amt": 1500,
    "cat": "Food",
    "date": "2026-10-31"
  }
]
```

CSV export columns: `name, category, amount, date`

## Design Decisions

- **Single file:** easy to share, host and edit.
- **No dependencies:** loads instantly and works offline once opened.
- **CSS variables:** one place to change colors and themes.
- **Green accent:** fits the Naira theme and keeps the UI calm.
- **Local-first:** no accounts, no servers, no tracking.

## Browser Support

Works on any modern browser:
- Chrome, Edge, Brave, Opera
- Safari (iOS and macOS)
- Firefox

## Privacy and Data Storage

- All data stays on your device, in your browser.
- Nothing is sent to any server.
- Clearing browser data, using private mode, or switching devices will remove or hide your expenses.
- **Back up regularly** with Export CSV.

## Troubleshooting

| Problem | Fix |
|---|---|
| Expenses disappear after refresh | Your browser may be blocking localStorage or you're in private mode. Use a normal window. |
| Amount won't add | Amount must be greater than zero and the name can't be empty. |
| Budget bar not showing | Enter a budget amount first. |
| CSV won't download | Allow downloads for the page in your browser settings. |
| Layout looks cramped on desktop | The app is built mobile-first. Zoom out or open it on your phone. |

## Roadmap

- [ ] Charts for spending by category
- [ ] Custom categories
- [ ] Recurring expenses (data, rent, subscriptions)
- [ ] Income tracking and balance
- [ ] Import from CSV
- [ ] Install as a PWA (works like a real app)
- [ ] Multiple budgets per category

## Contributing

Ideas and improvements are welcome.

1. Fork the repo
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push: `git push origin feature/your-feature`
5. Open a pull request

## License

MIT License. Free to use, modify and share.

## Author

Built by **Fawaz**.
