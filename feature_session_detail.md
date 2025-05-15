# セッション詳細機能 設計書

## 概要

セッション詳細機能は、タイムテーブルや検索などから遷移した個別セッションの詳細情報を表示し、登壇者情報やブックマーク、シェアなどの操作を提供します。

---

## 画面・UI構成
- セッションタイトル、概要、時間、会場
- 登壇者プロフィール（アイコン・名前・略歴）
- ブックマークボタン
- シェアボタン
- タグ・トラック情報

---

## 主なクラス・責務
- `SessionDetailScreen`：セッション詳細画面のUIコンポーネント
- `SessionDetailViewModel`：詳細データ取得・状態管理
- `SessionRepository`：セッションデータ取得
- `BookmarkManager`：ブックマーク状態管理

---

## 振る舞い・ユースケース詳細

### 1. 詳細表示
- タイムテーブルや検索画面からSessionデータを受け取り、詳細画面に遷移
- ViewModelがSession IDで詳細データを取得し、UIに反映

### 2. ブックマーク操作
- ブックマークボタンをタップでBookmarkManager経由で状態をトグル
- 状態は即時UIに反映、ローカルDBやサーバーにも同期

### 3. シェア
- シェアボタンからセッション情報を外部アプリに共有

---

## データフロー
1. ViewModelがRepository経由で詳細データを取得
2. Stateとして保持し、UIに反映
3. ユーザー操作（ブックマーク、シェア等）をViewModelで処理

---

## 使用技術・ライブラリ
- Jetpack Compose
- Kotlin Flow/StateFlow
- Hilt
- Retrofit/OkHttp
- Room
- Material3

---

## テスト方針
- UIテスト（画面表示・ブックマーク・シェア）
- ユニットテスト（ViewModel、Repository）

---

## 備考
- 詳細は[公式リポジトリ](https://github.com/DroidKaigi/conference-app-2023)参照
