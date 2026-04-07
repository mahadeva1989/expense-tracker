# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start dev server at http://localhost:5173
npm run build     # Production build
npm run preview   # Preview production build
npm run lint      # Run ESLint
```

No test framework is configured.

## Architecture

This is a single-file React app — all logic and UI lives in [src/App.jsx](src/App.jsx). There are no components, no routing, and no external state management.

**State in App.jsx:**
- `transactions` — array of `{ id, description, amount, type, category, date }`. `amount` is stored as a string (known bug — causes string concatenation instead of numeric addition in totals).
- `filterType` / `filterCategory` — control which transactions are shown in the table.
- Form fields (`description`, `amount`, `type`, `category`) — controlled inputs for adding a new transaction.

**Data flow:** All state is local to `App`. No persistence (data resets on page reload). Categories are a hardcoded array: `["food", "housing", "utilities", "transport", "entertainment", "salary", "other"]`.

**Intentional issues (course material):** The app has a known bug (amounts stored as strings break numeric totals), poor UI styling, and messy code — these are meant to be fixed as part of the course exercises.
