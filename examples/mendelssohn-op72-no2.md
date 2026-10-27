# Worked example — Mendelssohn, *Kinderstücke* Op. 72 No. 2

> **This is a format demonstration, not an authoritative analysis.** The bar numbers follow the boundary list of the cited article (see §6); nothing here has been checked against a printed score. Rows the article's boundary list does not cover are tagged `[inferred]`. A real run must tag every row from its own evidence — see "Evidence and limits" in `SKILL.md`.

**Piece:** Felix Mendelssohn Bartholdy, *Sechs Kinderstücke für das Pianoforte*, Op. 72 No. 2 `[lit]`
**Key / meter / tempo:** E-flat major, 2/4, *Andante sostenuto* `[lit]`
**Length:** 42 bars `[lit]` — "7 systems × 6 bars" is this example's own reconstruction, not an observation `[inferred]`

## 0. Evidence

| Tag | Where it comes from here |
|---|---|
| `[lit]` | the boundary list of the cited article, or the work's key/meter/tempo metadata |
| `[inferred]` | cadence typing and canonic detail by this analysis, without the score |
| `[score]` | would be used for every row in a real run |

## 1. Cadence table

| Bar | Cadence | Key | Evidence | Note |
|---|---|---|---|---|
| 8 | HC | V (B-flat) | `[inferred]` | phrase *a* closes on the dominant |
| 14 | PAC | I (E-flat) | `[lit]` | phrase *b* closes in the tonic — **A ends here** |
| 18 | close in the dominant area | B-flat (temporary) | `[inferred]` | phrase *c*, the theme restated on the dominant |
| 22 | pause, **not a cadence** | open | `[lit]` | phrase *d*; "a certain pause" |
| 32 | — | — | `[inferred]` | climax (diminished seventh / augmented sixth) — not a cadence |
| 38 | dominant preparation | V | `[lit]` | end of the instrumental recitative |
| 42 | PAC | I (E-flat) | `[lit]` | final bar |

## 2. Sections

| Part | Bars | Contents | Close |
|---|---|---|---|
| Introduction | 1–4 | accompaniment figure; theme pickup on beat 2 of bar 4; joins A at a **non-cadential boundary** | — |
| **A** | 5–14 | a 5–8 (HC), b 9–14 (PAC) | **closed in the tonic** |
| **B** — a development, not an independent part | 15–38 | c 15–18 (theme on the dominant), d 19–22 (pause), e 23–26, f 27–30, g 31–34 (climax at 32), recitative 35–38 | **open**, dominant preparation |
| Coda | 39–42 | echo of the introduction's figure | starts at a **non-cadential boundary** (39); closes **PAC** at 42 |

Under rule 3 (theme + cadence + weight) B fails the cadence test, so it is a **development**; `B` is kept only as a position label, so the diagram stays readable.

```
Intro(1–4) + A(5–14: a5–8, b9–14) + B(15–38) + Coda(39–42)
= 4 + 10 + 24 + 4 = 42
```

## 3. Conclusion

**Simple binary form, without reprise, with introduction and coda.**

- A is a closed period (HC → PAC) `[lit]` for the PAC at 14.
- B is developmental: it opens with the theme restated on the dominant, passes through a pause, introduces new material, builds to the climax at bar 32, and dissolves into a recitative that prepares the dominant.
- The coda returns to the introduction's accompaniment figure — a frame, **not** a recapitulation of A.

**Rejected reading:** simple ternary (A–B–A′). It fails because no theme of A returns after B: bars 39–42 bring back the introduction's *accompaniment*, not A's melody, and only for 4 bars — below the ≥ half-of-A threshold in rule 2.

## 4. Why not ternary (and why the tempting readings fail)

| Reading | Why it tempts | Why it fails |
|---|---|---|
| Simple ternary (A–B–A′) | three thematic groups (a,b ｜ c,d ｜ e,f,g) | no theme returns after B; only the intro's accompaniment comes back |
| Rounded binary (A B A′) | something *does* come back at 39 | the return is the intro's texture, not A's theme, and only 4 bars — a frame, not a reprise |
| Compound ternary | the middle feels like a "trio" | no closed middle in a contrasting key, no da capo, 42 bars total |
| Binary with A = 5–22 | sounds like "theme + restatement" | bar 14 is already a PAC; c, d are the dominant restatement that opens B |

## 5. Takeaway

The decisive evidence is the **cadence plan**: one closed part (A), one open development (B), one closing coda. That is binary, regardless of how many thematic groups the middle contains.

## 6. Source, and where this analysis differs from it

The bar numbers follow the German Wikipedia article on the *Sechs Kinderstücke*, whose boundary list is
**intro 1–4 · A 4–14 · B 14–22 · C 22–34 · recitative 34–38 · postlude 38–42** — a three-part reading.
(A real run cites the permalink and access date; the URL is omitted here.)

This analysis keeps 5–14 / 15–38 / 39–42 and concludes **binary**, i.e. it disagrees on purpose:

- the article's `A` and `B` split at 14, but 14 is already a PAC — A is closed there, which is what makes it a part;
- the article's `C` (22–34) plus recitative (34–38) has **no closing cadence** — it runs open into the dominant, so c–g and the recitative are one development, not a part.

Two one-bar discrepancies remain and must be settled against the score, not against either text:

| Item | Article | This table |
|---|---|---|
| Start of A | bar 4 (counts the pickup) | bar 5 |
| Start of the recitative | bar 34 | bar 35 |

Leaving them unresolved is the point: quoting a boundary from memory while the neighbouring bar count drifts is the **bar-number drift** pitfall in `SKILL.md`, and it is invisible unless the evidence tag says where the number came from.
