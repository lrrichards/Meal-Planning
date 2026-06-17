# Recipes — Agent Context

## What This Folder Is
Individual recipe notes, plus index and reference files for browsing, ingredient analysis, and nutrition tracking.

## Folder Structure

```
Recipes/
├── CLAUDE.md              ← You are here
├── Recipe Index.md        ← Dataview table of all recipes, grouped by cooking method
├── Ingredient Overlap.md  ← DataviewJS: shows ingredients shared across 2+ recipes
├── Nutrition Reference.md ← Per-ingredient nutrition facts and diet compatibility (see below)
├── Casserole/             ← Recipes baked in a casserole dish
│   └── READ ME.md
├── CrockPot/              ← Slow cooker recipes
│   └── READ ME.md
├── Normal/                ← Standard stovetop or oven recipes
│   └── READ ME.md
├── One Pan/               ← Everything cooked in one skillet/frying pan
│   └── READ ME.md
├── One Pot/               ← Everything cooked in one deep pot or Dutch oven
│   └── READ ME.md
├── Sheet Pan/             ← Oven recipes on a sheet pan
│   └── READ ME.md
├── Air Fryer/             ← Air fryer recipes
│   └── READ ME.md
├── Instant Pot/           ← Pressure cooker recipes
│   └── READ ME.md
├── Microwave/             ← Microwave recipes
│   └── READ ME.md
├── Grill/                 ← Grill/BBQ recipes
│   └── READ ME.md
├── Waffle Maker/          ← Anything cooked in a waffle maker (chaffles, chaffle bread)
│   └── READ ME.md
├── No Cook/               ← No heat required — salads, wraps, sandwiches
│   └── READ ME.md
├── Desserts/              ← Dessert recipes (any method, any ingredient count)
│   └── READ ME.md
└── Freezer Meals/         ← ALL assemble-and-freeze meals: slow cooker bags, freezer casseroles,
    └── READ ME.md            one-pot simmer bags, sheet pan bags, freezer burritos, microwave trays.
                              Definition broadened 2026-06-09 (was slow-cooker-only). Cook equipment
                              goes in tags (crockpot, casserole, one-pot, sheet-pan, microwave, air-fryer).
```

## Nutrition Reference.md

`Nutrition Reference.md` is a master lookup table of every distinct ingredient used across all recipes. It exists so that recipe nutrition can be calculated without re-researching common ingredients each time.

### What it contains
Each row has: **Ingredient · Unit · Calories · Protein · Fat · Carbs · Fiber · Sugar · Sodium · Diets**

### Unit conventions
- **Bulk ingredients** (proteins, produce, dairy, beans, pasta, canned goods, sauces used in quantity): **per 100g**
- **Seasonings, spice blends, dry mixes** (taco seasoning, garlic powder, ranch, etc.): **per 1 tsp**
- **Liquid condiments and small-use items** (soy sauce, olive oil, butter, honey, vinegars, mustard, tomato paste, etc.): **per 1 tbsp**
- **Packet seasonings** (au jus, onion soup mix used as a packet): **per 1 packet**

### Diet tag key
| Tag | Meaning |
|---|---|
| K | Keto (very low net carbs — no grains, beans, sugar, starchy veg) |
| LC | Low-Carb (broadly reduced carbs, less strict than keto) |
| P | Paleo (no grains, legumes, dairy, or refined sugar) |
| W30 | Whole30 (no grains, legumes, dairy, added sugar, or processed food) |
| VG | Vegetarian (no meat, poultry, or seafood) |
| VN | Vegan (no animal products) |
| GF | Gluten-Free |
| DF | Dairy-Free |

### Rules for updating Nutrition Reference.md
**Whenever a new recipe is added, check every ingredient in its frontmatter `ingredients:` list against Nutrition Reference.md. For any ingredient not already present:**

1. Determine the correct unit (see Unit conventions above)
2. Look up nutrition values (USDA FoodData Central or typical product average for branded items)
3. Determine which diet tags apply using the diet definitions above
4. Add a new row to Nutrition Reference.md in alphabetical order
5. Use the same ingredient name format as the frontmatter (lowercase, singular)

**Do NOT add duplicate rows.** Before adding, scan the file for the ingredient — near-duplicates like "frozen broccoli" and "broccoli" consolidate to one entry ("broccoli"). Apply the same consolidation logic used throughout the file (fresh/frozen/canned variants of the same vegetable = one row; different cuts of the same meat = one row per cut if nutritionally distinct).

