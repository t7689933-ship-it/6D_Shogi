# todo

## Plan
- [x] 仕様書.md と既存 `index.html` を確認して要件を整理
- [x] 対戦モードを「1端末対戦」と「AI対戦」に分離
- [x] 駒表示を通常将棋の向き（向かい合わせ）として視認しやすく調整
- [x] UI全体の視認性を改善（情報整理・配色/余白の改善）
- [x] 検証コマンド実行と結果記録
- [x] コミットとPR作成

## Progress Log
- ユーザー要望3点を確認。
- 既存実装は `aiMode` 単体選択で、1端末対戦とAI対戦がUI上で明確分離されていない状態。
- `matchMode`（1端末対戦/AI対戦）と `aiSide`（先手/後手/両方）に分離し、AI対戦時のみAI設定と手動AIボタンを有効化する実装に変更。
- 駒表示に `▲/▽` を追加し、向きが一目でわかるように調整。
- 初期配置を「先手が下段・後手が上段」に変更し、通常将棋の向かい合う配置へ修正。
- パネル余白・影、文字強調、セル文字サイズ調整などで見やすさを改善。

## Verification Log
- ✅ `python3 -m http.server 4173` を起動し、Playwrightで `http://127.0.0.1:4173` を表示してモード切替を確認、スクリーンショット取得（`browser:/tmp/codex_browser_invocations/6022401f28aa231d/artifacts/artifacts/ui-updated.png`）。
- ✅ `git diff --check`
- ✅ `git status --short`（変更対象が `index.html` と `.codex/tasks/todo.md` のみ）
