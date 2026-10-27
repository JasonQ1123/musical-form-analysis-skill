# Musical Form Analysis — an Agent Skill

A portable `SKILL.md` skill that teaches an AI agent to analyse musical form the way a theory class does: **delimit sections by cadences, type them from thematic and tonal layout, and produce a checkable diagram — not a guess.**

Works with any agent that loads `SKILL.md` bundles (DSH, Claude-style skills, and similar).

## Why

Most wrong form analyses fail in the same three ways:

1. calling a return of the **accompaniment** a recapitulation;
2. treating a **pause** as a cadence and cutting a section there;
3. turning **thematic groups** (a, b | c, d | e, f, g) into "parts" without cadential support.

This skill encodes the counter-rules and a decision tree that separates binary, ternary, compound ternary, rondo, variations, and sonata.

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

The folder name is irrelevant to the agent; the `name:` field in `SKILL.md` is what matters.

## Use

Ask naturally:

- "What form is this piece?"
- "Is this simple ternary or compound ternary?"
- "Analyse the form of this score" (with an image attached)
- "单三还是复三？"

The agent loads the skill, builds a cadence table, and returns a diagram plus a conclusion with the evidence.

## What is inside

`SKILL.md` contains:

- three rules (cadence-first boundaries; reprise = theme return; part = theme + cadence + weight);
- a six-step workflow (coordinates → cadences → themes → tonal plan → parts → classification);
- a cadence table (PAC / IAC / HC / PC / DC / modulating / pause);
- a classification decision tree;
- pitfalls, a pre-submission checklist, and an EN/中文 glossary;
- a worked example: Mendelssohn, *Kinderstücke* Op. 72 No. 2 (42 bars, simple binary).

`examples/` holds longer worked analyses.

## Example output

```
Intro(1–4) + A(5–14: a5–8, b9–14) + B(15–38) + Coda(39–42)
= 4 + 10 + 24 + 4 = 42

A closes with a PAC in the tonic at bar 14.
B is developmental and stays open (pause at 22; dominant preparation at 38).
→ simple binary, no reprise, with introduction and coda.
```

## License

MIT — see [LICENSE](LICENSE).
