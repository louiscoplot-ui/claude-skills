---
name: browser-automation
description: >
  Advanced browser automation with Playwright: session management, navigation, form filling,
  file downloads, network interception, screenshots, PDF generation. Use when user says
  "automate browser", "fill this form automatically", "automate login", "navigate multiple pages",
  "download files automatically", "intercept API calls", "browser bot".
---
# Browser Automation

## Save/Load Session (persist login)
storage = await page.context.storage_state()
json.dump(storage, open('session.json', 'w'))
context = await browser.new_context(storage_state='session.json')

## Wait Strategies
await page.wait_for_selector('.results', timeout=10000)
await page.wait_for_load_state('networkidle')
async with page.expect_response('**/api/**') as r: await page.click('.load')
data = await (await r.value).json()

## Intercept API Responses
page.on('response', async lambda r: results.append(await r.json()) if '/api/' in r.url else None)

## File Download
async with page.expect_download() as dl: await page.click('.download-btn')
await (await dl.value).save_as('file.xlsx')

## Infinite Scroll
while True:
    await page.evaluate('window.scrollTo(0, document.body.scrollHeight)')
    await page.wait_for_timeout(1500)
    if height unchanged: break

## Multi-Tab Parallel
semaphore = asyncio.Semaphore(5)
pages = await asyncio.gather(*[open_tab(context, url) for url in urls])

## Remove Webdriver Flag
await context.add_init_script("Object.defineProperty(navigator,'webdriver',{get:()=>undefined})")
