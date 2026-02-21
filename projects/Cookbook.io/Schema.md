Originally, I **planned on sketching out [[ERD]] diagrams manually in order to have something to present to an employer**, however, this is mostly a **waste of time** because I have to learn a new syntax in order to make it, and I can **just auto generate an up to date diagram directly from the Prisma schema** using `prisma generate`. Then I can write this in mermaid in my obsidian docs so that I can have a source of truth, and **it can be exported to PDF by default I** believe.
	Clarification: `prisma generate` by itself only creates the Prisma client, not diagrams. You need an extra generator such as `prisma-erd-generator`, which runs as part of `prisma generate` and can output Mermaid (and SVG/PNG/PDF).
	1. No extra diagram syntax – **You don’t need to learn Mermaid deeply**; the **generator produces it for you.**
Then there is a bit of complexity with the ERD generation as well because you want to have the mermaid output so that you can have reliable diagrams in your documentation. However, the images are much better at exporting into PDF and I read that mermaid is unreliable. It is important to me that my documentation looks as professional as possible so that I can look as good as possible for potential employers.
1. Install the full stack: `prisma-erd-generator`, `@mermaid-js/mermaid-cli`, and `puppeteer`.

# Recipe Data Model
---
```ts
model Recipe {

id String @id @default(cuid(2))

title String

description String?

servings Int?

prepTimeMinutes Int?

cookTimeMinutes Int?

totalTimeMinutes Int?

sourceUrl String?

sourceAuthor String?

images String[]

notes String[]

nutrition Json? // { calories?, protein?, carbs?, fat?, ... }

createdAt DateTime @default(now())

updatedAt DateTime @updatedAt

  

ingredients Ingredient[]

steps RecipeStep[]

tags RecipeTag[]

}
```

- [[CUID2]] is supported in Prisma 7
	- Secure, collision-resistant ids optimized for horizontal scaling and performance. Next generation UUIDs
- `images String[]`
	- Will this contain paths to the images?
- `ingredients Ingredient[]`
	- Every recipe has a list of ingredients
- `steps RecipeStep[]`
	- Every recipe has a series of steps
- `tags RecipeTag[]`
	- Every recipe has recipe tags