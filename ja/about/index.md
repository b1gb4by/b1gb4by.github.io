# WHORU?


## 基本情報

| 項目     | 内容                                                                        |
| :------- | :-------------------------------------------------------------------------- |
| 氏名     | 岡本 泰典 (オカモト タイスケ)                                               |
| 生年月日 | 1996/12/02                                                                  |
| 最終学歴 | 大阪工業大学 情報科学部 ネットワークデザイン学科 (旧: 情報ネットワーク学科) |

## 保有スキル

- Golng でのバックエンド開発、設計、テスト、運用、保守
- クリーンアーキテクチャを意識したコーディング
- TDD でのテストコード開発
- Kubernetes での開発、設計、テスト、運用、保守
- Prometheus, Grafana を使用した監視メトリクスの収集
- CI / CD の環境構築、運用
- DRM の資格([CWIP](https://www.widevine.com/): Certified Widevine Implementation Partner)の保有

## 技術スタック

| カテゴリ                                       | 技術スタック                                        |
| :--------------------------------------------- | --------------------------------------------------- |
| Programing langage / Library etc.              | Go, Python, Java, PHP, C, Solidity                  |
| Programing langage / Library etc. (individual) | C++, C#, V, Zig, gRPC                               |
| Framework                                      | Gin(Go), Falcon(Python), Spring Boot(Java)          |
| Infrastructure                                 | GCP                                                 |
| Middleware                                     | Redis, Memorystore                                  |
| Database                                       | MySQL, Cloud SQL                                    |
| Data analytics                                 | BigQuery                                            |
| Environment setup                              | Ansible, Cloud Build. Docker, Terraform(individual) |
| Container Orchestration                        | Kubernetes, Rancher, CloudRun                       |
| IaaS                                           | CloudStack, vSphere                                 |
| CI                                             | ArgoCD, CircleCI, Cloud Build, GitHub Actions       |
| Monitoring                                     | Prometheus, Grafana                                 |
| Service Mesh                                   | Istio, Linkerd(individual)                          |
| Code Management                                | GitHub, GitLab, Bitbucket                           |

## 職務経歴詳細

### 株式会社 IDC フロンティア (2021/09 ~ 現在)

#### Kubernetes as a Service (KaaS) 開発

- プロジェクト規模
  - 約 40 名 (チーム: 2 名)
- 役割
  - 機能検討、設計、コーディング、その他、調査、研究など
- プロジェクト詳細
  - CloudStack の CSI Drive/Cloud Controller Manager/Ingress Controller の各種機能・実装の調査・研究
  - Rancher 向けの Cluster Autoscaler の開発、実装
  - vSphere をベースとしたプライベートクラウドの開発、実装
  - Kubernetes Addon の自動化、独自機能の実装
  - 社内でのコンテナ / Kubernetes の普及・促進活動

### パペルック株式会社 (2021/02 ~ 2021/08)

#### 自社の商品発注管理システムの開発・運用

- プロジェクト規模
  - 約 2~4 名
- 役割
  - テックリード、機能検討、設計、コーディング、レビュー
- プロジェクト詳細
  - Go 言語での API 開発
  - GCP 内で完結するサービスの運用
  - CloudBuild + CloudRun での CI/CD の構築、及び開発スピードの促進
  - 自社で使用している EC プラットフォーム(Shopify)との連携

#### 中国、韓国 EC サイトなどとの連携システムの開発・運用

- プロジェクト規模
  - 個人開発
- 役割
  - 機能検討、設計、コーディング
  - アライアンスとの仕様検討、及び交渉
- プロジェクト詳細
  - Go 言語による API, バッチ処理, Webhook の実装
    - バッチ処理では並行処理を使用し、2~3 万件/日の登録処理を実施
  - Slack との連携を行い、エラー発生時などの早期検知を実現

また、以下の業務を兼務

- 社内ネットワークの整備、及び保守
- D2C 事業でのクライアントのサイトの構築、及び運用、保守
- Google App Script + Google Analytics を使用し、自社 EC サイトの日時レポートの自動化

### 株式会社ビデオマーケット (2019/04 ~ 2021/01)

#### 配信サービス内の再生基盤のリニューアル

- プロジェクト規模
  - 約 20 名
- 役割
  - API の機能検討、設計、コーディング、レビュー
  - クラウドインフラの設計、コーディング、レビュー
  - 監視ツールの導入
  - CI/CD 内への脆弱性チェックを導入
- プロジェクト詳細
  - 既存で動いている PHP の再生基盤を Golang へリプレイス
  - GKE を使用したマイクロサービス化
  - Kustomize を用いた Kubernetes におけるマニフェストの環境差分の管理コストの削減
  - サービスメッシュを活用し、マイクロサービス間の通信をセキュアに保つ
  - 使用用途を切り分け、それぞれに BigQuery, Redis など適した DB を導入
  - Grafana, Prometheus を用いたアラートの実装

また、業務の一環として以下の DRM の資格を取得

- CWIP (Certified Widevine Implementation Partner)
  - 2020 年 12 月 合格

## 業務外活動

### CloudNative Days

- 日本最大級のクラウドネイティブ・テックカンファレンスに実行委員として参画
- これまで以下のカンファレンスにて Observability チームを担当
  - [Observability Conference 2022 by CloudNative Days](https://event.cloudnativedays.jp/o11y2022)
  - [CloudNative Security Conference 2022 by CloudNative Days](https://event.cloudnativedays.jp/cnsec2022)
  - [CloudNative Days Tokyo 2022](https://event.cloudnativedays.jp/cndt2022)

#### テックカンファレンスの運営 (2021/11 - 現在)

### 株式会社 Relie

#### 技術コーチ (2022/01 - 現在)

- 役割
  - 技術研修の実施
  - エンジニアリングにおける課題解決の支援

#### 総合プラットフォームの開発 (2021/07: 1 ヶ月)

- プロジェクト規模
  - 約 3 名
- 役割
  - API の設計、コーディング、開発、レビュー
  - DB の構築、及びマイグレーションの自動化
  - クラウドサーバの構築、運用、保守
- 仕様技術
  - Golang
  - GCP (GAE, CloudSQL, BigQuery)

友人が起業した会社のサービス開発のバックエンド全般をサポート. また、インフラの構築を担当.

### 株式会社 GiGs

#### 音声プラットフォームの開発 (2019/07 - 2019/11: 5 ヶ月)

- プロジェクト規模
  - 約 2 名
- 役割
  - 独自メディア再生プレイヤーの設計、実装、テスト
- 仕様技術
  - HTML, CSS, JavaScript

友人が起業した会社のサービスの開発の一部をサポート.

### 株式会社ライズアース

#### LP サイトの作成 (2017/10 - 2017/12: 3 ヶ月)

- プロジェクト規模
  - 個人開発
- 役割
  - WordPress の構築、運用、保守
  - LP サイトの作成
- 仕様技術
  - WordPress, PHP, JavaScript, CSS, MySQL

友人が起業した会社の LP の作成から公開、運用を全て行う.

