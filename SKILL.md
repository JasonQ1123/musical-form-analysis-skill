---
name: musical-form-analysis
description: Analyze the form of a piece or score excerpt — binary (simple / rounded), ternary (simple / compound), rondo, variations, sonata, barform, arch. Sections are delimited by cadences and typed from thematic and tonal layout; the output is a checkable cadence table with an evidence tag per row, a form diagram, and a conclusion that also names the rejected reading. Use when asked "what form is this", "is it binary or ternary", "simple or compound ternary", "is this a sonata", "analyze this piece", or given a score image, MIDI, or just a title; 中文：这首曲子是什么曲式、分析一下曲式、单三还是复三、单二还是单三、是不是奏鸣曲式、段落怎么划分.
---

# Musical Form Analysis

## When to use

- The user asks what form a piece or excerpt is in, or wants sections, a form diagram, or a comparison of binary / ternary / compound ternary.
- Input may be a score image, MIDI, a text description, or just a title and opus number.
- The user doubts an existing analysis: verify it independently instead of agreeing with it.
- **If you cannot see the score and cannot hear the piece, say so before analysing** and follow the evidence rules below.

## Evidence and limits

Tag every factual claim, and carry the tag into the output.

| Tag | Meaning |
|---|---|
| `[score]` | read from the score or scan in front of you |
| `[audio]` | heard in a recording, not read |
| `[lit]` | taken from a published analysis — cite it |
| `[inferred]` | reasoning only; no score, no recording |

- With only `[inferred]` evidence, **do not print a bar-level cadence table.** Give the generic outline for the genre, tag every claim `[inferred]`, and name the two or three bars that would settle the question.
- Never let a cited analysis's segmentation stand in for your own: cite it *and*, if you differ, say where and why.
- Never invent bar numbers, opus numbers, key signatures, or movement counts.

## Three rules

1. **Boundaries between main parts follow cadences.** A boundary between two main parts must land on a cadence (PAC/IAC/HC). A pause is not a cadence. Exception: introduction, coda, and link boundaries follow the thematic or textural entry — label them **non-cadential boundary** rather than pretending a cadence is there.
2. **A reprise must be substantial.** The theme returns with melody + key + structural position, *and* the return stands as its own section — at least half of A, closing the tonic in its own right. A return of one phrase still inside B is **rounded binary** (A B A′), not ternary.
3. **A "part" = theme + cadence + weight.** Miss one and it is a phase of a development, not an independent part. Operative test for weight: ≥ 8 bars, or at least two phrases. (This is the Classical instrumental default; in Baroque binary and in a trio middle, tonal closure alone can define a part.)

## Workflow

### 0. Fix the coordinates

- Confirm work, edition, bar numbers; count barlines; note anacrusis, repeats, D.C./D.S.
- **Inventory the signs before anything else:** `||:` `:||`, 1st/2nd endings, `D.C. al fine` / `D.S.`, fermatas, double bars. These decide sections more often than harmony does.
- Build a "system → bars" table (e.g., 6 bars per system: system 1 = 1–6, system 2 = 7–12 …).
- Read once through for the large shape (macro), and only then measure bar by bar (micro).
- Mark changes of tempo, dynamics, texture, and accompaniment pattern.
- If the scan is illegible, report only what is verifiable (system and bar vicinity); never invent bar numbers.

### 1. Phrase and cadence

At each phrase end check three things: bass motion (V–I, V–vi, IV–V), melodic final (1/3/5), rhythm (long note, rest, fermata).

| Type | Effect | Bass | Melody |
|---|---|---|---|
| PAC (perfect authentic) | full close | V–I, both root position | tonic |
| IAC (imperfect authentic) | weaker close | V–I inverted, or non-tonic melody | 3rd/5th |
| HC (half) | open | stops on V | any |
| PHC (Phrygian half) | open, minor | iv6–V | — |
| PC (plagal) | soft close | IV–I | tonic |
| DC (deceptive) | surprise | V–vi | — |
| Modulating cadence | new key | PAC/IAC in the new key | new tonic |
| Evaded / aborted | no arrival | V, then the phrase continues | — |
| Pause (not a cadence) | breath | — | — |

