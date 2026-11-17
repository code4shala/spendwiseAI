# SpendWise AI

A free-first personal finance tracker starter built with React, Vite, Tailwind CSS and Supabase.

## Included in this starter

- Email/password sign-up, login and logout
- Protected application routes
- Add, edit and delete income/expense transactions
- Search and filter transactions
- Dashboard totals and charts
- Monthly category budgets
- Supabase Row Level Security policies
- Responsive sidebar layout

The AI assistant uses a Supabase Edge Function and Groq. Follow [AI_SETUP.md](./AI_SETUP.md) to configure the Groq secret and deploy the function. CSV import/export, savings goals and transfers are also included in this project.

## Requirements

- Node.js LTS
- A Supabase project
- npm

## Run locally

1. Install dependencies:

   ```bash
   npm install
   ```

2. Copy `.env.example` to `.env` and fill in your Supabase project URL and anon/publishable key.

3. In Supabase SQL Editor, run `supabase/migrations/001_initial_schema.sql`.

4. In Supabase Authentication settings, enable Email authentication. For local testing, configure the site URL as `http://localhost:5173`.

5. Start the app:

   ```bash
   npm run dev
   ```

## Security notes

- The frontend uses only the Supabase anon/publishable key. This key is designed for client use when Row Level Security is correctly enabled.
- Never put a Supabase service-role key or Gemini API key in the frontend `.env`.
- Review and test every RLS policy before storing real financial data.
- This starter is for learning and portfolio development, not a certified financial product.

## Build

```bash
npm run build
```

## Design customization

The main application uses a dark, responsive theme. Shared design tokens are at the top of `src/index.css` under `:root` (`--sw-bg`, `--sw-surface`, `--sw-border`, `--sw-text`, `--sw-accent`, and related values). Change these values to adjust the app-wide palette. Layout hooks such as `.app-shell`, `.app-sidebar`, `.app-topbar`, `.app-content`, `.app-nav-link`, `.auth-card`, `.field-input`, `.btn-primary`, and `.btn-secondary` are semantic class names you can customize independently.

## CSV export

The export is Excel-friendly UTF-8 CSV (with a BOM and Windows-style line endings) and includes only the essential, re-importable fields: `title`, `amount`, `type`, `category`, and `transaction_date`. Amounts remain numeric; internal IDs and optional notes are not exported.


## AI assistant setup

See [AI_SETUP.md](./AI_SETUP.md) for the required Groq API key secret, Supabase Edge Function deployment commands, and troubleshooting steps.
