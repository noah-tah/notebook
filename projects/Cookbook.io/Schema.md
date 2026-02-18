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
- All Recipe objects have the following:
	- id
	- title
- Not ever recipe has:
	- description
	- servings
	- preTimeMinutes
	- totl
- [[CUID2]] is supported in Prisma 7
	- Secure, collision-resistant ids optimized for horizontal scaling and performance. Next generation UUIDs
