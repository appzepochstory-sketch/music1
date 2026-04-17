# Mood セクション 背景画像 / Gemini (Imagen) プロンプト

**用途**: LPの「その女性は暗いバーの中、琥珀のように輝いて見えた。」セクションの背景

**保存先**: `assets/mood-bar.jpg`（または `.png`）
**置いたら**: リロードするだけで自動的にmoodセクションの背景に敷かれる（CSSで既に読み込み設定済み）

---

## 推奨：Gemini Imagen用プロンプト

コピペしてGeminiで投げる：

```
A cinematic photograph of an empty, dimly-lit late-night bar counter,
shot from a slight low angle facing the bar.
A single pendant lamp hanging above the counter casts a warm amber spotlight
— the only light source in the entire frame — creating a perfect cone of
honey-colored glow onto a polished dark mahogany bar top.
One empty rocks glass sits on the counter within the light, amber whiskey still
glowing in it. Behind the bar, rows of bottles sink into deep brown shadow.
The rest of the room is almost pitch-black, only faintly revealing silhouettes.
Atmospheric haze and subtle dust particles drift through the light beam.
Mood: solitary, intimate, after-midnight, 90s film-noir jazz bar.
Color palette: deep obsidian browns, warm amber, soft orange highlights,
almost no other colors.
Photographic realism, 35mm film grain, shallow depth of field,
aspect ratio 16:9 (horizontal), no people, no text.
```

---

## 補足プロンプト（縦長バージョン・モバイルで上寄りに表示したい場合）

```
(Same scene as above) but vertical composition 3:4, the single amber pendant
lamp in the upper third of the frame, bar counter sweeping into dark foreground.
```

---

## 調整のコツ

- **もっと暗くしたい**: "extremely low key lighting, 95% of frame in shadow" を追加
- **琥珀感を強くしたい**: "saturated amber tones, golden-honey color temperature"
- **人を入れたい（女性の後ろ姿だけ）**: "a woman's silhouette from behind, seated at the counter, only her shoulder and long wavy hair visible in the amber light"
- **席にウィスキーを強調**: "a half-full glass of whiskey on the rocks glowing in the amber spotlight, condensation on the glass"

---

## LP 側の仕様（すでに仕込み済み）

```css
.mood__bg{
  background-image: url('./assets/mood-bar.jpg');  ← ここを読む
  opacity: .55;
  filter: brightness(.55) contrast(1.05) saturate(.9);
}
```

画像を保存 → 自動で適切な暗さに加工されて背景に差し込まれる。
`.mood__bg::after` で下半分に黒グラデを重ねて、本文テキストの可読性も確保済み。

画像ファイル名を変えたい場合は `index.html` のCSS内で `mood-bar.jpg` を差し替え。

---

## 出来上がり後の流れ

```bash
# 1. Geminiで生成した画像を保存
#    → Epochstory/AMBER-LP/assets/mood-bar.jpg

# 2. ブラウザでリロードして確認
#    → mood セクションに自動で敷かれる

# 3. push
cd /Users/yuu/Documents/Claude/Epochstory/AMBER-LP
git add assets/mood-bar.jpg
git commit -m "Moodセクション背景にバーカウンター画像を追加"
git push
```
