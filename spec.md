# BLOC — design-furniture-urban Spec

**Status:** Approved  
**Author:** torifo  
**Created:** 2026-05-19  
**Updated:** 2026-05-19

---

## 1. Overview

### Problem Statement
都市生活者（20〜35代）向けの家具サイトは「おしゃれ感」を出そうとして柔らかく曖昧になり、製品のスペックが埋もれる。一方でIKEA的な機能重視サイトは個性がなく、「この家具を選んだ」という所有感・自己表現が薄い。

### Goal
「BLOC」という架空の都市型家具ブランドのランディングページを、**ブラック/ホワイト交互セクション×超大型コンデンストタイポグラフィ**で実装する。写真よりタイポグラフィが主役のグラフィックデザイン的アプローチで、情報が明快かつスタイリッシュに見える体験を作る。

### Non-Goals
- EC機能
- ローダー・マーキー・grain overlay・カスタムカーソル・セリフフォント
- 柔らかいグラデーション・有機的な形状

### Background
- BLOCは架空ブランド。東京・NY・ベルリンの都市的なアパートを想定
- `design-furniture-urban` リポジトリ予定
- 「グラフィックデザインがUIになる」実験。写真がなくても成立するか検証

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 都市生活者 (20–35代) | 一瞬でブランドのスタンスを感じたい | 「自分向け」かどうかを即判断できる |
| US-02 | 同上 | 製品名・価格・サイズをストレスなく確認したい | 余計な説明文を読まずに決断できる |
| US-03 | 同上 | スペックを一覧で比較したい | 複数製品を同時に見て選べる |
| US-04 | 同上 | 375pxでも同じ力強さを感じたい | モバイルで見ても印象が落ちない |

### Acceptance Criteria (EARS notation)

**US-01: ヒーロー体験**
- WHEN ページを開いた THEN 全黒背景に超大型「BLOC」と1行のタグラインが表示される
- WHEN ヒーローが表示された THEN テキストがopacity 0 → 1 の0.8sフェードで現れる

**US-02: 製品番号制セクション**
- WHEN 各製品セクションをスクロールした THEN 背景色が交互に切り替わる（黒背景・白背景）
- WHEN 製品セクションを見た THEN 「01」などの超大型番号がセクション背景に薄く表示される（decorative）
- WHEN 製品セクションを見た THEN 製品名・素材・価格・サイズが一読で把握できるレイアウトになっている

**US-03: スペック一覧テーブル**
- WHEN スペックセクションに到達した THEN 全製品の主要スペックが比較可能なテーブル形式で表示される

**US-04: モバイル対応**
- WHEN 375px幅で閲覧した THEN 全セクションが横スクロールなしで表示される
- WHEN モバイルで製品セクションを見た THEN 画像とテキストが縦積みになる

---

## 3. Functional Requirements

| ID | Requirement | Priority | Notes |
|----|-------------|----------|-------|
| FR-01 | 全黒ヒーロー（超大型ブランド名＋1行タグライン＋スクロール指示） | P0 | フェードイン0.8s |
| FR-02 | 製品セクション×3（黒・白・黒 交互、oversized背景番号） | P0 | 各min-height 100svh |
| FR-03 | 各製品セクションに画像＋製品名＋素材＋価格＋CTA | P0 | |
| FR-04 | スペック比較テーブル（全製品、白背景） | P1 | モノスペースフォント |
| FR-05 | ミニマルコレクショングリッド（全4製品、ハードボーダー） | P1 | |
| FR-06 | フルブラックCTAセクション（大型コピー＋ボタン） | P1 | |
| FR-07 | 1行フッター | P2 | |
| FR-08 | スクロールリビール（opacity only、0.6s、translateYなし） | P1 | |
| FR-09 | モバイル対応 | P0 | |

---

## 4. Architecture

### Page Structure

```
index.html
├── nav                          # ミニマル（ロゴ左・リンク右、透明）
├── section.hero-black           # 全黒ヒーロー（100svh）
├── section.product-sec.dark     # 製品01（黒背景）
├── section.product-sec.light    # 製品02（白背景）
├── section.product-sec.dark     # 製品03（黒背景）
├── section.specs-table          # スペック比較テーブル（白）
├── section.collection-grid      # ミニコレクショングリッド
├── section.cta-full             # フルブラックCTA
└── footer                       # 1行
```

### Key Design Decisions

| Decision | Chosen | Rationale | Rejected alternatives |
|----------|--------|-----------|----------------------|
| テーマ | 黒白交互 | 単調さを防ぎつつコントラストを維持 | 全黒（暗すぎる）・全白（軽すぎる） |
| フォント | Barlow Condensed（Heavy/Black） | 狭い画面でも大型タイポが機能する | Archivo Black（HVILE/ARCHと差が小さい） |
| 背景番号 | decorative oversized（opacity 0.06） | タイポグラフィが構造を作る。写真なしでも成立 | なし（単調）・フォアグラウンド（うるさい） |
| ローダー | なし | インスタントに始まるべき。都市生活者は待たない | あり |
| grain/cursor | なし | グラフィックデザインの純度を下げない | あり |
| CTAボタン | ハードエッジ（border 1px、hover塗りつぶし） | 建築的・直線的 | 丸角・グラデーション |

---

## 5. Design System

### Color Palette
```css
--black:    #0A0A0A;   /* ほぼ黒（pure blackより温度がある） */
--white:    #F5F5F3;   /* オフホワイト */
--accent:   #E84C1B;   /* ホットオレンジレッド */
--border:   #1E1E1E;   /* 黒セクションのボーダー */
--border-l: #DCDCDA;   /* 白セクションのボーダー */
--mono:     #888888;   /* スペックテキスト */
```

### Typography
```css
--font-display: 'Barlow Condensed', sans-serif;
--font-body:    'Barlow', sans-serif;
```
- Google Fonts: `Barlow+Condensed:ital,wght@0,400;0,500;0,700;0,800;0,900;1,400` + `Barlow:wght@300;400;500`

### Motion
```css
/* フェードイン: opacity 0 → 1, 0.8s ease */
/* リビール: opacity only (translateYなし) */
/* hover: background-color 0.2s (sharp, no ease) */
```

---

## 9. Testing Strategy (Visual QA)

| Layer | Scenarios |
|-------|-----------|
| Desktop (1280px) | 黒白交互確認・oversized番号・スペックテーブル |
| Mobile (375px) | 縦積み・番号が見切れないか・テーブルのスクロール |
| フォント | Barlow Condensed Black / Heavy の読み込み確認 |
| コントラスト | 黒背景の白テキスト（WCAG AA: 4.5:1以上） |

---

## 10. Implementation Notes

- ヒーロー大型ブランド名: `font-size: clamp(6rem, 20vw, 22rem); font-weight: 900; letter-spacing: -0.04em`
- 背景装飾番号: `font-size: clamp(16rem, 35vw, 50rem); opacity: 0.06; position: absolute; pointer-events: none; user-select: none`
- 製品セクション: `display: grid; grid-template-columns: 1fr 1fr; min-height: 100svh; align-items: center`
- スペックテーブル: CSS Gridで `grid-template-columns: 2fr repeat(3, 1fr)`。`border-collapse` 相当をGrid gapで実現
- CTAセクション: `min-height: 80svh; display: flex; flex-direction: column; justify-content: center; padding: 6rem 3rem`
- アクセントカラー `#E84C1B` は製品価格・CTA・hover時のみ使用。多用しない
