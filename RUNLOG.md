# RUNLOG — website-builder-site v2 + kit v0.1 build

Kit: website-builder-kit-v0.1.1 (responsive states promoted to canonical; v0.1 frozen superseded)

## Inputs

- Proposal (governing): `governor/review/website-builder-site-v2-2026-10-12/PROPOSAL.md` (§2 design system, §3 kit spec, §5 output contract, §9 acceptance).
- Placement brief: `review/website-builder-site-v2-2026-10-12/BRIEF.json` (2 scopes, 11 outputs).
- v1 content sources: `governor/output/website-builder-site-2026-10-12/` (index, services, proof, contact) — copy intent and IA preserved, presentation elevated.

## Skeleton conformance (per page)

- `index.html` ← `skeletons/home.html`: filled `head/nav/hero_*`, `services_preview` (3 tier cards carried from v1 services), `proof_strip` (band-alt verify lede + proof link), `final_cta`. No slots omitted.
- `services.html` ← `skeletons/services.html`: filled `service_cards` (v1's 3 tiers verbatim intent), `delivery_guarantees` (v1's 3 guarantees), `process_steps` (3 generic steps: scope → build → verify & deliver; process copy only, no factual claims), `final_cta`.
- `proof.html` ← `skeletons/proof.html`: filled `verification_table` (v1's 4 rows), `claims_limiting_note` (v1 timeline/cost note), `metrics_optional` / `case_cards_optional` / `testimonial_placeholder_optional` as clearly-marked `[OWNER TO SUPPLY]` placeholders only — no figures, cases, or quotes invented.
- `contact.html` ← `skeletons/contact.html`: filled `mailto_cta`, `contact_details` (name/email/phone/service area/social, all `[OWNER TO SUPPLY]`), `no_form_no_tracking_note` (v1 copy preserved), `faq` (4 process questions; answers state process only, no invented facts).

## Frozen-token conformance

- The `:root` block and all eleven canonical classes (`.measure .band .band-alt .btn .btn-primary .btn-ghost .card .kicker .grid-2 .grid-3 .active`) are inlined VERBATIM from kit v0.1 `tokens.css` into each page. No token or canonical-class contradiction.
- Purely ADDITIVE page styling (new selectors only — none redefines a canonical class or token). Complete inventory, audited across all four pages (base declarations; media-query inner rules are CANONICAL v0.1.1, not additions — see responsive note below):
  - Shared by all 4 pages: `body`, `h2`, `h3`, `.site-header`, `.site-header .measure`, `.brandmark`, `.site-nav`, `.site-nav a:not(.active)`, `.site-nav a:hover`, `.hero-band`, `.hero-band .kicker`, `.hero-band h1`, `.hero-band .lede`, `.hero-band .btn-ghost`, `.hero-ctas`, `.section-lede`, `.card p`, `.rule`, `.site-footer`, `.site-footer a`, `.site-footer .cols`, `.site-footer ul`, `.site-footer li`, `.bottom-bar`, `.bottom-bar .measure`.
  - `services.html` only: `.check-list`, `.check-list li`, `.check-list li::before`, `.step-num`.
  - `proof.html` only: `.verify-table`, `.verify-table th, .verify-table td`, `.verify-table tr:last-child th, .verify-table tr:last-child td`, `.verify-table th`, `.result-pass`, `.claims-note`, `.placeholder`, plus two inline presentation declarations (`<small style="font-size:.875rem;color:var(--ink-muted)">`, `<p style="margin-top:1.5rem">`).
  - `contact.html` only: `.detail-list`, `.detail-list li`, `.detail-list strong`, `.quiet-note`, `.faq dt`, `.faq dd`, plus one inline spacing declaration (`<p style="margin-top:1.5rem">`).
  - Logged here per §3.4.
- Kicker rule honored: white kicker on dark hero bands; no accent-colored body text anywhere (accent used only on decorative `.rule` bars, check bullets, and note borders).
- One `aria-current="page"` + `.active` nav link per page (self-link). Additive `.site-nav a:not(.active)` reset lets the canonical `.active` underline render (fix pass). Stacked nav at `@media (max-width: 640px)` (includes 640px); horizontal strictly above. `@media (max-width: 860px)` collapses 3-col grids + hero type to 2rem.

## Manual review checklist (bounded, per proposal §6/§9 — checker covers metadata only)

- [x] All internal links resolve to the 4 sibling pages (relative hrefs, no external links except `mailto:`).
- [x] Placeholders flagged as expected `[OWNER TO SUPPLY: …]`: email/phone (all pages incl. mailto hrefs), owner name/service area/social (contact), year (footers), metrics/cases/testimonial (proof).
- [x] HTML structure: single `h1` per page, hierarchical h2/h3, `<main>` landmark around body sections between hero and footer (fix pass), `lang="en"`, meta viewport + description, inline-SVG data-URI favicon on all 4 pages, no external assets/frameworks/fonts/JS/form backends.
- [ ] Metadata checker pass (`tools/task_output_check.py`) — not run in this scope; Governor to run.
- [ ] Owner visual approval — pending (carries over from v1).

## Fix pass (QA, 2026-10-12)

- Active-link contradiction fixed: additive nav reset narrowed to `.site-nav a:not(.active)` on all 4 pages so the canonical `.active` underline renders.
- Attribution qualified: proof hero (kicker/h1/lede) states the v1 pages were the wf-1101 demonstration and v2 is a hand-authored redesign with determinism deferred; historical v1 verification table intact. Index proof-strip lede + CTA reworded to attribute verification to v1, with no implication v2 reproduction was verified.
- `<main>` landmark restored around body sections between hero and footer on all 4 pages (matches skeletons + v1).

## Responsive conformance (v0.1.1 re-inline, 2026-10-12)

- The `@media (max-width: 860px)` and `@media (max-width: 640px)` rules were promoted word-for-word to canonical kit definitions in `website-builder-kit-v0.1.1/tokens.css`; each page inlines that canonical block VERBATIM (byte-identical, verified by diff). Page-level responsive overrides no longer exist as overrides — they are frozen canonical copies.
- Content, copy, placeholders, heroes, footers unchanged; prior fix-pass corrections (active-link scope, attribution, `<main>` landmarks) preserved.

## SHA-256 (pages, post-v0.1.1-re-inline — SUPERSEDED by cascade fix; preserved from commit 21a06d6 for audit trail)

- `index.html`: `4a6d31e48c0387b98fad448e42cc8b0222a165a97678109077f37e6ee8a89ee1`
- `services.html`: `db05365be64dddd6cf97edfb68f634fb564f99a1ec18798804ed4760b21eb0d2`
- `proof.html`: `76b8aec3dd8551de55c0cf7f04d7cb78ea44f4caa333f4856bb5cb63aaad7717` (meta-description v1 credit, micro-fix)
- `contact.html`: `a1373ba1e0e8861785d623973f105b6ea23ad2764f25964ef0ea78ddc404e56e`

## SHA-256 (pages, post-cascade-fix — CURRENT)

- `index.html`: `325298ede6abed8555669ae83f12798d5ba0dd4758d91d09032bad05cb119754`
- `services.html`: `3b3df53332b3cef5531c08794cb3b64ed4cfaaab57f2cf15e94263baf7ecc97f`
- `proof.html`: `2cdee1736e8f630169405ffff5a74c04e0c33ac4f0b3cd65d52c89f868ea6e02` (cascade-fix current; pre-fix `76b8aec3…` preserved above)
- `contact.html`: `2f8f0a17dbcd56c94e8a0062e78751cb97c92232cc2c95d33e9f9fcdf8cd7b23`

## Appendix — v2.1 aesthetics revision (2026-10-12)

Kit line bump: `website-builder-kit-v0.1.1` → `website-builder-kit-v0.1.2` (v0.1/v0.1.1 untouched). Proposal (governing): `governor/review/website-builder-site-v2.1-2026-10-12/PROPOSAL.md` (§2 work items, §8 acceptance). Brief amendment is coordinator action (not done here).

### Per-change notes (§2.1–§2.4)

- **2.1 Semantic token rename:** `tokens.css` = v0.1.1 content VERBATIM except 13 literal→semantic renames (`--bg`→`--color-bg`, `--bg-alt`→`--color-bg-alt`, `--ink`→`--color-text`, `--ink-muted`→`--color-text-muted`, `--brand`→`--color-brand`, `--brand-deep`→`--color-brand-deep`, `--accent`→`--color-accent`, `--line`→`--color-line`, `--card`→`--color-surface`, `--r-sm`→`--radius-sm`, `--r-md`→`--radius-md`, `--measure`→`--layout-measure`, `--font`→`--font-body`; full map in kit README) plus 2 ADDED tokens `--type-hero-min: 2rem` / `--type-hero-max: 3.5rem` (§2.2). All 4 pages re-inlined from v0.1.2 by scripted splice — canonical block verified byte-identical substring of each page. Zero stale literal refs (exact-name grep over kit + pages). Skeletons: verbatim copies of v0.1.1 (identical hashes — they carry no token references, so no reference updates applied).
- **2.2 Fluid hero type:** additive rule `.hero-band h1 { font-size: clamp(var(--type-hero-min, 2rem), 1.2rem + 4vw, var(--type-hero-max, 3.5rem)); … }` on all 4 pages. Bounds rem-anchored (respect user font-size/zoom); canonical `@media (max-width: 860px)` fixed `2rem` retained verbatim per frozen rule, SOFTENED by cascade fix-pass (see Fix-pass section below): at ≤860px the canonical 2rem rule governs (same specificity, later in source); the clamp is fluid only above 860px up to the 3.5rem cap. The 320px word-fit arithmetic (~240px longest word < ~272px content width) is computed from source values only — browser rendering NOT-PERFORMED.
- **2.3 Inline SVG icon set + favicon:** hand-authored, no editor metadata/ids, all `currentColor`, all `aria-hidden="true"` + `focusable="false"` (decorative; adjacent text carries meaning). Set: logo monogram (rounded-square + W, 346B, in `.brandmark` all pages), service icons — document/layers/refresh (292/314/320B; index + services cards), check bullets (215B each; services guarantee list, replacing the old `.check-list li::before` CSS check — rule retired), pass checks (214B; proof result pills), mail icon (307B; contact mailto CTA). Favicon replaced with path-based monogram data-URI (~315B link tag, no `<text>` element). Per-page SVG totals: index 1272B (4), services 1917B (7), proof 1202B (5), contact 653B (2) — all ≤2KB/icon, logo ≤8KB, ≤30KB/page. Content, placeholders, attribution, nav actives unchanged.
- **2.4 A11y fixes (markup/CSS only):** skip-to-content link (`<a class="skip-link" href="#main">`, offscreen until `:focus`) + `<main id="main" tabindex="-1">` on all 4 pages; `:focus-visible` 3px brand outline (white override on hero/footer dark surfaces); `.brandmark` now `inline-flex` for logo alignment (no visual change otherwise).

### A11y checklist per page (§2.4 a–f)

Contrast ratios (computed relative luminance, same palette all pages): body `#14202E`/white **16.46:1**; muted `#5A6B7E`/white **5.47:1**; muted/`#F6F7F9` **5.10:1**; white/`#143DA8` (hero/footer/buttons) **9.28:1**; white/`#1B4FD8` (btn-primary/result pills) **6.65:1** — all ≥ 4.5:1.

- `index.html` — (a) skip link present/targets `#main`; (b) focus-visible brand outline, white on hero/footer; (c) single h1, h2×3 → h3×3 logical order, header/nav-main-footer landmarks; (d) zero `<img>`, all inline SVG decorative `aria-hidden`; (e) ratios above, PASS; (f) 200% zoom: rem-based type, collapsing grids (860/640px), wrapping CTAs, no fixed heights — static source only (rem-based type, collapsing grids, wrapping CTAs, no fixed heights observed in source); live 200%-zoom NOT-PERFORMED (no browser in this lane).
- `services.html` — (a)(b) same; (c) single h1, h2×4 → h3×6; (d) same, check SVGs decorative (li text carries meaning); (e) PASS; (f) same as index (static source only); live 200%-zoom NOT-PERFORMED.
- `proof.html` — (a)(b) same; (c) single h1, h2×3 → h3×5; table uses `scope="col"` headers; (d) same, pass-icon SVGs decorative (pill text carries status); (e) PASS; (f) same as index (static source only); live 200%-zoom NOT-PERFORMED.
- `contact.html` — (a)(b) same; (c) single h1, h2×2, no h3 (matches v2); `dl.faq` dt/dd structure kept; (d) same, mail SVG decorative (link text carries meaning); (e) PASS; (f) same as index (static source only); live 200%-zoom NOT-PERFORMED.

### New file hashes (post-v2.1)

- `website-builder-kit-v0.1.2/tokens.css`: `e1e67e12ada1d2ff6fb92da99f56ea90f3e6e2e4fd0436b73d9aac093b37e30e`
- `website-builder-kit-v0.1.2/README.md`: `b234f5a13cea6c95100257145ebca1b77976260f672867ea7870660808385fda`
- `website-builder-kit-v0.1.2/skeletons/`: identical to v0.1.1 (`contact e6aa8c8f…`, `home 231a38dd…`, `proof 5ce7b678…`, `services f6a60713…`)
- `index.html`: `325298ede6abed8555669ae83f12798d5ba0dd4758d91d09032bad05cb119754`
- `services.html`: `3b3df53332b3cef5531c08794cb3b64ed4cfaaab57f2cf15e94263baf7ecc97f`
- `proof.html`: `2cdee1736e8f630169405ffff5a74c04e0c33ac4f0b3cd65d52c89f868ea6e02`
- `contact.html`: `2f8f0a17dbcd56c94e8a0062e78751cb97c92232cc2c95d33e9f9fcdf8cd7b23`

Additive-selector inventory delta vs prior RUNLOG entry: shared adds `.skip-link`, `.skip-link:focus`, `:focus-visible`, `.hero-band :focus-visible`, `.site-footer :focus-visible`, `.icon-logo`, `.icon-card` (+`.btn-icon` contact only, +`.pass-icon` proof only, +`.check-icon` services only); `.brandmark` extended with `display:inline-flex;align-items:center;gap:.5rem`; `.hero-band h1` base size now `clamp(...)`; services retired `.check-list li::before`. Kicker rule honored; accent still decorative-only.

### Fix pass — cascade order (QA FAIL remediation, 2026-10-12)

**Fault:** the canonical v0.1.2 block sat BEFORE additive base rules, so equal-specificity additive rules won source order everywhere (footer 3-col persisted below 860px; clamp overrode the canonical mobile 2rem; hero padding/header/nav-gap overrides lost below 640px).

**Fix (all 4 pages, CSS order only — zero content/copy/placeholder/aria changes):** additive base styling now comes FIRST with a one-line order-note comment; the canonical v0.1.2 block (skeletons untouched — out of scope) follows BYTE-IDENTICAL (substring-verified post-fix). Fluid-clamp design preserved: clamp governs above 860px, canonical 2rem at/below it.

**OBSERVED static-analysis results (source only):** per page, additive rule precedes its canonical counterpart in source for all 5 contested pairs — (1) `.hero-band h1` clamp vs canonical-860 `2rem`; (2) `.site-footer .cols` grid vs canonical-860 `1fr`; (3) `.hero-band` padding vs canonical-640 `2.5rem 0`; (4) `.site-header .measure` flex vs canonical-640 column; (5) `.site-nav` flex vs canonical-640 column. Specificity of each pair is an exact tie (e.g. `.hero-band h1` = (0,1,1) both sides), so later-source canonical wins; the three-valued hero behavior is therefore 2rem at ≤860px (canonical), fluid clamp 860px→cap, 3.5rem max. No additive selector equals any canonical BASE selector (checked programmatically), so moving the canonical base rules later introduces no new overrides. Breakpoint values observed in source: `max-width: 860px` and `max-width: 640px`, unchanged.

**NOT-PERFORMED (no browser in this lane):** browser rendering, keyboard walkthrough, live 200%-zoom. 2026-10-12 operational attempt: local HTTP server started, but browser navigation to both localhost and file:// URLs is blocked by environment policy — verification genuinely unavailable here, not skipped. Owner visual approval in their own browser serves as the rendering check. Contrast ratios remain computed-from-source-hex (relative luminance), not measured. Prior appendix language overstating operational certainty ("no-loss-by-construction", unqualified mobile claims) is corrected in place above.

**Post-fix hashes:** `index.html 325298ede6abed8555669ae83f12798d5ba0dd4758d91d09032bad05cb119754`, `services.html 3b3df53332b3cef5531c08794cb3b64ed4cfaaab57f2cf15e94263baf7ecc97f`, `proof.html 2cdee1736e8f630169405ffff5a74c04e0c33ac4f0b3cd65d52c89f868ea6e02`, `contact.html 2f8f0a17dbcd56c94e8a0062e78751cb97c92232cc2c95d33e9f9fcdf8cd7b23` (hash block above updated to match).

## Appendix — v2.1 page re-inline retry (2026-10-13)

Context: a prior attempt's page edits were reported as never landed; this retry re-verified all 4 pages in place against kit v0.1.2 and the §2 work items. FINDING: the v2.1 re-inline was already present on disk — every page hash-matched the post-fix hashes recorded above, so NO page bytes were changed in this retry (re-applying identical content would only churn hashes). Verification below is fresh evidence from this run, not carried over.

### Fresh verification (this run, source only)

- **Hashes (unchanged, re-measured):** `index.html 325298ede6abed8555669ae83f12798d5ba0dd4758d91d09032bad05cb119754`, `services.html 3b3df53332b3cef5531c08794cb3b64ed4cfaaab57f2cf15e94263baf7ecc97f`, `proof.html 2cdee1736e8f630169405ffff5a74c04e0c33ac4f0b3cd65d52c89f868ea6e02`, `contact.html 2f8f0a17dbcd56c94e8a0062e78751cb97c92232cc2c95d33e9f9fcdf8cd7b23`.
- **2.1 renames:** all 13 semantic tokens + `--type-hero-min/--type-hero-max` present (1 definition each) in all 4 pages; zero stale v0.1.1 literal names (exact-name grep, exit 1 = no match).
- **Canonical block:** kit `tokens.css` content is a byte-identical substring of each page (CANONICAL-VERBATIM ×4); additive base styling precedes the canonical block in source on all 4 pages (order-note comment line 10, canonical comment follows) — canonical-block-last cascade preserved.
- **2.2 hero clamp:** `clamp(var(--type-hero-min, 2rem), 1.2rem + 4vw, var(--type-hero-max, 3.5rem))` present once per page; rem-anchored bounds.
- **2.3 SVG + favicon:** per-page SVG totals — index 4/1272B, services 7/1917B, proof 5/1202B, contact 2/653B; max single SVG 346B (logo monogram); all `currentColor`, all decorative `aria-hidden="true"` + `focusable="false"`; data-URI favicon link present on all 4 pages. Budgets OK (≤2KB/icon, logo ≤8KB, ≤30KB/page).
- **2.4 a11y:** skip-link ×1, `:focus-visible` ×3, single `<h1>` ×1, `<main id="main">` ×1, one `aria-current="page"` ×1 per page — all confirmed on all 4 pages. Copy, placeholders, attribution, landmarks, and nav actives untouched (no page bytes changed).
- **Scope:** pages only, in place. No kit/brief/commit/push edits made in this retry.

### Change notes

- Page files: NO CHANGES (already conformant; hashes identical to post-fix block).
- This RUNLOG: appended this appendix entry only.
