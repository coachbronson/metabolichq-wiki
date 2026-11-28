---
title: My Daily Focus
summary: The client's daily page of goals, habits and the check-in; habit streaks and achievements; the coach's Goals & habits tab and habit report
updated: 2026-11-28
sources: ["#1174", "#1214", "#1215", CHANGELOG 2026-11-28, "v8.85.0", "v8.86.0", "v8.87.0"]
---

# My Daily Focus (#1174, done Nov 28)

The daily check-in page became **My Daily Focus**: goals, habits and the check-in on one page. Built in four parts,
all merged Nov 28 and on staging until promoted (#1174, done in PRs #1183, #1205, #1210 and #1213; "How this was
resolved"). "Goals are the outcome. Habits are the actions." (the Goals & habits screen, #1174).

## The client's page (v8.85.0)

- Opened from Home's card and its own menu item. Top to bottom: a progress ring (habits ticked today and questions
  answered), **Goals** (the ones picked to show, or the first 2) with **Reached**, **Habits** (picked ones, up to 5,
  or the first 4) ticked on every tap for today or any of the last 100 days, each with its streak, then **How you
  feel**: the space's check-in (default or custom, see [Biometrics and signals](biometrics-and-signals.md#check-ins)),
  one compact row per rating. Notes and the last 14 check-ins are a tap away (#1174, PR #1205).
- **Goals & habits** screen: up to 6 goals with an optional "by" date (a coach's goal is tagged Coach and locked),
  the Reached list, habits grouped (from your coach, your space's, your own, starter ideas), and ticks for what shows.
- Home's card is a summary: habits done today, the check-in's status, the first goal shown.
- Links, reminders and Getting started keep working (the page key is unchanged) (CHANGELOG 2026-11-28).

## His limits (#1174)

- 6 goals in all, at most 3 from coaches; reached goals don't count toward either.
- The client can't change or remove a coach's goal or habit.
- Up to 5 habits shown; habits are every day or 1–7 times a week.
- 9 starter habits, kept in code. The space's default habits are set by head coaches.
- Held in the security rules and again in the app with plain messages (PR #1183).

## Coaches (v8.86.0)

- Portal → Clients → the client → **Goals & habits** tab: the **habit report** (7/30/90-day completion counted from
  the day each habit was added, current and best streak, a 12-week calendar), the coaches' goals (up to 3) and
  habits, the client's own read only, and the Reached list with dates (PR #1210).
- Space settings' check-in card is now **My Daily Focus**, with **Default habits** (head coaches add and change;
  other coaches read).
- The coach data export gets `goals.csv`, `habits.csv` and `habit_days.csv` (PR #1183).

## Habit-streak achievements (v8.87.0)

- His rule: **habit streaks only**, nothing for reaching a goal, and nothing that rewards weight loss or eating less
  (#1174, PR #1213).
- One achievement per habit, named after it, under **Habits** on Achievements: daily habits at 7, 30 and 100 days in
  a row; weekly habits at 4 and 12 weeks in a row on target. Coaches see them on a client's Achievements.
- Not on the member card or the workout wrap-up shared to Community, because a habit's name is the client's own words.
- Open: should habits clients write themselves earn achievements (#1215, needs his decision)? The My Daily Focus
  how-to videos are re-made once it's on production (#1214).

## Related

[Biometrics and signals](biometrics-and-signals.md) · [Coach portal](coach-portal.md) ·
[Training](training.md) · [Help and how-to](help-and-howto.md)
