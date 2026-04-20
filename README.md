<div align="center">

# MAAZ

**Zero Trust Maturity Atelier**

*Never trust. Always verify.*

[![License: MIT](https://img.shields.io/badge/License-MIT-246CF7.svg)](./LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-001744.svg)](./CHANGELOG.md)
[![Edition](https://img.shields.io/badge/edition-Ztelier-7BA05B.svg)](#)
[![CISA ZTMM](https://img.shields.io/badge/CISA_ZTMM-v2-246CF7.svg)](https://www.cisa.gov/zero-trust-maturity-model)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE_ATT%26CK-Enterprise-C04A4A.svg)](https://attack.mitre.org/)
[![MITRE ATLAS](https://img.shields.io/badge/MITRE-ATLAS-5B4B9E.svg)](https://atlas.mitre.org/)

![MAAZ Social Preview](./social-preview.png)

</div>

---

## Overview

**MAAZ** is a single-file HTML tool that assesses your organization's
Zero Trust maturity against **CISA ZTMM v2**, cross-maps each control
to **MITRE ATT&CK Enterprise** and **MITRE ATLAS** techniques,
and produces a CISO-ready executive report — all without sending a
byte of your data anywhere.

Designed for use in **Architecture Workshops (AW)** with enterprise
customers, MAAZ runs entirely in the browser, reads no cookies, makes
no network calls beyond loading its own CDN dependencies at startup,
and stores nothing except optional user-triggered snapshots.

> **日本語：** MAAZは、CISA ZTMM v2 の 6ピラー × 18コントロールを、
> MITRE ATT&CK（50技法）と MITRE ATLAS（13技法）の脅威軸でクロスマッピングし、
> AS-IS と TO-BE のギャップから投資優先度を導出するシングルHTMLツールです。
> Architecture Workshop での実戦運用を想定しており、オフラインで完結します。

---

## Why MAAZ

Most Zero Trust maturity assessments stop at a heatmap. MAAZ goes further:

| Capability | What it means |
|---|---|
| **SCF — Scope Coverage Factor** | Corrects theoretical TO-BE maturity into **effective** coverage by accounting for what's actually in scope (NHI, legacy LAN/WAN, shadow IT). Surfaces the bottleneck pillar automatically. |
| **ATT&CK ∪ ATLAS mapping** | 63 techniques (50 Enterprise + 13 AI/ML) mapped to concrete ZT control levels. See exactly which threats your TO-BE actually mitigates. |
| **CISO Executive Report** | A4-portrait 8-page print-optimized deliverable. Cover, Summary, Assessment, Threat Landscape, Coverage Gap, Roadmap, Recommendations, Appendix. |
| **Shape Diagnosis** | Four-type radar classification (基礎構築型 / 偏在型 / 均整型 / 進行型) with priority ladder and next-action preview. |
| **Action derivation** | Auto-generates Quick Win / Short-term / Strategic items from each AS-IS → TO-BE gap, with priority inferred from the linked threat severity. |

---

## Features

- **6 pillars × 18 controls** — CISA ZTMM v2 full coverage (Identity,
  Devices, Networks, Applications, Data, Cross-Cutting).
- **63 threat techniques** — MITRE ATT&CK Enterprise 50 + MITRE ATLAS 13,
  each with Japanese descriptions, TO-BE mitigations, and ZT actions.
- **Interactive matrix editor** — Click cells to set AS-IS (fill) and
  TO-BE (dashed outline) per control.
- **6 industry presets** — Financial, Healthcare, Manufacturing, Retail,
  Government, SMB.
- **Dual themes** — Paper (light) and Indigo (dark), respecting OS
  `prefers-color-scheme`.
- **Exports** — JSON (full snapshot), CSV (technique list),
  CSFA (control-scoring format for external analysis), print/PDF.
- **WCAG AA keyboard navigation** — Full focus-visible ring coverage.
- **Fully offline** — Works in air-gapped environments once the CDN
  assets are cached.

---

## Quick Start

```bash
# Clone
git clone https://github.com/taka-taka-z/maaz.git
cd maaz

# Open — no build step, no install
open MAAZ_Ztelier_v1_0_0.html   # macOS
start MAAZ_Ztelier_v1_0_0.html  # Windows
xdg-open MAAZ_Ztelier_v1_0_0.html  # Linux
```

Or simply double-click the HTML file.

**First-run flow:**

1. **Intro** — Enter customer name and (optionally) apply an industry preset.
2. **Assessment** — Click matrix cells to set AS-IS / TO-BE per control.
3. **Scope** (optional but recommended) — Mark resource coverage (Y/P/N/N-A)
   for each pillar to activate SCF correction.
4. **Dashboard** — Review maturity gauge, coverage donuts, pillar radar,
   and shape diagnosis.
5. **Threats** — Filter 63 techniques by phase, actor, or mitigation status.
6. **Actions** — Inspect auto-derived Quick Win / Short / Strategic plan.
7. **Export** — Print to PDF (CISO Report) or export JSON/CSV.

---

## Browser Support

| Browser | Minimum |
|---|---|
| Chrome / Chromium | 120+ |
| Edge | 120+ |
| Safari | 17+ |
| Firefox | 121+ |

> **Note for Zscaler ZIA users:** all CDN dependencies (React, Babel,
> Google Fonts) must pass through your proxy. If your policy blocks
> unpkg.com or fonts.googleapis.com, the tool will still render
> functionally but with system-font fallbacks.

---

## Frameworks & References

| Framework | Version | Source |
|---|---|---|
| **CISA ZTMM** | v2.0 (April 2023) | [cisa.gov/zero-trust-maturity-model](https://www.cisa.gov/zero-trust-maturity-model) |
| **MITRE ATT&CK** | Enterprise | [attack.mitre.org](https://attack.mitre.org/) |
| **MITRE ATLAS** | 2024 | [atlas.mitre.org](https://atlas.mitre.org/) |
| **NIST SP 800-207** | 2020 | [csrc.nist.gov](https://csrc.nist.gov/publications/detail/sp/800-207/final) |
| **Ztelier Common Kit** | v1.3 | Design system tokens |

---

## Tech Stack

- **React 18** (UMD CDN, no build)
- **Babel Standalone** (in-browser JSX transform)
- **Pure CSS** design tokens (no Tailwind, no preprocessor)
- **Single HTML file** — everything inlined, distributable via email or Slack

The whole tool is one `.html` file. No package.json, no node_modules,
no bundler. Open it, use it, share it.

---

## Project Structure

```
maaz/
├── MAAZ_Ztelier_v1_0_0.html   # The entire tool
├── README.md                   # You are here
├── CHANGELOG.md                # Version history
├── LICENSE                     # MIT
├── social-preview.png          # GitHub social preview (1280×640)
├── .gitignore
└── docs/
    ├── release-notes-v1.0.0.md # Release notes (Japanese)
    └── linkedin-post-draft.md  # Announcement post draft
```

---

## Disclaimer / 免責事項

- This is a **personal project** by the author, published under the MIT
  License. It is **not an official Zscaler product**, nor is it endorsed
  by Zscaler, MITRE, or CISA.
- Assessment outputs are **educational and reference-oriented**. Investment
  decisions should involve qualified security architects familiar with
  your specific environment.
- Framework mappings reflect the author's interpretation of public
  specifications and may evolve. Verify against the authoritative sources
  linked above before citing in formal deliverables.

> **日本語：** 本ツールは個人プロジェクトであり、Zscaler・MITRE・CISAの公式
> 製品ではありません。出力はあくまで参考情報として扱い、重要な投資判断は
> 貴社環境に精通したセキュリティアーキテクトの助言を得た上で行ってください。

---

## License

[MIT](./LICENSE) © 2026 taka-taka-z

---

## Acknowledgments

- **CISA** for publishing ZTMM v2 as an open reference.
- **MITRE** for ATT&CK and ATLAS — the foundations on which most modern
  threat-informed defense rests.
- **NIST** for SP 800-207, the canonical Zero Trust architecture
  definition.
- Every Architecture Workshop participant whose questions sharpened
  MAAZ into a real field tool.

---

<div align="center">

**Designed by 髙岡 隆佳 — Evangelist & Transformation Architect**

*Part of the Ztelier suite · MAAZ · Forg · Endeavor*

</div>
