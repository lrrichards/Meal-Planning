# Recipe Index

Browse all recipes. Filter by cooking method below.

---

## All Recipes

```dataview
TABLE method as "Method", servings as "Serves", prep_time as "Prep", cook_time as "Cook", tags as "Tags"
FROM "Meal Planning/Recipes"
WHERE file.name != "Recipe Index" AND file.name != "Ingredient Overlap" AND file.name != "CLAUDE.md" AND file.name != "READ ME" AND file.name != "Here is where to put recipes" AND title
SORT method ASC
```

---

## By Method

### Casserole
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Casserole"
WHERE title
SORT file.name ASC
```

### CrockPot
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/CrockPot"
WHERE title
SORT file.name ASC
```

### Normal
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Normal"
WHERE title
SORT file.name ASC
```

### One Pan
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/One Pan"
WHERE title
SORT file.name ASC
```

### One Pot
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/One Pot"
WHERE title
SORT file.name ASC
```

### Sheet Pan
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Sheet Pan"
WHERE title
SORT file.name ASC
```

### Air Fryer
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Air Fryer"
WHERE title
SORT file.name ASC
```

### Instant Pot
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Instant Pot"
WHERE title
SORT file.name ASC
```

### Microwave
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Microwave"
WHERE title
SORT file.name ASC
```

### Grill
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/Grill"
WHERE title
SORT file.name ASC
```

### No Cook
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook"
FROM "Meal Planning/Recipes/No Cook"
WHERE title
SORT file.name ASC
```

### Freezer Meals
```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook", tags as "Tags"
FROM "Meal Planning/Recipes/Freezer Meals"
WHERE title
SORT file.name ASC
```

---

## Desserts

```dataview
TABLE servings as "Serves", prep_time as "Prep", cook_time as "Cook", tags as "Tags"
FROM "Meal Planning/Recipes/Desserts"
WHERE title
SORT file.name ASC
```