- **A cadence is a point of arrival, not just a progression.** Confirm the phrase close *and* the metric arrival (strong beat, end of the hypermetric group). An internal V–I in mid-phrase is not a cadence.
- An evaded cadence is positive evidence of a **continuous** join: do not cut a section there.

Record: bar, key, type, open/closed, evidence tag.

### 2. Label the themes

- Number ideas a / b / c … (motive, rhythm, accompaniment pattern).
- Track repetition, variation, sequence, fragmentation, combination.
- Distinguish three look-alikes: theme return / texture return / frame (intro–coda echo).
- Measure any return: how many bars, which phrases, does it close the tonic? This number decides binary vs ternary.

### 3. Tonal plan

- Tonic, relative, dominant, subdominant, remote keys.
- Is each part **closed** (收拢: cadence in its own key) or **open** (开放: modulation / stop on the dominant)?
- Note whether the second key belongs to the same exposition (sonata) or is an independent section's key.

### 4. Qualify the parts

Score each candidate section:

1. Independent theme (or theme group)?
2. Independent cadential close?
3. Sufficient structural weight (a period or more — ≥ 8 bars or two phrases)?

All three → independent part; missing cadence → a phase of the development. Say which term you are using: **part** (部) or **development** (展开部), and keep it consistent through the diagram, the table, and the conclusion.

### 5. Classify

**Q0. Genre gate — settle this before the binary/ternary question.** These do not fit that question at all:

| Genre | Decisive test |
|---|---|
| Sonata | exposition closes in the secondary key (dominant / relative major); the recapitulation returns the second theme **in the tonic**. A recapitulation is a return, so the ternary test misfires if run first. |
| Sonata-rondo | refrain in rondo layout, but episodes form a two-key exposition and a recapitulation |
| Rondo | refrain returns ≥ 3 times, each time closed; name single-theme / contrasting |
| Variations | a theme transformed continuously (strict / free), not restated intact |
| Barform (AAB) | two related phrases then a contrasting *closing* section (Bar); common in chorales and Lieder |
| Arch | tonal or thematic mirror (ABCBA) |
| Through-composed | no repetition of a section at all |

None of these → continue.

**Q0b. Read the signs.** `D.C. al fine` / `D.S.`, or a written-out complete return of A, means **compound ternary (trio form)**. The return may be written out or supplied by the da capo — do not require to *see* it in the notated music.

```
Q1 Does the theme return?
├─ yes → is the return its own section?
│   ├─ yes (≥ half of A, closes the tonic in its own right) → three parts
│   │   ├─ middle closed (new key + new theme + full cadence, often new tempo/texture)
│   │   │   → compound ternary (trio)
│   │   └─ middle open → simple ternary (with reprise)
│   └─ no (a phrase or two, still inside B) → rounded binary (A B A′), not ternary
└─ no → Q2 How many closed parts?
    ├─ 0 → through-composed / continuous; name the genre, do not force binary or ternary
    ├─ 1 (A) + development + coda → binary (continuous)
    ├─ 2 (A and B each cadence) → binary, without reprise
    ├─ 3, each cadence, no return → ternary without reprise (sectional / 并列)
    ├─ ≥ 4 → rondo or a multi-part form — go back to Q0
    └─ intro–coda echo only → frame, not a return → binary
```

State the outcome in one of these names, and do not mix them: binary (continuous) / binary without reprise / **rounded** binary (A B A′, the return short) / **balanced** binary (A and B of equal weight, no separate return) / simple ternary (with reprise) / ternary without reprise (并列) / compound ternary (trio form) / rondo / variations / sonata / barform / arch / through-composed.

### 6. Diagram and conclusion

```
Intro(1–4) + A(5–14: a5–8, b9–14) + B(15–38) + Coda(39–42)
= 4 + 10 + 24 + 4 = 42
```

The conclusion must contain, in this order:

1. the form label;
2. the bar-level evidence, each with its tag (`[score]`, `[lit]`, `[inferred]` …);
3. **the rejected reading** — the strongest alternative and the single piece of evidence that kills it.

Conclusion template:

> The piece is in **__ form**. A (bars _–_) closes with a **__ cadence** `[score]`; B (bars _–_) is **__** (developmental / contrasting) and ends **__**; the whole closes **__**. Key evidence: (1) the cadence at bar _; (2) whether the theme returns, and for how long; (3) whether the middle is closed. Strongest rejected reading: __, which fails because __.

