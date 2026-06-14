---
name: design-furniture-urban
description: "furniture brand landing-page design study — 'urban' theme/persona (pure HTML/CSS/JS, no build). Use when designing a 'urban'-style furniture brand site aesthetic. No Excuses. Just Furniture. furniture brandの「urban」テーマLPのデザイン参照スキル。"
---

# design-furniture-urban

A landing-page **design study** for a fictional **urban**-theme furniture brand (pure HTML + CSS + vanilla JS, no build, GitHub-Pages ready). Use this as a **style / design-system reference** when building a similar aesthetic.

架空の「urban」テーマのfurniture brand LP デザイン研究。同種の世界観を作るときの**スタイル／デザインシステム参照**として使う。

## When to use / 使いどころ
- **EN:** designing a 'urban'-style furniture brand site — match its palette, typography and layout discipline.
- **JP:** 「urban」系のfurniture brandサイトを設計するとき。配色・タイポ・レイアウト規律を流用。

## Bundled assets / 同梱アセット
This skill folder is the reference implementation — start from these files:
- `index.html` — full page markup
- `style.css` — design tokens (CSS custom properties) + layout
- `script.js` — vanilla JS (if present)
- `README.md` — full bilingual doc, brand context and series links

## Design reference / デザイン参照
_Lifted from the repo README — see README.md for the complete, bilingual version._

### Overview
**furniture design research series** の「アーバン」ペルソナ作品。

都市生活者（20〜35代）が求める「スタンスが瞬時に伝わる」体験を、黒白交互セクション×超大型コンデンストタイポグラフィで実現する。写真よりもタイポグラフィが主役になれるか、というグラフィックデザイン的実験。

---

### Brand
| | |
|--|--|
| **Brand** | BLOC |
| **Tagline** | No Excuses. Just Furniture. |
| **Aesthetic** | アーバン・グラフィック × 建築的ブルータリズム |
| **Target Persona** | 20–35代、東京/NY/ベルリン的都市生活者、狭い空間に個性を出したい |
| **Color** | Near Black `#0A0A0A` + Off White `#F5F5F3` + Hot Orange `#E84C1B` |
| **Display Font** | Barlow Condensed |
| **Body Font** | Barlow |

---

### Design Approach
「グラフィックデザインがUIになる」という命題を検証する。

- **黒白交互セクション**: 製品ごとに背景色が反転。視線のリセットで各製品への集中を生む
- **超大型タイポ**: ヒーロー `clamp(6rem, 20vw, 22rem) / weight 900` — 写真なしでも画面が成立するか
- **背景装飾番号**: `opacity: 0.06` で製品番号を背景に忍ばせる。意識されるかどうかの境界線
- **スペック比較テーブル**: 全製品を横断比較できるCSS Gridテーブル
- **アクセントカラーの制限**: `#E84C1B` は価格・CTA・ボタンの3箇所のみ

**排除したUI要素**: ローダー・マーキー・grain・カスタムカーソル・セリフフォント・柔らかいグラデーション

---

## Tech / 技術
- Vanilla HTML / CSS / JS — single file (`index.html`)
- Google Fonts: [Barlow Condensed](https://fonts.google.com/specimen/Barlow+Condensed), [Barlow](https://fonts.google.com/specimen/Barlow)
- ビルドツール不要

## How to apply / 適用方法
1. Reuse `style.css` custom properties (color / type / spacing tokens) as the design-system base.
2. Copy `index.html` layout as the starting structure, then swap brand name and content.
3. Keep the palette, font pairing and layout discipline described above.

---
> The brand is fictional (design study) — replace all brand/content. Full context: see **`README.md`**.
