---
title: "Focus Together"
excerpt: "A calm, sound-first study game for friends · Expo, React Native Web, TypeScript, Supabase"
collection: portfolio
type: apps
order: 1
---

*Personal project · Sep 2026 – present · Expo (React Native Web), TypeScript, Supabase (Postgres, Auth, Realtime), Playwright, GitHub Actions, EAS Hosting · [focustogether.expo.app](https://focustogether.expo.app)*

<!-- PICTURE: hero screenshot of the office during a study session (images/focus-office.png) -->

## What it is

A study game for a small group of friends. You "go to work" together: study at your desk in a shared office, earn poker chips for every minute you focus, and spend earned breaks in a shared allotment garden where you can chat and tend crops.

## How it plays

* **Car park:** where the app opens. Friends who are at work show as their car or bike, in the bay that matches their desk.
* **Office:** twelve identical desks; you're given a random one when you arrive. Set a timer and study. While a session runs, nothing else in the app is reachable. On a phone, leaving the page for more than 10 seconds ends the session with no chips.
* **Payout:** about 1 chip per minute studied, plus an earned break of 1 minute per 5 studied.
* **Garden:** walk about with a thumbstick or arrow keys, chat in speech bubbles, grow crops in real time over a few days (they wither if not picked within 2 days of ripening), water friends' plots, write letters, add friends and trade at the market.
* **Shed:** a shop for vehicles, desk items and seeds.

<!-- PICTURE: the game loop, either a screenshot strip of car park → office → payout → garden, or the loop diagram from docs/PLAN.md redrawn (images/focus-loop.png) -->

## Design principles

* **Calm over clever:** muted palettes and slow motion, with no badges, feeds, red dots or confetti. The timer is the only number that changes while you study.
* **Presence, not pressure:** you see friends' cars, desks and avatars, but there are no leaderboards and nobody else's chip count.
* **Sound is the world:** all audio is procedural (Web Audio API, no audio files). Rain, wind, thunder, birds and crickets are each driven by a weather parameter; scenes crossfade over ~3 s, and indoors the weather passes through a low-pass "window" filter.

## Shared weather

Weather is one deterministic cycle computed from the clock, so every player sees and hears the same weather at the same moment with no server involved. Smooth value noise on several time scales (hours, ~30 min, ~10 min) produces cloud, rain, wind, storm and fog values; rain only falls under heavy cloud, and storms need heavy rain and strong wind. Over a year it is tuned to be roughly Bristol-like: clear ~38% of the time, cloudy 35%, wet 23%, misty 3%. Lightning strikes also fall at deterministic moments, so everyone in the garden sees the flash together and hears the thunder later the further away it is.

<!-- PICTURE: the same scene in clear weather vs a storm, or dawn vs night (images/focus-weather.png). Use the ?weather= and ?hour= preview parameters to capture them -->

## Architecture

* **The server is the source of truth** for chips, status, inventory, plots and trades. Clients never write to tables: every change goes through a security-definer Postgres function using `auth.uid()`, and row-level security only allows reads.
* **Realtime:** garden chat and player positions travel over Supabase Realtime Broadcast on private per-player channels, with RLS deciding who may listen and speak.
* **Clock correction:** every RPC returns the server time, and the client corrects its countdowns against it.
* **Routing:** while a session runs, every place except the office is removed from the navigator, so deep links and the back button can't escape it.
* **Testing and delivery:** scenario tests for the game rules run against plain Postgres, and Playwright browser tests click through the web build. GitHub Actions runs lint, typecheck, the web export and both test suites on every pull request, and deploys to EAS Hosting on merge to `main`. Database changes ship as nine numbered SQL migrations, each with a runbook.
