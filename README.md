# Musical Form Analysis — an Agent Skill

A portable `SKILL.md` skill that teaches an AI agent to analyse musical form the way a theory class does: **delimit sections by cadences, type them from thematic and tonal layout, and produce a checkable diagram — not a guess.**

Written against the plain `SKILL.md` + YAML frontmatter convention shared by DSH, Claude-style skills, and similar loaders; the only hard requirement is a `name` and a `description` in the frontmatter.

## Why

Most wrong form analyses fail in the same three ways:

1. calling a return of the **accompaniment** a recapitulation;
2. treating a **pause** as a cadence and cutting a section there;
3. turning **thematic groups** (a, b | c, d | e, f, g) into "parts" without cadential support.

The skill encodes the counter-rules, a decision tree that separates binary / rounded binary / ternary / compound ternary, a genre gate that keeps sonata, rondo, variations, barform and arch form out of that tree, and an evidence tag on every claim so a bar number can never appear without saying where it came from.

## Install

User-wide (all projects):

```bash
git clone https://github.com/JasonQ1123/musical-form-analysis-skill.git
mkdir -p ~/.dsh/skills
cp -r musical-form-analysis-skill ~/.dsh/skills/musical-form-analysis
```

Project-wide:

```bash
mkdir -p .dsh/skills
cp -r musical-form-analysis-skill .dsh/skills/musical-form-analysis
```

The `name:` field in `SKILL.md` is what identifies the skill; keeping the folder name identical to it is the safe default.

## Use

Ask naturally — English or Chinese:

- "What form is this piece?"
- "Is this simple ternary or compound ternary?"
- "Is this binary or ternary — and is it rounded?"
- "Is this a sonata?"
- "Analyse the form of this score" (with an image attached)
- "单三还是复三？" / "单二还是单三？" / "这首曲子是什么曲式？" / "是不是奏鸣曲式？"

The agent clears the genre gate first, builds a cadence table with evidence tags, and returns a diagram plus a conclusion that also names the reading it rejected.

## What is inside

`SKILL.md` contains:

- an **evidence contract** (`[score]` / `[audio]` / `[lit]` / `[inferred]`), including the rule that a title-only prompt may not produce a bar-level table;
- three rules: cadence-first boundaries (with a "non-cadential boundary" label for intro / coda / link), a **substantial-reprise test** (≥ half of A, closing the tonic) that separates rounded binary from ternary, and part = theme + cadence + weight;
- a six-step workflow (coordinates → cadences → themes → tonal plan → parts → classification), with repeat signs and `D.C. al fine` read *before* any harmonic judgement;
- a cadence table (PAC / IAC / HC / PHC / PC / DC / modulating / evaded / pause) plus the arrival test that stops internal V–I from being counted as a cadence;
- a **genre gate** (sonata, sonata-rondo, rondo, variations, barform, arch, through-composed) ahead of the binary/ternary tree;
- the binary/ternary decision tree, including the 0-closed-parts and ≥ 4-closed-parts fall-throughs;
- pitfalls, a pre-submission checklist, and an EN/中文 glossary;
- a worked example: Mendelssohn, *Kinderstücke* Op. 72 No. 2 (42 bars, simple binary), with the full analysis in `examples/`.

`examples/mendelssohn-op72-no2.md` holds the full cadence table, the provenance tags, the table of tempting-but-wrong readings, and an explicit note of where the analysis **differs from the article it cites**.

## Example output

```
Intro(1–4) + A(5–14: a5–8, b9–14) + B(15–38) + Coda(39–42)
= 4 + 10 + 24 + 4 = 42

A closes with a PAC in the tonic at bar 14          [lit]
B is developmental and stays open (pause at 22; dominant preparation at 38)
→ simple binary, no reprise, with introduction and coda.

Rejected reading: simple ternary — bars 39–42 bring back the introduction's
accompaniment, not A's melody, and only for 4 bars.
```

## Scope and limits

- The rules are the **Classical instrumental** default. Baroque binary, chorale/barform, and trio middles are handled by the genre gate, but the cadence-first logic is stated for the common-practice repertory.
- The skill deliberately stops at **section-level** analysis: it does not do Schenkerian reduction, motivic counterpoint, or harmonic function analysis beyond what cadence typing needs.
- The Mendelssohn example is a **format demonstration**: its bar numbers come from the cited article, not from a score, and it says so. Use it as a template for what the output should look like, not as an authority on Op. 72 No. 2.

## License

MIT — see [LICENSE](LICENSE).
