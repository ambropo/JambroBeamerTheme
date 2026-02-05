# AI Agent Instructions — JAMBRO Beamer Theme Maintenance

## 0) Mission (non-negotiable deliverables)

Your job is to maintain a small, disciplined “theme repo” with three always-up-to-date artifacts:

1. **`beamerthemejambro.sty`**

   * Clean, logically ordered, well commented.
   * Compiles without errors/warnings that are *caused by the theme* (document-specific warnings are acceptable, but flag them).
   * Backwards compatible unless explicitly instructed otherwise.

2. **`ChangeLog.md`**

   * Lists **all changes since the previous Git commit** (not “since last time you looked”).
   * Clear, concrete, and searchable.

3. **`Demo.tex`**

   * A minimal but comprehensive demo that **exercises every user-facing feature** of the `.sty`.
   * Compiles cleanly and showcases the theme’s intended look.

**Definition of done:** all three compile / render correctly together, and the changelog matches the diff against the previous commit.

---

## 1) Working principles

### 1.1 Don’t bluff

* **Never claim something works unless you compiled `demo.tex` successfully.**
* If you cannot test (e.g., missing TeX packages), say so explicitly and provide the best safe alternative (e.g., reduced test + what remains unverified).

### 1.2 Minimal, safe edits

* Prefer **small, local changes**.
* Avoid reformatting unrelated sections.
* No “drive-by” style changes unless they fix a real problem.

### 1.3 Backwards compatibility

* If a change could break existing slides:

  * Provide a compatibility shim where feasible, or
  * Gate it behind an option toggle, or
  * Very clearly document it as **BREAKING** in `ChangeLog.md`.

### 1.4 Commenting standard

* Comments should explain **why** (intent, constraints, tradeoffs), not narrate **what** LaTeX already says.
* Use short section headers and consistent comment style.

---

## 2) Repository workflow (always follow)

### Step A — Start from Git truth

* Identify the **previous Git commit** as the baseline.
* Your changelog must correspond to `git diff <previous-commit>..HEAD` (or staged diff if preparing a commit).

### Step B — Make the change

* Update `beamerthemejambro.sty`.
* Update/extend `demo.tex` so the modified feature is exercised.
* Update `ChangeLog.md` with an entry that matches the actual diff.

### Step C — Test

Run at least:

* `latexmk -pdf -interaction=nonstopmode demo.tex`
  (or an equivalent compile command)

Record outcomes:

* If errors: fix and recompile.
* If warnings: decide if theme-caused; if yes, fix or document.

### Step D — Consistency check

* Ensure every new/changed user-facing command, color, environment, template, or option:

  * is documented in comments in `.sty`,
  * appears in `demo.tex`,
  * is described in `ChangeLog.md`.

---

## 3) `beamerthemejambro.sty` structure rules

### 3.1 Ordering (keep stable)

Organize the file into predictable blocks (use clear section headers):

1. **Preamble / guards**

   * `\ProvidesPackage`, required packages, version string if any.
2. **Options**

   * `\DeclareOption` / `\ProcessOptions`.
3. **Core theme settings**

   * Beamer font/theme/color settings.
4. **Colors**

   * Centralize color definitions in one place.
5. **Fonts & typography**
6. **Layout**

   * margins, headline/footline, title page, section pages.
7. **Blocks, theorem styles, itemize/enumerate**
8. **Macros (user-facing)**

   * Clearly mark “public API” vs internal helpers.
9. **Compatibility shims / deprecated items**
10. **End of file sanity**

* Any final defaults.

Do not scatter related settings across the file.

### 3.2 Public API discipline

* Treat any command/environment intended for slide authors as **public API**.
* For each public API item:

  * Provide a one-line doc comment.
  * Add a `demo.tex` example.

### 3.3 Naming conventions

* Internal helpers: prefix consistently (e.g., `\jambro@...`).
* Public commands: consistent, readable naming; avoid cryptic abbreviations.

### 3.4 Avoid fragile hacks

* Prefer Beamer-supported hooks/templates over low-level patching.
* If patching is necessary, comment:

  * what is being patched,
  * why it is necessary,
  * what could break.

---

## 4) `demo.tex` requirements (feature coverage checklist)

`demo.tex` is not a “pretty slide deck”; it’s a **test harness**.
**Rule:** If it’s in `.sty` and user-facing, it must appear in `demo.tex`.

---

## 5) `ChangeLog.md` rules (must match Git diff)

### 5.1 Format (simple and consistent)

Use one entry per “work session” (or per commit if you prefer). Template:

* **Date (YYYY-MM-DD)** — short title

  * **Added:** …
  * **Changed:** …
  * **Fixed:** …
  * **Deprecated:** …
  * **Removed:** …
  * **BREAKING:** …

### 5.2 Content rules

* Be concrete: reference filenames and features.
* If behavior changed: describe *before → after*.
* If a change required updating `demo.tex`, mention it.
* If you fixed a bug: include the symptom and the cause (briefly).


---

## 6) Quality gates before you say “done”

You may only mark the work complete if all are true:

* `demo.tex` compiles successfully.
* The theme compiles without introducing errors.
* `demo.tex` demonstrates every public feature.
* `ChangeLog.md` accurately reflects the actual diff vs previous commit.
* Comments in `.sty` are updated where behavior changed.

---

## 7) What to do when something is unclear

* Don’t guess user intent.
* Implement the safest default (backwards compatible).
* Document assumptions in comments + changelog.
* If a design choice is ambiguous, provide **two options**:

  * default (safe),
  * alternative (behind an option toggle), with clear instructions.

---

## 8) Communication style in outputs

* Dry, precise, minimal fluff.
* When reporting changes, prefer:

  * “I changed X to Y because Z; demo shows it on slide N.”
* If something is unverified, state it plainly.