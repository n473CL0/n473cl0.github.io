---
title: "UWCheck"
excerpt: "One calendar and to-do list for every UW deadline: Canvas, Ed and CSE course websites · Node.js, npm"
collection: portfolio
order: 3
published: false  # AI-written draft: rewrite the excerpt and text in your own words, then delete this line
---

*Personal project · Oct 2026 – present · Node.js, HTML/CSS/JavaScript, GitHub Actions, npm · [n473cl0.github.io/uwcheck](https://n473cl0.github.io/uwcheck/) · [Code on GitHub](https://github.com/n473CL0/uwcheck)*

<!-- PICTURE: the month calendar next to the to-do list. Already in the repo: docs/screenshot-light.png (and docs/screenshot-dark.png) -->

## What it is

A local app that pulls every deadline from a University of Washington student's courses into one calendar and to-do list. It's published on npm, so installing it is one command: `npx uwcheck@latest --install`.

## Where deadlines come from

Each source is one small module, so adding another tool is one new file:

* **Canvas:** the course calendar feed (.ics), so no API token is needed.
* **Ed:** the Ed lessons API, with the student's own API token. With no courses configured, it picks up every active course on the account.
* **CSE course websites:** the public `assignments.html` pages that UW CSE courses often use to list work before it appears on Ed.

## Features

* A month calendar and a to-do list, with search, keyboard shortcuts and ticking items off.
* Reminders a day and two hours before each deadline.
* A calendar feed to subscribe to from Apple Calendar or Outlook.
* Installs as an app in the Start menu, Spotlight or app launcher, runs in the background, and updates itself from a button in the header.

## How it's built

* **No dependencies:** a single Node.js server with no npm packages, serving a one-page front end.
* **Private by design:** it only listens on `127.0.0.1`. The Canvas feed URL and Ed token stay in a config file on the student's computer and are only ever sent to Canvas and Ed.
* **Testing and release:** tests use Node's built-in test runner and run on Ubuntu and Windows in GitHub Actions, alongside a smoke test; a second workflow publishes new versions to npm.
