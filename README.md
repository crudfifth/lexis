# Lexis

Lexis は、現代の組織運営に必要な業務支援機能を統合したモジュール型Webシステムです。  
本システムは Ruby on Rails（APIモード）と SolidJS による高速で再利用性の高いアーキテクチャで構成されています。  
複数の業務領域を一元管理することで、社内オペレーションの効率化と情報資産の構造化を実現します。

---

## 機能一覧

### 勤怠管理
- 出退勤打刻、修正申請、休暇管理
- 承認フロー付き
- 日/週/月単位のカレンダー表示と履歴ログ

### 工数・タスク管理
- タスクのプロジェクト割当・担当者アサイン
- 作業時間記録、タイムライン/カンバン表示
- 工数集計と稼働率の可視化

### 日報・週報投稿
- Markdown対応投稿フォーム
- チーム単位の公開設定、投稿承認制
- 履歴管理と検索機能

### 顧客・案件管理（CRM）
- 顧客・案件・アクション履歴の管理
- ラベル・ステータス管理、進捗トラッキング
- 絞り込み・フィルタ・担当者別一覧

### 社内ドキュメント共有
- ナレッジのカテゴリ別管理、全文検索
- ドキュメントバージョン履歴と復元
- アクセス制御と編集権限管理

---

## 技術スタック

### バックエンド
- Ruby on Rails 7（APIモード）
- PostgreSQL
- Devise（認証）+ Pundit（認可）
- Sidekiq + Redis（ジョブ処理）
- pg_search（全文検索）
- WickedPDF（PDF出力）

### フロントエンド
- SolidJS（Vite構成）
- TypeScript
- Tailwind CSS
- Zustand または Context API（状態管理）
- Axios（API通信）

---

## ディレクトリ構成

```
app/
lexis/
├── backend/                  # Rails APIモード
│   ├── app/
│   │   ├── controllers/
│   │   │   ├── api/
│   │   │   │   ├── v1/
│   │   │   │   │   ├── attendances_controller.rb
│   │   │   │   │   ├── tasks_controller.rb
│   │   │   │   │   ├── reports_controller.rb
│   │   │   │   │   ├── clients_controller.rb
│   │   │   │   │   ├── documents_controller.rb
│   │   ├── models/
│   │   │   ├── user.rb
│   │   │   ├── attendance.rb
│   │   │   ├── task.rb
│   │   │   ├── report.rb
│   │   │   ├── client.rb
│   │   │   ├── document.rb
│   │   ├── serializers/
│   │   │   ├── attendance_serializer.rb
│   │   │   ├── ...
│   │   ├── policies/
│   │   │   ├── task_policy.rb
│   │   ├── services/
│   │   │   ├── pdf_exporter.rb
│   │   └── jobs/
│   │       ├── report_digest_job.rb
│   ├── config/
│   │   ├── routes.rb
│   │   ├── initializers/
│   │   │   ├── devise.rb
│   │   │   ├── cors.rb
│   ├── db/
│   │   ├── migrate/
│   │   ├── seeds.rb
│   └── spec/ or test/         # RSpec or Minitest
│
├── frontend/                 # SolidJS (Vite)
│   ├── public/
│   │   ├── index.html
│   ├── src/
│   │   ├── app/              # ルーティング、ページレベル
│   │   │   ├── routes/
│   │   │   │   ├── dashboard/
│   │   │   │   │   ├── index.tsx
│   │   │   │   ├── attendances/
│   │   │   │   ├── tasks/
│   │   │   │   ├── reports/
│   │   │   │   ├── clients/
│   │   │   │   ├── documents/
│   │   ├── components/       # 再利用可能なUIパーツ
│   │   │   ├── form/
│   │   │   ├── layout/
│   │   │   ├── table/
│   │   │   ├── inputs/
│   │   ├── features/         # ドメインごとに分離されたロジック層
│   │   │   ├── attendance/
│   │   │   │   ├── api.ts
│   │   │   │   ├── hooks.ts
│   │   │   ├── task/
│   │   │   ├── report/
│   │   │   ├── client/
│   │   │   ├── document/
│   │   ├── hooks/            # 共通カスタムHooks
│   │   ├── lib/              # 汎用ライブラリ（util, api client）
│   │   ├── providers/        # contextや状態管理
│   │   ├── stores/           # Zustandなどで状態管理
│   │   ├── styles/
│   │   │   ├── tailwind.css
│   │   ├── assets/
│   │   └── index.tsx
│   ├── vite.config.ts
│   ├── tsconfig.json
│   └── package.json
│
├── docs/                     # システム設計・仕様書
│   ├── architecture.md
│   ├── models.md
│   ├── api-spec.md
│   ├── roles-permissions.md
│
├── .env                      # 環境変数ファイル
├── README.md
└── LICENSE

```
