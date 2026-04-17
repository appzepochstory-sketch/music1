# AMBER - 琥珀色の光 / LP

CDジャケ写企画「AMBER」のランディングページ。1ファイルHTML。

## 構成
- `index.html` — 本体（CSS/JSインライン、外部依存はGoogle Fontsのみ）
- `assets/` — 画像を置く場所
- `video-prompt.md` — 参考動画用のAI動画生成プロンプト

## 画像を差し替える

### 1. ジャケ写（Hero）
添付した `AMBER` ジャケ画像を保存：

```
assets/amber-jacket.png
```

→ 自動的に Hero の右側に表示される。ファイルがないときは仮レタリングが出る（フォールバック済み）。

### 2. airina ポートレート（任意）
アーティスト紹介セクションに写真を出したい場合：

```
assets/airina.jpg
```

→ 出さない場合は、背景に "airina" と流れる大きなレタリングのまま残る（これはこれで雑誌っぽい）。

## Vimeoリンクを埋め込む

`index.html` で `data-vimeo=""` と `<!-- iframe差し込みポイント -->` を探す。2通り用意：

### A. クリックで再生開始（遅延ロード・推奨）
```html
<div class="player__placeholder" id="player-placeholder"
     data-vimeo="https://player.vimeo.com/video/XXXXXXXXX">
```
→ レコード盤をクリックするとiframeに差し替わって自動再生。

### B. 直接iframe埋め込み
`player__placeholder` ごと消して：
```html
<iframe src="https://player.vimeo.com/video/XXXXXXXXX"
        allow="autoplay; fullscreen; picture-in-picture" allowfullscreen
        style="position:absolute;inset:0;width:100%;height:100%;border:0;"></iframe>
```

## ストリーミングリンクを追加する

`index.html` の `.streams__list` 2箇所（artistセクション＋outroセクション）を編集。
今は YouTube / Instagram / Spotify / Apple Music / X の5枠。Spotify以降はURL未設定なので `href="#"` のまま。URLがもらえたら差し替え。

## こまちゃん基準の遵守ポイント
- Header 不要 ✅（`.mark` は固定ロゴのみ、メニュー項目なし）
- Hero 1枚絵 ✅（ジャケ写＋タイポのみ、右の縦長カラム）
- メタ英語タイトル禁止 ✅（セクションの見出しは日本語、英語はキャプション的な小文字扱い）
- 番号小さく中身主役 ✅（`.num` / `① Concept`のみ小さく）
- フリー素材ベース ✅（外部画像依存なし、ジャケ写は自前）
- セクション境界あいまい ✅（同じ `--paper` 背景、境界線なし、パディングで余白）
- 装飾動き ✅（スクロール連動レコード、reveal、微視差、文字揺れなし）
- ギミック1つ ✅（右下のレコードがスクロールでくるくる回る）
- LINE一本ではなくSNSアイコン導線 ✅

## ローカルで確認
どれか1つ：
```sh
# Python
cd Epochstory/AMBER-LP && python3 -m http.server 4173

# Node
cd Epochstory/AMBER-LP && npx serve -l 4173 .

# そのまま
open Epochstory/AMBER-LP/index.html
```

## 今後 Vol.02 以降を足すとき
`artist` セクションをコピーして `②` → `③` と番号を上げていくだけでOK。
同じトーンで各アーティスト回を足せる作りにしてある。
