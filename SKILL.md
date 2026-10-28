---
name: musical-form-analysis
description: Analyze musical form, section boundaries, thematic returns, competing readings, key/mode changes, and cadences from available score, audio, MIDI, or cited evidence, with Chinese or English output. Use for binary/ternary distinctions, rondo, variations, sonata, and related form questions; 中文：分析曲式、划分段落、单二还是单三、单三还是复三、是不是奏鸣曲式、调式转变小节与终止式简图。
---

# Musical Form Analysis

English | [简体中文](SKILL.zh-CN.md)

Analyze form from checkable observations of themes, tonal movement, cadences, and formal function. Distinguish observation from interpretation; do not turn one plausible reading into a rule for every piece.

Produce a fully localized Chinese or English analysis in the language explicitly requested; otherwise match the user's language. Localize the chart/table headings, key and mode names, cadence types, legends, notes, and final reply together. Keep evidence tags and musical symbols unchanged. Provide both languages together only when requested; the exact label mappings are in the compact-format reference.

## Scope and input

The cadence terminology below primarily fits common-practice tonal music. For earlier, later, non-tonal, or mixed repertory, state the analytical convention and use relevant thematic, rhythmic, textural, or textual organization rather than forcing a tonal form label.

- **Score or scan:** inspect the actual notation using available tools. Establish the edition and measure numbering. If a passage is illegible, identify its location and leave its details unresolved.
- **Audio:** use an available recording and identify it. Give timestamps; use bar numbers only when reliably aligned to a score or a verified counting scheme.
- **MIDI:** use an available event reader or renderer. Verify time signatures, pickup, tracks, and measure mapping before citing bars. MIDI events can support pitch/rhythm observations, but do not by themselves establish notated repeat signs, spelling, or the intended edition.
- **Text description:** attribute the supplied observations to the user or document; do not represent them as your own score reading.
- **Title only:** look for an identifiable score, recording, or published analysis if suitable tools are available. If none can be inspected, say so and limit the answer to a provisional hypothesis or the evidence needed to decide. A genre expectation is not a finding about this work.

This skill supplies an analytical procedure, not a score-recognition, listening, MIDI-parsing, or retrieval tool. State material access limits before presenting the analysis; use what the environment actually supports.

## Screenshot and image budget

- Reuse supplied images and local score files. When file access is available, inspect or render the source directly instead of repeatedly capturing a score viewer. Cache each needed page rendering and reuse it for later crops. If its resolution cannot resolve a specific notational detail, allow one higher-resolution re-render of that local passage from the source and cache the result. Do not render the whole score in advance merely to make images available.
- Keep a short text record of inspected pages/systems/bars, observations, unresolved questions, and saved image paths. Reuse those observations through segmentation, cadence checking, and report writing; a new analytical step does not itself require another screenshot or redisplay.
- Before requesting another image, identify the specific missing musical fact and its location. If the existing view is readable, continue from it. For the same unresolved detail, default to at most one additional close-up, including any targeted source re-render, containing the relevant staves and enough surrounding context. If it remains illegible, mark it unverified rather than cycling through screenshots or zoom levels.
- Plan long-score inspection in stages. Default to a soft budget of four images returned for inspection per stage, with a cumulative checkpoint at eight known image returns in the current conversation. Count page views, crops, re-rendered close-ups, and redisplays; these working defaults are not API size limits. Before exceeding either checkpoint, save a concise text record of covered locations, supported findings, unresolved questions, image paths, the known cumulative count, and the remaining scope. Extend the budget only for named necessary passages with a bounded extra-image count. If many pages remain, provide partial findings and a text handoff for a fresh conversation instead of repeatedly starting more batches. A new stage does not reset the cumulative count or remove earlier image messages; do not invent counts for unavailable history.
- Return one image per inspection call by default. For long scores, inspect needed pages sequentially and retain text notes; do not return a whole-score image batch or both a full page and its crops together. Prefer a relevant system/passage crop over another full-page or full-screen image. Preserve accidentals, ledger lines, voice context, and arrival notes; do not shrink notation until those details disappear. Keep originals on disk and do not print base64 into tool output or chat.
- If a tool or request reports `413` / `Payload Too Large`, stop image capture and resubmission. Do not retry the same payload or add more images. Preserve available findings and paths as text; use a smaller crop only if the environment supports a genuinely smaller request. If accumulated conversation images still prevent requests, report the limitation and provide a text handoff for a fresh conversation when possible; do not claim that saving files removes earlier image messages.
- For generated chart checks, open the final PNG once. Reopen only after a material correction, focusing on the changed area when possible; avoid screenshots after every layout adjustment. Keep the required final inline preview and file link.

