<p align="center">
  <img src="maaz_icon.png" alt="MAAZ Icon" width="160"/>
</p>

<h1 align="center">MAAZ — Zero Trust Assessment</h1>

<p align="center">
  <strong>MITRE ATT&CK & ATLAS × ZTMM Cross-Mapping Assessment Tool</strong><br/>
  <em>Implementation-Driven Zero Trust Maturity Evaluation</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-4.0-blue" alt="Version"/>
  <img src="https://img.shields.io/badge/license-Apache_2.0-blue" alt="License"/>
  <img src="https://img.shields.io/badge/frameworks-ZTMM_×_ATT&CK_×_ATLAS_×_NIST_AI_RMF-green" alt="Frameworks"/>
  <img src="https://img.shields.io/badge/deployment-Single_HTML-purple" alt="Deployment"/>
</p>

---

## MAAZとは

MAAZは、4つのセキュリティフレームワークを1つの統合ビューにクロスマッピングする**単一HTMLファイルのアセスメントツール**です。どのフレームワーク単独でも答えられない問いに対して、一画面で答えを導出します：

> *「ZTMMのこのコントロールをLv1からLv3に上げると、具体的にどのMITRE ATT&CK / ATLAS脅威が緩和され、同時にNIST AI RMFのどの要件が充足されるか？」*

従来のアプローチでは、ATT&CKは脅威をカタログするが防御方法は指示しない、ZTMMは成熟度を定義するがどの脅威が消えるか不明、NIST AI RMFはガバナンス要件を示すが技術的対策との接続が弱い——MAAZはこの三軸を橋渡しします。

---

## クイックスタート

```bash
# クローン
git clone https://github.com/taka-taka-z/maaz.git
cd maaz

# ブラウザで開くだけ（サーバー不要）
open MAAZ_ZT_Assessment.html
```

インストール不要、依存関係なし、オフライン動作可能。

---

## 統合フレームワーク

| フレームワーク | 役割 | 本ツールでの位置付け |
|:---|:---|:---|
| **CISA ZTMM v2** | ゼロトラスト成熟度モデル（6ピラー×18コントロール×Lv1-4） | 実装軸 —「どう実装するか」 |
| **MITRE ATT&CK** | サイバー攻撃手法のナレッジベース（50技法） | 脅威軸 —「何を防ぐか」（従来型） |
| **MITRE ATLAS** | AI/ML攻撃手法のナレッジベース（13技法） | 脅威軸 —「何を防ぐか」（AI特有） |
| **NIST AI RMF 1.0** | AIリスク管理フレームワーク（4機能×17項目） | 管理軸 —「何を管理すべきか」 |
| OWASP LLM Top 10 2025 | LLMアプリの脆弱性ランキング | 参照 — ATLAS技法への補助マッピング |
| EU AI Act 2024 | EU AI規制 | 参照 — ガバナンスLv4の準拠基準 |

---

## コアワークフロー（3ステップ）

```
Step 1: ZTダッシュボード     →  AS-IS / TO-BE 成熟度レベルを設定
         ↕（反復）
Step 2: 脅威×ZTマッピング   →  未対応脅威の把握 & TO-BE調整
         ↓
Step 3: アクション計画       →  ロードマップ自動生成
```

### Step 1: ZTダッシュボード
6ピラー×18コントロールのAS-IS/TO-BEレベルを設定。業種プリセット（金融・医療・製造・IT・政府・中小企業）で一括適用可能。レーダーチャートとピラー別バーチャートでギャップを即座に可視化。

### Step 2: 脅威×ZTマッピング
全63脅威技法がどのコントロールで緩和されるかをマトリクス表示。脅威アクタープロファイル（APT29/APT28/Lazarus/APT10/Generic AI Actor）でフィルタリング可能。AS-IS/TO-BEカバレッジマトリクスで「赤→緑」の変化を確認。

### Step 3: アクション計画
ギャップから自動生成されたアクションカードを3フェーズ（Quick Win → Short-term → Strategic）×優先度（Critical/High/Medium）のロードマップ表示で参照。コントロール依存関係を検証し、前提条件未達を警告。

---

## v4 主要機能

| 機能 | 説明 |
|:---|:---|
| **ATLAS Phase 5（13技法）** | プロンプトインジェクション、RAGデータ窃取、エージェントセッションスマグリング等のAI固有脅威を統合 |
| **脅威アクタープロファイル** | APT29/APT28/Lazarus/APT10/Generic AI Actorの5グループを内蔵、技法フィルタリング対応 |
| **業種別TO-BEプリセット** | 金融・医療・製造・IT・政府・中小企業の6パターンでTO-BEレベルを一括適用 |
| **コントロール依存関係** | 18コントロール間の前提条件を定義、ロードマップ策定時に依存関係を検証 |
| **サブテクニック展開** | T1566、T1059、T1078等の上位技法を下位手法に展開して詳細評価 |
| **JSON import/export** | 評価データの保存・復元、MGA Calculatorとのデータ連携に対応 |
| **スナップショット比較** | 最大5件のスナップショットを保存し、AS-IS/TO-BEの時系列変化を比較 |
| **エグゼクティブレポート** | ピラー別成熟度・Critical優先アクションTop10・スナップショット履歴を1画面に集約 |
| **NHI分類体系** | 6カテゴリ（サービスアカウント/APIキー/OAuthトークン/AIエージェントID/証明書/CI CD）のリスクと対策を体系化 |
| **AISPMメトリクス** | 4カテゴリ16指標の管理ダッシュボード |
| **ライト/ダークモード** | プロジェクター投影（ライト）と通常作業（ダーク）の切替、WCAG AAコントラスト準拠 |
| **印刷対応** | エグゼクティブレポートの印刷用CSS対応 |
| **アクセシビリティ** | キーボードナビゲーション、aria-expanded属性対応 |

