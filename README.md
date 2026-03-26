# Nose — Site Structure, AI Section Playbook, and Weekly Update Routine

This README is the practical operating guide for maintaining **Nose** (`emlynoregan/nose`) as it currently exists.

It documents:

1. What the site is and how it is deployed
2. What has been built so far (especially the AI section)
3. How to create/edit pages in the existing style
4. How to research and source AI content
5. A weekly routine for keeping the AI section current

---

## 1) What Nose is

Nose is a lightweight static site (HTML + CSS) for long-form analysis and curated research.

### Current repo shape

- `.github/workflows/static.yml` — GitHub Pages deploy workflow
- `public/index.html` — home page
- `public/ai-progress.html` — AI hub page
- `public/ai-weekly.html` — weekly AI blog page
- `public/american-models.html` — US model landscape page
- `public/chinese-models.html` — China model landscape page
- `public/other-models.html` — non-US/non-China model landscape page
- `public/energy-transition.html` — energy topic page
- `public/deglobalization.html` — deglobalization topic page
- `public/styles.css` — shared stylesheet for all pages

### Deployment model

- Push to `main`
- GitHub Actions publishes `public/` to GitHub Pages
- No JS framework, no build step, no package manager required

---

## 2) What has been requested and implemented so far

Bel asked for a practical AI-section redesign with model pages, sources, and ongoing updates.

### Implemented changes

#### AI hub + topic structure
- AI page now includes:
  - A dedicated **AI Weekly Blog** section (placed above model cards)
  - Model topic cards for:
    - American Models
    - Chinese Models
    - Other Models

#### Leaf model pages
Created:
- `american-models.html`
- `chinese-models.html`
- `other-models.html`

Each page includes:
- Notable companies + model families
- Capability notes
- Indicative pricing (USD / 1M input/output tokens)
- **Per-card source links** (required)

#### AI Weekly Blog
Created:
- `ai-weekly.html`

Current structure:
- Weekly heading
- One **featured** long-form article up front (~500–1000 words target)
- Then shorter “other updates” cards
- Source links on each item
- Added a **bull/bear case callout** under the featured article

#### Current featured topic
- Claude Code vs Cursor Composer 2
- Includes:
  - Anthropic plan bundling/subsidy discussion
  - Cursor Composer 2 launch and mixed sentiment/controversy
  - Developer workflow and cost implications

---

## 3) Content architecture and page conventions

## AI section navigation

### AI hub page (`ai-progress.html`)
Use this order:
1. Hero
2. Back link
3. **AI Weekly Blog section** + card
4. Model Landscape section + regional cards
5. “How to read this” note and freshness stamp

### Weekly page (`ai-weekly.html`)
Use this order:
1. Hero + intro
2. Week heading (e.g. “Week of 26 March 2026”)
3. Featured article
4. Bull/Bear callout (if relevant)
5. Other updates cards
6. Notes/caveat line

### Model pages (`american/chinese/other-models.html`)
Each company card should include:
- Company/lab name
- Strength line
- Model list with pricing if available
- **Sources line** with links

---

## 4) Design system and CSS conventions

Everything is in `public/styles.css`.

### Existing reusable blocks
- Core site layout, typography, nav, hero, cards
- `.topics-grid`, `.topic-card`
- Model page classes:
  - `.model-page`, `.model-groups`, `.model-company`, `.model-list`, `.price`, `.sources`
- Weekly/blog classes:
  - `.blog-list`, `.blog-entry`
  - `.featured-article`, `.eyebrow`
  - `.bull-bear-box`, `.bull-bear-col`

### Rule of thumb
- Reuse existing classes first
- Add new classes only when the pattern is likely reusable
- Keep visual style aligned with existing dark theme (subtle borders, minimal color accents)

---

## 5) Research approach (LLM and model-market content)

For AI pages, research should be both **fast** and **source-disciplined**.

## Source hierarchy

### Tier 1 (preferred)
- Official model/vendor pages
- Official pricing/docs/changelogs
- Official announcements/blogs

### Tier 2
- Reputable coverage (TechCrunch, Fortune, CNBC, MIT Tech Review, etc.)
- Useful for sentiment, market framing, controversies, and context

### Tier 3 (use with caution)
- Community threads (Hacker News, Reddit, forum posts)
- Use as **sentiment evidence**, not primary factual authority

## Research workflow
1. Start with official announcement/pricing/docs
2. Add 1–2 credible secondary analyses
3. Add community sentiment only where it materially informs user experience
4. Add links directly on the relevant card/article section
5. Use caveats for fast-changing info (pricing, model versions, availability)

## Required caveats for AI content
- “Pricing can change quickly”
- “Indicative pricing, route/provider-dependent”
- “Free routes may vary by quota/availability”
- Add a “Last updated” stamp on pages with price-heavy content

---

## 6) How to add or update a page

1. Copy structure from the nearest existing page in `public/`
2. Keep header/nav/footer consistent with other pages
3. Add content using existing card/article patterns
4. Add source links where factual claims appear
5. Add/update styles in `styles.css` only as needed
6. Check links manually (especially new external source links)
7. Commit and push to `main`
8. Verify published page after GitHub Pages deploy

---

## 7) Weekly AI update routine (recommended)

Use this routine once per week (or whenever significant news breaks).

## A) Quick scan (20–40 min)
- Check official updates from:
  - OpenAI
  - Anthropic
  - Google DeepMind / Gemini API changelog
  - Major Chinese labs (Qwen, DeepSeek, Moonshot, etc.)
  - Mistral / other key non-US/non-China providers

## B) Pick one featured story
Select one item with strong strategic relevance, e.g.:
- Developer platform battle
- Major model release with market impact
- Pricing reset / major policy or procurement shift

Write **500–1000 words** with:
- What happened
- Why it matters
- Who benefits / who is pressured
- Practical implications for developers and buyers
- Source links at the end

## C) Add 4–8 short update cards
Each card:
- 1 short headline
- 2–4 sentence summary
- 2–3 links for further reading

Aim to cover:
- American model ecosystem
- Chinese model ecosystem
- Other/open-weight ecosystem
- One cross-cutting theme (policy, infra, economics, enterprise adoption)

## D) Optional bull/bear block
If feature topic has market uncertainty, include:
- Bull case (upside path)
- Bear case (risk path)

## E) Refresh model pages only when needed
Don’t churn pricing weekly unless there are clear changes.
Update leaf pages when:
- model lineup changes materially
- major pricing shifts occur
- source links become stale or broken

## F) Final QA checklist
- [ ] All new claims have links
- [ ] No orphan cards or dead internal links
- [ ] Page order remains: featured first, cards second
- [ ] Copy is concise and non-hyped
- [ ] Last-updated notes are current where applicable

---

## 8) Editorial style guide (short)

- Write for informed generalists and technical readers
- Prefer clear argument over hype
- Use uncertainty language where appropriate (“appears”, “early signal”, “mixed sentiment”)
- Separate:
  - hard facts (source-backed)
  - interpretation (analysis)
- Keep paragraphs short for scanability

---

## 9) Maintenance philosophy

Nose should remain:
- Minimal and maintainable (simple static files)
- Well-sourced (easy to audit claims)
- Incrementally updated (no unnecessary redesign churn)

Default stance: evolve the AI section through regular, well-referenced updates rather than frequent structural rewrites.