## Evidence contract

Attach evidence tags to factual observations in the text, table rows, and diagram. A tag may cover a clearly identified group of observations; do not repeat it after every word.

| Tag | Meaning and locator |
|---|---|
| [score] | notation directly inspected; identify edition/file and bar, beat, page, or system |
| [audio] | recording directly heard; identify recording and timestamp |
| [midi] | events directly inspected; identify file, track, and verified bar or tick range |
| [lit] | a claim actually supported by a consulted source; give a retrievable link or bibliographic citation and page/section |
| [reported] | an observation supplied by the user or another unverified description; attribute it |
| [inferred] | an analytical interpretation or hypothesis; state its supporting observations and uncertainty |

- A source's section boundary does not also establish its cadence type, harmony, or thematic content. Attribute only what the source supports. Cite and explain disagreements with published readings.
- In a mixed-evidence row, distinguish supported observations from inferred details. For example, a sourced boundary and an unverified PAC are two different claims.
- Do not invent measure numbers, keys, cadences, or source details. Without inspected or explicitly sourced/reported bar-level observations, omit the bar-level cadence table. An [inferred] label does not license invented precision.
- Literature-only and user-description analyses are possible, but must be identified as such. Keep unresolved claims unresolved; a partial table is preferable to guessed rows.

## Analytical criteria

1. **Boundaries have several kinds of support.** Cadential arrival is strong evidence, considered alongside thematic entry, tonal movement, rhythm, texture, and formal function. A pause or an internal V–I is not automatically a cadence. Main sections can also join continuously, overlap, or begin by elision; explain a non-cadential boundary at any level rather than inventing closure.
2. **Formal hierarchy matters more than length.** Motives, phrases, themes, sections, and large parts are different levels. No universal eight-bar minimum, two-phrase minimum, or half-of-A threshold distinguishes them. Proportion is supporting evidence, interpreted in context.
3. **Returns must be identified by content and function.** Distinguish a theme's return from an accompaniment return, an introductory frame, a closing parallel, and a recapitulation. A return can be compressed, varied, or transposed. Its role in the whole decides the form, not a minimum duration alone.
4. **Label material identity and formal function separately.** Transposition, shortening, or a new tonal goal does not by itself make a-derived material a new theme c. Record the relationship (for example, a′ or an a-derived fragment) alongside its function (transition, continuation, or dominant preparation). Related material is not automatically a structural reprise, either. Show a transition/link as subordinate to a section or as a connector/shared span when supported; it need not be assigned wholly to one side, and its presence alone does not create a third main part.

## Workflow

### 1. Establish coordinates and the large shape

- Confirm the work/movement and the source actually available. Note pickup, numbering conventions, repeats, endings, D.C./D.S., Fine, and Coda instructions.
- Distinguish notated measure numbers from performed order and repeat-expanded duration. Follow the actual navigation instructions; a da capo establishes a return, not a form label.
- For a scan, count the bars in each system as needed; do not assume equal bars per system. Keep beat-level boundaries when a theme starts within a bar.
- Check a photographed score's readability first. If skew, curvature, or perspective obstructs reading, use available tools to crop or correct it as needed, retaining the original; clear notation needs no preprocessing. If using pixel comparisons, align the relevant local staff lines before comparing. Judge musical identity from pitches, rhythms, and voice context rather than pixel similarity alone. If the notation remains unreadable, leave the comparison unresolved.
- Sketch the large thematic/tonal trajectory before detailed segmentation. Track changes of tempo, texture, and accompaniment as clues rather than automatic section divisions.

