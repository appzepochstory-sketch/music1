# AMBER NFCキーホルダー使い方ポスター / Gemini プロンプト

**用途**: 商品同梱 or 店頭配布用の B5 ポスター（182×257mm 縦）
**ターゲット**: ミニCDケース風NFCキーホルダーを手にした人 → スマホをかざすと音楽が流れる仕組みを伝える
**ブランドトーン**: 琥珀色×ダスティブルー×深いブラウン、深夜のバー、ヴィンテージレコード、シネマティック

---

## ⚠️ 先に大事な前提

- **Gemini Imagen は画像内の日本語テキストをきれいに描けません**（文字化けする）。
- なので、**ポスターは2段階で作るのが鉄則**：
  1. **Imagen で「背景ビジュアル＋雰囲気」のみ生成**
  2. **CanvaやFigmaに取り込んで、日本語の説明テキストを上から重ねる**
- このドキュメントには両方のプロンプトと、テキスト原稿をまとめてあります。

---

## 🎨 PROMPT A: ポスター背景ビジュアル（Imagen 4 / Gemini）

英語で投げる。アスペクト比は B5 に近い `3:4` を指定する。

```
A vertical 3:4 cinematic poster background designed in the style of a vintage
late-night jazz bar. The composition is split into two atmospheric layers:

— UPPER HALF: A square album-jacket illustration of a mysterious woman with
long brown hair sitting at a dimly-lit bar counter, painted in warm amber and
muted dusty teal palette, hand-drawn 90s city-pop aesthetic, large red
"AMBER" lettering at the top of the jacket, subtle washi tape pinning the
top corners. Soft amber glow radiates around the jacket.

— LOWER HALF: A spinning black vinyl record half-emerging from below, with
a warm honey-amber glow leaking from the grooves. The record's center label
echoes the AMBER artwork. Tiny golden dust particles drift across a soft
spotlight beam from above.

— BACKGROUND: deep mahogany brown gradient with a single warm pendant lamp
glow at the center, fading into pitch black corners. Subtle 35mm film grain.
A faint vignette at the edges.

— EMPTY SPACE: Generous negative space at the very top and bottom for adding
typography later — leave roughly 25% of the upper area and 25% of the lower
area visually quiet and unobstructed.

Mood: solitary, intimate, after-midnight, late-90s editorial photography meets
hand-drawn illustration. Colors: amber #d47a39, dusty teal #8ea8a5, deep
brown #1a120b, cream #efe4d2.

Photographic realism for the record / lighting; illustrated for the album
jacket. Vertical 3:4 aspect ratio, high resolution, no text, no people other
than the woman in the painted jacket.
```

---

## 🎨 PROMPT B: もっとシンプル版（テキストの邪魔をしない用）

「タイポをガッツリ載せたい」「絵は薄めの背景でOK」なら、こちらでさらに静かな絵を：

```
A vertical 3:4 minimalist poster background. Deep mahogany brown gradient,
fading to pitch black at the corners. A single warm pendant lamp glow in the
upper third — only golden light source, soft and diffused.

In the lower-third, a dark vinyl record edge curves up from the bottom-left,
reflecting amber lamp light along its grooves. Floating golden dust particles
in the light beam. Faint 35mm film grain throughout.

Generous empty negative space across most of the frame for typography
overlay.

Mood: elegant, mysterious, after-midnight bar. Colors: amber #d47a39,
dusty teal accents, deep brown, cream. No text, no people, photographic
realism, vertical 3:4.
```

---

## 📝 ポスター用テキスト原稿（Canva等で重ねる）

下記のテキストを、生成した背景の上に配置する。
B5縦のレイアウト案を2案用意：

### 🅰 案A: 上にメインビジュアル / 下にハウツー

```
┌─────────────────────────────┐
│                             │
│         AMBER               │  ← 上25%エリア（タイトル・大）
│      琥珀色の光             │
│                             │
│    [生成画像のメイン部分]   │  ← 中央50%
│                             │
│ ─────────────────────────── │
│                             │
│ 🔓 HOW TO LISTEN            │
│                             │
│ ① スマートフォンの NFC を   │
│   ON にする                 │
│ ② キーホルダーの中央部分に  │
│   スマホをかざす            │
│ ③ ポップアップから          │
│   「開く」をタップ          │
│                             │
│ ─────────────────────────── │
│                             │
│ 4組のアーティストの中から   │
│ "あなたの一曲" がランダム   │
│ で再生されます。            │
│                             │
│ airina · gable · Kefu ·     │
│ zemreco                     │
│                             │
│   amber.epochstory.com      │  ← フッター
│                             │
└─────────────────────────────┘
```

### 🅱 案B: シンプル＆ミステリアス（1枚絵主役）

```
（最上部）
AMBER
琥珀色の光

（メインビジュアル中央いっぱい）

（下部・小さく）
タップして、夜を聴く。

スマホの NFC をオンにして、
キーホルダーにかざすだけ。

4曲のうち、どれが鳴るかは
あなた次第。

— Vol.01 airina / Vol.02 gable
   Vol.03 Kefu / Vol.04 zemreco

amber.epochstory.com
```

---

## 🪧 タイポグラフィ推奨

CanvaやFigmaに取り込んだあとの文字組み：

| 階層 | フォント例 | サイズ目安（B5基準） |
|---|---|---|
| メインタイトル `AMBER` | Fraunces 900（英字）| 約60–80pt |
| 副題 `琥珀色の光` | Shippori Mincho 700（明朝） | 約32–40pt |
| 見出し `HOW TO LISTEN` | Inter 600（小文字幅広） | 12pt / letter-spacing 0.3em |
| 手順本文 | Klee One / 游明朝 / Shippori Mincho | 13–15pt |
| アーティスト名4人 | Inter Italic / Fraunces Italic | 14pt |
| URL | Inter Mono または Fraunces | 11pt |

カラーは：
- 背景: `#1a120b`〜`#0f0a06`（深い夜の色）
- メインタイトル: `#d47a39`（琥珀）
- 本文: `#efe4d2`（生成り）
- アクセント線: `#e8a867`（柔らかい光）

---

## 📐 B5 サイズ仕様

- B5 縦: **182mm × 257mm**
- 印刷余白を考慮した安全マージン: 上下左右 10mm 以上
- 推奨解像度: **300dpi → 2150 × 3036px**
- Gemini で生成する画像は **1500 × 2000px 以上**（後で拡大しても画質維持）

---

## 🚀 おすすめワークフロー

1. **Gemini Imagen で PROMPT A or B を投げて背景生成**
   - 数枚生成してベストを選ぶ
2. **Canva / Figma に背景を取り込む**
   - B5 縦テンプレを作る（182×257mm）
3. **テキストレイヤーを上に配置**（上記 案A or 案B）
4. **NFC アイコン or QRコードを右下に小さく追加**（必要なら）
5. **PDF で書き出し → 印刷**

---

## 💡 NFCマークを入れたい場合

「NFC対応スマホでタップしてね」がパッと伝わるように、右下に小さく：

```
┌───┐
│ 🔓 │  TAP HERE
│NFC│
└───┘
```

このアイコンも Imagen で別途生成しても良いし、フリー素材（[font-awesome NFC icon](https://fontawesome.com/icons/wifi)とか）を使うのが速い。

---

## ✏️ 完成イメージ

「上にAMBERジャケ＋下にレコード」「ランプの光だけが灯る深夜のバー」「キーホルダーをスマホにかざすと曲が流れる仕掛け」を、ポスター1枚で物語的に伝えるイメージ。

Epochstory のチル＆エモ感 × 説明書としての機能性、両立させましょう🍷
