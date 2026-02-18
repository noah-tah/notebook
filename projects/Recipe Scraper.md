I want to write an app that scans the page and rips out the recipe and saves it into my obsidian repository.

What technology is capable of doing something like this?
What you want is **very doable** — you’re basically building a  
👉 _“recipe scraper + cleaner + markdown exporter”_.

There are 3 main pieces of tech involved:

---
[[Basic Idea]]
# Basic idea
 [[Basic Idea]]
[[Product Breakdown]]
[[Product Breakdown]]
[[High Level Architecture]]
# Overall Strategy
- schema-first approach
	- `Recipe`, `Ingredient`, and `RecipeStep`
		- These are interfaces that are the contract for what a recipe looks like.
- Why this matters
	- recipes sites are different
		- some use JSON-LD (structured data)
		- some use HTML with custom markup
		- Some use different formats, units, and naming.
- AI helps with normalization, turning messy site data and making it fit into my schema
	- ai can parse free text or semi structured html
	- map it into my interfaces
	- fill in optional fields when possibleA

[[Prisma Data Scheme Sketch]]