### 2. Locate phrase endings and cadences

Check harmonic motion, bass and melodic arrival, phrase function, and rhythmic/metric placement together. A strong beat supports a cadence but is not an absolute requirement. Distinguish the arrival from its preparation and from a later extension.

| Type | Common-practice criterion |
|---|---|
| PAC | V(7)–I, both chords in root position, tonic in the melodic upper voice at arrival |
| IAC | authentic arrival lacking a PAC condition, such as inversion or a non-tonic melodic ending |
| HC | phrase-ending arrival on V |
| PHC | minor-mode half cadence with iv6–V |
| Plagal | IV–I with closing function; distinguish a post-cadential extension from the principal close |
| Deceptive | an expected authentic close redirected, commonly V–vi in major or V–VI in minor |
| Evaded / aborted | an expected arrival is avoided or interrupted; identify what continues or starts there |
| Pause | a rhythmic event; cadence status must be established separately |

Name the local key and whether it is established or merely tonicized. A cadence in the dominant key can close a local theme while leaving the larger form tonally open. Specify the level meant by “open” or “closed.” An evasion weakens a closure claim but does not by itself forbid a thematic or formal boundary.

Track key/mode changes with their supported bar/beat of entry and destination, including returns to the home key. Distinguish modulation, a change of mode, tonicization, and a phrase ending on the dominant. A contrasting section, a new accidental, or a half cadence alone does not establish a new key. If a change is gradual or its exact onset cannot be established, give a supported span rather than an invented bar. When the inspected evidence supports no change, say so explicitly; when coverage is incomplete, keep the unchecked span unresolved.

Where the harmony can be established, record the **cadential formula** alongside the type: K46–D–T, D–T, S–D, K46–D, or a suitable Roman-numeral equivalent such as V7–I. Here K46 means cadential 6/4 and T/S/D name tonic/subdominant/dominant functions. Identify the local key and actual chords/inversions where supported; a function symbol alone is not a key or a complete chord specification. The formula exposes the harmonic interpretation for checking, but does not by itself establish a cadence or distinguish PAC from IAC: melodic arrival, inversion, and phrase function also matter.

Track uncertainty separately for the key, formula, cadence type, and closure. If the harmony is unreadable or unsupported, write **unknown / not verified** rather than supplying a likely formula to fill the row. Give an inferred formula only when specific observations support it, with its uncertainty. Any cadence or closure judgment that depends on unresolved harmony must remain provisional or undetermined; independently supported observations can still be reported.

For example, if the only readable features at a candidate boundary are a rest and a repeat sign, those features may be tagged [score]. The key, formula, cadence type, and tonal closure remain undetermined. The signs do not establish K46–D–T, PAC, or a home-tonic close.

When evidence supports a table, keep location, local key, harmonic formula, melodic/bass support, cadence/arrival type, closure level, formal role, and evidence distinguishable. Use the compact columns specified below; put supporting arrival notes and any closure-level distinction in brief notes rather than adding a wide column for every analytical field. Mark uncertain fields and gaps rather than filling every row.

### 3. Track material and structural levels

Label thematic ideas a, b, c as useful. Track repetition, variation, fragmentation, sequence, and returns. For candidate sections, assess thematic identity, tonal trajectory, closure, contrast, proportion, and role in the whole. No single feature is mandatory for every repertory.

Keep lower-case thematic labels separate from upper-case formal sections. Distinguish a developmental passage from a sonata development; new material need not constitute an independent section. Record the internal design of large sections when testing simple versus compound forms.

