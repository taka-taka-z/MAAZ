# Changelog

All notable changes to **MAAZ (Zero Trust Maturity Atelier)** are documented here.
This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
and follows the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

---

## [1.0.0] — 2026-04-21 — Ztelier Edition

First public release as the **Ztelier brand launch** edition.
Represents a ground-up redesign from the internal v4.x line, unified
under the Ztelier Common Kit v1.3 design system.

### Added
- **Active Defense (MITRE Engage)** — New Chapter 02.5.2 integrating 12
  selected Engage activities (EAC0001–EAC0023 subset) as a parallel track
  to ZTMM. Provides Y/P/N/NA scoring per activity, Engagement Goals
  coverage bars (Expose / Affect / Elicit), and α slider (0.15–0.35)
  for the boost coefficient. Enables organizations that cannot modify
  their network to still achieve measurable active-defense posture.
- **DCI (Deception Coverage Index)** — Composite score calculated from
  the 12 Engage activities. Boosts effective maturity as
  `effective = ZTMM + (100 − ZTMM) × DCI × α`, giving stronger lift to
  Lv1–2 organizations and diminishing returns toward Lv4.
- **AI-SCF (AI Scope Coverage Factor)** — Weighted scope of AI-specific
  resources (NHI / PAI / AI workload / AI SOC). ATLAS coverage on the
  dashboard now multiplies by `max(AI-SCF, DCI)` so that organizations
  with no AI controls cannot inflate ATLAS scores through general ZTMM
  maturity alone.
- **AD Boost indicator on Maturity Gauge** — AS-IS and TO-BE gauges now
  display the Active Defense contribution (`+X.X`) below the main score
  when DCI > 0, with the computed effective value shown alongside.
- **Snapshot restore** — Export chapter snapshots now support one-click
  restore of full assessment state (customer name, date, AS-IS, TO-BE,
  scope, Active Defense). Previous versions saved but could not restore.

### Changed
- **ATLAS mapping refactor** — The ZTMM-to-ATLAS technique map has been
  rewritten based on the AI-RMF × ATLAS × ZTA three-layer mapping.
  ATLAS techniques are now concentrated on AI-specific controls
  (AP-02, DA-01/02, CC-01/02/03, ID-02, DE-01) rather than being
  attached to generic network controls (NW-01/02). Partial coverage is
  now possible at Lv3 for several AI techniques, enabling graduated
  roadmap design.
- **Snapshot payload** — Now includes `id`, `customerName`,
  `assessmentDate`, and `scopeState` in addition to prior fields.
  Backward-compatible with older snapshot schemas.

### Fixed
- **ATLAS over-reporting bug** — Previously, reaching generic ZTMM Lv4
  would automatically mark ATLAS techniques as covered, even without
  any AI-specific controls. Dashboard now shows ATLAS coverage
  corrected by `max(AI-SCF, DCI)`, with an explanatory AI-Scope warning
  banner when the correction factor is below 99%.

---

## [1.0.0-preview] — 2026-04-20 — Ztelier Edition preview

Preview build before the ATLAS correction and Active Defense work.

### Added
- **Ztelier Common Kit v1.3 integration** — Paper (default light) and Indigo
  (dark) dual themes, driven entirely by CSS custom properties.
- **Scope Coverage Factor (SCF)** — Per-pillar resource-coverage assessment
  that corrects the theoretical TO-BE maturity into effective coverage,
  surfacing the bottleneck pillar automatically.
- **CISO Executive Report** — A4-portrait 8-page print-optimized report
  embedded in the tool (Cover, Summary, Assessment, Threat Landscape,
  Coverage Gap, Roadmap, Recommendations, Appendix).
- **Industry presets** — Six target-profile presets (Financial, Healthcare,
  Manufacturing, Retail, Government, SMB) for one-click TO-BE configuration.
- **Scope Coverage Factor (SCF) view** — Dedicated chapter (02.5) for
  resource-by-resource Y/P/N/N-A scoring across every pillar.
- **Bottleneck detection** — Automatic identification of the pillar whose
  narrow scope most damages effective coverage, with improvement simulation.
- **Shape Diagnosis** — Four-type radar-shape classification
  (基礎構築型 / 偏在型 / 均整型 / 進行型) with recommendation ladder.
- **WCAG AA focus-visible states** — Keyboard-navigation rings across all
  interactive elements (buttons, chips, matrix cells, nav tabs).
- **OS color-scheme respect** — Initial theme now follows
  `prefers-color-scheme` when no user preference has been saved.
- **Print color-adjust preservation** — Forces accurate color reproduction
  in PDF export regardless of browser defaults.

### Changed
- **Typography unified to Outfit** — Single-family display and sans-serif
  stack (replaces the v4.x Inter / IBM Plex Sans mix), with Noto Sans JP
  for Japanese and JetBrains Mono for tabular numerics.
- **Brand palette** — Ztelier Bright Blue `#246CF7` primary and
  Navy `#001744` ink (2026 brand tokens), replacing the v4.x Mars-red /
  tactical-dark visual identity.
- **Dashboard** — Reorganized into six chapters (Hero, Maturity Gauge,
  Threat Coverage, Pillar Radar, Roadmap Table, Residual Critical Threats,
  Executive Summary) with editorial-style chapter markers.
- **63 techniques** — Expanded coverage: MITRE ATT&CK Enterprise 50 +
  MITRE ATLAS 13, each with TO-BE mitigation guidance and ZT action
  recommendation.
- **Dynamic avatar** — Topbar now derives initials from the customer name
  (falls back to `MA` when unset).

### Fixed
- **Italic usage removed** — Replaced with weight + color differentiation
  throughout, per Ztelier v1.3 no-italic rule.
- **Font fallback consistency** — Eliminated `"Inter"` and other non-Ztelier
  fallbacks; all stacks resolve to Outfit / Noto Sans JP / JetBrains Mono.
- **Emoji UI glyphs replaced** — All warning (⚠) and check (✓) glyphs
  converted to inline `currentColor` SVGs for OS-independent rendering.

### Security / Privacy
- **Fully local execution** — No telemetry, no remote API calls, no
  analytics. All assessment data lives in browser memory and
  user-triggered exports.
- **No persistent storage of sensitive data** — Only snapshots (maturity
  levels, not customer details) may be saved to `localStorage`, and only
  when the user explicitly clicks *Save Snapshot*.

---

## Pre-release

Internal versions (v4.0.0 – v4.3.0) were distributed to Zscaler Japan SE
team for Architecture Workshop field use; these are not part of the public
release history.

[1.0.0]: https://github.com/taka-taka-z/maaz/releases/tag/v1.0.0
