# MAAZ v1.0.0 — Ztelier Edition リリースノート

**リリース日**: 2026-04-20
**配布形態**: シングルHTMLファイル（オフライン完結）
**ライセンス**: MIT

---

## ひとことで

CISA ZTMM v2 × MITRE ATT&CK × MITRE ATLAS を一枚に綴じ、
CISO向け A4 8ページ エグゼクティブレポートまで出力できる
**ゼロトラスト成熟度アセスメントツール**の公開版です。

Architecture Workshop の現場運用で鍛え上げた v4.x 系を、
Ztelier Common Kit v1.3 デザインシステム配下で**全面リデザイン**しました。

---

## v1.0.0 の 7 つのハイライト

### 1. Ztelier ブランド統合 — 視覚的な一貫性

Ztelier 傘下の MAAZ・Forg・Endeavor と完全に共通化された
カラートークン（Bright Blue `#246CF7` / Navy `#001744` / Sage `#7BA05B`）
と、Outfit + Noto Sans JP + JetBrains Mono の統一タイポグラフィで
再構築。LinkedIn投稿・社内資料・顧客提出物の見た目が揃います。

### 2. SCF — Scope Coverage Factor

**成熟度が高くても、スコープが狭ければ効かない。**

ZTMM Lv3 達成を謳うプロジェクトの多くで、NHI（Non-Human Identity）
未対応・LAN/WAN の従来接続残存などにより、実効カバレッジが想定を
大きく下回る問題を数式で可視化します。

各ピラーのリソース網羅率を Y/P/N/N-A で評価 → 技法カバレッジに
乗算 → **ボトルネック柱を自動特定**し、改善シミュレーションまで
提示します。

### 3. CISO Executive Report（A4 8ページ）

印刷ボタン一発で、以下の構成の A4 縦 8ページレポートが PDF 化されます：

| Page | 内容 |
|---|---|
| 1 | Cover — 顧客名、実施日、KPI サマリ |
| 2 | Executive Summary — 現状評価と投資判断の一文要約 |
| 3 | Assessment Detail — 18コントロール詳細 |
| 4 | Threat Landscape — ATT&CK/ATLAS カバレッジ |
| 5 | Coverage Gap — SCF 分析・ボトルネック |
| 6 | Roadmap — Quick Win / Short / Strategic |
| 7 | Recommendations — 優先度付き施策 |
| 8 | Appendix — フレームワーク参照・注記 |

CISO・経営会議への提出を想定した正式ドキュメントとして設計しました。

### 4. Shape Diagnosis — 形状診断

6ピラー・レーダーチャートの形状から、組織のゼロトラスト成熟段階を
4類型に分類します：

- **基礎構築型** — 全柱 Lv2 未満、まず底上げが必要
- **偏在型** — 強弱の開きが大きく、最弱柱に集中投資が効果的
- **均整型** — バランス良いが中位で停滞しがち
- **進行型** — 複数柱が成熟に向けて進行中

### 5. 業界プリセット 6 種

金融、医療、製造、小売、政府、SMB の典型的 TO-BE 目標を
ワンクリック適用。後からコントロール単位で微調整できます。

### 6. 63 技法のクロスマッピング

MITRE ATT&CK Enterprise から実戦頻出の 50 技法（Picus Red Report 2025
等を参照）、MITRE ATLAS から 13 技法を選定。各技法に日本語説明・
TO-BE 緩和策・ZT アクション推奨を併記しました。

### 7. WCAG AA アクセシビリティ

全インタラクティブ要素に `:focus-visible` リングを実装。キーボード
専用の操作が可能で、アクセシビリティ検査にも耐えます。

---

## 使い方（30 秒版）

1. リポジトリから `MAAZ_Ztelier_v1_0_0.html` をダウンロード
2. ダブルクリックでブラウザ起動
3. Intro → 顧客名入力 → 業界プリセット適用
4. Assessment → セルクリックで AS-IS / TO-BE 設定
5. Scope → リソース網羅性を Y/P/N/NA で評価（任意）
6. Dashboard で全体像を確認
7. Export → 印刷 / PDF で CISO Report 出力

---

## データの扱いについて

- **完全オフライン動作**：外部 API 呼び出しは起動時の CDN
  （React / Babel / Google Fonts）のみ。
- **テレメトリなし**：利用状況・評価データを一切送信しません。
- **ローカル保持のみ**：スナップショット機能は明示的に押下時
  `localStorage` に保存。顧客名や評価詳細は含まれません。

ZIA 環境では CDN アクセスが必要です。ポリシーで unpkg.com /
fonts.googleapis.com をブロックしている場合、システムフォント
フォールバックで動作します（機能は保持されます）。

---

## ブラウザ要件

- Chrome / Edge 120+
- Safari 17+
- Firefox 121+

IE11 および古い Edge は**非対応**です。

---

## フレームワーク参照

| フレームワーク | バージョン |
|---|---|
| CISA ZTMM | v2.0 (2023-04) |
| MITRE ATT&CK | Enterprise |
| MITRE ATLAS | 2024 |
| NIST SP 800-207 | 2020 |

---

## 既知の制約 / ロードマップ候補

本 v1.0.0 は GA リリースですが、以下は v1.x で検討中です：

- 日本語 / 英語 UI 切替（現状は日本語前提、英語は部分的）
- CSFA（Cyber Security Framework Assessment）連携の双方向化
- Forg 組織摩擦係数との統合（F_org とのマトリクス連動）
- Amplify ZTMM Goal Setting との連動

---

## 免責事項

本ツールは個人プロジェクトであり、Zscaler・MITRE・CISA の公式
製品ではありません。出力結果はあくまで参考情報として扱い、
重要な投資判断は貴社環境に精通したセキュリティアーキテクトの
助言を得た上で行ってください。

フレームワーク・マッピングは著者による公開仕様の解釈であり、
正式提出物に引用する際は、一次情報源（CISA / MITRE / NIST）を
確認してください。

---

## クレジット

Designed by **髙岡 隆佳** — Evangelist & Transformation Architect

Part of the **Ztelier** suite — MAAZ · Forg · Endeavor

License: [MIT](../LICENSE)

---

## フィードバック

Issue・Pull Request 歓迎です。AW 現場での使用感、フレームワーク・
マッピングへの修正提案、SCF 係数の精緻化案など、実戦の声が一番の
改善ドライバになります。
