# BLOC Design Learnings

## 目的

都市生活者ペルソナ（20–35代）は「スタンスが伝わるまでの時間」が短い。BLOCでは、黒白交互セクション×超大型コンデンストタイポグラフィによって、写真がなくても「このブランドは自分向けかどうか」を瞬時に判断できる体験を設計した。

BLOCは架空ブランドであり、実在の店舗・商品ではない。

---

## 「グラフィックデザインがUIになる」実験

BLOCの設計課題は**タイポグラフィだけで画面が成立するか**。

| 捨てたもの | 理由 |
|-----------|------|
| ライフスタイル写真 | タイポが主役のとき写真は「添付」になる |
| grain / cursor | グラフィックデザインの純度を下げない |
| セリフフォント | 都市的・現代的・建築的。装飾的な書体は場違い |
| 柔らかいグラデーション | ハードエッジが建築的な誠実さを作る |
| ローダー | 都市生活者は待たない。インスタントに始める |

写真があると視線がそこに集中し、タイポグラフィが「説明」に格下げされる。BLOCでは**製品写真は各セクションに1枚のみ**配置し、タイポと等面積に扱う。

---

## レイアウト

```
全黒ヒーロー（100svh）→ 製品01（黒）→ 製品02（白）→ 製品03（黒）
→ スペックテーブル（白）→ コレクショングリッド → フルブラックCTA → 1行フッター
```

### 黒白交互の仕組み

```css
.product-sec          { background: var(--black); color: var(--white); }
.product-sec.light    { background: var(--white); color: var(--black); }
```

単純だが強力。視線が「切り替わる」たびに意識がリセットされ、各製品への集中が生まれる。

### 背景装飾番号

```css
.product-num-bg {
  font-size: clamp(16rem, 35vw, 50rem);
  font-weight: 900;
  opacity: 0.06;
  position: absolute;
  pointer-events: none;
  user-select: none;
  line-height: 0.85;
}
```

`opacity: 0.06` — 意識されるか否かの境界線。これ以上暗いと消え、これ以上明るいと主張しすぎる。

---

## CSS

主要な判断:

```css
:root {
  --black:  #0A0A0A;   /* pure blackより0.04%明るい。温度がわずかにある */
  --accent: #E84C1B;   /* ホットオレンジレッド。価格とCTAのみ使用 */
  --font-display: 'Barlow Condensed', sans-serif;
}

/* ヒーロー大型タイポ */
.hero-title {
  font-size: clamp(6rem, 20vw, 22rem);
  font-weight: 900;
  letter-spacing: -0.04em;   /* タイトな詰め。建築的 */
  line-height: 0.85;
}

/* CTAはハードエッジ */
.bloc-cta {
  border: 1px solid currentColor;
  padding: 1rem 2.5rem;
  transition: background .15s, color .15s;   /* sharpな切り替え */
}
.bloc-cta:hover { background: currentColor; color: var(--black); }
```

`letter-spacing: -0.04em` と `line-height: 0.85` の組み合わせが「建築的なタイポグラフィ」を作る。詰まることで凝縮された都市感が出る。

---

## フォント

- Display: `Barlow Condensed weight 900/800/700`  
  — コンデンストで都市的。大型サイズでも画面幅を食わない。Archivo Blackより横幅が狭く密度が高い
- Body: `Barlow weight 300/400`  
  — 同一ファミリーで統一感。切り替えが自然

`clamp(6rem, 20vw, 22rem)` の範囲設定が重要。375pxでも6remで読めるヒーロータイトル、1440pxでも22rem止まりで溢れない。

---

## アクセントカラーの使い方

`#E84C1B` は **3箇所のみ** 使用する：
1. 製品価格
2. CTAテキスト（白セクション内）
3. フルブラックCTAのボタン

それ以外で使うと希少価値が失われ、単なる「赤いサイト」になる。

---

## スペックテーブルの設計

```css
.specs-table {
  display: grid;
  grid-template-columns: 2fr repeat(3, 1fr);
}
.specs-header-cell { font-family: var(--font-display); font-weight: 700; }
.specs-cell        { font-size: 0.8rem; letter-spacing: 0.05em; }
```

`<table>` を使わない理由：モバイルでの列制御とborder-collapseの代替がCSS Gridで完結する。

---

## furniture シリーズとの対比

| 軸 | BURL（artisan） | BLOC（urban） |
|----|----------------|--------------|
| テーマ | ライト（クラフト紙） | 黒白交互 |
| 主役 | テキスト（カタログ形式） | タイポグラフィ（グラフィック） |
| 製品表示 | テーブルリスト | 番号制セクション（1製品1章） |
| フォント | DM Serif + IBM Plex Mono | Barlow Condensed + Barlow |
| アクセント | 錆び赤 #8B3829 | ホットオレンジ #E84C1B |
| アニメーション | opacity 0.6s（印刷的） | opacity 0.8s（瞬時） |
| 写真の役割 | プロセス・職人 | 1枚のみ。タイポと等面積 |
