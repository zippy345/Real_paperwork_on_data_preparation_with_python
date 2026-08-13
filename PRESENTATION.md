# Data Preparation with Python — 10-Slide Talk (50 minutes)

> Source material: `README.md` in this repo. Audience: mixed room — curious newcomers, junior analysts, mid-level practitioners, and senior/professional data people all in the same seats. Format below is built so every rank finds their level: plain definition first, real stakes second, technical depth layered in after trust is earned.

---

## How to use this document

Each slide block below gives you four things:
- **On the slide** — the actual text/visual, kept to the 6×6 rule (max ~6 bullets, ~6 words each). This is what the audience reads.
- **You say** — what you say out loud, which is *always* more than what's on the slide. Slides are a skeleton; your voice is the content.
- **Visual** — what to show instead of, or alongside, text (pull directly from README diagrams/tables).
- **Time** — running budget across 50 minutes, including a 5-minute Q&A buffer at the end.

**One rule governs the whole deck:** never read your slide to the audience. The slide is what they see; your talk is what they hear. If the two are identical, cut the talk or cut the slide.

**Timing map (50 min total):**

| Slide | Topic | Minutes | Running total |
|---:|---|---:|---:|
| 1 | Hook + title | 2 | 2 |
| 2 | What is data preparation? (plain) | 5 | 7 |
| 3 | Why it matters (the cost of getting it wrong) | 6 | 13 |
| 4 | A short history — who built this discipline | 5 | 18 |
| 5 | Where preparation lives: the CRISP-DM lifecycle | 5 | 23 |
| 6 | The preparation workflow, step by step | 6 | 29 |
| 7 | Real-world cases across industries | 6 | 35 |
| 8 | Why Python + the modern tool landscape | 6 | 41 |
| 9 | Quality, governance, and getting it production-ready | 5 | 46 |
| 10 | Takeaways + call to action | 3 | 49 |
| — | Q&A buffer | 1–5 | 50–54 |

---

## Slide 1 — Title & Hook

**On the slide**
```
Real-World Data Preparation with Python
[Your name, title, date]

"The result was mathematically correct —
 and completely wrong."
```

**You say:** Open with a 30-second real (or realistic) story where a number was technically accurate but operationally false — a duplicated customer, a currency mix-up, a "zero" that actually meant "no data." Do not explain the mechanism yet — just plant the tension. Promise: "By the end of this talk you'll know exactly why that happens, and what a professional does to prevent it."

**Visual:** Full-bleed title slide, one punchy quote, your credentials in small type. No bullets, no logo clutter.

**Time:** 2 min

---

## Slide 2 — What Is Data Preparation? (Plain Definition)

**On the slide**
```
Data = recorded facts, not the truth itself
Data Preparation = getting data ready
  for a DIFFERENT purpose than it was
  collected for

🥕 Think: washing & cutting vegetables
   before you can cook the meal
```

**You say:** Walk through the README's kitchen analogy in your own words — raw ingredients arrive dirty and irregular; someone must wash, sort, and cut before cooking starts. Define, out loud, in one sentence each: raw data, clean data, tidy data, missing data, duplicate, outlier, grain. Do this fast and conversationally — this slide is the floor everyone stands on for the rest of the talk, especially your newcomers.

**Visual:** Simple two-panel image or icon pair: "raw ingredients" → "prepped ingredients," relabeled "raw data" → "analysis-ready data."

**Time:** 5 min

---

## Slide 3 — Why It Matters: The Cost of Getting It Wrong

**On the slide**
```
Bad prep doesn't crash the program.
It quietly produces the WRONG answer.

• Duplicate orders → revenue counted twice
• Missing coded as 0 → biased model
• Future data leaks in → fake accuracy
• Names as ID → wrong people merged
```

**You say:** Pick 3–4 rows from the README's "chain from defect to consequence" table and narrate each as a mini-story with a real consequence (money lost, unsafe clinical decision, unfair automated decision). Land on the line: "There is usually no error message. The number just looks fine and is false." This is the slide that convinces skeptical seniors this is a real discipline, not busywork.

**Visual:** The defect → consequence table, trimmed to 4 rows max, large font, color-highlight the "consequence" column.

**Time:** 6 min

---

## Slide 4 — A Short History: Who Built This Discipline

**On the slide**
```
1662  John Graunt      — first structured
                          public-health tables
1854  Nightingale/Farr — data that changed policy
1970  Edgar Codd       — the relational model
1991  Guido van Rossum — Python is born
2008  Wes McKinney     — pandas: DataFrames
1999  CRISP-DM         — the industry lifecycle
```

**You say:** Tell it as a story, not a list — humans have always needed to trust records (censuses, ledgers, mortality tables) before they could act on them. Spend the most breath on Graunt (turned messy death records into the first real demographic tables) and McKinney (why pandas mattered for everyone in the room today). This slide earns credibility with technical audience members and gives newcomers a narrative anchor instead of dry facts.

**Visual:** Horizontal timeline graphic, 6 dots, names and years only — details live in your voice, not the slide.

**Time:** 5 min

---

## Slide 5 — Where Preparation Lives: CRISP-DM

**On the slide**
```
CRISP-DM: Cross-Industry Standard
Process for Data Mining

Business → Data → PREPARATION → Model
Understanding Understanding  ↑↓      → Evaluate → Deploy
                    (loops back constantly)
```

**You say:** Explain CRISP-DM is not a straight line — it's a loop, and preparation is usually where teams spend the most real effort, even though it gets the least glamour. Say plainly: modeling is 20% of the work and 80% of the conference talks; preparation is the reverse. Mention SEMMA/TDSP/KDD exist too, but you're standardizing on CRISP-DM for this talk because it's the most widely recognized.

