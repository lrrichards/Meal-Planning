# Ingredient Overlap

Ingredients used in **2 or more recipes** — sorted by how many recipes share them.

Use this to pick recipes that share ingredients and cut your grocery bill.

---

```dataviewjs
const pages = dv.pages('"Meal Planning/Recipes"')
  .where(p =>
    p.ingredients &&
    p.file.name !== "Recipe Index" &&
    p.file.name !== "Ingredient Overlap" &&
    p.file.name !== "CLAUDE.md" &&
    p.file.name !== "Here is where to put recipes"
  );

const map = {};

for (const page of pages) {
  const ings = Array.isArray(page.ingredients) ? page.ingredients : [page.ingredients];
  for (const ing of ings) {
    if (!ing) continue;
    const key = ing.toString().toLowerCase().trim();
    if (!map[key]) map[key] = { display: ing.toString().trim(), recipes: [] };
    map[key].recipes.push(page.file.link);
  }
}

const shared = Object.values(map)
  .filter(e => e.recipes.length >= 2)
  .sort((a, b) => b.recipes.length - a.recipes.length);

if (shared.length === 0) {
  dv.paragraph("No shared ingredients yet — add more recipes.");
} else {
  dv.table(
    ["Ingredient", "# Recipes", "Recipes"],
    shared.map(e => [e.display, e.recipes.length, e.recipes])
  );
}
```

---

## How to use this

1. Look for ingredients near the top (used most often).
2. Pick 2–3 recipes that share those ingredients.
3. Buy one bulk pack — it covers multiple meals.

**Example:** If chicken thighs appear in 4 recipes, plan those 4 meals in the same week and buy one large bag instead of four small ones.
