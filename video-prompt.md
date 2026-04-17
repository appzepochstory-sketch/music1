# AMBER 参考動画 生成プロンプト（音なし）

参考動画（Shutterstock グリーンスクリーンのレコード）のイメージに、
添付したAMBERのジャケ画像をレコード盤中央ラベルとしてはめた動画を作るためのプロンプト集。

---

## 方針

「Shutterstockのグリーンスクリーン動画を実際に買う」のと、
「AI動画生成で0から作る」の2通りがある。後者向けに3モデル分のプロンプトを用意。

いずれも **音なし**（後からVimeoで音を載せる前提）。
アスペクトは **16:9** / **1:1** のどちらかを選ぶ（LPの`.player`は16:9を想定）。

---

## 参考プロンプト① Runway Gen-3 / Kling / Luna 等向け（英語・リッチ）

```
Cinematic close-up of a black vinyl record slowly rotating on a dark mahogany turntable,
shot from a slight three-quarter high angle. The record's center label features the
provided artwork — an illustrated woman with long brown hair resting her chin on her hand,
warm amber and dusty teal palette, hand-drawn 90s city-pop aesthetic.
The label says "AMBER" in bold vermilion serif at the top.
Warm tungsten bar light from the side casts a soft golden glow on the vinyl grooves,
revealing subtle concentric reflections that shimmer as it spins.
Gentle dust motes drift across the light beam. Faint film grain.
Shallow depth of field; background out of focus into deep brown bokeh.
Record rotates smoothly at 33⅓ rpm. 10 seconds, seamless loop, 16:9, no text overlay, no audio.
Mood: late-night jazz bar, whiskey on the rocks, intimate and nostalgic.
```

**差し替えポイント**
- 画角を縦長にしたいなら `16:9` を `9:16` に
- 1分以上欲しいなら末尾に `, extended duration 30 seconds` を追記

---

## 参考プロンプト② Google Imagen Video / Veo 向け（自然文）

```
平日の夜のバーカウンター。ダークブラウンのターンテーブルの上に、
AMBERと書かれたヴァーミリオン色のレタリングとイラスト（長い茶髪の女性が頬杖をついている姿）がプリントされた
ブラックヴァイナルのレコードが、ゆっくりと時計回りに回転している。
琥珀色の間接照明が側面から差し込み、盤面のグルーヴに柔らかな反射を落とす。
空気中にゆっくりと舞う埃、わずかなフィルムグレイン、浅い被写界深度で背景はダークブラウンの
ボケ。33⅓回転で滑らかに回り、10秒のシームレスループ。16:9横長、テキストオーバーレイなし、音声なし。
ムード：深夜のジャズバー、ノスタルジックで親密。
```

---

## 参考プロンプト③ グリーンスクリーン素材 × ジャケット合成用（効率重視）

**Shutterstockの参考動画をそのまま買う場合、以下の合成プロンプトをCapCut / After Effects / Runway Act-One などに渡す**：

```
Overlay task:
Take the provided circular album artwork (AMBER — illustrated woman in amber/teal palette,
red "AMBER" title at top) and composite it as the center label of the spinning vinyl record
in the green-screen reference footage. Scale the artwork to match the label diameter
(approx 35% of record width). Keep the artwork perfectly aligned with the rotating record
so it spins with it. Mask everything green to transparent, output on a solid
dark brown (#2a1810) background with a subtle radial warm amber glow centered behind the disc.
Final export: 1080p, 16:9, 10-second loop, no audio.
```

---

## 動画が出来たらやること

1. Vimeo にアップ（音源ファイルも同時にアップして一本化、またはSoundCloud埋め込みに差し替え）
2. `index.html` の `data-vimeo="..."` に動画URLを記入
   ```html
   <div class="player__placeholder" id="player-placeholder"
        data-vimeo="https://player.vimeo.com/video/123456789">
   ```

---

## 参考：動画の静止画プロンプト（サムネ用）

Vimeoサムネを差し替えたい場合、同じジャケ写をメインにした1枚絵を：

```
Flat lay vintage vinyl record with AMBER artwork on its center label,
sitting on a dark wooden bar top next to a glass of whiskey on the rocks.
Warm amber tungsten lighting from upper left, soft shadows, film grain,
editorial photography, 3:2 ratio.
```
