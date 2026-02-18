Originally, I planned on sketching out ERD diagrams manually in order to have something to present to an employer, however, this is mostly a waste of time because I have to learn a new syntax in order to make it, and I can just autogenerate an up to date diagram directly from the Prisma schema using `prisma generate`. Then I can write this in mermaid in my obsidian docs so that I can have a source of truth, and it can be exported 

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
