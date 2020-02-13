## 導入事例
### メルカリ
#### 導入に踏み切った理由
- モノリシックな構造だと、プロダクトの成長に影響が出る
    - 入社してすぐのメンバーが、変更を加えるのに調査すべき影響範囲が広すぎる
    - 開発メンバーが増えれば増えるほど、開発速度が落ちる

#### どう浸透させたか
- APIゲートウェイアーキテクチャへの移行
  - 全てのリクエストは、APIゲートウェイを通す
  - 新しいサービスを作成する際は、配下に置くことで独立した開発が可能に
- サービス感のコミュニケーションプロトコルの統一
  - gRPC
- 新規のマイクロサービスのためのテンプレート
  - 標準的なGoのパッケージ構成
  - モニタリング,エラーリポーティング
  - Dockerfile
  - CIの設定
- インフラへのアクセス制限のデザイン

#### 参考
- https://codezine.jp/article/detail/11473
- Mercari Tech Conf 2018発表
  - https://logmi.jp/tech/articles/320198
  - https://speakerdeck.com/mercari/mtc2018-microservices-platform-at-mercari?slide=78