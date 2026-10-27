# Fixed compact format for musical form analysis

English | [简体中文](compact-analysis-format.zh-CN.md)

This guide fixes the presentation fields, their order, and the notation style; findings must still be checked for each piece. **The complete analysis can be delivered in Chinese or English.** Follow an explicitly requested output language; otherwise match the user's message. Change chart/table headings, field labels, key names, cadence types, legends, notes, and the final reply together. Keep musical symbols and evidence tags unchanged. Include both languages in one result only when requested. An explicit request for another layout takes precedence; the evidence requirements still apply.

## Output-language mapping

The guide's language does not determine the result's language: this English guide can produce a wholly Chinese result, and the Chinese guide can produce a wholly English result.

| Chinese label / wording | English label / wording |
| --- | --- |
| 大段括线 | Section brackets |
| 乐句 | Phrase |
| 主体小节 | Core bars |
| 小节数 | Bar count |
| 调性／调式 | Key / mode |
| 终止到达 | Cadential arrival |
| 终止式 | Cadential formula |
| 终止类型 | Cadence type |
| 大段／乐句 | Section / phrase |
| 长度 | Length |
| 终止式与类型 | Cadential formula and type |
| 第N小节（必要时注明拍位）→ 新调性／调式 | m. N (beat, if needed) → new key / mode |
| 降E大调；c小调；D多利亚调式 | E-flat major; C minor; D Dorian |
| 完满全终止；不完满全终止；半终止 | Perfect authentic cadence (PAC); imperfect authentic cadence (IAC); half cadence (HC) |
| 未确认；暂定；连续衔接／无独立终止 | Not verified; provisional; continuous join / no independent cadence |

English charts may use `PAC`, `IAC`, and `HC` in cells, expanded in a short legend. Chinese charts use Chinese cadence names by default. Keep the same T/S/D notation in English when suitable, such as `D⁷—T, PAC`; explain tonic/subdominant/dominant in the legend. Translating only the title while leaving other labels and notes in the other language is insufficient.

## 1. Two opening items

1. **Form:** one sentence giving the form and any necessary qualification, such as “simple ternary with varied reprise; the middle section repeats on its own.” This is a wording example, not a form verdict to copy.
2. **Key / mode:** the home key plus a list of changes. Do not substitute a long harmonic discussion for clear bar locations and destination key names.

For every confirmed change, use the following field pattern. It does not describe an actual piece:

```text
m. N (beat, if needed) → new key / mode
m. M → return to [full home-key name]
```

- Give tonic and quality/mode: `E-flat major`, `C minor`, or `D Dorian`, rather than only “dominant key” or a letter.
- For Chinese output use `第N小节（必要时注明拍位）→ 新调性／调式`, with full names such as “降E大调” or “c小调”; a return must also name its bar and home key.
- Distinguish modulation, a change between parallel major/minor modes, brief tonicization, and a dominant prolongation. An accidental, a change of dynamics/texture, the start of a contrasting section, or a half cadence alone does not establish modulation.
- For gradual modulation or a pivot chord, distinguish the supported change span from the point of confirmation. If the exact onset is unclear, report “mm. N–M gradually move toward …” rather than inventing a precise beat.
- For brief tonicization without a confirmed new key, write “m. N: brief tonicization of …; modulation not established.” Do not include it among confirmed modulations.
- If the whole piece has been checked and no change is supported, write “The piece remains in [key]; no confirmed modulation or change of mode.” If only part is readable, write “Readable passages are in [key]; mm. N–M are not verified,” rather than asserting no change throughout.
- In Chinese the corresponding statements are “全曲为……；未发现可确认的转调或大小调转换” and “可辨部分为……；第N—M小节未确认”.
- Specify natural/harmonic/melodic forms of a mode only when the notation supports the distinction and it matters to the analysis; the key signature alone does not decide it.

## 2. Fixed chart layout

At the top, give the form name, the performed large-section sequence, and a short key/mode conclusion. Brackets show the main sections. Each column represents a supported phrase or unit at an appropriate level. Keep this row order:

```text
                   Section brackets (e.g. A, B, A′, as supported)
Phrase             Material label, such as a, a′, b
Core bars          Written span consistent with the numbering note
Bar count          Actual core length of this unit
Key / mode         Full name; include the bar of any within-phrase change
Cadential arrival  Arrival bar, with beat if needed
Cadential formula  Short harmonic-function formula
Cadence type       Type in the output language; not verified if unresolved
```

The row order is fixed, not the number of columns/sections or a four-/eight-bar length. Show links, expansions, contractions, non-cadential joins, and shared bars as supported; do not invent phrases or cadences to fill cells. Distinguish hierarchy, written spans, and performed repeat order.

Use a white background, clear brackets, and aligned columns. A light tint may highlight the key/mode row; decoration must not crowd the content. Render inversion numbers legibly. If a font cannot display `a‴`, use `a'''` rather than leaving a missing-glyph box. With many columns, widen the canvas or split the figure instead of shrinking text below readability.

