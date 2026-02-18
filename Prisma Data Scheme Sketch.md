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