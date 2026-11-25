---
title: Nutrition (food diary and macros)
summary: Macro rules, targets, calories opt-in, food diary layout, whole-food %, electrolytes, macro calculator, recipes
updated: 2026-11-25
sources: ["#981", CHANGELOG 2026-11-24, notes, CHANGELOG, "#355", "#356", "#335", "#666", "#858"]
---

# Nutrition

Shipped as major version 4.0. Included in the base membership; partner coaches get it at the same time.

## Macro rules

- Track and target **protein, fat and total carbs** only (total carbs for everyone; previously net carbs). No fiber,
  no alcohol.
- Targets are one number each: protein **≥**, fat **≤**, carbs **≤**, but the goal is to hit each one. Within 5% either
  way = on target; >5% below/above = below/above, shown in 508-compliant colors.
- **Calories off by default.** Client opts in under Settings; the coach can turn it on/off per client in the portal.
  Reports are macros in grams as eaten — never calories unless opted in, never macro ratios by calorie.
- When calories are on, macros set the calorie target. Want a different calorie target? Suggest a macro change (lower →
  reduce total carbs; higher → increase protein). Changed macros stay lightly colored with the +/− change shown to the
  left of the box; undo back to the last saved targets.
- Coach sets targets; the client edits only if allowed (Space settings default).
- Body weight lives only in [Biometrics](biometrics-and-signals.md).
- Nutrition achievements never reward under-eating; nothing awarded for weight loss.

## Food diary

- Date selector like Workouts; at least 7 days ahead. No meals: one list of food per day.
- Day ☰ menu: copy day to today (past days), copy, paste on another day.
- Search sits directly on the diary (no "+ Add food" page); results as you type. Tabs: Search · Frequent ·
  Favorites · Quick add; UPC scan icon top right. Favorites starred in results.
- Cronometer-style top summary with progress bars: Macros slide left/right to a **Hydration** window. Water entered at
  the bottom of the Food log, shown as a count; no water target.
- **Electrolytes**: sodium, potassium and magnesium in mg.
- ‹ Back from a food returns to the day on screen, however the day was changed (‹ ›, Today, the calendar, Copy day
  to today) (#666 fixed Nov 24 by #981; previously it could land on an earlier day and log the next food there).
- Food data: USDA and FatSecret APIs; 7-day search cache (revisit once usage is known).

## Whole-food %

- Unique to MetabolicHQ. Branded foods that are really one plain food (e.g. plain chicken legs) count as whole.
- Processed meats (bacon, sausage, deli meat, hot dogs) and cheese do **not** count.
- Quick adds have a Whole food checkbox and an optional Amount (g) box (amount needed to count).
- Coaches see a tag on foods a client marked whole themselves. The Whole foods search tab shows only whole foods.

## Macro calculator

Coach Bronson's Macro Calculator v3.0 (from Cognito Forms) is built into Nutrition → Targets and the portal (v4.2):
goal, body weight and body fat from Biometrics, activity level, total-carbs slider; protein ≥ lean mass (×1.25 to
gain), fat ≤ lean mass + activity (×0.75 for fat loss); warns under 70 g fat.

## Planned

Recipes (#356), recipe and history import from other nutrition apps (#355, medium), meal-photo AI logging (#335),
recipe grabber from an image (#357). Once recipes exist: license cookbook authors' recipes (#333; usage metric vs flat
fee undecided). Diet presets (keto, carnivore, low carb, high protein, balanced) that fill in starting macro
targets, still adjustable by hand (#858, medium). Oxalate add-on (#477): see [Client add-ons](client-add-ons.md).

## Known bugs

- None open in this area (#666 fixed Nov 24, above).

## Related

[Coaching methods](../business/coaching-methods.md) · [Biometrics and signals](biometrics-and-signals.md)
