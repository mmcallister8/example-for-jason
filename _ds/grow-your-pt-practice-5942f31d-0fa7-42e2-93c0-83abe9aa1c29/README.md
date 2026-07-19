# Grow Your PT Practice — design system conventions

Marketing site design system for a cash-based physical therapy marketing agency. Brand personality: the credible operator — professional, direct, proof-driven. Full spec: `guidelines/gyptp-design-system.md`. Read `styles.css` and `tokens/tokens.css` before styling; every color, radius, shadow, spacing, and duration is a CSS variable there — never hardcode hex.

## Setup

Link `styles.css` (it imports `tokens/tokens.css` and Google Fonts Manrope 500/700/800 + Inter 400/500/600). Headings use Manrope (`--font-display`), body/UI uses Inter (`--font-body`). Never Manrope for paragraphs, never Inter for large headings. Sentence case everywhere; all-caps only via `.eyebrow`.

## Critical color rules

1. **Never put white text on `--teal-500`** — it fails WCAG (2.6:1). Teal-500 is an accent: the `pt` logo highlight, icons, borders, and elements on navy.
2. Buttons/links on **light** backgrounds use `--teal-700` fill with white text (`.btn--primary`), hover `--teal-800`.
3. On **navy** sections, CTAs use `--teal-500` fill with `--navy-900` text (`.btn--primary-navy-bg`).
4. **Gold** (`--gold-500`, always with `--navy-900` text) marks premium only: "Most popular" badges, upsell moments. Max twice per page.
5. Page rhythm: alternate `--white` / `--offwhite` sections; `--navy-800` sections for hero, stats/proof, and final CTA band. ~70% light, 30% navy.
6. Teal text never on offwhite/gray at body sizes — only large headings (24px+) or on navy.

## Class vocabulary (all in styles.css)

- **Type:** `.display`, `h1`–`h4`, `.eyebrow`, `.body-lg`, `.body-sm`, `.stat`. Highlight ONE phrase per major heading with `.hl` (teal-600 on light, teal-400 inside `.on-navy`) — the logo's teal-`pt` motif is the site's signature.
- **Sections:** `.on-navy` on a navy-800 section flips headings to white, `.hl` to teal-400, links to teal-400.
- **Buttons:** `.btn` + `.btn--primary` | `.btn--primary-navy-bg` | `.btn--secondary` | `.btn--secondary-navy-bg` | `.btn--ghost`; `.btn--lg` for hero/CTA bands. One primary per section. Verb-first labels ("Book a strategy call"), never "Submit"/"Learn more".
- **Badges:** `.badge` + `.badge--default` | `.badge--accent` | `.badge--premium` | `.badge--success-stat`.
- **Cards:** `.card`, `.card--bordered` (on offwhite), `.card--clickable`, `.card--featured` (2px teal border, featured pricing tier only), `.icon-tile` (40px teal-100 square holding a 22px teal-700 outline icon).
- **Forms:** `.field-label`, `.input`, `.input--error`, `.field-error`. 48px tall fields, real-example placeholders, minimum fields (name, email, phone).
- **Stats:** `.stat-block` inside `.on-navy`; number in `.stat` (renders teal-400), label in `.stat-label`.
- **Links:** `a.link`.

Icons: Lucide/Tabler outline, 2px stroke, 22–24px, teal-700 on light / teal-400 on navy. Never filled or multicolor. Avoid illustration; use real screenshots and photos as proof.

## Logo

Assets and full rules: `components/foundations/Logo/` and `guidelines/logo.md`. The mark is a navy-800 rounded tile (radius ≈23% of size) holding lowercase Manrope-800 "pt" in teal-500, paired with a two-line "grow your / practice" wordmark. Use `logo-lockup-light.svg` on white/offwhite; on navy sections use `logo-lockup-navy.svg` (tile flips to teal-500 with navy-900 "pt" — never white "pt" on teal-500). Mark alone (`logo-mark.svg`) only for favicon/avatar/footer. In navigation, rebuild it in HTML for crispness: a `52px`/`32px` tile (`border-radius:12px`/`8px`, `background:var(--navy-800)`, `color:var(--teal-500)`) beside Manrope-800 wordmark text at the same size, lowercase always, clearspace half the tile height.

## Idiomatic snippet

```html
<section class="on-navy" style="padding: var(--space-9) var(--space-7)">
  <div class="eyebrow">For cash-based PT owners</div>
  <h1 class="display">Fill your schedule with <span class="hl">cash-pay patients</span></h1>
  <p class="body-lg" style="color: var(--navy-200); max-width: 65ch">
    Facebook ads built by a team that only works with cash PT practices.
  </p>
  <a class="btn btn--lg btn--primary-navy-bg" href="#">Book a strategy call</a>
  <a class="btn btn--lg btn--secondary-navy-bg" href="#">See real results</a>
</section>
```

## Voice

Direct, plain, specific, second person, short sentences. No em dashes. Banned: "unlock", "leverage", "seamless", "empower", "elevate", "revolutionize", "game-changer", "simply", "just". Lead with outcomes and numbers. Say "patients", never "customers". CTAs name the honest next step.
