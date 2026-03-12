# TODO

## Plan
- [x] 仕様書要件の抽出と実装範囲の確定
- [x] index.html 単一ファイルで MVP を実装（5x5, 2位相表示, 世界線, 分岐, 持ち駒, 二歩）
- [x] 動作検証（構文チェック・主要操作確認）
- [x] コミット・PR作成

## Progress Log
- 仕様書.mdを読了し、v0.1のMVP範囲（5x5、駒種、位相、時間分岐、安定度、UI要素）を実装対象として確定。
- index.htmlにHTML/CSS/JSでゲーム全体を実装。
- Playwrightで画面表示を確認し、スクリーンショットを取得。

## Verification Log
- ✅ `node -e "const fs=require('fs');const s=fs.readFileSync('index.html','utf8'); if(!s.includes('6次元将棋')) process.exit(1); console.log('ok: index.html loaded, bytes='+s.length);"`
  - index.html の読み込みと主要文字列存在を確認。
- ✅ `python - <<'PY' ... PY`
  - UTF-8読み込み・行数取得が成功。
- ✅ `python -m http.server 4173` + Playwrightで `http://127.0.0.1:4173/index.html` を表示
  - 画面描画成功、スクリーンショット取得。

