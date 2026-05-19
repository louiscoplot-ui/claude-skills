---
name: bot-performance
description: >
  Optimize bot and scraper performance: async concurrency, batching, caching, rate limiting,
  retry logic, memory efficiency. Use when user says "make my scraper faster", "concurrent requests",
  "async scraping", "rate limiting", "retry on failure", "optimize my bot", "my scraper is slow".
---
# Bot Performance

## Async Playwright (5 concurrent tabs)
semaphore = asyncio.Semaphore(5)
async def scrape_one(browser, url):
    async with semaphore:
        page = await browser.new_page()
        await page.goto(url)
        data = await page.evaluate('...')
        await page.close()
        return data
results = await asyncio.gather(*[scrape_one(browser, url) for url in urls])

## Async HTTP (aiohttp, 10 concurrent)
connector = aiohttp.TCPConnector(limit=10)
async with aiohttp.ClientSession(connector=connector) as session:
    results = await asyncio.gather(*[fetch(session, url) for url in urls])

## Retry with Exponential Backoff
@retry(max_attempts=3, delay=2, backoff=2)
def fetch_page(url): return requests.get(url, timeout=10)

## SQLite Cache
cache.get(md5(url)) or (fetch(url) -> cache.set(md5(url), result))
TTL: 3600s default

## Rate Limiter
min_interval = 1.0 / calls_per_second
if elapsed < min_interval: sleep(min_interval - elapsed)

## Memory: Generators
def scrape_pages(urls):
    for url in urls: yield fetch(url)  # one at a time not all in RAM