**Do NOT edit existing rows** unless correcting a clear error. Existing values are already established baselines.

---

## Recipe Note Format

Each recipe uses this frontmatter:

```yaml
---
title: Recipe Name
method: crockpot
servings: 6
prep_time: 15 min
cook_time: 6 hr
tags: [chicken, extreme-budget]
ingredients:
  - chicken thighs
  - onion
  - garlic
---
```

### Tagging conventions
- **Do NOT echo the method in tags.** The `method:` field already stores it; a `crockpot`/`one-pot`/`casserole` tag is redundant and was removed vault-wide on 2026-05-29. Do not add `oven` or `stovetop` tags either — the method implies the equipment.
- **Budget:** the only budget tag is `extreme-budget`. Do not use a bare `budget` tag.
- **Meal type:** every recipe gets at least one of `breakfast`, `lunch`, `dinner`, `dessert`, `snack`. Tag ALL slots a dish genuinely fits (multiple allowed): hearty mains = `dinner`; soups, sandwiches, salads, bowls, quesadillas, burritos and other portable/reheatable dishes = `lunch` + `dinner`; egg/hash dishes = `breakfast`; bread sides with no real meal slot = `snack`. Applied vault-wide 2026-06-05.
- **Diet (keto):** two tags, applied by carb load, not recipe name. `keto` = strict keto only (very low net carbs, high fat — no bread, rice, pasta, beans, sugar, starchy veg). `low-carb` = reasonably low-carb but not strict keto. A strict recipe gets BOTH `keto` and `low-carb`; a loose one gets only `low-carb`. These are diet tags, never folders — keto recipes stay in their cooking-method folder.
- **Plurals:** use `eggs` (not `egg`) and `lentil` (singular) as tags.
- **Protein:** `beef` and `turkey` are treated as interchangeable (ground beef/turkey swap freely) — don't "correct" one to the other.
- Exception: on Freezer Meals, keep the equipment tag (`crockpot`, `casserole`, `one-pot`, `sheet-pan`, `microwave`, `air-fryer`) — it describes how the meal is cooked/reheated after freezing, not the recipe's `method` (`Freezer Meal`). Extended from crockpot-only on 2026-06-09 when the folder definition broadened.