### 4. Test the whole-form organization

Consider these before reducing the whole to two or three parts. They can contain binary/ternary subsections or overlap as descriptions; this is not an exclusive genre gate.

| Organization | Evidence to examine |
|---|---|
| Sonata | exposition's tonal/formal trajectory and its later resolution, usually in a tonic-oriented recapitulation; contrasting first/second melodies are not required |
| Sonata-rondo | recurring refrain combined with exposition/recapitulation functions and tonal resolution |
| Rondo | recurrent refrain alternating with episodes, commonly ABACA or ABACABA; count appearances including the initial statement, and allow altered or shortened returns |
| Variations | a theme or framework organizing successive transformations, sectional or continuous; an intact restatement can still occur |
| Bar form (AAB) | two Stollen followed by an Abgesang at the relevant structural level; the units need not be single phrases |
| Arch | a meaningful thematic or tonal mirror, such as ABCBA; say what is mirrored |
| Through-composed | no governing large-scale sectional recurrence or variation scheme; local motives can still recur |

### 5. Distinguish binary and ternary readings

Use the reprise layout, tonal plan, internal design, and formal functions together. Repeat marks support the layout without determining it alone.

| Reading | Working criterion |
|---|---|
| Binary | two principal reprises/parts, often repeated; the second completes the overall tonal/formal trajectory |
| Sectional binary | the first reprise closes in the home tonic |
| Continuous binary | the first reprise ends away from a home-tonic close, commonly in the dominant or relative key |
| Simple binary (unrounded) | no structural return of the opening theme in the latter part; closing parallels may still occur |
| Rounded binary | opening material returns within the second reprise's departure-and-return trajectory; do not impose a return-length cutoff |
| Balanced binary | recognizable closing material of the first reprise returns at the end of the second, normally adjusted to the home tonic; equal section lengths are not the criterion |
| Simple ternary | A–B–A′ at the main level, with a contrasting middle and a return functioning as the third main section; sections need not have equal lengths or uniformly closed endings |
| Compound ternary / trio form | a large A–B–A organization whose main units have subordinate sectional designs, commonly binary/ternary designs in minuet-and-trio or scherzo-and-trio; inspect the internal hierarchy |

“Sectional/continuous,” “rounded/unrounded,” and “balanced” describe different properties and can combine. Do not present them as mutually exclusive labels. A complete da capo or a closed contrasting middle can occur in simple ternary; neither proves compound ternary. Conversely, no fixed small bar count rules out a compound organization.

For rounded binary versus ternary, explain whether the return belongs to the second reprise's ongoing trajectory or functions as the third main section. Proportion, closure, repeat layout, and thematic completeness support that judgment; none settles it alone. If the evidence supports both readings, explain the ambiguity instead of forcing a unique answer.

If a user's textbook calls an ABC design “ternary without reprise / 并列单三部,” state that convention and justify the hierarchy. Three themes or three cadences alone do not establish three main parts.

### 6. Present the result

Use the fixed compact study-sheet format in [Compact analysis format](references/compact-analysis-format.md); read it when preparing the deliverable. Keep the language requested by the user. Its layout and notation are defaults for this skill; its example symbols are not findings about a new piece.

