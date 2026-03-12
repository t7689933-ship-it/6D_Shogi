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