## Pitfalls

| Pitfall | Symptom | Fix |
|---|---|---|
| Texture return taken as reprise | closing bars bring back the opening accompaniment | check whether the theme melody returns |
| Short return taken as ternary | a phrase of A comes back at the end | return ≥ half of A, closing the tonic on its own → else rounded binary |
| da capo ignored | trio middle, then "no return in the score" | `D.C.` *is* the return → compound ternary |
| Pause taken as cadence | a "breath" treated as a section boundary | boundaries need PAC/IAC/HC |
| Internal V–I taken as cadence | a 12-row cadence table for a 40-bar piece | cadence needs phrase close + metric arrival |
| Thematic groups taken as parts | a,b｜c,d｜e,f,g → "three parts" | each part needs cadential support |
| Agreeing with a ready-made answer | copying a chart/answer that says "binary" | verify independently with cadences |
| Citing a source and silently contradicting it | source gives A/B/C, conclusion says binary | cite, then state where and why you differ |
| Fabricated bar numbers under a title-only prompt | a confident 1–42 table with no score | tag `[inferred]`; no bar-level table without a score |
| Bar-number drift | quoting 14/22 from memory | count barlines; build the system table |

## Checklist

- [ ] Do the section bar counts add up to the total?
- [ ] Does every boundary either have a cadence or carry a "non-cadential" label?
- [ ] Are pause and cadence distinguished?
- [ ] Are texture return and theme return distinguished?
- [ ] Is the reprise measured (bars / phrases / does it close the tonic)?
- [ ] Are repeats and D.C./D.S. accounted for?
- [ ] Are thematic groups and parts distinguished, and is "part" vs "development" used consistently?
- [ ] Is the middle genuinely closed (new key + new theme + full cadence)?
- [ ] Is the genre gate cleared before binary/ternary was applied?
- [ ] Does every claim carry an evidence tag, and does the text avoid a bar-level table on `[inferred]` evidence alone?
- [ ] Is the rejected reading named, with the evidence that kills it?
- [ ] Do the conclusion and the diagram agree?
- [ ] Is the terminology consistent (binary / rounded binary / ternary / compound; with / without reprise)?

## Glossary (EN / 中文)

PAC 完满全终止 · IAC 不完满全终止 · HC 半终止 · PHC 弗里几亚半终止 · PC 变格终止 · DC 阻碍终止 · evaded cadence 规避终止 · period 乐段 · phrase 乐句 · motive 动机 · closed 收拢性 · open 开放性 · developmental 展开性 · false recapitulation 假再现 · supplementary cadence 补充终止 · exposition 呈示部 · development 展开部 · recapitulation 再现部 · coda 尾声 · introduction 引子 · trio 三声中部 · binary 二部曲式 · rounded binary 有再现单二部 · binary without reprise 无再现单二部 · ternary without reprise 并列单三部 · compound ternary 复三部曲式 · da capo 返始 · barform 巴曲式 · arch form 拱形曲式 · sonata-rondo 回旋奏鸣曲式.

## Worked example: Mendelssohn, *Kinderstücke* Op. 72 No. 2

- E-flat major, 2/4, 42 bars, *Andante sostenuto*.
- Cadences: bar 8 HC (V); bar 14 PAC (I); bar 22 pause (not a cadence); bar 32 climax (diminished seventh / augmented sixth, not a cadence); bar 38 dominant preparation; bar 42 PAC (I).
- Parts: A 5–14 (closed); B 15–38 (developmental, open); Coda 39–42.
- Form: **simple binary** (no reprise, with introduction and coda).
- Rejected reading: simple ternary — the closing bars bring back the *introduction's* accompaniment, not A's melody, and only for 4 bars.
- Lessons: do not mistake the closing accompaniment figure for a reprise; do not fold the dominant restatement (c, d) into A; do not turn the thematic groups (a,b ｜ c,d ｜ e,f,g) into three parts without cadential support.

Full cadence table, provenance tags, and the table of tempting-but-wrong readings: [examples/mendelssohn-op72-no2.md](examples/mendelssohn-op72-no2.md).