- **Lead:** one-sentence form conclusion and a short key/mode summary. List each verified change as `m. N (beat, if needed) → new key / mode`, including a later return; otherwise explicitly state no confirmed change or identify the unresolved span. Use the corresponding Chinese wording for Chinese output.
- **Chart:** formal-section brackets above phrase columns, followed by the fixed rows `Phrase → Core bars → Bar count → Key / mode → Cadential arrival → Cadential formula → Cadence type`, or their mapped Chinese labels. Use the actual hierarchy, number of phrases, and lengths; do not force A–B–A′ or 4+4.
- **Matching table:** `Section / phrase | Core bars | Length | Key / mode | Cadential arrival | Cadential formula and type`, or the mapped Chinese columns. Prefer short supported notation such as `D⁷—T, PAC` / `D⁷—T，完满全终止` or `T—D⁷, HC` / `T—D⁷，半终止`. Expand English abbreviations in a short legend. Preserve inversions and keep formula, cadence type, and key uncertainties explicit.
- **Brief notes:** source and evidence tags; numbering, pickups, repeat navigation and shared bars; the bass/melodic arrivals needed to check cadence labels; and any material limitation or consequential competing reading. Do not turn the compact summary into a full harmonic essay unless requested.
- **Files:** for an adequately supported score analysis, render the chart as a PNG when tools permit and save a matching concise Markdown report. Put generated analysis files outside the source/project directory unless the user explicitly chooses another destination. Show the PNG inline and link to the saved file after checking it opens. If rendering is unavailable, give the same layout as a text/table without claiming an image was produced.

Without adequate bar-level evidence, omit unsupported chart/table fields or give a limited textual result. The fixed format never requires invented bars, changes of key, or complete-looking cadence rows.

## Final checks

- Do all factual details have traceable score/audio/MIDI, literature, or reported support?
- Are cadence, pause, thematic entry, and formal boundary distinguished?
- Are local tonal closure and home-tonic closure distinguished?
- Are verified key/mode changes tied to their bar/beat and destination, including returns, without mistaking tonicization or a half cadence for modulation?
- Are repeat navigation, pickup, within-bar starts, overlaps, and counting conventions accounted for?
- Does the form label match the hierarchy, thematic/tonal trajectory, and diagram?
- Were any duration threshold, repeat sign, or closed middle used as a verdict by itself?
- Are material identity and formal function distinguished, including in transitional passages?
- Are formula, cadence type, and closure supported separately, with uncertainty carried into dependent judgments rather than hidden by an [inferred] tag?
- If image processing was needed, was musical identity checked from notation rather than pixel matching alone?
- Does the conclusion preserve unresolved evidence and plausible alternatives?
- Do the chart and table agree in the fixed compact layout, with clear arrival locations and short, supported cadence formulas?
- Are headings, key/mode names, cadence labels, legends, and notes all in the requested output language rather than only translating the document title?
- Are generated analysis artifacts outside the project unless another destination was requested, and are delivered PNGs openable and linked?

## References and examples

- [Compact analysis format](references/compact-analysis-format.md): required default presentation for the chart, key/mode changes, cadence notation, numbering notes, and external artifact delivery. Read when preparing an analysis result.
- [Synthetic decision cases](examples/decision-cases.md): consult for contrasts involving da capo, internal hierarchy, balanced/rounded binary, material versus function, uncertain cadence fields, and scan comparisons. These test reasoning from supplied facts, not score-reading or image-processing accuracy.
- [Mendelssohn evidence audit](examples/mendelssohn-op72-no2.md): consult when an earlier analysis or title-only prompt offers unverified precise claims. This is not a worked score analysis or an answer key for Op. 72 No. 2.

## Glossary (EN / 中文)

PAC 完满全终止 · IAC 不完满全终止 · HC 半终止 · PHC 弗里几亚半终止 · plagal cadence 变格终止 · deceptive cadence 阻碍终止 · evaded cadence 规避终止 · cadential formula 终止式 · K46 终止四六和弦 · S 下属功能 · D 属功能 · T 主功能 · period 乐段 · phrase 乐句 · motive 动机 · transition/link 连接部 · exposition 呈示部 · development 展开部 · recapitulation 再现部 · coda 尾声 · introduction 引子 · trio 三声中部 · binary 二部曲式 · rounded binary 再现二部曲式（常见教材称再现单二部） · simple ternary 单三部曲式 · compound ternary 复三部曲式 · da capo 返始 · bar form 巴曲式 · arch form 拱形曲式 · sonata-rondo 回旋奏鸣曲式。Terminology varies by textbook; state the convention when it affects the classification.
