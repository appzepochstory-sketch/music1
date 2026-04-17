# GitHub Pushの手順（こまちゃん向け・全手順）

リポジトリ: https://github.com/appzepochstory-sketch/music1

## 今の状態
ローカルは準備完了。あとは **Personal Access Token (PAT)** を取得してプッシュするだけ。

- ✅ git init 済み
- ✅ 初回コミット済み
- ✅ remote (origin) 設定済み
- ❌ push ← これを今からやる

---

## STEP 1. GitHub でトークン（PAT）を発行

GitHub の Web にログインした状態で以下：

### 1-1. トークン作成ページを開く
以下のURLを直接開く：

👉 https://github.com/settings/tokens/new

もしくは手動で：
1. https://github.com 右上のアイコン → **Settings**
2. 左下の **Developer settings** をクリック
3. **Personal access tokens** → **Tokens (classic)** を選択
4. 右上の **Generate new token** → **Generate new token (classic)** を選択

### 1-2. トークン設定
以下のように入力：

| 項目 | 設定値 |
|---|---|
| **Note** | `AMBER LP push`（任意の分かる名前） |
| **Expiration** | `30 days` や `90 days`（長すぎ注意、この作業が終われば削除してOK） |
| **Select scopes** | ✅ **repo** に全部チェック（repoを1クリックで配下全部チェック入る） |

→ 一番下の緑ボタン **Generate token** をクリック。

### 1-3. トークンをコピー
`ghp_xxxxxxxxxxxxxxxxxxxx` みたいな文字列が表示される。

⚠️ **このページを閉じるとトークンは二度と見られない**。今すぐコピー！

---

## STEP 2. ターミナルで push（1コマンドだけ）

ターミナルで以下を実行。`YOUR_TOKEN` の部分にコピーしたトークンを貼る：

```bash
cd /Users/yuu/Documents/Claude/Epochstory/AMBER-LP

git push https://YOUR_TOKEN@github.com/appzepochstory-sketch/music1.git main
```

例：トークンが `ghp_abc123...` だったら：
```bash
git push https://ghp_abc123...@github.com/appzepochstory-sketch/music1.git main
```

→ 成功すると `To https://github.com/...` と出て完了。

---

## STEP 3. トークンを URL から削除（セキュリティ）

push後、remoteのURLにトークンが埋まっているとGitログに残って危険。
以下でクリーンに：

```bash
git remote set-url origin https://github.com/appzepochstory-sketch/music1.git
git remote -v
# → origin https://github.com/appzepochstory-sketch/music1.git (fetch/push) が表示されればOK
```

---

## 以降のpush

2回目以降は、毎回トークンを手入力するのではなく、**macOS Keychain** に覚えさせると楽：

```bash
git config --global credential.helper osxkeychain
```

これを入れておくと、次回以降の `git push` で一度だけusername/passwordを聞かれる：
- Username: `appzepochstory-sketch`
- Password: （さっきのトークンを貼る）

→ 以降は自動でトークンが使われる。

---

## GitHub Pages で公開したい場合

1. リポジトリ: https://github.com/appzepochstory-sketch/music1
2. **Settings** → 左メニュー **Pages**
3. **Source** を `Deploy from a branch` に
4. **Branch** を `main` / `/ (root)` にして Save
5. 数十秒後に `https://appzepochstory-sketch.github.io/music1/` で公開される

---

## トラブル

### `remote: Support for password authentication was removed` エラー
→ パスワード欄に GitHub のログインパスワードを入れた場合に出る。**必ずトークンを入れる**。

### `Permission denied` or `403` エラー
→ トークンに `repo` スコープがついてない。トークン作成画面で `repo` に✅を入れ直して再発行。

### 間違ってトークンを commit してしまった
→ GitHubのトークン画面（https://github.com/settings/tokens）でそのトークンを **Revoke**。
→ そのあと新しいトークンを発行してやり直す。
