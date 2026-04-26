# Focus — Task Manager

A clean, minimal, and fully-featured task management app built as a single self-contained HTML file. No frameworks, no build tools, no dependencies — just open it in a browser and start getting things done.

![Focus Task Manager](https://img.shields.io/badge/version-1.0.0-brightgreen) ![HTML](https://img.shields.io/badge/built%20with-HTML%20%2F%20CSS%20%2F%20JS-orange) ![No dependencies](https://img.shields.io/badge/dependencies-none-blue) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## ✨ Features

### Task Management
- **Add tasks** — Type and press Enter or click the `+` button
- **Complete tasks** — Click the circular checkbox to mark as done; completed tasks appear in a separate section with strikethrough text
- **Edit tasks** — Double-click any task text or use the edit icon to rename inline
- **Delete tasks** — Remove individual tasks with the trash icon; bulk-clear all completed tasks at once
- **Drag & drop reordering** — Grab the handle on the left of any task to reorder manually

### Organization
- **Categories** — Tag tasks as `Work`, `Personal`, `Study`, or `Health`
- **Priority levels** — Set priority to `High`, `Medium`, or `Low`; high and medium priorities show a color-coded left border and badge
- **Timestamps** — Each task displays a relative time label (e.g., "Just now", "2h ago", "Yesterday")

### Filtering & Sorting
- **Sidebar filters** — Filter by All, Active, Completed, or any category
- **Toolbar tabs** — Quickly switch between All / Active / Completed views
- **Live search** — Filter the visible task list in real time by keyword
- **Sort options** — Sort by Newest, Oldest, Priority, or Alphabetical

### Progress Tracking
- **Ring chart** — An animated SVG ring shows overall completion percentage
- **Progress bar** — A horizontal bar also tracks completion
- **Motivational headings** — Dynamically updated messages ("Keep it up!", "Halfway there!", "All done! 🎉")
- **Live counters** — Sidebar and footer counts update instantly as you work

### UI & Experience
- **Light / Dark mode** — Fully themed with a toggle in the sidebar; preference is saved across sessions
- **Responsive design** — Works on desktop and mobile; sidebar becomes a slide-in drawer on small screens
- **Toast notifications** — Subtle pop-up messages confirm actions like deletions and bulk clears
- **Smooth animations** — Tasks animate in on creation and out on deletion
- **Persistent storage** — All tasks and theme preference are saved to `localStorage` so your data survives page refreshes

---

## 🖥️ Screenshots

| Light Mode | Dark Mode |
|---|---|
| *(Add screenshot here)* | *(Add screenshot here)* |

---

## 🚀 Getting Started

### Option 1 — Download & Open
1. Download `todo-app.html`
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge)
3. That's it — no installation required

### Option 2 — Clone the Repo
```bash
git clone https://github.com/your-username/focus-task-manager.git
cd focus-task-manager
open todo-app.html   # macOS
# or
start todo-app.html  # Windows
```

> **Note:** Because the app uses `localStorage`, it must be opened in a browser. It does not require a server.

---

## 🗂️ Project Structure

```
focus-task-manager/
└── todo-app.html    # The entire app — HTML, CSS, and JS in one file
```

Everything lives in a single file for maximum portability. You can host it on GitHub Pages, share it as an email attachment, or keep it on a USB drive.

---

## 🧠 How It Works

### Data Model
Each task is stored as a plain JavaScript object:

```js
{
  id: "abc123",        // Unique ID generated at creation
  text: "Buy groceries",
  done: false,
  ts: 1714123456789,   // Unix timestamp (ms)
  category: "personal", // "work" | "personal" | "study" | "health" | ""
  priority: "high"     // "high" | "med" | "low" | ""
}
```

The full task array is serialized to JSON and saved under the key `focus_tasks` in `localStorage`.

### State Management
The app uses simple global variables and a single `render()` function — no virtual DOM, no reactive framework. Any mutation to the `tasks` array is followed by `save()` (writes to localStorage) and `render()` (rebuilds the DOM).

### Filtering Logic
`getFiltered()` applies filters in this order: category/status filter → keyword search → sort. This means search works within whichever category view you're currently in.

### Drag & Drop
Uses the native HTML5 Drag and Drop API. `dragSrc` tracks the source task ID; on drop, the two tasks are swapped in the `tasks` array and the order is persisted.

---

## ⌨️ Keyboard Shortcuts

| Action | Shortcut |
|---|---|
| Add a task | `Enter` in the input field |
| Save an edit | `Enter` while editing |
| Cancel an edit | `Escape` while editing |

---

## 🎨 Theming & Customization

The UI is built entirely with CSS custom properties, making it easy to retheme.

### Color Tokens (Light Mode defaults)

| Variable | Value | Usage |
|---|---|---|
| `--bg` | `#F5F2EC` | Page background |
| `--surface` | `#FFFFFF` | Card / sidebar background |
| `--accent` | `#2D5A3D` | Primary green — buttons, active states |
| `--accent2` | `#C17B2F` | Secondary amber — hover on add button |
| `--danger` | `#B33A3A` | Red — delete actions |
| `--text` | `#1C1A14` | Primary text |
| `--text2` | `#6B6655` | Secondary text |
| `--text3` | `#ABA896` | Muted / placeholder text |

### Category Colors
Each category has its own background and foreground token pair:

| Category | Token prefix |
|---|---|
| Work | `--tag-work-bg` / `--tag-work-fg` |
| Personal | `--tag-personal-bg` / `--tag-personal-fg` |
| Study | `--tag-study-bg` / `--tag-study-fg` |
| Health | `--tag-health-bg` / `--tag-health-fg` |

To change a color, edit the corresponding CSS variable in the `:root` block at the top of the `<style>` section.

### Typography
The app uses three Google Fonts:
- **Fraunces** (serif) — headings, logo, page title
- **DM Sans** (sans-serif) — body text, inputs, buttons
- **DM Mono** (monospace) — timestamps, counters, percentage

---

## 🌐 Hosting on GitHub Pages

1. Push `todo-app.html` to a GitHub repository
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your app will be live at `https://your-username.github.io/repo-name/todo-app.html`

---

## 🔒 Privacy

All data is stored locally in your browser's `localStorage`. Nothing is sent to any server. There are no analytics, no cookies, and no network requests (except loading Google Fonts on first open).

---

## 🛠️ Browser Support

| Browser | Support |
|---|---|
| Chrome / Edge | ✅ Full |
| Firefox | ✅ Full |
| Safari | ✅ Full |
| iOS Safari | ✅ Full |
| Android Chrome | ✅ Full |

Requires a browser that supports ES6, CSS custom properties, and the Drag and Drop API (all modern browsers).

---

## 📋 Roadmap / Ideas

- [ ] Due dates and overdue indicators
- [ ] Subtasks / checklists within a task
- [ ] Export tasks to CSV or JSON
- [ ] Import tasks from a file
- [ ] Multiple lists / projects
- [ ] Recurring tasks
- [ ] Keyboard shortcut to focus input (`/`)
- [ ] PWA support (offline-first, installable)

---

## 🤝 Contributing

Contributions are welcome! Since this is a single-file app, please keep that constraint in mind.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes to `todo-app.html`
4. Commit: `git commit -m "Add my feature"`
5. Push: `git push origin feature/my-feature`
6. Open a Pull Request

---

## 📄 License

MIT License — free to use, modify, and distribute. See [LICENSE](LICENSE) for details.

---

*Built with ♥ using vanilla HTML, CSS, and JavaScript.*
