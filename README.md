# codex_Q-A

Spring Boot、Bootstrap、OracleDB を用いた技術系 Q&A Web アプリケーションの構想まとめです。

## アーキテクチャ
- **バックエンド**: Spring Boot (Spring Web, Spring Security, Spring Data JPA)
- **フロントエンド**: Bootstrap + Thymeleaf
- **データベース**: Oracle Database

## データベース設計
| テーブル | 主なカラム | 説明 |
|---|---|---|
| `users` | `id`, `username`, `password`, `roles` | ユーザ情報 (パスワードはハッシュ化) |
| `threads` | `id`, `title`, `content`, `user_id`, `created_at`, `view_count` | スレッド(質問) |
| `answers` | `id`, `thread_id`, `content`, `user_id`, `created_at` | 回答 |
| `bookmarks` | `user_id`, `thread_id`, `created_at` | ブックマーク |

## 主な機能
### ログイン機能
Spring Security を利用したフォーム認証。

### スレッド一覧表示
- 投稿されたスレッドを全て表示。
- 閲覧数による人気順、または投稿日時順での並び替え。
- 各スレッドに対してログインユーザはブックマーク可能。

### スレッド詳細閲覧
- 一つのスレッドに複数の回答を表示。
- 表示時に閲覧数をカウントアップ。

### スレッド削除
- 投稿者本人または管理者のみ削除可能。

## 開発メモ
- Spring Initializr で Web, Security, JPA, Thymeleaf を選択してプロジェクト生成。
- Oracle JDBC ドライバを `pom.xml` に追加。
- `application.properties` に Oracle 接続設定を記載。
- Bootstrap を `src/main/resources/static` に配置。
- 主要エンティティやコントローラ、サービスを実装予定。

