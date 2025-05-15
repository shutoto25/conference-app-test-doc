# タイムテーブル機能 設計書

## 概要

タイムテーブル機能は、DroidKaigiカンファレンスの全セッションを時系列で一覧表示し、ユーザーがセッションの詳細確認やブックマーク、検索などを行える中核的な画面・機能です。

---

## 画面・UI構成
- セッション一覧（時間軸・トラック別表示）
- 日付・トラック切り替えタブ
- セッションカード（タイトル、登壇者、会場、時間、ブックマークボタン等）
- 検索・フィルタ機能
- セッション詳細画面への遷移

---

## 主なクラス・責務
- `TimetableScreen`：タイムテーブル画面のUIコンポーネント（Compose）
- `TimetableViewModel`：状態管理・データ取得
- `TimetableRepository`：APIやローカルDBからセッションデータ取得
- `Session`：セッションデータモデル
- `BookmarkManager`：ブックマーク状態管理

---

## データフロー
1. ViewModelがRepository経由でセッション一覧データを取得
2. 取得データをUI状態（State）として保持
3. ユーザー操作（ブックマーク、検索、日付切替等）をViewModelで処理し、Stateを更新
4. UI（TimetableScreen）がStateを監視し、画面を自動更新

---

## 使用技術・ライブラリ
- Jetpack Compose（UI）
- Kotlin Flow/StateFlow（状態管理）
- Hilt（DI）
- Retrofit/OkHttp（API通信）
- Room（ローカルDB）
- Material3

---

## テスト方針
- Robolectric＋Roborazziによるスクリーンショットテスト
- テストロボットパターンによるUIテスト分離
- Fake APIによるデータ取得テスト
- ユーザー操作（ブックマーク、検索等）のユニットテスト

---

## 備考
- Companion Branch方式でスクリーンショット管理
- 機能詳細・クラス構成は[公式リポジトリ](https://github.com/DroidKaigi/conference-app-2023)を参照
