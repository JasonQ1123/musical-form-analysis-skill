# Musical Form Analysis — an Agent Skill

English | [简体中文](README.zh-CN.md)

A portable skill for evidence-based musical form analysis: relate thematic and tonal organization, cadences, and formal function to a checkable diagram, while preserving uncertainty where the sources do not decide.

The entrypoint is SKILL.md with YAML name and description fields. It is plain Markdown and can be used by compatible skill loaders. Score reading, listening, MIDI parsing, and source retrieval depend on the host's available tools; this repository does not implement them.

## Why

The skill addresses recurring mistakes:

1. treating an accompaniment return as a thematic recapitulation;
2. treating a pause or internal V–I as a cadence;
3. confusing thematic groups with large formal parts;
4. using da capo, section length, or a closed middle as a sufficient classification rule;
5. attaching precise bar numbers and cadence labels to claims that lack evidence;
6. confusing thematic relationship with formal function: a transformed motive need not be a new theme or a structural reprise, and a transition need not be a third main part;
7. hiding a cadence's harmonic basis behind a label, or treating a guessed formula as support for a confident cadence and closure judgment.

It distinguishes observations from interpretations, considers the whole-form organization before its subsections, and compares plausible alternative readings without requiring a false certainty.

## Install

The following commands use DSH's skill directory. For another compatible host, use that host's configured skills directory.

User-wide (all projects):

~~~bash
git clone https://github.com/JasonQ1123/musical-form-analysis-skill.git
mkdir -p ~/.dsh/skills
cp -r musical-form-analysis-skill ~/.dsh/skills/musical-form-analysis
~~~

Project-wide:

~~~bash
mkdir -p .dsh/skills
cp -r musical-form-analysis-skill .dsh/skills/musical-form-analysis
~~~

The name field identifies the skill; keeping the installed folder name identical to it is the safe default.

## Use

Ask naturally in English or Chinese:

- “What form is this piece?”
- “Is this simple ternary or compound ternary?”
- “Is this binary or ternary — and is it rounded?”
- “Is this a sonata?”
- “Analyse the form of this score” with an attached score.
- “单三还是复三？” / “单二还是单三？” / “这首曲子是什么曲式？” / “是不是奏鸣曲式？”

The agent establishes its sources and coordinates, examines themes, tonal movement, cadences, and hierarchy, then gives the supported diagram and conclusion. A bar-level table is included only when bar-level evidence exists. Title-only input does not justify invented segmentation.

For score-based results, the default is a compact study sheet: section brackets over phrase columns, followed by phrase labels, bar spans, lengths, key/mode, cadential arrival, formula, and type. Verified key/mode changes are tied to their bar/beat and destination; no change and unresolved passages are stated explicitly. Cadences use short supported forms such as `D⁷—T, PAC` (perfect authentic cadence), with brief evidence notes. When rendering is available, the PNG chart and matching concise Markdown report are saved outside the source/project directory unless another destination is requested. The [fixed compact format](references/compact-analysis-format.md) specifies the layout and notation; it does not prescribe a piece's form, keys, or phrase lengths.

The analysis can be delivered entirely in Chinese or English. Request the language explicitly, or let it follow your message. Chart/table labels, key and mode names, cadence types, legends, notes, and the final reply change together; musical symbols and evidence tags stay the same. The fixed-format guide is available in [English](references/compact-analysis-format.md) and [简体中文](references/compact-analysis-format.zh-CN.md).

## What is inside

[SKILL.md](SKILL.md) ([简体中文](SKILL.zh-CN.md)) contains:

- input handling for score, audio, MIDI, descriptions, and title-only questions;
- evidence tags for inspected notation, recordings, MIDI events, literature, reported observations, and inference;
- context-sensitive boundary and return criteria without universal length thresholds;
- cadential formulas (K46–D–T, D–T, S–D, or Roman-numeral equivalents) where supported, with separate uncertainty for harmony, cadence type, and closure;
- bar/beat-specific key and mode changes, distinguished from tonicization and half cadences, plus a fixed compact chart/table format for keys and cadences;
- separate labels for material identity and formal function: an a-derived passage can serve as a transition without becoming a new theme or a structural reprise;
- conditional score-image correction when readability requires it, with musical identity checked from notation rather than pixel similarity alone;
- a workflow covering coordinates, cadences, thematic/tonal organization, structural levels, classification, and output;
- whole-form criteria for sonata, rondo, variations, bar form, arch, and through-composed designs;
- binary/ternary distinctions that separate tonal closure, thematic return, closing parallels, and internal hierarchy;
- output checks and an EN/中文 glossary.

[Synthetic decision cases](examples/decision-cases.md) provide explicit input facts and expected reasoning for common confusions, including transformed transitional material, unknown cadence formulas, and skewed score comparisons. They are constructed examples, not claims about real compositions or tests of score-reading or image-processing accuracy.

[The Mendelssohn evidence audit](examples/mendelssohn-op72-no2.md) replaces the earlier unverified worked analysis. No score, recording, or retrievable supporting citation accompanies that case, so it does not establish a form label, cadence table, or bar count for the piece.

## Example output from synthetic supplied observations

Suppose the supplied description establishes that the first repeated section ends in the dominant, and its closing melody returns in the home tonic at the end of the second repeated section. The opening theme does not return.

> The supplied description supports **continuous, balanced binary form** [reported, inferred]. The first reprise ends away from a home-tonic close; the second ends with the first reprise's closing material adjusted to the home tonic [reported]. “Balanced” refers to that closing correspondence, not equal lengths [inferred]. Rounded binary is less supported because the description reports no structural return of the opening theme [reported, inferred]. This reading has not been checked against a score.

## Scope and limits

- Cadence terms primarily follow common-practice tonal conventions. Adapt the analysis to the repertory and identify textbook conventions when they affect the label.
- Formal categories can be hierarchical: a rondo refrain or a trio can itself be binary. The skill does not require a single label to describe every level.
- The focus is section-level form. Harmonic and motivic detail should support that task rather than become an unrelated full analysis.
- Current examples validate reasoning from stated facts and evidence limits. They do not provide a score-verified benchmark for real compositions.

## License

MIT — see [LICENSE](LICENSE).
