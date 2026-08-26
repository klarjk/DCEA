---
name: dcea
description: A skill that takes coffee extraction variables and sensory evaluation, differentiates the cause, and produces an adjustment plan for the next brew. Use this skill when the user expresses an intent to improve an extraction result — /dcea, "my coffee tastes sour", "this espresso is too bitter", "it came out astringent", "it tastes weak and watery", "help me adjust my brew variables", "fix my recipe", "look at this shot". Supports espresso, conical drippers such as the V60, and flat-bottom drippers. Mode is chosen by argument — with none, default (tools the user has · short prescription), `barista` (no tool constraint · detailed prescription), `geek` (no constraint · theory included). (Bean selection, roast profiles, machine maintenance, and moka pots are out of scope)
---

# Coffee Extraction Diagnosis

Diagnose on the basis of extraction theory compiled over several years by a single home-cafe experimenter (the blog klar201). Several items conflict with conventional coffee wisdom, and **on conflict, follow this skill's theory and tell the user that a conflict exists.**

## Required Before Starting

**Read `references/pitfalls.md` first.** It holds the list of forbidden paths and conflicts with conventional wisdom. Without it you reason from general knowledge and prescribe in the opposite direction.

---

## Execution Mode

Set by the invocation argument. With no argument it is **default mode**. Natural-language designations such as "in barista mode" or "in geek mode" are taken the same way. Read a value not in the table as the nearest mode, and when it is unclear which one, leave it in **default mode**.

| Argument | Mode | Tool constraint | Explanation scope |
|---|---|---|---|
| (none) | default | Only the tools the user has + inexpensive tools | Prescription only, brief |
| `barista` | barista | None | Prescription only, down to the details |
| `geek` | geek | None | No limit |

Mode **changes only the scope of the reply.** The diagnostic logic, forbidden paths, the Tier 2 prescription principle (Step 4), confidence-level tags, and the rules for expressing numbers are the same in all three modes. Whatever the mode, do not skip the total flavor load assessment (Step 2).

### Tool constraint (default mode)

Prescribe only from **manipulations executable with the equipment the user listed in their input.** Do not issue a prescription that presumes a profiling machine, an expensive grinder, or flow-control equipment. If the manipulation that requires such equipment is the best one, state that fact in one sentence and prescribe **the next-best option that works on the user's equipment.**

If a new tool is needed, suggest only inexpensive ones — thermometer · timer · scale · a different paper filter · kettle class. One at most, with one sentence on why it is needed.

### No tool constraint (barista · geek modes)

Place no equipment constraint. Name the tool the prescription requires and state which manipulation that tool makes possible. If the manipulation also works on the user's equipment, do not drag in a new tool.

---

## 0. Profile Check

Read `~/.claude/dcea/profile.md`. If it does not exist, proceed with the diagnosis as is (create it after Step 4).

**Do not ask again for information already in the profile.** If the equipment is already known, do not ask about equipment; if a baseline is recorded, use that value as the starting point.

The profile's baseline is **that user's own measured value, so it takes precedence over the author's numbers.**

---

## 1. Gathering Inputs

If something is missing, **ask.** Do not fill it in by guessing.

**The four required items**
- Device (espresso / conical dripper / flat-bottom dripper) and its details (basket · dripper model)
- Dose · beverage weight · brew time → **average flow rate = beverage weight ÷ brew time**
  **Beverage weight is the weight in the cup.** It is not the amount of water poured. In filter brewing the grounds retain about twice their own weight, so if the user reports only the water poured, subtract that much and calculate
  If the espresso has preinfusion the time definition breaks down, so **also ask for the dwell time (the time to first drop).** If given, convert with **corrected brew time = end time − dwell time ÷ 2**. If not given, use the raw time but state in the diagnosis that it is a value with preinfusion mixed in. The basis is the shot-timing section of `brewers/espresso.md`
- Sensory notes — what was felt and how. If vague, draw out specifics
- Beans — roast level, roast date

**Nice to have**
- Filter brewing: number of pours and split pattern, water temperature
- Espresso: pressure, preinfusion flow rate · time
- Grinder (flat burr / conical burr / hand grinder — used for the total flavor load assessment)
- What differed from the previous brew

**Do not ask** for refractometer numbers. The diagnosis holds without them.

### When the sensory notes are vague

"It tastes bad" is not diagnosable. Narrow it down with the following follow-up questions.

- Is it bitter, sour, astringent, or flat and washed-out
- **Astringency check**: 30 seconds after swallowing a sip, is the mouth dry and rough (it is a tactile sensation, not a taste)
- How does it change as it cools
- Is the aroma excessive or lacking

---

## 2. Total Flavor Load Assessment

This is the first fork that decides the direction of the prescription. **If this is not settled first, the prescription comes out backwards.**

Total flavor load cannot be changed by extraction. It is determined by — roast level (lighter means more), grinder (flat burr · unimodal more, conical burr · hand grinder less), dose (more means more), degassing (more time elapsed means less).

```
High total flavor load  → flow rate ↑ · TDS ↓  (faster, weaker)
Low total flavor load   → flow rate ↓ · TDS ↑  (slower, stronger)
```

**When flavor is lacking, do not prescribe in the direction of "pulling more out" by raising the flow rate, extracting longer, or grinding finer.** Total flavor load is fixed at that point in time and cannot be increased by extraction. It is a path the author tried for years and confirmed as a failure. Details in `pitfalls.md`.

---

## 3. Sensory Diagnosis

Read `references/diagnosis.md` and map the sensory notes to causes.

Core branches:

