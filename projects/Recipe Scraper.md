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

# Prisma Data Schema Sketch
```
// prisma/schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model Recipe {
  id               String   @id @default(cuid())
  title            String
  description      String?
  servings         Int?
  prepTimeMinutes  Int?
  cookTimeMinutes  Int?
  totalTimeMinutes Int?
  sourceUrl        String?
  sourceAuthor     String?
  images           String[]
  notes            String[]
  nutrition        Json?    // { calories?, protein?, carbs?, fat?, ... }
  createdAt        DateTime @default(now())
  updatedAt        DateTime @updatedAt

  ingredients Ingredient[]
  steps       RecipeStep[]
  tags        RecipeTag[]
}

model Ingredient {
  id       String  @id @default(cuid())
  recipeId String
  recipe   Recipe  @relation(fields: [recipeId], references: [id], onDelete: Cascade)
  name     String
  amount   Float?
  unit     String?
  order    Int     @default(0)

  @@index([recipeId])
}

model RecipeStep {
  id       String  @id @default(cuid())
  recipeId String
  recipe   Recipe  @relation(fields: [recipeId], references: [id], onDelete: Cascade)
  text     String
  order    Int     @default(0)

  @@index([recipeId])
}

model Tag {
  id       String      @id @default(cuid())
  name     String      @unique
  recipes  RecipeTag[]
}

model RecipeTag {
  recipeId String
  tagId    String
  recipe   Recipe @relation(fields: [recipeId], references: [id], onDelete: Cascade)
  tag      Tag    @relation(fields: [tagId], references: [id], onDelete: Cascade)

  @@id([recipeId, tagId])
}
```

- potential problem with `cuid`
	-  Status: Deprecated due to security. Use [Cuid2](https://github.com/paralleldrive/cuid2), instead.
- https://github.com/paralleldrive/cuid