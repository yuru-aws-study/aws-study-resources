# AWS サーバーレス開発 学習ガイド

    AIが勝手に生成した学習の進め方なので、話半分で読んでください。詳細についてはメンバーで話し合って決めるので、以下は更新対象。

このドキュメントは、ゼロからAWSサーバーレスアプリケーションを開発できるようになるまでの道筋を示します。

---

## 📍 学習の全体像
```
環境構築（1-2週間）
    ↓
Stage 1: 基本構成（3-4週間）
    ↓
Stage 2: データ駆動（3-4週間）
    ↓
Stage 3: 高度な機能（3-4週間）
    ↓
個人/チームプロジェクト
```

**合計期間**: 約3-4ヶ月（個人のペースによる）

---

## 🛠️ 環境構築（最初にやること）

### 前提条件
- パソコン（Windows/Mac/Linux）
- インターネット接続
- 2-3時間の作業時間

### 必要なアカウント

#### 1. GitHubアカウント
無料で作成できます。コード管理とコラボレーションに使います。

👉 詳細: [Wiki - GitHubアカウント作成](https://github.com/yuru-aws-study/aws-study-resources/wiki/GitHubアカウント作成)

#### 2. AWSアカウント
無料枠があります。クレジットカード登録が必要ですが、無料枠内なら課金されません。

👉 詳細: [Wiki - AWSアカウント作成](https://github.com/yuru-aws-study/aws-study-resources/wiki/AWSアカウント作成)

### ローカル開発環境のセットアップ

#### Windows の場合
WSL2（Windows Subsystem for Linux）を有効化します。

👉 詳細: [Wiki - Windowsセットアップ](https://github.com/yuru-aws-study/aws-study-resources/wiki/Windowsセットアップ)

#### Mac の場合
Homebrewをインストールして、必要なツールをセットアップします。

👉 詳細: [Wiki - Macセットアップ](https://github.com/yuru-aws-study/aws-study-resources/wiki/Macセットアップ)

### 必須ツールのインストール

1. **Git**: コード管理
2. **AWS CLI**: AWSをコマンドラインで操作
3. **SAM CLI**: サーバーレスアプリ開発ツール
4. **Docker**: ローカルでLambda関数をテスト
5. **VS Code**: 推奨エディタ

👉 詳細: [Wiki - 開発ツールのインストール](https://github.com/yuru-aws-study/aws-study-resources/wiki/開発ツールのインストール)

### AWS認証設定

AWS CLIでAWSアカウントに接続します。
```bash
aws configure
```

👉 詳細: [Wiki - AWS CLI設定](https://github.com/yuru-aws-study/aws-study-resources/wiki/AWS-CLI設定)

---

<details><summary>AI作の学習プラン（展開可能）</summary>


## 🎯 Stage 1: 基本構成（3-4週間）

### 目標
SAM Hello Worldをデプロイして、API経由でアクセスできるようにする。

### Week 1: Hello World デプロイ

**やること**:
1. SAMプロジェクト初期化
2. ローカルでテスト
3. AWSにデプロイ

**完了チェック**:
- [ ] `sam init` でプロジェクト作成
- [ ] `sam local start-api` でローカル起動
- [ ] `sam deploy` でAWSにデプロイ
- [ ] ブラウザからAPIにアクセスして応答確認

👉 詳細: [Wiki - Hello Worldデプロイ](https://github.com/yuru-aws-study/aws-study-resources/wiki/Hello-Worldデプロイ)

### Week 2-3: 認証機能の追加

**やること**:
1. Cognitoユーザープールを作成
2. API Gatewayに認証を追加
3. ユーザー登録・ログイン機能実装

**完了チェック**:
- [ ] Cognitoでユーザー登録ができる
- [ ] ログインしてJWTトークンを取得できる
- [ ] トークン付きでAPI呼び出しができる

### Week 4: フロントエンド（オプション）

**やること**:
1. Reactアプリを作成
2. S3にデプロイ
3. Cognitoと連携

**完了チェック**:
- [ ] ブラウザでログイン画面が表示される
- [ ] ログイン後にAPIを呼べる

---

## 📊 Stage 2: データ駆動（3-4週間）

### 目標
DynamoDBにデータを保存・取得できるアプリケーションを作る。

### Week 1: DynamoDB設計・実装

**やること**:
1. テーブル設計（アクセスパターンの洗い出し）
2. template.yamlにDynamoDB追加
3. Lambda関数からCRUD操作

**完了チェック**:
- [ ] DynamoDBテーブルが作成される
- [ ] Lambda関数からデータ書き込み
- [ ] Lambda関数からデータ読み取り

👉 詳細: [Wiki - DynamoDB入門](https://github.com/yuru-aws-study/aws-study-resources/wiki/DynamoDB入門)

### Week 2: CRUD API作成

**やること**:
1. GET/POST/PUT/DELETE エンドポイント作成
2. エラーハンドリング
3. CORS設定

**完了チェック**:
- [ ] POST /items でデータ作成
- [ ] GET /items でデータ一覧取得
- [ ] GET /items/{id} で個別取得
- [ ] PUT /items/{id} でデータ更新
- [ ] DELETE /items/{id} でデータ削除

### Week 3: 定期実行

**やること**:
1. EventBridgeで定期実行設定
2. Lambda関数で自動処理

**完了チェック**:
- [ ] 1時間ごとに自動実行される
- [ ] CloudWatch Logsでログ確認

### Week 4: UI実装

**やること**:
1. データ一覧表示
2. 作成・編集・削除機能

---

## 🚀 Stage 3: 高度な機能（3-4週間）

### Week 1: 非同期処理（SQS）

**やること**:
1. SQSキューを作成
2. Lambda関数でバッチ処理

**完了チェック**:
- [ ] メッセージがSQSに送信される
- [ ] Lambda関数がバッチ処理する
- [ ] エラー時にリトライされる

### Week 2: AI統合（オプション）

**やること**:
1. Bedrockでテキスト生成
2. Lambda関数から呼び出し

**完了チェック**:
- [ ] Bedrock APIを呼び出せる
- [ ] テキスト生成が動作する

### Week 3: CI/CD自動化

**やること**:
1. GitHub Actionsワークフロー作成
2. 自動テスト・デプロイ設定

**完了チェック**:
- [ ] mainブランチpushで自動デプロイ
- [ ] デプロイ履歴が確認できる

### Week 4: 監視・ログ

**やること**:
1. CloudWatch Logsで監視
2. エラーアラート設定

</details>

---

## 🆘 困ったときは

### Discord で質問
- `#環境構築で困った` - セットアップ関連
- `#AWS関連` - AWS技術的な質問
- `#CI/CD・GitHub Actions` - デプロイ関連

### GitHub で検索
- [Wiki](https://github.com/yuru-aws-study/aws-study-resources/wiki) - よくある問題の解決策
- [Discussions](https://github.com/yuru-aws-study/aws-study-resources/discussions) - 過去の議論

### トラブルシューティング
👉 [Wiki - トラブルシューティング](https://github.com/yuru-aws-study/aws-study-resources/wiki/トラブルシューティング)

---

## 📚 参考リソース

### 公式ドキュメント
- [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/)
- [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/)
- [DynamoDB Developer Guide](https://docs.aws.amazon.com/dynamodb/)

### ハンズオン
- [AWS SAM Workshop](https://catalog.workshops.aws/complete-aws-sam/)
- [Serverless Patterns](https://serverlessland.com/patterns)

---

## 🎓 学習のコツ

### 小さく始める
最初から完璧を目指さず、Hello Worldから少しずつ機能を追加していく。

### 手を動かす
記事を読むだけでなく、必ず自分でコードを書いて実行する。

### 失敗を恐れない
エラーは学習の機会。エラーメッセージをよく読んで、調べて、質問する。

### 成果を共有
小さな成功でもDiscordで報告。お互いのモチベーションになる。

---

**最終更新**: 2025-11-30  
**バージョン**: 1.0.0
