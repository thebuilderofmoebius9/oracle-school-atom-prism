# Design

## Source of truth
- Status: Active
- Last refreshed: 2026-07-05
- Primary product surfaces: single-page GitHub Pages landing for Oracle School.
- Evidence reviewed:
  - `README.md`
  - `index.html`
  - Discord task `1523305442590330910`: build Oracle School site and deploy to GitHub Pages.
  - Oracle Prism feedback in `1512079809021214730`: remove duplicate charts, favor proof density, systems lens, accessibility, responsive layout.

## Brand
- Personality: living school, proof-first, calm but magical, technical without being cold.
- Trust signals: explicit Rule 6, record/retrieve/prove, labeled metrics, build/deploy proof.
- Avoid: generic AI marketing, unverified numbers, chartjunk, duplicate panels, emoji-as-icons in core UI.

## Product goals
- Goals:
  - Explain Oracle School in one scroll.
  - Make visitors understand what students build.
  - Make proof culture visible: memory, tools, deploy, verify.
  - Provide a contest-ready static page for GitHub Pages.
- Non-goals:
  - Full LMS implementation.
  - Auth, dashboard, forms, payment, or backend.
- Success signals:
  - Workshop proof wall includes verified GitHub repo links, not generic claims.
  - Discord index/mirror artifacts are visible as curriculum evidence.
  - Page is readable on mobile and desktop.
  - Public safety scan passes.
  - GitHub Pages URL returns 200 and correct title.

## Personas and jobs
- Primary personas:
  - New builders deciding whether Oracle School is real.
  - Existing Oracle agents comparing design directions.
  - Axe/Nat reviewing fleet contest submissions.
- User jobs:
  - Understand the school quickly.
  - See proof artifacts and principles.
  - Decide whether the page is worth sharing.
- Key contexts of use: Discord link preview, mobile reading, public website review.

## Information architecture
- Primary navigation: Promise, Path, Proof, Principles.
- Core routes/screens: one static page with anchored sections.
- Content hierarchy:
  - Hero → scoped numbers → curriculum path → workshop proof wall → Discord index → principles → contest/deploy note.
  1. Hero: what Oracle School is.
  2. Metrics: labeled scope to prevent 772 vs 653 confusion.
  3. Path: learning journey.
  4. Proof: examples of real work.
  5. Principles: compact rules.

## Design principles
- Principle 1: Less, but better — every panel must earn its space.
- Principle 2: Data-ink honesty — no duplicate visualizations or unlabeled numbers.
- Principle 3: Systems over screenshot — tokens, responsive behavior, and accessibility are part of beauty.
- Tradeoffs: Use a handcrafted static page for speed and deploy reliability; no dependency-heavy framework.

## Visual language
- Color: dark cosmic base with gold/cyan/violet accents; accessible contrast first.
- Typography: system sans for speed; tabular figures for metrics.
- Spacing/layout rhythm: 8px scale; wide desktop grid; single-column mobile.
- Shape/radius/elevation: soft panels, restrained glow; no random shadow scales.
- Motion: one meaningful ambient hero motion; reduced-motion disables it.
- Imagery/iconography: CSS/SVG sigil and geometric proof marks; no core emoji icons.

## Components
- Existing components to reuse: static sections, cards, stat blocks, CTA links.
- New/changed components:
  - Workshop repo card grid with direct GitHub links.
  - Discord index evidence cards with message/channel/attachment counts. skip link, proof chips, scoped metric cards, lens notes.
- Variants and states: focus-visible, hover, mobile wrapping, reduced motion.
- Token/component ownership: CSS variables in `index.html` for this static prototype.

## Accessibility
- Target standard: WCAG AA intent.
- Keyboard/focus behavior: visible focus ring; skip link to main.
- Contrast/readability: dark base with high-contrast text; muted text remains readable.
- Screen-reader semantics: landmarks, heading order, aria labels for decorative visuals.
- Reduced motion and sensory considerations: `prefers-reduced-motion` disables animation.

## Responsive behavior
- Supported breakpoints/devices: mobile 360+, tablet 768+, desktop 1120+.
- Layout adaptations: hero/grid collapse to one column on mobile.
- Touch/hover differences: links/buttons have 44px+ touch area and visible focus.

## Interaction states
- Loading: no runtime loading state; static page only.
- Empty: not applicable.
- Error: not applicable.
- Success: deploy verification proof in README/report.
- Disabled: not applicable.
- Offline/slow network: static page, no third-party scripts.

## Content voice
- Tone: concise, grounded, bilingual where useful.
- Terminology: Oracle, memory loop, proof-first, Rule 6, build/scan/deploy.
- Microcopy rules:
  - Use numbers only with scope and source; avoid “we did many workshops” without repo/artifact links. label metric scope; avoid inflated claims.

## Implementation constraints
- Framework/styling system: no build dependencies; plain HTML/CSS.
- Design-token constraints: CSS variables only.
- Performance constraints: no external JS; no remote fonts; no heavy images.
- Compatibility constraints: modern evergreen browsers, GitHub Pages static hosting.
- Test/screenshot expectations: HTML exists, leak scan passes, live URL verified.

## Open questions
- [ ] Should `school.buildwithoracle.com` CNAME point to the winning GitHub Pages entry? Owner: Axe. Impact: production deploy.
- [ ] Which metric should be canonical on the final production site: roster badge 190, unique awakenings ~653, or raw records 772? Owner: school/fleet. Impact: trust wording.
