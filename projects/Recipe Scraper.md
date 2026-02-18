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
- The original CUID is deprecated because it:
	- Leaks information (host fingerprint, creation time)
	- Is easier to predict than CUID2
	- Has weaker collision resistance
		[[CUID2]] fixes this by hashing all entropy sources, so IDs don’t reveal host or time and are harder to guess.
- Prisma already support CUID2

# Once happy with schema
### 5. Create the database and tables

`npx prisma migrate dev --name init`

### 6. Generate the client

`npx prisma generate`

### 7. Use the client in code
```ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

// Example: create a recipe

const recipe = await prisma.recipe.create({

  data: {

    title: 'Scrambled Eggs',

    ingredients: {

      create: [

        { name: 'egg', amount: 2, unit: null, order: 0 },

        { name: 'milk', amount: 0.25, unit: 'cup', order: 1 },

      ],

    },

    steps: {

      create: [

        { text: 'Whisk eggs and milk together.', order: 0 },

        { text: 'Cook in a nonstick pan over medium heat.', order: 1 },

      ],

    },

  },

  include: { ingredients: true, steps: true, tags: true },

})
```

# Here’s what that line does:

```
recipe   Recipe  @relation(fields: [recipeId], references: [id], onDelete: Cascade)
```




## Parts of the line

|Part|Meaning|
|---|---|
|recipe|Name of the relation field on this model (e.g. Ingredient or RecipeStep). Lets you do ingredient.recipe to get the parent Recipe.|
|Recipe|The model this relation points to.|
|fields: [recipeId]|The foreign key column on this model that stores the recipe’s ID.|
|references: [id]|The field on Recipe that recipeId refers to (the primary key).|
|onDelete: Cascade|When the referenced Recipe is deleted, also delete this record.|

## What it means in practice

This defines a one-to-many relation:

- One Recipe has many Ingredients (or RecipeSteps).

- Each Ingredient/RecipeStep belongs to one Recipe via recipeId.

onDelete: Cascade means: if you delete a recipe, all its ingredients and steps are deleted automatically.

## Is this what you want?

Yes, for a cookbook app this is usually what you want:

- Ingredients and steps are tied to a recipe.

- Deleting a recipe should remove its ingredients and steps.

- You can still load a recipe with its ingredients/steps via include.