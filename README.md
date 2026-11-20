# Skybound

A small, responsive Flappy Bird-style game built with React, canvas, and Supabase.

## Run locally

1. Install Node.js 20.19+ or 22.12+.
2. Run `npm install`, then `npm run dev`.
3. Sign in to your Supabase dashboard, select the project, open **SQL Editor → New query**, and run the contents of [`supabase/schema.sql`](./supabase/schema.sql) to create the shared leaderboard, grant public table access, and apply its row-level security policies. If you already ran an earlier version, rerun the updated SQL.
4. Copy `.env.example` to `.env.local` and add your Supabase project URL and **publishable** key. Restart the dev server.

Players enter a display name before they can start; after each flight, their score (including zero) is submitted to the shared leaderboard. The game remains playable without Supabase; the leaderboard then shows a connection/setup message instead of shared scores. Never put a Supabase service-role key in a browser app.

Scores are submitted from the browser, so the SQL policies validate their shape but cannot prove that a score was earned legitimately. Enforcing trustworthy scores requires server-side validation.
