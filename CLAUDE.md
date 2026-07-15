# CLAUDE.md — Writing portfolio, one-page site

## What this is

A single-page writing portfolio for Mercedes Torrendell — writer and interviewer covering AI, language, and the people caught between them. Published at The Creative Independent. The page has ONE job: an editor at an AI language company opens it, understands her take in 10 seconds, and clicks through to two published pieces.

Audience: editors and brand people at AI companies (first reader: DeepL). They see hundreds of portfolios. This one must feel like a quiet, confident print object — not a template.

## The concept (do not dilute)

The site performs its own thesis: **translation from complex/heated language into precise human language.** The hero is a two-line "translation pair":

- Line A (small, machine register): a sentence people actually say — labeled `what we say`
- Line B (large, human register): the same sentiment, made MORE PRECISE — labeled `what we mean`

Rule for the pair: line B is never cheerier than line A, only truer. The typeface switch carries the meaning: line A is mono (machine/heat), line B is serif (human/precision).

Everything else on the page is a quiet index. **The wording is the design. The layout's job is to get out of the way.**

## Tokens

Palette — warm black & white, translucent feel. NO color anywhere. These six values are the entire palette:

- `--paper: #FAF9F5` (page background, warm off-white)
- `--ink: #1C1B18` (primary text, warm near-black)
- `--ink-soft: #6E6A62` (secondary text, warm gray)
- `--ink-faint: #9B968C` (labels, meta, captions)
- `--hairline: #E3DFD5` (all rules/dividers, 1px max)
- `--halo: rgba(28,27,24,0.05)` (the atmosphere gradient only)

Type — three roles, the switch between them is semantic:

- Display/serif (`what we mean`, section-opening lines): a quiet serif with presence. Prefer "Newsreader" or "Source Serif 4" (Google Fonts). NOT Playfair Display (template tell).
- Body/sans: "Inter" or system sans, weights 400 and 500 only. Never 600/700.
- Machine/mono (`what we say`, tags, meta): "IBM Plex Mono" or "JetBrains Mono", small sizes only (12–13px).

Type scale: 12 / 13 / 15 / 18 / 26 / clamp(28px, 5vw, 44px) for the hero serif line. Line-height 1.5 body, 1.3 display. Letter-spacing +0.08em on tiny uppercase-ish labels (but use lowercase, not caps).

Spacing: slow and generous. Base unit 8px; sections separated by 96–128px on desktop, 64px mobile. Max content width 680px, centered. One column. No grid gymnastics.

## Atmosphere (the moodboard feel)

Reference: soft blurred-gray Japanese/print posters — translucent, grainy, warm monochrome.

- Behind the hero only: one large soft radial gradient (`--halo`), blurred, barely perceptible — like breath on glass. Nothing behind other sections.
- Optional fine grain: an SVG noise texture or CSS grain overlay at 2–4% opacity, full page. If it reads as "effect," remove it.
- That's it. Chanel rule: before shipping, remove one accessory.

## Page structure (top to bottom)

1. **Header**: name left (lowercase, 12px), one line right: `writing on ai, language, people` (12px, --ink-faint). No nav menu — the page is one screen of scroll.
2. **Hero — the translation pair** (centered, lots of air):
   - label `what we say` (mono, --ink-faint)
   - the quoted sentence (mono, 13px, --ink-soft, max-width 44ch)
   - a 1px vertical hairline, ~40px tall, as the "translation" gesture
   - label `what we mean`
   - the serif line (clamp size, --ink, max-width 26ch)
   - FINAL HERO COPY (confirmed, do not change): "AI is stealing our jobs." → "The jobs are being redrawn — and we deserve a say in the drawing."
3. **The take** (2–3 sentences, 15px, --ink-soft, centered or left, max 52ch). Placeholder — Mercedes provides.
4. **Published** — index rows, each: title (15px, --ink) + one-line context (13px, --ink-faint) + publication tag (mono 12px, right-aligned). Rows separated by --hairline top borders. Entries: César Fieiras interview (TCI), Roopa Vasudevan interview (TCI), link "all interviews →" to her TCI author page.
5. **Essays** — same row pattern. Entries: the new AI/translation essay (Substack), "We Are Not Being Given the Words" (Substack).
6. **In progress** — same row pattern, mono `forthcoming` / `preview` tags: Valerie Fuchs interview (forthcoming, TCI), SOFTER Global (newsletter preview), narrative-gap essay (in development).
7. **Footer**: left `berlin · es / en`, right `contact ↗` (mailto) + LinkedIn. 11–12px, --ink-faint. Hairline above.

All titles/links are real once provided — ASK for the URLs, do not invent them.

## Interaction

- Links: --ink, underline on hover only (1px, --hairline color transitioning to --ink). No color change. Whole index row is the click target.
- One optional signature micro-moment: on page load, the hero's serif line fades in 200ms AFTER the mono line — the translation "arrives." Respect `prefers-reduced-motion` (no animation at all).
- Nothing else moves. No scroll animations, no parallax, no cursor effects.

## Forbidden (hard rules)

- No color. No blue links, no accent color, no brand colors.
- No cards, boxes, borders around content blocks, or drop shadows. Hairlines only.
- No icons except the two `↗` characters (use the text character, not an icon font).
- No gradients except the single hero halo.
- No stock imagery, no illustrations, no emoji, no headshot on v1.
- No frameworks, no build step: one `index.html`, embedded CSS, zero or near-zero JS. Google Fonts is the only external resource.
- No "portfolio template" moves: no skill bars, no logo strips, no testimonial cards, no numbered 01/02/03 section markers, no dark mode toggle.
- No Title Case. Sentence case (or lowercase for labels) everywhere.

## Quality floor

- Responsive to 360px: hero serif line scales via clamp, index rows stack the tag under the title, spacing drops to 64px.
- Semantic HTML: `<header>`, `<main>`, `<section>` with real headings (h1 = her name or visually-hidden), `<footer>`.
- Visible keyboard focus (2px --ink outline, offset 2px). Alt/aria where needed.
- Meta: `<title>Mercedes Torrendell — writing on AI, language, people</title>`, description tag, OG title/description. Language `en`.
- Lighthouse-clean: no layout shift, fonts with `display=swap`.

## Deploy

Target: this folder pushes to GitHub, auto-deploys on Vercel. Keep everything in root: `index.html` (+ optional `grain.svg`). Custom domain later: `writing.thesphereimpact.com` via CNAME in Squarespace DNS — not part of this build.

## Working style

Build in this order: tokens + type first, hero second, index third, atmosphere last. After building, self-critique against the Forbidden list and the moodboard adjectives: warm, translucent, quiet, print-like, wording-first. If any element competes with the words, cut it.
