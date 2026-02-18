1️⃣ Page scraping (getting the content)

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
2️⃣ Recipe extraction (the REAL problem)

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

Fallback options
- **Mozilla** Readability.js
- Mercury Parser
- Goose Extractor


3️⃣ Exporting to your Obsidian vault

Since **Obsidian** uses plain Markdown, this part is easy.

Your app can:
1. Convert recipe → Markdown template
