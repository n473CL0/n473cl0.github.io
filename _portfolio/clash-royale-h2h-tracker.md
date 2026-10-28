---
title: "Clash Royale Head-to-Head Tracker"
excerpt: "Tracking head-to-head records between friends from the Supercell API · React, FastAPI, PostgreSQL, Docker"
collection: portfolio
order: 4
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*Personal project · Jan 2026 – Feb 2026 · React, Tailwind CSS, Python (FastAPI, SQLAlchemy), PostgreSQL, Docker Compose, nginx*

<!-- PICTURE: the dashboard on a phone, showing a head-to-head tally and the leaderboard -->

## What it is

A full-stack web app that tracks head-to-head battle records between friends in Clash Royale, using the official Supercell API.

## Features

* Sign up with email and password, link your in-game player tag, and add friends by searching or with invite links.
* A mobile-first dashboard with head-to-head tallies, a match table, player profile cards and a leaderboard.
* Password reset by email and an in-app feedback form during the beta.

## How it's built

* **Frontend:** React and Tailwind CSS, served by nginx.
* **Backend:** FastAPI with SQLAlchemy. Passwords are hashed with bcrypt, and sessions use JWTs (7-day login tokens, 15-minute password-reset tokens).
* **Syncing:** a background task wakes every 30 minutes and pulls each user's recent battles from the Supercell API, with requests run off the event loop and throttled between users. Each battle gets a deterministic ID hashed from its time and both players, so a battle seen from both friends' battle logs is only stored once.
* **Database:** PostgreSQL holding users, friendships, invites and deduplicated matches.
* **Deployment:** Docker Compose runs the frontend, backend and database as separate containers.
