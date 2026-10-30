<div align="center">

<img src="assets/banner.svg" alt="uxpeak UX/UI rules for Claude" width="100%">

[Русский](README.md) | **English**

[![Claude Code](https://img.shields.io/badge/Claude%20Code-plugin%20v1.0.0-0969da?style=flat-square&logo=claude&logoColor=white)](.claude-plugin/plugin.json)
[![YouTube](https://img.shields.io/badge/source-YouTube%20%40uxpeak-1f2328?style=flat-square&logo=youtube)](https://www.youtube.com/@uxpeak)
![Videos](https://img.shields.io/badge/videos-23%20·%205.5%20h-1f2328?style=flat-square)
![Language](https://img.shields.io/badge/lang-RU-1f2328?style=flat-square)
[![Test](https://img.shields.io/badge/test-17%2F17%20flaws%20found-1f2328?style=flat-square)](evals/product-page-review/README.md)

A Claude skill that reviews and designs interfaces by the rules of the
**[uxpeak](https://www.youtube.com/@uxpeak)** YouTube channel: everything the author teaches across
all of the channel's videos, as do's, don'ts and the reasons behind them.

```
/plugin install uxpeak-ux-ui --marketplace DiasTime/uxpeak-ux-ui
```

</div>

---

> **Note.** The skill itself is written in Russian. Claude reads it fine and answers in the language
> of your conversation; only the files in this repository are in Russian.

## What it does

The skill triggers on its own whenever the conversation is about interfaces: a screen review, a
redesign, a product page, a paywall, onboarding, filters, search, bottom navigation, conversion.

| Mode | When | What you get |
| :-- | :-- | :-- |
| **Review** | A screenshot, Figma frame, HTML or live page | Findings ranked critical → important → polish → next level, each with what is wrong, why, and a concrete fix |
| **Design** | A new screen, flow or front-end code | A step-by-step process from ranking elements to micro-interactions, with concrete numbers for tap targets, sizes and contrast |
| **Compare** | "Which of these two is better?", A/B | Which question each variant asks the user, the interaction cost, where the trust is |

It complements visual-style skills such as `design-taste-frontend`: those set the look, this one
makes the UX decisions.

## Install

This is a Claude Code plugin, and the repository doubles as the `diastime` marketplace, so it
installs in one step.

**Inside Claude Code** (2.1.275 or later):

```
/plugin install uxpeak-ux-ui --marketplace DiasTime/uxpeak-ux-ui
```

**From a terminal:**

```bash
claude plugin install uxpeak-ux-ui --marketplace DiasTime/uxpeak-ux-ui
```

**Older versions**, in two steps:

```
/plugin marketplace add DiasTime/uxpeak-ux-ui
/plugin install uxpeak-ux-ui@diastime
```

The skill is available in the next session (or right after `/reload-plugins`). It triggers on its
own; to call it by hand, use `/uxpeak-ux-ui:uxpeak-ux-ui`. Add `--scope project` to share it with
everyone who opens the project.

| Action | Command |
| :-- | :-- |
| Update | `claude plugin update uxpeak-ux-ui@diastime` |
| Disable | `claude plugin disable uxpeak-ux-ui@diastime` |
| Uninstall | `claude plugin uninstall uxpeak-ux-ui@diastime` |

<details>
<summary><b>Without the plugin system: a plain skill folder</b></summary>

Clone into your skills folder; recent Claude Code versions load it as the `uxpeak-ux-ui@skills-dir`
plugin:

```bash
git clone https://github.com/DiasTime/uxpeak-ux-ui.git ~/.claude/skills/uxpeak-ux-ui
```

For older versions or other agents, copy just [`skills/uxpeak-ux-ui`](skills/uxpeak-ux-ui) into
your skills folder: it is a self-contained skill with its own `SKILL.md`.

</details>

## The 12 core ideas

1. **Every element asks the user a question.** Make it an easy one: "can I try it for free?"
   instead of "is this worth $19 a month?".
2. **Rank first, then design.** If you can't say what gets read first, neither can the user.
3. **Show, don't hide.** Every extra tap, dropdown or banner adds interaction cost.
4. **Answer questions before they are asked.** The total in the button, the result count in the
   filter button, "free cancellation until…".
5. **Specificity is trust.** "4.9 ★ · 221 reviews", "start in 2 taps", one price instead of a range.
6. **Design a system, not a single screen.** Icons that work on any photo, cards that look the same
   whatever the data.
7. **Looking simpler ≠ deciding easier.** Filters split across pages look clean but break the decision apart.
8. **Meet people where they are.** A simple start for newcomers, their plan for regulars, stats for power users.
9. **Use decision psychology, honestly.** Smart defaults, progress that doesn't start at zero,
   value before sign-up, price anchors. Only real numbers and deadlines.
10. **Consistency.** One type family, one icon style, one grid, one corner radius.
11. **Feedback on every action.** Selected states differ in at least two ways; motion comes last.
12. **Learn from shipped products and test.** Real screens, not only Dribbble; test, optimise, test again.

## What's inside

| File | Contents |
| :-- | :-- |
| [`.claude-plugin/`](.claude-plugin) | Plugin manifest and the `diastime` marketplace |
| [`SKILL.md`](skills/uxpeak-ux-ui/SKILL.md) | Core ideas, do/don't cheat sheet, review and design workflows |
| [`references/visual-ui.md`](skills/uxpeak-ux-ui/references/visual-ui.md) | Hierarchy, type, colour, grid, shadows, icons, imagery |
| [`references/ux-psychology.md`](skills/uxpeak-ux-ui/references/ux-psychology.md) | 15 principles with bad/good examples and ethical limits |
| [`references/conversion-ecommerce.md`](skills/uxpeak-ux-ui/references/conversion-ecommerce.md) | 15 product page mistakes, paywall, pricing, booking |
| [`references/mobile-patterns.md`](skills/uxpeak-ux-ui/references/mobile-patterns.md) | Navigation, input, search, filters, lists, empty states |
| [`references/process-and-craft.md`](skills/uxpeak-ux-ui/references/process-and-craft.md) | Design thinking, Figma, prototyping, building a site from scratch |
| [`references/sources.md`](skills/uxpeak-ux-ui/references/sources.md) | All 23 videos and what was taken from each |
| [`evals/product-page-review`](evals/product-page-review/README.md) | Test page with 17 planted flaws and both reviews |
| [`docs/test-prompt.md`](docs/test-prompt.md) | A prompt and checklist to test the skill on a whole site |

Only the skill's description (~340 tokens) is added to every session. `SKILL.md` (~6.7k tokens)
loads when the skill fires, the references only when needed.

## Test

A mobile product page with 17 planted flaws, same request to two independent agents:

| | With skill | Without skill |
| :-- | :-: | :-: |
| Planted flaws found | **17 / 17** | 16 / 17 |
| Review length | ~900 words | ~1,700 words |

The baseline missed "1 kg" in the product title while the quantity is selectable, and even listed it
as a strength.

## How it was built

```
yt-dlp video list  →  audio of 23 videos  →  whisper.cpp (small.en)  →  manual extraction  →  SKILL.md + 6 references
```

About 5.5 hours of audio from every video and short on the channel (2023–2026), transcribed locally;
the rules were extracted by hand. Sponsor and course plugs are left out. Only what the author says out
loud made it in. Figures like "conversion went from 2% to 7%" are the channel's examples, not guarantees.

## Legal notice

Unofficial project, not affiliated with uxpeak. The rules are paraphrased from the channel's public
videos; no transcripts or video fragments are included. All rights to the videos and original
materials belong to their authors. If the rules help you, go to the source:
[youtube.com/@uxpeak](https://www.youtube.com/@uxpeak) and [uxpeak.com](https://www.uxpeak.com).
