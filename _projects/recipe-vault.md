---
title: "recipe-vault"
summary: "Self-hosted recipe manager with ingredient-based search and automatic unit conversion."
status: "Active"
date: 2026-05-18
stack: [Python, FastAPI, SQLite, HTMX]
tags: [web app, self-hosted, python]
repo: https://github.com/yourname/recipe-vault
demo: https://recipes.example.com
---

## Overview

A personal recipe manager I run on a home server. Import a recipe from
a URL, and it strips the ads/life-story preamble and stores just the
ingredients and steps.

## Current state

Core import + search is working. Working on:

- [ ] Meal planning calendar view
- [ ] Grocery list generation from a week's plan
- [x] URL importer with ad/boilerplate stripping
- [x] Ingredient-based fuzzy search

## Architecture

```
browser (HTMX) → FastAPI → SQLite
                      ↓
              recipe-scraper (import)
```

Kept the frontend to HTMX + server-rendered templates on purpose —
didn't want a JS build step for a tool only I use.

## Lessons so far

Recipe sites have wildly inconsistent HTML structure, so the importer
leans on a handful of common schema.org `Recipe` markup patterns first,
then falls back to heuristics.
