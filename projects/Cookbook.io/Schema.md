Originally, I **planned on sketching out [[ERD]] diagrams manually in order to have something to present to an employer**, however, this is mostly a **waste of time** because I have to learn a new syntax in order to make it, and I can **just auto generate an up to date diagram directly from the Prisma schema** using `prisma generate`. Then I can write this in mermaid in my obsidian docs so that I can have a source of truth, and **it can be exported to PDF by default I** believe.
	Clarification: `prisma generate` by itself only creates the Prisma client, not diagrams. You need an extra generator such as `prisma-erd-generator`, which runs as part of `prisma generate` and can output Mermaid (and SVG/PNG/PDF).
	1. No extra diagram syntax – **You don’t need to learn Mermaid deeply**; the **generator produces it for you.**
Then there is a bit of complexity with the ERD generation as well because 

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
