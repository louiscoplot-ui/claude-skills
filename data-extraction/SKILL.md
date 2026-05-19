---
name: data-extraction
description: >
  Extract, parse, and pipeline data from websites, APIs, PDFs, HTML, JSON, CSV, databases.
  Use when user says "extract data from X", "parse this HTML", "scrape this site", "build a
  data pipeline", "extract from PDF", "parse JSON response", "ETL pipeline", "data collection",
  "get data from API", "bulk data extraction".
---
# Data Extraction

## Static HTML (BeautifulSoup)
soup = BeautifulSoup(html, 'html.parser')
items = [{ title: card.select_one('h2').text, price: card.select_one('.price').text }
         for card in soup.select('article.card')]

## Dynamic JS (Playwright)
await page.goto(url)
await page.wait_for_selector('.card')
items = await page.evaluate('() => [...document.querySelectorAll(".card")].map(el => ({...}))')

## JSON Embedded in Page
pattern = r'window\.ArgonautExchange\s*=\s*(\{.*?\});'
data = json.loads(re.search(pattern, html, re.DOTALL).group(1))

## API Pagination
while True:
    data = requests.get(url, params={'page': page}).json()
    if not data['results']: break
    results.extend(data['results'])
    page += 1
    time.sleep(1)

## PDF Extraction
with pdfplumber.open(path) as pdf:
    text = '\n'.join(p.extract_text() for p in pdf.pages)
    tables = [t for p in pdf.pages for t in p.extract_tables()]

## Pipeline Pattern
pipeline = fetch -> clean -> deduplicate -> export
run each step in sequence, yield for memory efficiency

## Deduplication
seen = set()
unique = [r for r in records if (key := tuple(r[f] for f in key_fields)) not in seen and not seen.add(key)]
