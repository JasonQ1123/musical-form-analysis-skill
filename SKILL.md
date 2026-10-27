---
name: musical-form-analysis
description: Analyze the form of a piece or score excerpt (binary, ternary, compound ternary, rondo, variations, sonata). Sections are delimited by cadences and typed from thematic and tonal layout; the output is a checkable cadence table, form diagram, and conclusion. Use when asked "what form is this", "simple or compound ternary", "analyze this piece", or given a score image.
---

# Musical Form Analysis

## When to use

- The user asks what form a piece or excerpt is in, or wants sections, a form diagram, or a comparison of binary / ternary / compound ternary.
- Input may be a score image, MIDI, a text description, or just a title and opus number.
- The user doubts an existing analysis: verify it independently instead of agreeing with it.

## Three rules

1. **Boundaries follow cadences.** A section boundary must land on a cadence (PAC/IAC/HC). A pause is not a cadence.
2. **Recapitulation means the theme returns** — melody + key + structural position. An accompaniment pattern, texture, or dynamic level alone is a frame, not a return.
3. **A "part" = theme + cadence + weight.** Miss one and it is a phase of a development, not an independent part.

## Workflow

### 0. Fix the coordinates

- Confirm work, edition, bar numbers; count barlines; note anacrusis, repeats, D.C./D.S.
- Build a "system → bars" table (e.g., 6 bars per system: system 1 = 1–6, system 2 = 7–12 …).
- Mark changes of tempo, dynamics, texture, and accompaniment pattern.
- If the scan is illegible, report only what is verifiable (system and bar vicinity); never invent bar numbers.

### 1. Phrase and cadence

At each phrase end check three things: bass motion (V–I, V–vi, IV–V), melodic final (1/3/5), rhythm (long note, rest, fermata).

| Type | Effect | Bass | Melody |
|---|---|---|---|
| PAC (perfect authentic) | full close | V–I, root position | tonic |
| IAC (imperfect authentic) | weaker close | V–I inverted, or non-tonic melody | 3rd/5th |
| HC (half) | open | stops on V | any |
| PC (plagal) | soft close | IV–I | tonic |
| DC (deceptive) | surprise | V–vi | — |
| Modulating cadence | new key | new key V–I | new tonic |
| Pause (not a cadence) | breath | — | — |

Record: bar, key, type, open/closed.

### 2. Label the themes

- Number ideas a / b / c … (motive, rhythm, accompaniment pattern).
- Track repetition, variation, sequence, fragmentation, combination.
- Distinguish three look-alikes: theme return / texture return / frame (intro–coda echo).

### 3. Tonal plan

- Tonic, relative, dominant, subdominant, remote keys.
- Is each part closed (cadence in its own key) or open (modulation / stop on the dominant)?

### 4. Qualify the parts

Score each candidate section:

1. Independent theme (or theme group)?
2. Independent cadential close?
3. Sufficient structural weight (a period or more)?

All three → independent part; missing cadence → a phase of the development.

### 5. Classify

```
Q1 Does the theme return (melody + key + structural position)?
├─ yes → three parts
│   ├─ middle closed (new key + new theme + full cadence, often new tempo/texture)
│   │   → compound ternary (trio)
│   └─ no → simple ternary (with reprise)
└─ no → Q2
    Q2 How many closed parts?
    ├─ 1 (A) + development + coda → simple binary
    ├─ 2 (A and B each cadence) → still simple binary (B's second half develops)
    ├─ 3, each cadence → simple ternary without reprise (sectional / 并列)
    └─ intro–coda echo only → frame, not return → binary
```

Other types: rondo (refrain cycles), variations (theme transformed continuously), sonata (two-key exposition + development + recapitulation).

### 6. Diagram and conclusion

```
Intro(1–4) + A(5–14: a5–8, b9–14) + B(15–38) + Coda(39–42)
= 4 + 10 + 24 + 4 = 42
```

Conclusion template:

> The piece is in **__ form**. A (bars _–_) closes with a **__ cadence**; B (bars _–_) is **__** (developmental / contrasting) and ends **__**; the whole closes **__**. Key evidence: (1) the cadence at bar _; (2) whether the theme returns; (3) whether the middle is closed.

## Pitfalls

| Pitfall | Symptom | Fix |
|---|---|---|
| Texture return taken as reprise | closing bars bring back the opening accompaniment | check whether the theme melody returns |
| Pause taken as cadence | a "breath" treated as a section boundary | boundaries need PAC/IAC/HC |
| Thematic groups taken as parts | a,b｜c,d｜e,f,g → "three parts" | each part needs cadential support |
| Agreeing with a ready-made answer | copying a chart/answer that says "binary" | verify independently with cadences |
| Bar-number drift | quoting 14/22 from memory | count barlines; build the system table |

## Checklist

- [ ] Do the section bar counts add up to the total?
- [ ] Does every boundary have a cadence?
- [ ] Are pause and cadence distinguished?
- [ ] Are texture return and theme return distinguished?
- [ ] Are thematic groups and parts distinguished?
- [ ] Is the middle genuinely closed (new key + new theme + full cadence)?
- [ ] Do the conclusion and the diagram agree?
- [ ] Is the terminology consistent (binary / ternary / compound; with / without reprise)?

## Glossary (EN / 中文)

PAC 完满全终止 · IAC 不完满全终止 · HC 半终止 · PC 变格终止 · DC 阻碍终止 · period 乐段 · phrase 乐句 · motive 动机 · exposition 呈示部 · development 展开部 · recapitulation 再现部 · coda 尾声 · introduction 引子 · trio 三声中部.

## Worked example: Mendelssohn, *Kinderstücke* Op. 72 No. 2

- E-flat major, 2/4, 42 bars, *Andante sostenuto*.
- Cadences: bar 8 HC (V); bar 14 PAC (I); bar 22 pause (not a cadence); bar 32 climax (diminished seventh / augmented sixth, not a cadence); bar 38 dominant preparation; bar 42 PAC (I).
- Parts: A 5–14 (closed); B 15–38 (developmental, open); Coda 39–42.
- Form: **simple binary** (no reprise, with introduction and coda).
- Lessons: do not mistake the closing accompaniment figure for a reprise; do not fold the dominant restatement (c, d) into A; do not turn the thematic groups (a,b ｜ c,d ｜ e,f,g) into three parts without cadential support.