## 3. Fixed matching-table columns

```text
Section / phrase | Core bars | Length | Key / mode | Cadential arrival | Cadential formula and type
```

- Each row corresponds to the same unit in the chart; key names, bars, lengths, formulas, and types must agree.
- Core spans may be separated from pickups, but the numbering note must locate the pickups. Use the actual cadential arrival, which need not be the span's last bar or final note.
- For a within-unit key change, write “original key → new key (m. N)” in the key/mode cell. Do not omit a change because it is not at a section opening. Locate the return to the home key in the same way.
- For a non-cadential boundary write “continuous join / no independent cadence.” If harmony is unreadable, write “formula not verified; cadence type not verified.” Key, formula, and type can have different levels of certainty; preserve each separately.
- Put the minimal supporting melodic/bass arrivals, inversions, and closure-level qualifications in brief notes below the table instead of adding a wide column for each item. Mark disputed cells “provisional” and briefly identify the evidence gap that matters to the conclusion.

## 4. Fixed cadence notation

Default to **T/S/D function symbols + necessary inversion or seventh + cadence type in the output language**, consistently across the table. Roman-numeral equivalents may be added in a short checking note; do not crowd every cell with parallel symbol systems.

| Notation example | Conditions |
| --- | --- |
| `D⁷—T, PAC` | Dominant seventh to tonic, both chords in root position, melody arrives on tonic, and the motion has cadential function |
| `D⁷—T, IAC` | Root-position dominant seventh to tonic with a melodic arrival on the tonic chord's third/fifth; if an inversion is present, change the formula to match |
| `T—D⁷, HC` | This actual progression has been verified and the phrase ends on the dominant seventh; it does not establish modulation to the dominant key |
| `S—D, HC` | Subdominant-to-dominant motion and phrase-ending function are verified; do not replace the actual path to fit a preferred template |
| `K⁶₄—D⁷—T, PAC / IAC` | The cadential 6/4 and following chords are verified; classify the actual arrival separately |

These examples specify notation and conditions, not ready-made answers:

- T means tonic function, S subdominant, D dominant, D⁷ dominant seventh, and K⁶₄ cadential 6/4. Plain text may use `K46`, with its 6/4 meaning stated. D⁷ must not replace a dominant triad D, and not every close should be filled out as `K⁶₄—D⁷—T`.
- Preserve actual inversions and chord qualities. If T/S/D does not clearly express minor-mode, modal, or unusual harmony, use an explained Roman-numeral or suitable alternative convention rather than imposing a major-key formula.
- **Check formula and type separately.** The same `D⁷—T` can support different authentic-cadence types; bass, melodic arrival, inversions, and phrase function still matter. An internal dominant–tonic progression is not automatically a cadence.
- Use half, plagal, deceptive, evaded/aborted, and other cadence categories where supported; do not force every row into PAC or IAC. If harmony is unknown, dependent type and tonal-closure judgments remain unresolved.

Use a short legend for only the symbols that appear in the result, and one or a few arrival-note comments to support easily confused types. Unless detailed harmony is requested, omit beat-by-beat passing chords and ornaments.

## 5. Brief numbering, repeat, and evidence notes

Below the chart/table, state the details needed to locate the claims:

- Source file/page/system and whether numbers come from the edition or are assigned for this analysis. For assigned numbers, check bars per system. Distinguish a complete bar that begins with rests from a true incomplete pickup bar; do not always call the opening bar 0 or 1.
- Whether repeats are expanded; the numbering and route of first/second endings; and actual D.C./D.S. navigation. Do not count an alternative ending as an extra consecutive phrase.
- Exact pickup positions, within-bar entries, and shared bars. Explain core lengths separately from spans that include pickups. Count shared bars only once in the total.
- Tag source/observed material with `[score]`, `[audio]`, `[midi]`, `[lit]`, or `[reported]`; mark form, key, and cadence interpretations `[inferred]` and give support. A tag may cover an explicitly identified group of chart/table fields, but locators must remain traceable.

## 6. Delivery and storage

With sufficient evidence and rendering tools, deliver one structural PNG chart and a matching concise Markdown report. In the final reply, show the PNG using its absolute local path and include a link to the actual file. Open it first to check Chinese/English text, superscripts/primes, alignment, and clipping; a tool's success message alone is not delivery. Without rendering tools, use a text chart/table with the same fields and state that no image was generated.

Save analysis artifacts, crops, and temporary files **outside the source/current project** by default. Prefer the session's agreed destination or a platform output folder that lies outside the project; otherwise a user-document folder such as `CodexOutputs/musical-form-analysis/` is suitable. Do not hard-code a user's name or absolute path. Honor an explicit destination. This rule concerns analysis artifacts and does not prevent authorized edits to the skill's source files.

The fixed format never overrides the main skill's evidence requirements. For title-only input or unverified bars, give a limited result and identify missing evidence; do not create a complete-looking chart with invented bars, key changes, or cadence types.