**Visual:** Reproduce the README's CRISP-DM mermaid flowchart — six boxes in a loop, preparation box highlighted in a contrasting color.

**Time:** 5 min

---

## Slide 6 — The Preparation Workflow, Step by Step

**On the slide**
```
1. Define purpose & who "one row" means
2. Inventory & acquire sources
3. Keep a raw, untouched copy
4. Profile before you fix anything
5. Write rules BEFORE irreversible edits
6. Clean → integrate → reshape
7. Validate at every boundary
8. Publish with documentation, not just files
```

**You say:** Walk this as a repeatable checklist, not trivia — this is the part your intermediate/professional audience will photograph. Emphasize two non-negotiables: (a) never overwrite raw data — it's your evidence; (b) profile before you touch anything, because you cannot fix what you haven't measured. Use one 20-second concrete example (e.g., the retail demand case from the README) to make it real.

**Visual:** The README's preparation-workflow mermaid diagram, simplified to remove the "acceptance criteria" loop-back detail if space is tight — keep the loop arrow, it's the whole point.

**Time:** 6 min

---

## Slide 7 — Real-World Cases Across Industries

**On the slide**
```
Banking      → point-in-time credit snapshots
Retail       → is "0 sales" really 0, or out of stock?
Healthcare   → missing ≠ zero; identity errors harm people
Telecom      → don't call customers who already churned
Public health→ wrong denominator = wrong policy
```

**You say:** Pick 4–5 industries from the README's industry table that best match who's in the room (ask before the talk, or read the room). For each, state the raw mess, the one critical fix, and the failure if skipped — in one breath each. This is the slide where junior/intermediate audience members go "oh, this is literally my job."

**Visual:** 5-row table, three columns only: Industry / Sneaky problem / What breaks if ignored. No more than 5 rows — resist pulling all 17 from the README.

**Time:** 6 min

---

## Slide 8 — Why Python, and the Tools Around It

**On the slide**
```
Why Python:
✓ One language: ingest → clean → model → ship
✓ pandas / Polars / DuckDB for real scale
✓ Readable — domain experts can review it

The stack:
NumPy → pandas/Polars → scikit-learn
SQL/dbt → Airflow/Dagster → Great Expectations
```

**You say:** Be honest and balanced here — say Python isn't "best" at everything (SQL wins for set-based warehouse work, R still strong in statistics) but wins on breadth: one language covers the entire lifecycle from a Jupyter notebook to a production pipeline. Name-drop the tool categories fast (ingestion, storage, orchestration, validation) so professionals in the room clock that you know the real landscape, without turning this into a tool-by-tool lecture.

**Visual:** Simple layered stack diagram — Storage → Processing (pandas/Polars/Spark) → Validation (Pandera/Great Expectations) → Orchestration (Airflow/Dagster) → Delivery.

**Time:** 6 min

---

## Slide 9 — Quality, Governance, and Production-Readiness

**On the slide**
```
"Clean" isn't a feeling — it's testable.

  customer_id is never null
  status in [active, suspended, closed]
  freshness ≤ 26 hours

+ Privacy: minimize, secure, document
+ Bias: audit BEFORE modeling, not after
```

**You say:** Show that professional data prep is executable, not vibes — a rule either passes or fails, same as a unit test. Pivot to governance in one clear beat: preparation decisions touch real people, so privacy minimization and bias auditing aren't side topics, they're part of the job. This is the slide senior/professional attendees use to judge whether you actually operate at production maturity.

**Visual:** The README's YAML data-contract snippet, trimmed to 4–5 lines, shown as a code block with syntax highlighting.

**Time:** 5 min

---

## Slide 10 — Takeaways & Call to Action

**On the slide**
```
1. Raw data is not the truth — it's a recording.
2. "Clean" is contextual: fit for THIS purpose.
3. Prep is where most real effort — and risk — lives.
4. Test it. Document it. Never overwrite raw.

→ Explore the repo. Start with one messy file.
```

**You say:** Return to your opening story from Slide 1 and resolve it — name exactly which of these four principles would have caught it. Close with a direct, low-friction ask: point them to the repo, and suggest the smallest possible first action (e.g., "pick one spreadsheet you already distrust and profile it this week"). End on time — a talk that finishes early to a silent room beats one that runs over into people packing bags.

**Visual:** Four-point recap, large type, plus a QR code or short link to the repository.

**Time:** 3 min, then open the floor.

---

## Delivery notes (for you, not the slides)

- **6×6 rule:** no slide should carry more than ~6 lines of ~6 words. If you need more text, it belongs in your mouth, not the screen.
- **One idea per slide.** Every slide above has exactly one job. If you catch yourself defending two ideas on one slide, split it — but you only have 10, so cut ruthlessly from the README rather than cramming.
- **Speak to the back row, write for the front row.** Slide text should be legible from 10 meters; your explanation carries the nuance the slide can't hold.
- **Layer the audience, don't fork the talk.** Slide 2 protects newcomers; slides 6, 8, and 9 are where intermediate/professional attendees lean in. You never need a separate "beginner track" — the plain-language opening buys you the room's trust to go technical later.
- **Rehearse the transitions, not just the slides.** The strongest 50-minute talks are judged on the sentences *between* slides ("So if raw data isn't the truth — how do professionals actually get from mess to trustworthy? That's a workflow, not a trick.") — script those bridges once, then never read them again.
- **Protect the Q&A buffer.** If you're behind by Slide 7, cut detail from Slide 8 (tool landscape), not from Slides 2–3 (definition and stakes) or Slide 10 (close). The room forgives a shorter tool tour; it does not forgive a talk with no ending.
