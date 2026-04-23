# Handoff: 飲みノート (NomiNote) Landing Page

## Overview
飲みノートは、飲み会の会話をAIが議題ごとに要約するiOS/Androidアプリです。本バンドルは、リリース時に公開する公式LP（1ページ縦長スクロール）＋法務ページ3点（プライバシー／利用規約／特商法表記）のデザイン一式です。

LPの最重要ミッションは **「録音することへの心理的ハードルを下げる」** こと。これを達成するため、2つのコアバリュー（①録音を残さない／②プライベートな話は要約しない）と同席者への約束を、視覚的に「特別扱い」しています。

## About the Design Files
このバンドルに含まれるHTML/CSSファイルは、**デザインのリファレンス（プロトタイプ）** であり、そのまま本番にコピーして使うためのものではありません。意図しているレイアウト、トーン、インタラクションを正確に示すための設計資料です。

Claude Code（または担当エンジニア）には、**これらのHTMLデザインをプロジェクトの既存環境で再現する** ことを期待しています。

- すでにフロントエンドの環境（Next.js / Astro / SvelteKit / Nuxt など）があれば、その慣習・ライブラリ・コンポーネント体系に沿って実装してください。
- まだ環境がない場合は、静的LPに最適な構成を選んでください（**Astro 推奨**。理由：ビルド出力が純粋な静的HTML＋最小JS、画像最適化とSEOタグ周りが手厚い、Lighthouse 90+を取りやすい）。

## Fidelity

**High-fidelity (hifi)** — ピクセルパーフェクトに近いモックです。色・タイポグラフィ・余白・角丸・影はすべて意図通りに決まっています。ピクセル単位で忠実に再現してください。以下のデザイントークンが既に `assets/nm-tokens.css` に全て入っています。

なお、モックアップ中の「アプリ画面の縮小イメージ」（§3のBefore/After、§7の使い方4ステップ内のサムネ、§8の共有モーダル）は **プレースホルダです**。本番では:
- §3・§8 → 実アプリの同等スクリーンショット画像に差し替え
- §7 → 実アプリのスクリーンショット画像に差し替え（4枚）
を推奨します。

## Pages / Sections

ページは全部で4つ:
1. `index.html` — LP 本体（1ページ縦長スクロール）
2. `privacy.html` — プライバシーポリシー（DRAFT）
3. `terms.html` — 利用規約（DRAFT）
4. `legal.html` — 特定商取引法に基づく表記（DRAFT）

### index.html セクション構成（上から順に）

| # | セクション | 目的 | 特記 |
|---|---|---|---|
| 0 | Fixed Nav | ブランド・主要セクションへのジャンプ | スクロール時に背景が暗く |
| 1 | Hero | キャッチコピー＋アプリアイコン＋ストアバッジ | 最上部 |
| 2 | Problem | 「飲み会で録音、できないですよね」 | 録音する人／される人、両方の不安を引用カードで |
| 3 | Solution | 「全部録って、要約だけ残す」 | Before / After の2カラム |
| 4 | ★Core Value 1 | **録音を残さない** | A. クラウド非アップ / B. 24h削除を並列大型カードで |
| 5 | ★Core Value 2 | **プライベートなことは要約しない** | 要約する／しないの対比リスト |
| 6 | ★同席者への約束 | 録音される側への誓約 | 和紙風一筆箋＋縦書き数字＋朱印モチーフ |
| 7 | How (使い方4ステップ) | 01〜04の連番カード | 各ステップに小さな画面サムネ |
| 8 | Share | 「共有できるのは要約だけ」 | 共有モーダルのモック |
| 9 | Pricing | Free / ¥300月 / ¥2,980年 | 3カード横並び、24h削除はどのプランでも変わらないことを明示 |
| 10 | FAQ | アコーディオン | 録音する側 / される側 / プライバシー / 技術 / 料金 の5タグ |
| 11 | Developer Letter | なぜ作ったか | 開発者からの長文メッセージ |
| 12 | Final CTA | キャッチコピー再掲＋ストアバッジ | 最終誘導 |
| 13 | Footer | リーガルリンク必須 | プライバシー／利用規約／特商法表記 |

**★マークの3セクションは「特別扱い」が意図です:** 背景色を `--nm-bg-raised` に切り替え、上下に大きな余白、セクション見出しを他より1.2倍大きく、と視覚的にコア部分であることを伝えています。

## Core Design Tokens

すべて `assets/nm-tokens.css` に定義済み。CSS変数として流用してください。

### Colors（ダークモード基調・冷色一切なし）
```
--nm-bg:           #1a1512  /* 深い焦げ茶・背景 */
--nm-bg-raised:    #201812  /* ★セクション背景 */
--nm-surface:      #231b17  /* カード */
--nm-surface-2:    #2a211c  /* カード強調 */
--nm-border:       #3a2e25  /* ヘアライン */
--nm-border-strong:#544234  /* 強調枠線 */

--nm-gold:         #d4a853  /* プライマリアクセント（CTA・見出し下線） */
--nm-gold-hover:   #b8913f
--nm-gold-deep:    #a08236
--nm-fg-on-gold:   #1a1512

--nm-fg:           #f4ecd8  /* プライマリテキスト */
--nm-fg-2:         #d9ccb0  /* 本文やや弱め */
--nm-fg-secondary: #a89684  /* セカンダリ */
--nm-fg-tertiary:  #6b5d4f  /* ヒント */

--nm-success:      #6fa77a  /* ✅ 完了 */
--nm-info:         #b59cff  /* 🔒 24h削除バッジ（soft lavender） */
--nm-rec:          #c4553c  /* 録音インジケータ */
```

