# Project Work Log

This file documents all changes made to this repository and their current state.
Claude Code or any AI agent should read this before doing any work in this repo.

---

## Session: June 2026

### 1. Personal Information Removal

**What was done:**
All recipe files and `CLAUDE.md` were scanned for personal information. A child's name ("Evan") and associated dietary notes ("Evan-safe (no tomatoes)" / "not Evan-safe") appeared in approximately 97 files. All references were removed.

- Personal name references: **fully removed**
- Tomato warnings that were useful were rewritten generically (e.g. "Contains tomatoes" instead of "not Evan-safe")
- `CLAUDE.md` was also cleaned

**Current state:** No personal names or family-identifying information exists anywhere in the repo.

---

### 2. Nutrition Reference File Created

**File:** `Nutrition Reference.md` (repo root)

**What it is:**
A master lookup table of every distinct ingredient used across all recipes — 269 ingredients total.

**Columns:** Ingredient · Unit · Calories · Protein (g) · Fat (g) · Carbs (g) · Fiber (g) · Sugar (g) · Sodium (mg) · Diets

**Unit conventions used:**
- Bulk ingredients (proteins, produce, dairy, beans, pasta, canned goods): **per 100g**
- Dry seasonings/spice blends (taco seasoning, garlic powder, ranch, etc.): **per 1 tsp**
- Liquid condiments and small-use items (soy sauce, olive oil, butter, honey, vinegars, mustard, tomato paste, etc.): **per 1 tbsp**
- Packet seasonings (au jus, etc.): **per 1 packet**

**Diet tags used:**
| Tag | Meaning |
|---|---|
| K | Keto |
| LC | Low-Carb |
| P | Paleo |
| W30 | Whole30 |
| VG | Vegetarian |
| VN | Vegan |
| GF | Gluten-Free |
| DF | Dairy-Free |

**Current state:** Complete. 269 ingredients with full nutrition and diet tags.

**Maintenance rule (IMPORTANT):** Any time a new recipe is added, every ingredient in its frontmatter `ingredients:` list must be checked against this file. If an ingredient is not present, add a new row in alphabetical order. See `CLAUDE.md` for detailed rules.

---

### 3. CLAUDE.md Updated

**What was added:**
- Full documentation of `Nutrition Reference.md` (purpose, unit conventions, diet tag key)
- Rules for keeping `Nutrition Reference.md` current when new recipes are added
- Step 4b inserted into the recipe-processing workflow: after writing a recipe note, check and update the nutrition reference
- Step 5 updated to include reporting new ingredients added to the reference

**Current state:** `CLAUDE.md` is the authoritative instruction file for this repo. It is complete and up to date as of this session.

---

### 4. Nutrition Facts Added to All Recipes

**What was done:**
A `## Nutrition (Estimated)` section was calculated and added to every recipe file. The section shows:
- Total for the entire recipe
- Per serving (based on the `servings:` frontmatter field)
- Columns: Calories, Protein, Fat, Carbs, Fiber, Sugar, Sodium

**How nutrition was calculated:**
- Ingredient quantities were parsed from the `## Ingredients` body section
- Quantities were converted to grams using standard unit conversions
- Per-100g nutrition values from `Nutrition Reference.md` were applied
- Values are estimates; actual nutrition varies by brand and preparation

**Scale:**
- 259 recipe files scanned
- **231 recipes** had complete enough ingredient lists to calculate automatically in the first pass
- **126 recipes** had vague or missing quantities (e.g. "Chicken thighs" with no amount, "Shredded cheese" with no quantity)

**Fixing vague quantities:**
The 126 recipes with missing quantities were fixed using standardized best-guess amounts:
- Proteins without amounts: e.g. "Chicken thighs" → "2 lb chicken thighs"
- Cheese toppings: e.g. "Shredded mozzarella cheese" → "1 cup shredded mozzarella cheese"
- Sour cream: → "½ cup sour cream"
- "White rice for serving" → "2 cups white rice"
- Cream cheese: → "4 oz cream cheese" (or 6 oz if recipe noted "most of an 8 oz block")
- Provolone/Swiss slices: → "4 oz"
- Bacon strips (to taste): → "6 slices bacon"
- "Leftover" or "remaining" ingredients: assigned standard standalone quantities
- Vague liquid condiments: assigned typical recipe amounts (e.g. soy sauce → "3 tbsp")

After fixing, nutrition was recalculated and added to all 126.

**Two recipes fixed manually:**
- `One Pan/Buttery Keto Pasta.md` — "Butter" had no amount; fixed to "2 tbsp butter". Also note: this is a very low-calorie side dish (~112 cal/serving) which is correct for shirataki noodles + butter.
- `Sheet Pan/Lemon Chicken.md` — "Chicken (breasts or thighs)" had no amount; fixed to "2 lb chicken thighs". The marinade oil was scaled from "~1 cup" down to "¼ cup" since most marinade oil is discarded and not consumed — a note was added to the recipe explaining this.

**Current state:** All 259 recipes have a `## Nutrition (Estimated)` section. Values are estimates.

**Important caveats for future agents:**
- Do NOT treat nutrition values as medically precise — they are estimates
- If a recipe is edited and ingredient quantities change, the nutrition section should be recalculated
- The nutrition section always ends with: *"Values are estimates based on standard ingredient amounts. Actual nutrition varies by brand and preparation."*
- When adding new recipes, calculate and add the nutrition section as part of the process (per `CLAUDE.md` Step 4b)

---

## Repository State Summary (as of this session)

| Item | Status |
|---|---|
| Personal information | Removed from all files |
| `Nutrition Reference.md` | Created — 269 ingredients, full nutrition + diet tags |
| `CLAUDE.md` | Updated with nutrition reference rules and workflow |
| Recipe nutrition sections | Added to all 259 recipes |
| Ingredient quantity standardization | Complete — all vague quantities filled in |

## File Structure Reminder

```
Meal-Planning/
├── CLAUDE.md                  ← AI instructions — READ THIS FIRST
├── Recipe Index.md            ← Dataview-generated — DO NOT EDIT MANUALLY
├── Ingredient Overlap.md      ← Dataview-generated — DO NOT EDIT MANUALLY
├── Nutrition Reference.md     ← Master ingredient nutrition lookup — KEEP CURRENT
├── PROJECT_LOG.md             ← This file
├── Air Fryer/
├── Casserole/
├── CrockPot/
├── Desserts/
├── Freezer Meals/
├── Grill/
├── Instant Pot/
├── Microwave/
├── No Cook/
├── Normal/
├── One Pan/
├── One Pot/
├── Sheet Pan/
└── Waffle Maker/
```

## Notes for Claude Code

- Always read `CLAUDE.md` before doing any work in this repo
- Never edit `Recipe Index.md` or `Ingredient Overlap.md` — they are Dataview-generated
- When adding new recipes, follow the full workflow in `CLAUDE.md` including updating `Nutrition Reference.md`
- Nutrition values use estimates — the parser used keyword matching on ingredient names, standard unit conversions, and USDA reference values
- Some recipes reference leftovers from other recipes (e.g. "Cooked shredded pork — see Slow Cooker Pulled Pork"). These were assigned standalone quantities for nutrition purposes.
- The GitHub token used in this session was a PAT with read/write access to `lrrichards/Meal-Planning`
