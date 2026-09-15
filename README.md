# Midterm Practical Exam - HAUDEX

This is your **midterm exam**. You are given a mostly-working **HAUDEX** app: a
Flutter mobile app with a home screen (a stats card over a list of monsters) and
a detail screen. It has five **bugs** and two **TODOs**. Fix them so every panel
and screen shows the correct value, then answer the **Canvas exam** with the
values your fixed app shows. That is your grade; you do not submit this repo.

## Rules (read first)

- **Closed book. One hour. One sitting.** Open only: this repo, VS Code, and a
  terminal. **No AI assistants, no web search, no messaging.**
- Everything you need is in Modules 4 and 5.
- Your answers go in the **Canvas exam**, not here.

## Setup and run

The 200 monsters are generated in memory (the same every run), so there is
nothing to install beyond the packages.

```bash
flutter pub get
```

On your own laptop:

```bash
flutter run                 # pick an emulator, a device, or Chrome
```

In a Codespace (no browser inside the container):

```bash
flutter run -d web-server --web-port=8080 --web-hostname=0.0.0.0
```

Codespaces forwards port 8080 - open it from the pop-up or the **Ports** tab.
Press `R` to hot restart after an edit.

Prefer the terminal? `dart run tool/report.dart` prints the five stats-card
values as text (the filter count, the list and the detail screen are read off
the running app).

## What to fix

Five bugs, marked in the code with `BUG A` ... `BUG E`, plus two `TODO`s:

- **lib/stats.dart (Module 5 - lists and logic):**
  - BUG A - "Most common type" is showing the **least** common one.
  - BUG B - "High HP" should count HP **strictly greater than** 70.
  - BUG C - "Top region" groups by the wrong field, so it shows an **element**
    name instead of a region.
  - **TODO 2** - finish `strongest()` so it returns the monster with the
    highest HP (right now the "Strongest" panel is wrong).
- **lib/home_screen.dart (Module 4 + 5 - state and lists):**
  - BUG D - the type filter updates a field but never calls `setState`, so the
    list and the "Showing N" count never change.
  - BUG E - every row in the list shows the **same** monster (the builder reads
    index `0` instead of the row's `index`).
  - **TODO 1** - tapping a tile does nothing. Open `DetailScreen` for that
    monster (import `detail_screen.dart`, then `Navigator.push` a
    `MaterialPageRoute`), **and** add the missing **Type**, **Element** and
    **Attack** rows in `lib/detail_screen.dart`.

When every stats panel shows a sensible value, the filter updates the list, each
row shows a different monster, and tapping a monster opens its full detail, you
have fixed everything. Read your answers off the app (or `dart run
tool/report.dart` for the stats card) and enter them in Canvas.

## No laptop? Fix it in the browser

You do not have to run anything locally. You can edit the files right on
github.com (open a file, click the pencil, commit), and every push runs your app
for you on GitHub. Open the run under the **Actions** tab and its **summary**
shows two things: a self-check of whether each bug and TODO is fixed, and **your
current answers to the 10 quiz questions**. It also saves a screenshot of your
app as the **app-screenshot** artifact.

This check does **not** grade you: your grade is the Canvas quiz. It only tells
you how far you have got. Read your answers from the run summary (or, if you can
run it, `dart run tool/report.dart` plus the app) and enter them in Canvas.

## The data

One list of **200 monsters** in `lib/data.dart`, each with a name, type,
element, HP, attack and region. Do not edit `lib/data.dart`. Good luck.
