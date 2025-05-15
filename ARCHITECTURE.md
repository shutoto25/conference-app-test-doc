# conference-app-2023 設計書

## 1. プロジェクト概要

conference-app-2023は、DroidKaigi 2023公式のカンファレンスアプリです。
Kotlin Multiplatform（KMP）を活用し、Android・iOS両対応のクロスプラットフォームアプリとして開発されています。

- GitHubリポジトリ: [DroidKaigi/conference-app-2023](https://github.com/DroidKaigi/conference-app-2023)
- ライセンス: Apache-2.0

---

## 2. ディレクトリ構成（抜粋）

```
conference-app-2023/
├── app-android/         # Androidアプリ本体
├── app-ios/             # iOSアプリ本体
├── app-ios-shared/      # iOS/Android共通コード
├── core/                # 共通ロジック・基盤
├── feature/             # 機能ごとの実装
├── build-logic/         # ビルドロジック
├── gradle/              # Gradle設定
├── scripts/             # 各種スクリプト
├── config/              # 静的解析等の設定
├── .github/             # GitHub Actions等
├── .idea/ .run/         # IDE設定
├── README.md
└── ...（その他省略）
```

---

## 3. 採用技術・設計方針

- Kotlin Multiplatform（KMP）
- Jetpack Compose（Android UI）
- SwiftUI（iOS UI）
- Material3デザイン
- Hilt（DI）
- Detekt（静的解析）
- CI/CD（GitHub Actions）
- テスト自動化（Robolectric, Roborazzi, Screenshot Testing）

---

## 4. テスト戦略

- Robolectric Native Graphics（RNG）＋Roborazziによるスクリーンショットテスト
- テストロボットパターンによるUIテストの分離
- Fake APIサーバによる安定したテスト環境
- Companion Branch方式でのスクリーンショット管理

詳細は[Testingセクション](https://github.com/DroidKaigi/conference-app-2023#testing)参照

---

## 5. 主要モジュール・役割

| ディレクトリ         | 役割・内容例                                 |
|----------------------|----------------------------------------------|
| app-android/         | Androidアプリ本体                            |
| app-ios/             | iOSアプリ本体                                |
| app-ios-shared/      | iOS/Android共通コード                        |
| core/                | 共通ロジック・基盤                           |
| feature/             | 機能ごとの実装                               |
| build-logic/         | Gradleビルドロジック                         |
| scripts/             | 開発・CI用スクリプト                         |
| config/              | Detekt等の静的解析設定                       |

---

## 6. 開発・ビルド要件

- JDK 17
- Xcode（iOS開発時）
- Ruby（iOSビルド用Fastlane等）
- Android Studio（KMMプラグイン推奨）

セットアップ・ビルド手順は[README](https://github.com/DroidKaigi/conference-app-2023#ios)参照

---

## 7. コントリビューション・CI

- GitHub ActionsによるCI/CD
- スクリーンショットテストの自動化
- PRごとにCompanion Branchで画像管理
- Detektによる静的解析

---

## 8. ライセンス

- Apache-2.0

---

## 参考リンク

- [DroidKaigi/conference-app-2023 GitHub](https://github.com/DroidKaigi/conference-app-2023)
- [Testingセクション（README内）](https://github.com/DroidKaigi/conference-app-2023#testing)

---

このドキュメントはDroidKaigi 2023公式リポジトリの公開情報をもとに作成しています。
