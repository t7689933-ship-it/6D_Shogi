# Task Todo

## Plan
- [x] 仕様書と実装を照合して重要ロジックの不具合候補を特定する
- [x] 根本原因に対する最小修正を実装する
- [x] 再現コマンドで修正前後の挙動を検証する
- [x] 変更を記録しコミットとPR作成を行う

## Progress Log
- 仕様書.md と index.html を確認。重要ロジックとして合法手生成と applyMoveToPosition を重点確認。
- 不具合特定: 王の「その場位相反転」手が無条件生成され、遷移先位相に自駒がいても合法扱いされる。
- 修正実装: `piecePseudoMoves` の王処理で、位相反転先に自駒がいる場合は手を生成しない条件分岐を追加。

## Verification Log
- Playwright検証(修正前): `illegal_phase_shift_generated: True`
- Playwright検証(修正後): `illegal_phase_shift_generated: False`
- Playwright検証(退行防止): `phase_shift_to_enemy_allowed: True`

---

## Plan (2026-03-12 初見ユーザー向けUI改善)
- [x] 仕様書と既存UIを確認し、初見ユーザーが迷う導線を特定する
- [x] 操作説明とラベル文言を、最小変更でわかりやすく改善する
- [x] 画面確認・スクリーンショット取得・結果記録を行う

## Progress Log (2026-03-12 初見ユーザー向けUI改善)
- `仕様書.md` と `index.html` を照合し、初見の詰まりどころを「分岐モードの意味」「次に何をすべきか不明瞭」「パネル名が抽象的」に整理。
- `index.html` に「はじめての方向け 3ステップ」ガイドを追加。
- コントロール文言を具体化（時間分岐モード、AIに1手だけ指させる、最初からやり直す）。
- 状況ヒントを「手番」「現在の選択状態（駒選択/移動先選択/打ち先選択）」を含む文に改善。

## Verification Log (2026-03-12 初見ユーザー向けUI改善)
- `python3 -m http.server 4173` でローカル起動し、Playwrightで画面を確認。
- スクリーンショット取得: `browser:/tmp/codex_browser_invocations/c90441917b3baa84/artifacts/artifacts/ui_onboarding.png`
