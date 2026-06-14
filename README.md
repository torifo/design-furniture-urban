# BLOC — design-furniture-urban

> **架空ブランド注記**: BLOCは本デザイン研究のために作成した架空ブランドです。実在のブランド・店舗・商品ではありません。

---

## Overview

**furniture design research series** の「アーバン」ペルソナ作品。

都市生活者（20〜35代）が求める「スタンスが瞬時に伝わる」体験を、黒白交互セクション×超大型コンデンストタイポグラフィで実現する。写真よりもタイポグラフィが主役になれるか、というグラフィックデザイン的実験。

---

## Brand

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

## Design Approach

「グラフィックデザインがUIになる」という命題を検証する。

- **黒白交互セクション**: 製品ごとに背景色が反転。視線のリセットで各製品への集中を生む
- **超大型タイポ**: ヒーロー `clamp(6rem, 20vw, 22rem) / weight 900` — 写真なしでも画面が成立するか
- **背景装飾番号**: `opacity: 0.06` で製品番号を背景に忍ばせる。意識されるかどうかの境界線
- **スペック比較テーブル**: 全製品を横断比較できるCSS Gridテーブル
- **アクセントカラーの制限**: `#E84C1B` は価格・CTA・ボタンの3箇所のみ

**排除したUI要素**: ローダー・マーキー・grain・カスタムカーソル・セリフフォント・柔らかいグラデーション

---

## Tech

- Vanilla HTML / CSS / JS — single file (`index.html`)
- Google Fonts: [Barlow Condensed](https://fonts.google.com/specimen/Barlow+Condensed), [Barlow](https://fonts.google.com/specimen/Barlow)
- ビルドツール不要

## Local Development

```bash
open index.html
# または
python3 -m http.server 8080
```

---

## Install as a skill / スキルとして導入

This repo ships a cross-agent **`SKILL.md`** (open standard) usable by both Claude Code and Codex CLI as a design-reference skill. Link the repo into the agent's skills directory:

このリポジトリは Claude Code / Codex CLI 共通の **`SKILL.md`**（オープン標準）を同梱し、デザイン参照スキルとして使えます。

```bash
# Claude Code
ln -s "$(pwd)" ~/.claude/skills/design-furniture-urban
# Codex CLI
ln -s "$(pwd)" ~/.codex/skills/design-furniture-urban
```

Restart the agent; it is matched automatically by the skill's `description` (skill name: `design-furniture-urban`). / エージェント再起動後、`description` に基づき自動マッチします。

## Series

このリポジトリは **furniture design research series** の一作です。

| Theme | Brand | Aesthetic | Persona | Site |
|-------|-------|-----------|---------|------|
| nordic | HVILE | 北欧オーガニック | 30–45代、素材重視の住まい手 | [design.furniture-nordic.riumu.net](https://design.furniture-nordic.riumu.net/) |
| luxury | VELA | ラグジュアリー・アトリエ | 40–60代、ラグジュアリー層 | [design.furniture-luxury.riumu.net](https://design.furniture-luxury.riumu.net/) |
| artisan | BURL | 職人工房・カタログ | 25–45代、クラフト志向 | [design.furniture-artisan.riumu.net](https://design.furniture-artisan.riumu.net/) |
| **urban** | **BLOC** | **アーバン・グラフィック** | **20–35代、都市生活者** | [design.furniture-urban.riumu.net](https://design.furniture-urban.riumu.net/) |
