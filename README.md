# writing-humanize

A Claude skill that removes signs of AI-generated writing from text — without rewriting content, simplifying language, or changing meaning.

Works across any domain: technical writing, blog posts, marketing copy, case studies, academic writing, legal documents, documentation.

---

## Credits and origin

This skill merges two sources:

- **[blader/humanizer](https://github.com/blader/humanizer)** — a Claude Code skill built on [Wikipedia's Signs of AI Writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) guide, covering 25 patterns across content, language, style, communication, and filler categories. The pattern library here is largely derived from that work. Full credit to [blader](https://github.com/blader).
- **writing-humanize** (my own earlier skill) — 12 patterns built for technical and developer content, with a voice-preservation layer and minimum-intervention philosophy not present in blader's version.

---

## What makes this different

Most humanization tools focus on pattern removal. This one adds a second constraint: **preserve the author's vocabulary**.

A legal writer's "indemnification" stays "indemnification." A developer's "isolate tenant data" stays "isolate tenant data." A doctor's "contraindicated" stays "contraindicated."

Swapping precise terms for casual synonyms makes writing less accurate. It also reads wrong to anyone who knows the domain. This skill treats vocabulary preservation as a hard rule, not a suggestion.

---

## What it detects

25 patterns across 5 categories:

- **Content** — significance inflation, vague attributions, promotional language, notability name-dropping, superficial analyses, formulaic challenge/triumph arcs
- **Language** — AI vocabulary words, copula avoidance, negative parallelisms, rule of three, synonym cycling, false ranges
- **Style** — em-dash overuse, boldface overuse, inline-header lists, title case headings, emojis as structure, hyphenated word pairs
- **Communication** — chatbot artifacts, cutoff disclaimers, sycophantic tone
- **Filler and hedging** — filler phrases, excessive hedging, generic conclusions, perfectly balanced structures

Plus 6 additional voice-specific patterns: formulaic headers, transition filler, label-before-opinion, parallel sentence structures, over-structured decision frameworks, telegraphing lists.

---

## Installation

### Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Naram-Alkoht/writing-humanize.git ~/.claude/skills/writing-humanize
```

### Claude.ai Projects

Upload `SKILL.md` directly to your project as a reference document.

---

## Usage

In Claude Code:

```
/writing-humanize

[paste your text here]
```

Or directly:

```
Humanize this text: [your text]
```

---

## Example

**Before:**

> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools are reshaping how engineers ideate, iterate, and deliver, underscoring their vital role in modern workflows.
>
> - 💡 **Speed:** Code generation is significantly faster, reducing friction and empowering developers.
> - 🚀 **Quality:** Output quality has been enhanced through improved training.
> - ✅ **Adoption:** Usage continues to grow, reflecting broader industry trends.
>
> I hope this helps! Let me know if you'd like me to expand on any section!

**After:**

> AI coding assistants speed up the parts of the job nobody wants to do. Config files, boilerplate, test scaffolding — the stuff that takes twenty minutes and teaches you nothing.
>
> The risk is how confident the suggestions look. I've accepted code that compiled and passed lint, then found later it missed the point entirely.
>
> Treat it like autocomplete and review every line. It's useful. Use it to avoid thinking, and it will help you ship bugs faster.

---

## License

MIT
