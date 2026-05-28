---
name: study-notes-summarizer
description: Summarize study material (lecture notes, textbook chapters, articles, PDFs) into concise, beginner-friendly notes. Use when the user asks to summarize, condense, simplify, or make study notes from study material, coursework, lectures, readings, or articles.
---

# Study Notes Summarizer

Turn long-form study material into clear, structured notes that are easy to review before an exam or revisit later.

## When to use

Trigger this skill when the user asks for any of:
- "Summarize this chapter / lecture / article / PDF"
- "Make study notes from..."
- "Help me revise..."
- "Simplify these notes"
- "Turn this into flashcards / cheat sheet"

## Inputs to collect

Before summarizing, confirm:
1. **Source** — a pasted text, a file path in the project, or a URL.
2. **Subject area** — e.g. Digital Business, IT, Banking, JS/Node. Helps tone and analogies.
3. **Output style** — pick one (ask if unclear):
   - **Quick recap** (5–10 bullets, key ideas only)
   - **Structured notes** (headings + sub-bullets, definitions, examples)
   - **Cheat sheet** (one-pager, dense, exam-ready)
   - **Flashcards** (Q → A pairs, good for active recall)
4. **Length target** — short / medium / detailed.

If the user just says "summarize this," default to **structured notes, medium length**.

## How to produce the summary

1. **Read the full source first.** Do not summarize partial input.
2. **Identify the spine** — the 3–7 core concepts the material is actually teaching.
3. **For each concept, capture:**
   - A one-line plain-English definition
   - Why it matters (the "so what")
   - One concrete example (use analogies from banking, IT, or everyday life when the topic is abstract)
4. **Flag exam-likely items** with a `⭐` prefix — definitions, formulas, frameworks, named models.
5. **Call out confusions** — if the source has terms that often get mixed up (e.g. "encryption vs hashing"), add a short "Don't confuse:" line.
6. **Skip filler** — anecdotes, repeated points, marketing language.

## Output format

Use Markdown. Default template for structured notes:

```markdown
# {{Topic}} — Study Notes

**Source:** {{file / URL / "pasted text"}}
**Style:** {{quick recap | structured | cheat sheet | flashcards}}

## Big picture
One short paragraph: what this material is fundamentally about.

## Key concepts
### 1. {{Concept name}}
- **Definition:** ...
- **Why it matters:** ...
- **Example:** ...
- ⭐ **Exam-likely:** ...

### 2. {{Concept name}}
...

## Quick recap (5 bullets)
- ...
- ...

## Terms to not mix up
- **X vs Y:** ...
```

For **flashcards**, use:
```markdown
Q: ...
A: ...
---
Q: ...
A: ...
```

## Tone

- Casual, friendly, plain English. No jargon without a one-line definition next to it.
- Treat the reader as smart but new to the topic.
- Prefer short sentences. Use analogies over abstract definitions when possible.

## After producing notes

Offer (in one line at the end) two follow-ups the user can pick:
1. "Want me to turn this into flashcards / a cheat sheet?"
2. "Want me to quiz you on these notes?"

Do not auto-save the notes to a file unless the user asks. If they do, save under `reflections/` or a path they specify, with a date-prefixed filename like `2026-05-19-{{topic-slug}}.md`.
