# DCEA — Coffee Extraction Diagnosis Skill

**D**ecent **C**offee **E**xtraction **A**ssistant

Tell it your extraction variables and what the cup tasted like, and it identifies the cause and gives you **one variable to change in the next brew**. A skill for Claude.

The diagnosis rests on extraction theory compiled over several years by a single home-cafe experimenter (the blog [klar201](https://blog.naver.com/klar201)). **Several items conflict with conventional coffee wisdom, and on conflict the skill follows its own theory** — while telling you that the conflict exists.

---

## What it does

- **Sensory note → cause** — astringency, greenness, piercing sourness, flatness, and bitterness are separated into distinct causes. In particular, astringency (peak instantaneous flow velocity) and greenness (average flow rate) are never lumped together.
- **One variable at a time** — prescriptions issue only from temperature, flow rate, brew ratio, and grind size, and only one changes per brew. Otherwise you cannot tell what worked.
- **Total flavor load first** — it gauges how much flavor the bean still holds before choosing a direction. When flavor is lacking, it does *not* prescribe "pulling more out" (higher flow rate, longer brew, finer grind).
- **Within the equipment you have** — in default mode, prescriptions use only manipulations your stated equipment can perform.

Supported brewers: espresso, conical drippers (V60 and similar), and flat-bottom drippers. Bean selection, roast profiles, machine maintenance, and moka pots are out of scope.

## Execution modes

Chosen by the invocation argument. With none, you get default mode.

| Argument | Tool constraint | Reply |
|---|---|---|
| (none) | Tools you have + inexpensive ones | Prescription only, brief (under 150 words) |
| `barista` | None | Prescription + manipulation details, second-choice options, side-effect signals (under 300 words) |
| `geek` | None | All of the above + mechanism, theoretical grounds, source numbers |

Mode changes **only the scope of the reply.** The diagnostic logic is identical across all three.

---

## Installation

Wherever you use it, **you start with the repository URL.** In Claude Code, Claude finishes the install for you; in chat, it builds the archive and you register it yourself.

### Ask Claude to do it — Claude Code (terminal · the Code tab in the desktop app · IDE extensions)

All three work the same way. Tell Claude:

```
Install https://github.com/klarjk/DCEA into ~/.claude/skills/dcea, using the en/ folder
```

The repository root is the Korean edition, so the `en/` folder is what you want. Doing it by hand:

```bash
git clone https://github.com/klarjk/DCEA.git ~/DCEA
ln -s ~/DCEA/en ~/.claude/skills/dcea
```

It is picked up without a restart. Type `/dcea` to confirm.

### Using it in chat — the Chat tab in the desktop app · claude.ai on the web · mobile

In chat, Claude cannot register the skill for you. It can go as far as building the archive; uploading it is your job. **Upload it once and it lives on your account,** available in all three. There is nowhere to upload on mobile, so register it from desktop or the web.

1. **Turn on code execution in Settings → Capabilities.** Without it the Skills section does not appear at all.
2. Get the archive. Ask Claude and it fetches the repository, zips it, and hands you a download link:

   ```
   Fetch https://github.com/klarjk/DCEA, put its en/ folder into a single folder named dcea, zip that, and give me a download link
   ```

   Downloading it straight from the [releases page](https://github.com/klarjk/DCEA/releases/latest) works the same — `dcea-en.zip` for English, `dcea.zip` for Korean.
3. Upload it via **Customize (sidebar) → Skills → + → Upload a skill** and toggle it on.

<details>
<summary>Building the archive yourself</summary>

The archive must contain the skill folder at its root. Files scattered at the top level are rejected.

```bash
git clone https://github.com/klarjk/DCEA.git dcea-src

# English
mkdir -p build/dcea && cp -R dcea-src/en/SKILL.md dcea-src/en/references dcea-src/en/sources build/dcea/
cd build && zip -r ../dcea-en.zip dcea && cd ..
```
</details>

### ChatGPT and other AI apps

They have no place to register a skill, so you attach the archive at the start of each conversation.

1. Download the archive from the [releases page](https://github.com/klarjk/DCEA/releases/latest). Expand the **Assets** list near the bottom of the page: `dcea-en.zip` is the English edition, `dcea.zip` the Korean one.
2. **Do not unzip it.** Drag the `.zip` straight into the chat box, or use the paperclip attachment button. The tool has to be able to open an archive, so check that your plan includes file upload and code execution.
3. Once it is attached, ask:

   ```
   Unpack the attached archive and diagnose my extraction following the procedure in SKILL.md.
   Read files from the references/ folder whenever you need them.
   ```

4. Repeat steps 1–3 in every new conversation. Nothing is stored on your account.

If the tool cannot handle archives at all, opening `SKILL.md` and pasting its full text still gets you a basic diagnosis — but without the diagnosis tables and variable dictionary in `references/`, the prescriptions come out coarser.

Either way it merely reads the files and follows along, so results will be less consistent than on Claude.

---

## Using it

In Claude Code type `/dcea`; in chat, just describe the symptom and the skill attaches itself.

```
/dcea today's shot came out astringent
this espresso is far too bitter
my V60 tastes like barley tea — barista mode please
/dcea geek why are you telling me to add another pour?
```

Anything missing gets asked for, so say as much as you know. Give it these four and it diagnoses without a round of questions:

1. **Brewer** — espresso / conical dripper / flat-bottom dripper, plus the basket or dripper model
2. **Dose · beverage weight · brew time** — beverage weight is **what is in the cup**, not the water you poured
3. **Sensory notes** — bitter, sour, astringent, flat? How it shifts as the cup cools is a clue too
4. **Beans** — roast level, roast date

No refractometer needed. It will not ask for one.

### Records

In Claude Code, your equipment, baselines, and diagnosis history accumulate in `~/.claude/dcea/profile.md`. Once the same prescription is confirmed effective twice, that value is promoted to a baseline — and from then on **your measured values take precedence over the author's numbers.** In chat and other AI tools nothing persists past the conversation, so state your equipment and usual settings in a line up front.

---

## Things to know

- **Every number is based on the author's equipment** (Lagom P64 + SSP cast, Decent XL, V60). Prescriptions are therefore never absolute values but "which way from last time." A different grinder or machine has a different optimum.
- **Confidence is tagged** — `[Verified]` direct experiment / `[Observed]` empirical observation / `[Theory]` derived from physics / `[Hypothesis]` the author's conjecture. A prescription resting on a hypothesis says so, and comes with a way to confirm it.
- **Where the author says he does not know, the skill says it does not know.** It does not invent an answer.

## Repository layout

The repository root is the Korean edition; `en/` is this English edition, with a 1:1 file structure.

| Path | Contents |
|---|---|
| `SKILL.md` | The diagnostic procedure and reply format |
| `references/` | Theory, diagnosis tables, variable dictionary, recipes, per-brewer mechanisms |
| `sources/blog/` | The blog posts the theory is drawn from (Korean) |

A `(Source NN)` tag in a reply points to `sources/blog/NN_*.txt`.
