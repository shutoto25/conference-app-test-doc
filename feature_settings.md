# ユーザー設定機能 設計書

## 概要

ユーザー設定機能は、アプリのテーマ切り替えや通知設定、アカウント情報の管理など、ユーザーがアプリの動作や表示をカスタマイズできる機能です。

---

## 画面・UI構成
- テーマ切り替え（ライト/ダーク/システム）
- 通知ON/OFFスイッチ
- アカウント情報表示・編集
- バージョン情報・ライセンス表示

---

## 主なクラス・責務
- `SettingsScreen`：設定画面のUIコンポーネント
- `SettingsViewModel`：設定状態管理・保存
- `UserRepository`：アカウント情報取得・更新
- `PreferencesManager`：ローカル設定保存

---

## 振る舞い・ユースケース詳細

### 1. テーマ切り替え
- ユーザー操作でテーマを選択し、PreferencesManagerに保存
- 画面全体のテーマが即時反映

### 2. 通知設定
- 通知ON/OFFスイッチで設定を切り替え、PreferencesManagerに保存
- 必要に応じてOSの通知権限も確認

### 3. アカウント情報管理
- ユーザー情報をUserRepositoryから取得し表示
- 編集時はAPI経由でサーバーに反映

### 4. バージョン・ライセンス表示
- アプリバージョンやOSSライセンス情報を表示

---

## データフロー
1. ViewModelがPreferencesManagerやUserRepositoryから設定・情報を取得
2. StateとしてUIに反映
3. ユーザー操作で設定変更時は即時保存・反映

---

## 使用技術・ライブラリ
- Jetpack Compose
- Kotlin Flow/StateFlow
- Hilt
- Room
- DataStore/SharedPreferences
- Retrofit/OkHttp

---

## テスト方針
- ユニットテスト（設定保存・取得、ViewModel）
- UIテスト（テーマ切り替え、通知設定、アカウント編集）

---

## 備考
- 詳細は[公式リポジトリ](https://github.com/DroidKaigi/conference-app-2023)参照