### Valid `method` values
| Value | Meaning |
|---|---|
| `crockpot` | Slow cooker |
| `instant-pot` | Pressure cooker |
| `single-pan` | One skillet/pan on stovetop |
| `sheet-pan` | Oven, everything on one sheet |
| `casserole` | Oven, baking dish |
| `stovetop` | Stovetop (pot or multiple pans) |
| `oven` | Oven (doesn't fit sheet-pan or casserole) |
| `air-fryer` | Air fryer |
| `waffle-maker` | Waffle maker (chaffles, chaffle bread) |
| `grill` | Grill |
| `no-cook` | No heat required |

### Ingredient naming rules
- Use lowercase, singular form: `chicken thigh` not `Chicken Thighs`
- Be consistent — `black beans` in every recipe, not `black beans` in one and `canned black beans` in another
- The Ingredient Overlap note matches on exact string — inconsistent names break the grouping

## Template
Use `Templates/Recipe Template.md` as the starting point for every new recipe.

## Processing Recipes from Transcripts

When the user pastes a YouTube transcript or any other recipe source, follow these rules exactly.

### Step 1 — Identify recipes
- Pull out every distinct recipe in the transcript.
- Note the recipe name as stated in the video/source.
- Skip anything that is not a meal or dessert (intros, stories, product plugs, etc.).

### Step 1b — Check for duplicates (do this before writing anything)
- The user does not track what they've already submitted, so always check existing recipes first to avoid duplicates.
- Compare each candidate against the existing library by **main protein + cooking method + core dish**, not just the exact title. List existing files (`find Recipes -name '*.md'`) and scan titles/ingredients.
- If it's a clear duplicate, **skip it** and tell the user you skipped it and why.
- If it's a meaningful variation (different method, notably different ingredients), **flag it and ask** before adding rather than silently creating a near-dupe.
- Note: a couple of legitimate same-name pairs already exist (e.g. `Honey Garlic Chicken` in both One Pan and Freezer Meals) — different method makes them distinct.

### Step 2 — Determine the folder
Use the primary cooking equipment to pick the folder:

| If the recipe uses... | Put it in... |
|---|---|
| A slow cooker / CrockPot | `CrockPot/` |
| An Instant Pot / pressure cooker | `Instant Pot/` |
| One skillet or frying pan for everything | `One Pan/` |
| One deep pot or Dutch oven for everything | `One Pot/` |
| A sheet pan in the oven | `Sheet Pan/` |
| A casserole dish in the oven | `Casserole/` |
| An air fryer | `Air Fryer/` |
| A waffle maker (chaffles, chaffle bread) | `Waffle Maker/` |
| A microwave | `Microwave/` |
| A grill or BBQ | `Grill/` |
| No heat at all | `No Cook/` |
| Multiple vessels or oven with no specific dish | `Normal/` |
| It is a dessert (any method) | `Desserts/` |
| It is assembled ahead and frozen, then cooked or reheated from frozen (any equipment) | `Freezer Meals/` |

If a recipe could fit two folders, pick the one that defines it most. Example: a pasta dish cooked in one pan goes in `One Pan/`, not `Normal/`.

### Step 3 — Count ingredients
- Do NOT count these as ingredients: salt, pepper, any dry seasoning/spice blend, oil, butter, garlic, water.
- Count everything else — broth, cream, cheese, canned goods, fresh produce, proteins, pasta, etc.
- Note the ingredient count in the tags (e.g. `5-ingredients`).

### Step 3b — Evaluate for extreme-budget tag
Add the tag `extreme-budget` to any recipe where the ingredients are very cheap and the meal is something people would make when money is tight. Judge based on ingredients only — not the recipe name.

**Tag it if:**
- Primary protein is a cheap cut (chicken thighs, ground beef, ground turkey, pork chops, ham, eggs, canned tuna, beans)
- Bulk of the meal is pantry staples (rice, pasta, dried beans, canned goods, frozen vegetables)
- Estimated cost is roughly $1–3 per serving
- No expensive ingredients (no fresh seafood, no premium cuts, no large amounts of heavy cream or specialty cheese as a main component)

**Do not tag it if:**
- It uses avocado, deli meats in large quantities, sun-dried tomatoes, or other pricier ingredients as a core component
- The dish relies heavily on heavy cream, large amounts of specialty cheese, or fresh herbs as main ingredients

Apply this tag to ALL recipes — not just new ones from transcripts. If an existing recipe qualifies, add the tag.

### Step 4 — Write the recipe note
- File name = recipe title, Title Case, no special characters.
- Use the frontmatter format shown above.
- `method` value must match the folder name exactly (e.g. folder `One Pan/` → `method: One Pan`).
- Ingredients in frontmatter: lowercase singular form, one per line.
- Body sections: **Ingredients** (with quantities), **Instructions** (numbered steps), **Notes** (tips, substitutions, serving ideas from the source).
- **Source link:** if the user provides a video/source URL, add a `## Source` section as the very last section of the note with a clickable markdown link: `[Watch on YouTube](URL)`. Only add it when a link is given (older notes won't have one). Use the platform name in the link text (YouTube, etc.).
- Extract quantities and steps from the transcript as accurately as possible.
- If the transcript skips a detail, make a reasonable note rather than guessing silently.
- **Filled-in amounts:** when a source never states an amount/time, fill in a sensible default but flag it in the recipe's Notes under a bold line: `**Filled in by Claude (not stated in video):** ...` (one line listing what was assumed and why). If nothing was assumed, write `No filled-in amounts — video stated everything.` This lets the user spot and adjust guesses after cooking. Convention started 2026-06-09; the per-recipe flags are the source of truth, with a session-level registry in `Meal Planning/CLAUDE.md`.

### Step 4b — Update Nutrition Reference.md
After writing the recipe note, check each ingredient in the frontmatter `ingredients:` list against `Nutrition Reference.md`. For any ingredient not already in the file, add a new row following the rules in the **Nutrition Reference.md** section above.

### Step 5 — After all recipes are created
- Report back: list each recipe, which folder it went in, the ingredient count, and any new ingredients added to Nutrition Reference.md.
- Do NOT update Recipe Index.md or Ingredient Overlap.md — Dataview handles those automatically.
- Update this CLAUDE.md only if a new folder was added.

## Notes for Claude
- Never edit Recipe Index.md or Ingredient Overlap.md manually — they are Dataview-generated
- Ingredient consistency across all recipes is critical — the Ingredient Overlap tool matches on exact string
- If a new cooking method comes up that has no folder, ask the user before creating one
- Update this CLAUDE.md if new folders or method values are added
- Always keep Nutrition Reference.md current — every new ingredient that appears in a recipe frontmatter must have a row in that file