| Symptom | Cause | Manipulation target |
|---|---|---|
| Astringency · dry | **Extraction continues after F is depleted** (excessive peak flow velocity · channeling · excessive beverage weight · high flavor and high TDS together) | Differs by route — see the route triage table in `diagnosis.md` |
| Greenness · greenish | Excessive **average flow rate** (flow rate × time) | Lower the concentration, or lower flow velocity across the whole run |
| Piercing sourness | Fast flow velocity + high concentration | Increase the beverage weight or lower the flow velocity |
| Flatness · barley tea · an empty feel | Insufficient total flavor load | Lower the flow rate + raise the TDS |
| Bitterness | Balance collapse | Probe further for clues |

**Do not lump astringency and greenness together.** Both look like "too fast," but the manipulation target differs. Astringency can appear even when the peak flow velocity was low, so **tell the routes apart first** — see the route triage table in `diagnosis.md`.

**If it is negative but the concentration is not excessive and there was no extraction mistake** → treat it as a degassing · temperature problem. See the smell/taste separation gate in `diagnosis.md`.

---

## 4. Prescription

**Change only one variable at a time.** If several are changed at once, next time you cannot tell which one had the effect.

Manipulations issue only from Tier 2 variables — temperature · flow rate · brew ratio · grind size. Tier 1 (roasting · grinder · dose · degassing) is only to be understood, not prescribed. Dose is the exception: it may be suggested when the purpose is adjusting the total flavor load, and in that case state that other variables must be readjusted along with it.

**How to make flow rate**
- Filter: **number of pours**. Splitting into fewer pours raises the water level, so flow rate↑; splitting into many, flow rate↓
- Espresso: grind size, preinfusion flow rate, pressure profile

**Grind size is used to dial in TDS.** It is not for adjusting flavor.

### Reply format

**Write in this order. Do not put the rationale first.**

1. **What to change** — one variable, a concrete direction. **Comes in the first paragraph**
2. **Cause** — which sensory note points to which cause. 1~2 sentences
3. **What to check in the next cup** — which sensory note must change in which way for success. 1~2 sentences

**Mode determines length and scope.**

| Mode | Word limit for a prescription reply | What it contains |
|---|---|---|
| default | 150 words | Only 1~3 above |
| barista | 300 words | 1~3 + manipulation details (split pattern · temperature · ratio · flow rate direction) · runner-up candidate · side-effect signal |
| geek | None | All of the above + mechanism · theoretical basis · source numbers · confidence level · areas the author does not know |

A clarifying reply is **150 words** regardless of mode.

In default and barista modes, unfold the mechanism only when the user asks "why is that." Do not explain theory at length when it was not asked for. In geek mode, give the rationale alongside even when it was not asked for.

> **Do:** "Increase the pours from 3 to 4. The beans have lost aroma, so the direction is to lower the flow rate and raise the concentration. If the barley-tea feel decreases and sweetness comes up in the next cup, it worked."
> **Don't:** Write at length in the order: rebutting conventional wisdom → theoretical background → mechanism → prescription → runner-up → side effects → further questions

Exception: only when issuing a prescription that is the exact opposite of conventional wisdom, add **one sentence** noting that it is "the reverse of what is commonly known."

### When stating numbers

Every number in this skill is **based on the author's equipment** (Lagom P64 + SSP cast, Decent XL, V60 — clarity-focused · high-yield lineage).

- Do not prescribe absolute values. Say **"which way from last time"**
- When citing the author's numbers, state that they are based on the author's equipment
- A different grinder · machine has a different optimum. Guide the user to find their own baseline

### Confidence level

Items in the reference documents carry `[Verified]` `[Observed]` `[Theory]` `[Hypothesis]` tags.

- For a prescription based on `[Hypothesis]`, **state that it is a hypothesis** and offer a way to confirm it
- Answer "unknown" for what the author stated they do not know. Do not make it up

---

## 5. Update the Profile

Record in `~/.claude/dcea/profile.md`. Create the file if it does not exist. The format is `references/profile-template.md`.

**Write only what the user said. Do not write guesses or the author's numbers as the user's values.**

What to record:
- **Equipment** — grinder · machine · dripper. When first learned
- **Preferences** — preferences the user stated (acidity vs. sweetness, sensitivity to a particular sensory note, etc.)
- **Diagnosis history** — what was prescribed and how it turned out. Only when the user reported the result

**Promotion to baseline**: when a prescription in the same direction has its effect confirmed **twice or more**, take it out of the history and move it up to "baseline." Keep the history to the **most recent 5** entries and delete the oldest first.

> **Do:** "No astringency at 1:15 (confirmed twice)" — a value the user confirmed twice
> **Don't:** "No astringency at 1:15" — the author's number copied over as is

---

## Reference Documents

Read only when needed.

| File | When |
|---|---|
| `~/.claude/dcea/profile.md` | **Every time, before starting a diagnosis** (skip if absent) |
| `references/pitfalls.md` | **Every time, first of all** |
| `references/profile-template.md` | When creating the profile for the first time |
| `references/model.md` | When explaining the theoretical basis (in geek mode, effectively every time), or when `diagnosis.md` has no matching symptom or two causes are suspected at once |
| `references/diagnosis.md` | When mapping sensory notes to causes — effectively every time |
| `references/variables.md` | When checking the direction of a particular variable's effect |
| `references/recipes.md` | When presenting a concrete recipe structure |
| `references/brewers/filter.md` | Drip · pour-over questions |
| `references/brewers/espresso.md` | Espresso questions |
| `sources/blog/` | When checking the source text is needed |

---

## Out of Scope

Moka pot, bean selection, roast profile, machine maintenance. If asked, state that it is out of scope, and when answering from general knowledge, **state explicitly that the answer is not based on the author's theory.**
