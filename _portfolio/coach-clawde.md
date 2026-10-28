---
title: "Coach Clawde"
excerpt: "A workout-tracking PWA that uses Claude as a strength and conditioning coach · React, TypeScript, Supabase"
collection: portfolio
order: 2
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*Personal project · Jun 2026 – present · React 19, TypeScript, Vite, Tailwind CSS, Zustand, Supabase, Vitest, Vercel · [Website](https://n473cl0.github.io/coachclawde/) · [Code on GitHub](https://github.com/n473CL0/coachclawde)*

<!-- PICTURE: phone screenshot of the session screen mid-workout, next to the week planner -->

## What it is

An installable web app (PWA) for planning and logging workouts, with Claude acting as the coach. It's in closed beta with multiple users.

## How it works

1. Pick your training days and add any notes, then press **Generate & Open Claude**. The app builds a self-contained prompt from your profile, injuries, a summary of your recent history, the programming rules and the week-plan JSON schema, and opens it pre-filled in a new Claude chat.
2. Claude returns a progressive-overload plan as JSON.
3. **Import** the JSON back into the app and train. Logged sessions sync to your account automatically.

## Features

* Week planner, program editor, live session mode with a rest timer and movement guides, cardio intervals, workout history, personal-best tracking and check-ins.
* Onboarding through a chat-style flow.
* Keeps the screen awake during a workout.
* A "What's new" sheet after each update. The build fails if the release notes don't match the app version, so an update can't ship without notes.

## Architecture

* **No custom server:** the browser talks to Supabase (Postgres, auth and row-level security) directly; each athlete's profile, plans and sessions live in their own rows.
* **Offline local mode:** without Supabase credentials the app runs as a single-user local app, so development needs no backend.
* **Accounts:** beta accounts are provisioned with email and password by a script, so the closed beta needs no email delivery. Magic-link sign-in is built but hidden behind a flag until SMTP is available.
* **Quality gates:** ESLint, a TypeScript build and Vitest tests for the logic must all pass before a change is committed.

<!-- PICTURE (optional): the "Generate & Open Claude" step, i.e. the app and the pre-filled Claude chat side by side -->
