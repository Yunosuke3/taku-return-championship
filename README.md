# TAKU 復帰 CHAMPIONSHIP 🥊

TAKU がいつ会社に戻ってくるかを、UFC の選手紹介っぽく予想して遊ぶ社内向けのお遊びアプリです。
復帰時期（1ヶ月／半年／1年／1年半／2年／2年半）がそれぞれ「架空のムキムキ TAKU ファイター」になっていて、
名前を入れて **長押しでパワーをためて離す＝スラム！** でコインを賭けます。誰がどこに賭けたかは下の一覧で見られます。

> ⚠️ これは遊び用のモックです。コインは架空で、実際のお金は一切かかりません。オッズ・戦績・参加者・プール額はすべてダミー値で、
> リロードすると初期状態に戻ります（サーバー保存はしていません）。ファイターはフィクションです。

## 中身

- `index.html` … アプリ本体。**これ 1 ファイルで完結**します（画像も中に埋め込み済み、外部依存はフォントと Google Fonts のみ）。
- `.github/workflows/deploy-pages.yml` … push すると GitHub Pages に自動デプロイするワークフロー（任意）。

## ローカルで見る

`index.html` をダブルクリックしてブラウザで開くだけです。ビルドやサーバーは不要です。

## Web に公開する（GitHub Pages）

### 1. GitHub にリポジトリを作って push する

GitHub で空のリポジトリ（例: `taku-return-championship`）を作成してから、このフォルダで以下を実行します。
`YOUR_NAME` は自分の GitHub ユーザー名に置き換えてください。

```bash
git init
git add .
git commit -m "TAKU 復帰 CHAMPIONSHIP"
git branch -M main
git remote add origin https://github.com/YOUR_NAME/taku-return-championship.git
git push -u origin main
```

（このフォルダはすでに `git init` + 初回コミット済みの状態で渡しています。その場合は `git remote add ...` と `git push` だけで OK です。）

### 2. Pages を有効化する（かんたんな方法）

1. リポジトリの **Settings → Pages** を開く
2. **Build and deployment** の **Source** を **Deploy from a branch** にする
3. **Branch** を `main` / `/(root)` にして **Save**
4. 数十秒〜数分で `https://YOUR_NAME.github.io/taku-return-championship/` に公開されます

### （任意）push で自動デプロイしたい場合

同梱の `deploy-pages.yml` を使うと、`main` に push するたびに自動で公開されます。使う場合は
**Settings → Pages → Source** を **GitHub Actions** に変更してください。上の「Deploy from a branch」を使うなら、
このワークフローは不要なので `.github/` ごと削除して構いません。

## 中身をいじる

- ファイター名・煽り文句・オッズ・ステータスは `index.html` 内の `const F = { ... }` と `const options = [ ... ]` を編集
- 賭けコインのレンジ（現状 50〜500）は `const MIN=50, MAX=500;`
- キャラ画像は `--fimg` の data URI を差し替え。ファイターごとに別画像にしたい場合は画像を複数用意して `POS` のように id で出し分けできます
- 色味・切り抜きは `const POS`（表示位置）と `const GOP`（色グレードの濃さ）を調整

## ライセンス

社内・個人利用向けのお遊びプロジェクトです。埋め込み画像はあなたが用意した素材なので、公開範囲は各自の判断でどうぞ。
