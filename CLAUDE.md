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

React app with no routing and no external state management. Components live in `src/`.

**Component tree:**
```
App
├── Summary
├── TransactionForm
└── TransactionList
```

**State ownership:**
- `App` — holds the `transactions` array (`{ id, description, amount, type, category, date }`). Passes it down and exposes `handleAdd` as `onAdd` to `TransactionForm`.
- `TransactionForm` — owns its own form fields state; calls `onAdd` with the built transaction object on submit.
- `TransactionList` — owns `filterType` and `filterCategory` state; filters and renders the received `transactions`.
- `Summary` — stateless; computes `totalIncome`, `totalExpenses`, and `balance` from the `transactions` prop.

**Shared constant:** `categories` array is duplicated in `TransactionForm` and `TransactionList` — no shared constants file yet.

**Data flow:** No persistence; data resets on page reload. This is a course starter project — some rough edges are intentional.
