# Signal — Design System

Working design system for a hackathon project on **hallucination detection**. The product does not have a name yet; **"Signal"** is a placeholder taken from the chosen color direction. Rename freely — it appears only in `thumbnail.html`, `readme.md` and `SKILL.md`.

## Sources

**None provided.** No codebase, Figma file, deck, or brand assets were attached. Everything here was authored from the brief: *"quick and easy design system for a hackathon project… we are working on hallucination detection."* Light mode is the default, the demo surface is **CLI / terminal**, and slides are needed for both a demo-day pitch and a technical walkthrough.

Because there was no source, there is **no logo**. The brand name is set in plain type (IBM Plex Mono, medium) wherever a mark would go. No mark was drawn or invented.

## Product context

One product, one job: take model output and tell the reader which parts are grounded in a source and which are not. Every screen is a variation on the same loop — *claim → evidence → verdict*. The four verdicts are the system's core vocabulary and have dedicated color tokens:

| Verdict | Meaning |
|---|---|
| Verified | Traced to a specific source span |
| Unsupported | No grounding found in the sources |
| Contradicted | Conflicts with a source |
| Unchecked | Not yet evaluated |

Primary surface is a CLI, so mono type carries real weight — it is not decoration.

## Visual foundations

**Palette.** Off-white paper (`#FBFAF8`) under a warm-cool ink ramp; near-black `#101828` for text and for the one dark surface (terminal blocks). Accents are used only to carry meaning: amber = unsupported, red = contradicted, green = verified, gray = unchecked. Indigo is reserved for links and focus rings. No decorative color. No gradients anywhere.

**Type.** IBM Plex Sans for everything readable; IBM Plex Mono for labels, scores, file paths, and CLI output. Display 44 / title 28 / heading 20 / subhead 16 / body 15 / small 13 / label 11. Display and title get `-0.02em` tracking; labels get `+0.11em`, uppercase, mono — the single recurring type motif. Body measure caps at 64ch.

**Spacing.** 4px base scale, 4→80. Card gutter 20px, section gutter 48px. Errs toward whitespace; density comes from the type scale, not from squeezing padding.

**Backgrounds.** Flat color only. No imagery, no illustration, no pattern, no texture, no full-bleed photography. The one "dark" moment is a terminal block on `--surface-terminal`.

**Borders and cards.** Cards are `--surface-card` white, 1px `--border-subtle`, `--radius-lg` (8px), `--shadow-sm`. Radii: 3px chips, 4px inputs/buttons in dense UI, 6px default buttons, 8px cards, pill for status chips. **Never a rounded card with a colored left border only** — verdict state is carried by a tinted background plus a full 1px border in the verdict color.

**The claim-highlight motif.** Flagged spans get a tinted background plus a 2px bottom border in the verdict color. This is the brand's signature graphic device and appears in the CLI (as color), in the UI, and on slides.

**Shadows.** Three steps: `sm` for resting cards, `md` for popovers, `lg` for dialogs. No inset shadows. No glow.

**Transparency and blur.** Sparingly — only for a dialog scrim (`rgba(16,24,40,.35)`). No frosted-glass panels.

**Motion.** Fast and unshowy: 120/180/280ms with `cubic-bezier(.2,.7,.3,1)`. Fades and 4px slides. No bounce, no spring, no scale-in. Verdict changes cross-fade the background tint; they never animate position.

**States.** Hover darkens (`--action-bg-hover`) or picks up `--action-ghost-bg-hover` for ghost buttons — never opacity fades. Press is a 1px downward nudge, no scale. Focus is a 3px indigo ring (`--shadow-focus`), always visible, never removed.

**Layout.** Left rail 264px fixed; content column centered at 64ch max for prose, full-width for tables. Sticky headers, no sticky footers.

## Content fundamentals

Plain, factual, second person. The product tells the reader what it found and what it could not find, and stops.

- **Voice:** "you" for the reader, never "we". The system speaks about itself in the third person only when naming an action: "Signal found 2 unsupported claims."
- **Casing:** sentence case for all UI copy, headings and buttons. Uppercase only for mono eyebrow labels.
- **Verdict language is fixed.** Always *verified / unsupported / contradicted / unchecked*. Never "hallucinated", "fake", "wrong", "lie", or "confident".
- **Uncertainty is stated, not hidden:** "No source span matched this claim" — not "This claim is false."
- **Numbers stay bare.** `0.42 support score`, `2 unsupported · 4 verified`. Mono, lowercase, middot separators.
- **No emoji.** No exclamation marks. No congratulatory copy on a clean result — "No unsupported claims found." is the whole message.

Examples:

> ✅ "Revenue growth of 41% does not appear in the source documents."
> ❌ "Uh oh! Looks like the model hallucinated 🤖"

> ✅ "Review claim" / "Dismiss" / "Open source"
> ❌ "Let's take a look!" / "Got it!"

## Iconography

Not yet established. No icon assets were provided, so nothing has been copied in and no icons have been drawn. When icons are needed, the intent is **Lucide** via CDN (`https://unpkg.com/lucide-static`) — 1.5px stroke, 16px and 20px sizes, `currentColor` — which matches the 1px-border, low-contrast line vocabulary here. This is a substitution, flagged below; unicode middots (`·`) and the verdict-colored highlight motif carry most of the signalling work today. No emoji, ever.

## Substitutions to confirm

1. **Fonts** — no binaries were provided. IBM Plex Sans + IBM Plex Mono are loaded from Google Fonts in `tokens/fonts.css`. Swap in real files if you have them.
2. **Icons** — Lucide, proposed but not yet wired up.
3. **Name and logo** — placeholder "Signal", plain type, no mark.

## Index

- `styles.css` — the one file consumers link; `@import`s only
- `tokens/fonts.css` — webfont loading
- `tokens/colors.css` — neutral + accent ramps, semantic aliases, verdict states
- `tokens/typography.css` — families, scale, leading, tracking, weights
- `tokens/spacing.css` — 4px scale, gutters, measure, rail width
- `tokens/elevation.css` — radii, borders, shadows, easing, durations
- `guidelines/*.card.html` — foundation specimen cards (Colors, Type, Spacing, Brand)
- `explorations/` — the three palette directions explored; Signal was chosen
- `thumbnail.html` — project tile
- `SKILL.md` — portable Agent Skill wrapper

**Not built yet:** components, slide templates, CLI UI kit.
