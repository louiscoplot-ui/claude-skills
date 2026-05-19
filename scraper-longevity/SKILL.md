---
name: scraper-longevity
description: >
  Make scrapers last longer before being blocked or rate-limited. Human-like behavior, rotation
  strategies, error handling, checkpointing, recovery. Use when user says "my scraper keeps getting
  blocked", "avoid rate limiting", "scraper gets detected", "make scraper last longer",
  "avoid getting banned", "how to scrape without being struck".
---
# Scraper Longevity

## Human-Like Timing
time.sleep(random.uniform(1.5, 4.0))  # between pages
random.uniform(0.05, 0.15) per keystroke when typing

## User Agent Rotation (5 real UAs)
USER_AGENTS = [Chrome/Win, Chrome/Mac, Firefox/Win, Safari/Mac, Chrome/Linux]
rotate every session or every 50 requests

## Session Manager
- New session every 50 requests
- Full browser headers on each session
- 3-8s pause between session resets

## Realistic Playwright Context
- Random viewport (1366/1440/1920 x 768/900/1080)
- locale: en-AU, timezone: Australia/Perth
- Remove webdriver flag via init_script

## Adaptive Backoff on Errors
429 -> respect Retry-After + 5-15s extra
403 -> pause 30s x consecutive_errors
exponential backoff: delay = base * 2^errors (cap 120s)

## Daily Volume Limits
300-500 pages/day max
Reset counter at midnight
Raise exception if limit reached

## Checkpointing
Save completed URLs + results to JSON after each fetch
On restart: skip already-done URLs
Never lose progress on crash

## Anti-Strike Checklist
- Delays 1.5-4s random between requests
- Rotate UA every session
- New session every 50 requests
- Backoff on 429/403
- Max 300-500 pages/day
- Checkpoint + resume on crash
- Respect Retry-After headers
- Scrape 2am-6am Perth time (off-peak)
- Never hammer same URL repeatedly
- Check robots.txt before starting
