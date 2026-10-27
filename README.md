# 少年野球スコアブック（PWA）

## 中身
- index.html … アプリ本体（単一ファイル）
- manifest.webmanifest … ホーム画面追加用の設定
- sw.js … オフライン動作用のService Worker
- icon-192.png / icon-512.png / icon-maskable-512.png … アイコン

## 公開方法（HTTPSが必須です）
次のどれかに、このフォルダの中身をそのままアップロードします。
- GitHub Pages / Netlify（Drop）/ Cloudflare Pages / Firebase Hosting など
- 試験用: このフォルダで `python3 -m http.server 8000` を実行し、http://localhost:8000 を開く

## 端末への追加
- iPhone/iPad: Safariで開く →共有→「ホーム画面に追加」
- Android: Chromeで開く →メニュー→「アプリをインストール」（またはアプリ内の「ホーム画面に追加」）

最初に1回、通信できる状態で開くと、以降はオフラインでも動きます。

## 更新方法
index.html を差し替え、sw.js の VERSION（例: scorebook-v2）を書き換えて再アップロードしてください。

## データ
- 試合データはその端末のブラウザ内（localStorage）に保存されます。端末をまたぐ共有はありません。
- 「速報・設定」タブの「全試合をバックアップ」で書き出せます（claude.ai上の試験版からの引っ越しにも使えます）。
- JSON/CSVはファイルとして書き出せます。

## HOPE-SABR連携
「速報・設定」→「PWA・連携」に連携先URLを入れて送信すると、試合データ（JSON, schema: scorebook/2）をPOSTします。
オフライン時は端末内に保留し、通信が戻ると自動で再送します。連携先のCORS許可が必要です。認証が必要な場合は別途追加してください。