### Typography
```
--nm-font-jp:   "Hiragino Sans", "Noto Sans JP", system-ui, sans-serif
--nm-font-ser:  "Cormorant Garamond", serif          /* 数字・引用 */
--nm-font-mono: "JetBrains Mono", monospace          /* 録音タイマー */
```
- 日本語行間は **1.7〜1.9** を厳守
- ヒーロー見出し: `clamp(32px, 5.4vw, 68px)` / weight 700 / line-height 1.35
- セクション見出し (h2): `clamp(30px, 4.4vw, 52px)` / weight 700 / line-height 1.3
- リード本文: `clamp(16px, 1.5vw, 19px)` / line-height 1.9
- 本文: 16px / line-height 1.85

### Spacing・Radius
- カード角丸: 16–18px
- ボタン角丸: 12–14px、ピル 999px
- セクション縦パディング: デスクトップ 120px / モバイル 72px
- セクション横パディング: デスクトップ 32px / モバイル 20px

### Ambient（ブランドの空気感）
- 背景全体に **3% のグレインオーバーレイ**（SVGノイズフィルタ、`mix-blend-mode: overlay`、`lp-root::before` で実装）
- ヒーロー上部と最終CTA付近に **ランタンのラジアルグロー**（gold 22% → 6% → transparent）1つずつ
- フルブリードのグラデーション壁紙は使わない

### Motion
- Ease: `cubic-bezier(0.32, 0.72, 0, 1)`
- Reveal-on-scroll: `opacity 0→1, translateY 24px→0`, 600ms, IntersectionObserver
- ナビ背景: スクロール20px超で `rgba(26,21,18,0.88)` に濃く

## Interactions & Behavior

- **Fixed Nav**: スクロール位置に応じて背景透明度が変化
- **Reveal on scroll**: `[data-reveal]` 属性の要素が view に入ると fade-up
- **FAQ アコーディオン**: クリックで開閉、`data-open="true/false"` で制御。ARIAも追加推奨
- **Tweaks パネル**: 開発・デザイン確認用。本番デプロイでは**このパネルと関連JSを削除**してください（`.lp-tweaks` と `TWEAKS` 定数、`setupTweaks()` / `applyTweaks()`）
- **ストアバッジ**: 現在はダミーの `href="#final"`。リリース時に実URLへ差し替え
- **画面内リンクのsmooth scroll**: CSS `scroll-behavior: smooth`（`html, body`）で実装

## Content Rules（重要・維持すべき）

- **です／ます調**。固い敬語にしない、カジュアルにもしない
- **絵文字は装飾ではなく分類記号**として使う: 🎯議題 / 📝要点 / 💡アイデア / 🔒プライバシー・24h削除 / 👥仲間 / 🎙録音 / ✅完了 / ⏳24h / 📁ファイル
- **禁止表現**: 「○倍速」「革命」「次世代」など派手な煽り
- **変更不可の文言**:
  - キャッチコピー: 「飲み会で生まれた『あのアイデア』を、シラフのあなたに届ける。」
  - コアバリュー見出し①: 「録音を残さない。」
  - コアバリュー見出し②: 「プライベートなことは要約しない。」

## Legal Pages（ひな形）

`privacy.html` / `terms.html` / `legal.html` はすべて `DRAFT` バッジ付きのひな形です。リリース前に以下を必ず更新してください:

- `legal.html`: 代表者氏名・正式住所・電話番号
- `privacy.html`: AI処理委託先（OpenAI / Anthropic のどちらを採用したか確定版に）
- `terms.html`: 制定日・施行日
- すべてのページから `DRAFT` バッジ (`.draft` クラス) を削除

## SEO / OGP

`index.html` の `<head>` に OGP・Twitter Card・Apple Touch Icon・theme-color を設定済み。`og:image` は現在アプリアイコンを指していますが、本番では **1200×630 の OGP 画像** を別途用意して差し替えてください。

## Accessibility メモ

- 現状の実装は最低限。本番化前に:
  - `[data-reveal]` の初期 `opacity: 0` は `prefers-reduced-motion: reduce` で無効化する
  - FAQ のアコーディオンに `aria-expanded` / `aria-controls` を追加
  - ストアバッジに `aria-label="App Storeでダウンロード"` 等を付与済みだが、リリース時は "近日公開" のため `aria-disabled` 相当の表現に
- ヒット領域は最低 44×44px

## Files in This Bundle

```
design_handoff_nominote_lp/
├── README.md                  ← このファイル
├── index.html                 ← LP本体
├── privacy.html               ← プライバシーポリシー（DRAFT）
├── terms.html                 ← 利用規約（DRAFT）
├── legal.html                 ← 特商法表記（DRAFT）
├── styles.css                 ← LP用スタイル
└── assets/
    ├── nm-tokens.css          ← 全デザイントークン
    └── app-icon-official.png  ← 正式アプリアイコン
```

## チェックリスト（リリース前）

- [ ] フレームワーク化（推奨: Astro）
- [ ] Tweaks パネル関連のコード削除
- [ ] ストアバッジのURLを App Store / Google Play 実URLに
- [ ] OGP 画像（1200×630）を作成・差し替え
- [ ] 法務3ページの `DRAFT` バッジ削除＋実情報反映
- [ ] `prefers-reduced-motion` 対応
- [ ] FAQ アコーディオンの ARIA 対応
- [ ] Lighthouse 90+ （Performance / Accessibility / SEO / Best Practices）
- [ ] 実機での表示確認（iOS Safari / Android Chrome / PC Safari / PC Chrome）
