# Recipe Repository

## Overview

This repository contains a structured collection of recipes organized by cooking method.

The goal is to maintain a recipe database that is easy to browse, search, expand, and use for meal planning.

Recipes may be added manually or with the assistance of AI tools. To keep the collection useful, all recipes should follow the same structure and naming conventions.

---

## Folder Structure

Recipes are organized by their primary cooking method.

```text
Recipes/
├── Casserole/
├── CrockPot/
├── Normal/
├── One Pan/
├── One Pot/
├── Sheet Pan/
├── Air Fryer/
├── Instant Pot/
├── Microwave/
├── Grill/
├── Waffle Maker/
├── No Cook/
├── Desserts/
└── Freezer Meals/
```

Choose the folder based on the primary cooking method used to prepare the recipe.

Examples:

* Slow cooker recipes belong in `CrockPot`
* Single skillet recipes belong in `One Pan`
* Single pot recipes belong in `One Pot`
* Air fryer recipes belong in `Air Fryer`
* Desserts belong in `Desserts`
* Assemble-and-freeze meals belong in `Freezer Meals`

If a recipe could fit multiple categories, choose the folder that best defines how it is prepared.

---

## Recipe Format

Every recipe should begin with YAML frontmatter.

Example:

```yaml
---
title: Beef and Rice Skillet
method: One Pot
servings: 6
prep_time: 10 min
cook_time: 30 min
tags: [beef, lunch, dinner]
ingredients:
  - yellow onion
  - ground beef
  - beef broth
  - rotel
  - frozen broccoli
  - white rice
  - shredded Mexican cheese
---
```

After the frontmatter, recipes should contain the following sections:

```markdown
## Ingredients

Ingredient list with quantities.

## Instructions

Numbered cooking instructions.

## Notes

Optional tips, substitutions, storage information, or serving suggestions.
```

---

## Ingredient Naming Rules

Ingredient names in frontmatter should:

* Be lowercase
* Be consistent across recipes
* Use the same wording whenever possible

Examples:

```yaml
ingredients:
  - chicken thigh
  - black beans
  - yellow onion
```

Avoid creating multiple names for the same ingredient.

Good:

```yaml
black beans
black beans
black beans
```

Bad:

```yaml
black beans
canned black beans
black bean
```

Consistency allows ingredient overlap analysis and searching to work correctly.

---

## Tagging Rules

Every recipe should include at least one meal category tag:

* breakfast
* lunch
* dinner
* snack
* dessert

Recipes may have multiple meal tags if appropriate.

Examples:

```yaml
tags: [lunch, dinner]
```

```yaml
tags: [breakfast]
```

### Budget Tag

Use:

```yaml
extreme-budget
```

for recipes made primarily from inexpensive ingredients.

Do not use:

```yaml
budget
```

### Low Carb and Keto Tags

Use:

```yaml
low-carb
```

for generally low-carbohydrate recipes.

Use:

```yaml
keto
```

and

```yaml
low-carb
```

together for recipes that meet strict keto requirements.

---

## Naming Conventions

Recipe files should use the recipe title as the filename.

Examples:

```text
Beef and Rice Skillet.md
Slow Cooker Chili.md
Chicken Alfredo.md
```

Use descriptive names.

Avoid generic names such as:

```text
Recipe 1.md
Dinner.md
Food.md
```

---

## Contributions

Contributions are welcome.

Before adding a recipe:

1. Check whether a similar recipe already exists.
2. Follow the existing folder structure.
3. Use the standard frontmatter format.
4. Follow ingredient naming conventions.
5. Keep formatting consistent with existing recipes.

Corrections, improvements, and additional recipes are encouraged.

---

## AI Generated Content

Many recipes, descriptions, tags, notes, and supporting files may have been created or assisted by AI tools.

Always verify:

* Ingredient quantities
* Cooking times
* Cooking temperatures
* Nutritional information
* Food safety recommendations

before preparing any recipe.

---

## Additional Documentation

The repository also contains a `CLAUDE.md` file that includes the complete ruleset used by AI assistants when creating or modifying recipes. Human contributors may find it useful when making large additions or maintaining consistency across the repository.

---

## License

Unless otherwise specified, the contents of this repository may be used, modified, and shared freely.