---

## ファイル構成

```
maaz/
├── README.md                         # 本ファイル
├── LICENSE                           # Apache License 2.0
├── MAAZ_ZT_Assessment.html           # ツール本体（単一HTML、3,600行）
├── MAAZ_ZT_Concept_Guide.docx        # コンセプトガイド（設計思想・クロスマッピング解説）
├── maaz_icon.png                     # アイコン（96×96 PNG）
└── screenshots/                      # スクリーンショット（任意）
    ├── dashboard_dark.png
    ├── dashboard_light.png
    ├── threat_mapping.png
    └── action_plan.png
```

---

## 技術仕様

- **ランタイム**: ブラウザのみ（サーバー不要、オフライン動作可能）
- **フレームワーク**: React 18.2（インライン埋込）
- **フォント**: Noto Sans JP / JetBrains Mono / Orbitron（Google Fonts、オフラインフォールバックあり）
- **データ永続化**: localStorage（スナップショット・テーマ設定）、JSON export/importで外部保存
- **テーマ**: 火星地表テーマ（ダーク/ライト切替対応、ニューモーフィズムUI）

---

## 詳細・検証タブ

コアフロー完了後のPDCA「Check」フェーズで活用。

| タブ | 目的 | 対象者 |
|:---|:---|:---|
| **脅威評価（検証）** | ZTMMレベル自動判定（理論値）と手動評価（実測値）の照合。RT検証済みフラグ対応 | セキュリティチーム + Red Team |
| **ガバナンス（AI RMF）** | NIST AI RMF 4機能×17項目の充足状況評価。クロスウォーク表による監査証跡 | CISO + コンプライアンス |

---

## 背景

MAAZは、ゼロトラスト・アーキテクチャの導入支援を通じて得られた実践知を体系化したものです。エンタープライズ環境でのArchitecture Workshopを数多く経験する中で、「フレームワークは揃っているのに、それぞれが孤立していて実装に直結しない」という課題に繰り返し直面しました。

本ツールの作者は [Zscaler](https://www.zscaler.com/) に所属するEvangelist & Transformation Architectであり、SSE/ゼロトラスト分野での知見がクロスマッピングの設計に反映されています。ただし、本ツール自体は特定のベンダー製品に依存しない設計であり、ZTMM成熟度の評価と脅威マッピングはベンダーニュートラルな観点で行われます。

---

## 免責事項

- MITRE ATT&CK® および MITRE ATLAS™ は The MITRE Corporation の商標です
- CISA ZTMM v2 は Cybersecurity and Infrastructure Security Agency の公開文書に基づきます
- NIST AI RMF 1.0 / NIST GAI Profile (AI-600-1) は National Institute of Standards and Technology の公開文書に基づきます
- OWASP LLM Top 10 は OWASP Foundation の公開文書に基づきます
- 本ツールにおけるクロスマッピング（ZTMM → MITRE技法、NIST AI RMF → ZTMM等）は作者による独自の対応付けであり、各フレームワークの公式な推奨ではありません

---

## バージョン履歴

| バージョン | 日付 | 変更内容 |
|:---|:---|:---|
| v4.0 | 2026-03 | ゼロトラスト実装駆動型に全面再設計：3ステップのコアワークフロー、ピラー中心のダッシュボード、アクション計画の自動生成、脅威×ZTマッピングマトリクス、ATLAS 13技法、脅威アクター5グループ、業種プリセット6種、JSON import/export、スナップショット比較、NHI分類体系、AISPMメトリクス、ライト/ダークモード、印刷対応、アクセシビリティ強化 |
| v3.0 | 2026-02 | ATLAS Phase 5（AI技術13件）追加、XAIスコアリング、NIST AI RMFタブ、アコーディオン展開式解説 |
| v2.0 | 2026-01 | ZTMM→MITRE自動導出システム、MGA Calculator連携 |
| v1.0 | 2025-12 | 初版リリース：ATT&CK 50技術 + ZTMMクロスマッピング |

### ロードマップ

- **v5.0（予定）**: NIST Cyber AI Profile（IR 8596）正式化に伴うCSF 2.0ベースへの移行を検討中。COSAiS等のAIエージェント・セキュリティ標準化動向も追跡

---

<p align="center">
  <img src="maaz_icon.png" alt="MAAZ" width="48"/>
  <br/>
  <strong>MAAZ</strong> — Where Zero Trust meets Threat Intelligence
  <br/>
  <em>Licensed under Apache 2.0</em>
</p>
