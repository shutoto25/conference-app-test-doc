# データ設計書（conference-app-2023）

## 1. 概要
conference-app-2023で利用される主なデータモデル・エンティティ・テーブル設計についてまとめます。

---

## 2. 主なデータモデル

### Session（セッション）

| フィールド名         | 型           | 説明                       |
|----------------------|--------------|----------------------------|
| id                   | String       | セッションID               |
| title                | String       | セッションタイトル         |
| description          | String       | セッション概要             |
| speakers             | List<Speaker>| 登壇者リスト               |
| startTime            | DateTime     | 開始時刻                   |
| endTime              | DateTime     | 終了時刻                   |
| room                 | String       | 会場名                     |
| tags                 | List<String> | タグ                       |
| isBookmarked         | Boolean      | ブックマーク状態           |
| track                | String       | トラック名                 |

---

### Speaker（登壇者）

| フィールド名         | 型           | 説明                       |
|----------------------|--------------|----------------------------|
| id                   | String       | 登壇者ID                   |
| name                 | String       | 氏名                       |
| bio                  | String       | 略歴                       |
| iconUrl              | String       | アイコン画像URL            |
| sessions             | List<String> | 担当セッションIDリスト     |

---

### Room（会場）

| フィールド名         | 型           | 説明                       |
|----------------------|--------------|----------------------------|
| id                   | String       | 会場ID                     |
| name                 | String       | 会場名                     |
| floor                | String       | フロア情報                 |

---

### Bookmark（ブックマーク）

| フィールド名         | 型           | 説明                       |
|----------------------|--------------|----------------------------|
| sessionId            | String       | セッションID               |
| userId               | String       | ユーザーID                 |
| createdAt            | DateTime     | 登録日時                   |

---

### User（ユーザー）

| フィールド名         | 型           | 説明                       |
|----------------------|--------------|----------------------------|
| id                   | String       | ユーザーID                 |
| name                 | String       | 氏名                       |
| email                | String       | メールアドレス             |
| iconUrl              | String       | アイコン画像URL            |
| settings             | Map<String, Any> | ユーザー設定             |

---

## 3. テーブル設計（Room/DB例）

#### sessions
- id (PK)
- title
- description
- start_time
- end_time
- room_id (FK)
- track

#### speakers
- id (PK)
- name
- bio
- icon_url

#### session_speakers
- session_id (PK, FK)
- speaker_id (PK, FK)

#### rooms
- id (PK)
- name
- floor

#### bookmarks
- session_id (PK, FK)
- user_id (PK, FK)
- created_at

#### users
- id (PK)
- name
- email
- icon_url
- settings (JSON)

---

## 4. 備考
- 実際のAPIレスポンスやDBスキーマは[公式リポジトリ](https://github.com/DroidKaigi/conference-app-2023)の実装を参照
- 必要に応じてER図や詳細設計も追加可能
