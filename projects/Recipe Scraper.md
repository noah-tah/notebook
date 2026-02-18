I want to write an app that scans the page and rips out the recipe and saves it into my obsidian repository.

What technology is capable of doing something like this?
What you want is **very doable** — you’re basically building a  
👉 _“recipe scraper + cleaner + markdown exporter”_.

There are 3 main pieces of tech involved:

---

# 1️⃣ Page scraping (getting the content)

- **Node.js**
	- `axios` / `fetch`
Use a headless browser:
- **Playwright** (best modern option)
- **Puppeteer**
- **Selenium**
These load the page like a real browser, so you can:
- wait for content to render
- click “jump to recipe”
- scroll if needed
- then extract the HTML

👉 If you want reliability, **Playwright is the move**.

# 2️⃣ Recipe extraction (the REAL problem)

Most recipe sites bury the recipe in garbage:

- life story
- ads
- popups
- unrelated images
You want **content extraction**.
### 🔥 Best solution: Structured data parsing
Most recipe sites include hidden JSON like:

```
<script type="application/ld+json">
{
  "@type": "Recipe",
  "name": "...",
  "recipeIngredient": [...]
}
</script>
```

You can parse this and get:

- title
- ingredients
- steps
- cook time
- servings
👉 This is the **gold standard** solution.

# Fallback options
- **Mozilla** Readability.js
- Mercury Parser
- Goose Extractor


# 3️⃣ Exporting to your Obsidian vault

Since **Obsidian** uses plain Markdown, this part is easy.

Your app can:
1. Convert recipe → Markdown template




- Node.js
- Playwright
- JSON-LD parser
- Markdown generator

Cookbook.io
- Scrapes recipe from website, cutting out life story and ads only keeping recipe, saves it to database. Application queries database and displays recipes on demand. To avoid legal trouble in the database schema i will make sure to take note of the author and the proper accreditation's. Is this legal? I am certain that it is technically feasible. I think that you could even use AI to determine what parts are life story and what parts are recipe in order to make the scraping more accurate.

# My Gamplan
