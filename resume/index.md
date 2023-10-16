# RESUME


## 基本情報

| 項目     | 内容                                                                        |
| :------- | :-------------------------------------------------------------------------- |
| 氏名     | 岡本 泰典 (オカモト タイスケ)                                               |
| 生年月日 | 1996/12/02                                                                  |
| 最終学歴 | 大阪工業大学 情報科学部 ネットワークデザイン学科 (旧: 情報ネットワーク学科) |

## 保有スキル

- Golangでのバックエンド開発、設計、テスト、運用、保守
- クリーンアーキテクチャを意識したコーディング
- TDDでのテストコード開発
- Kubernetesでのサービス開発、設計、テスト、運用、保守
- Kubernetesコンポーネントの開発、設計、テスト、運用、保守
- Kubernetes周辺のエコシステム（Observability系ツール）の導入、運用、保守

## 技術スタック

| カテゴリ                                       | 技術スタック                                            |
| :--------------------------------------------- | :---------------------------------------------------|
| Programming language / Library etc.              | Go, Python, Java, PHP, C, Solidity                |
| Programming language / Library etc. (individual) | C++, C#, V, Zig, gRPC                             |
| Framework                                      | Gin(Go), Falcon(Python), Spring Boot(Java)          |
| Infrastructure                                 | Google Cloud                                                 |
| Middleware                                     | Redis, Memorystore                                  |
| Database                                       | MySQL, PostgreSQL(individual), Cloud SQL            |
| Data analytics                                 | BigQuery                                            |
| Environment setup                              | Ansible, Cloud Build, Docker, Terraform(individual) |
| Container Orchestration                        | Kubernetes, Rancher, CloudRun                       |
| IaaS                                           | CloudStack, vSphere                                 |
| CI                                             | ArgoCD, CircleCI, Cloud Build, GitHub Actions       |
| Monitoring                                     | Prometheus, Grafana                                 |
| Service Mesh                                   | Istio, Linkerd(individual)                          |
| Code Management                                | GitHub, GitLab, Bitbucket                           |

## 職務経歴詳細

### 株式会社 IDC フロンティア (2021/09 ~ 現在)

| 項目                | 内容    |
| :----------------- | :------ |
| プロジェクト規模       | 約 1 名 |
| 役割 | 学習コンテンツの企画、作成、学習会の実施など |
| 業務内容 | コンテナ・Kuberentesの社内での普及、およびクライアントへの導入時の技術支援 |
| 使用した技術 | Kubernetes, Docker etc...|

- 社内でコンテナ・Kubernetsの普及を加速させるために学習コンテンツを作成し、エンジニアに対し学習会を実施しました
  - 学習会は3か月で構成され、各回ごとにアンケートなどの回答をお願いしていました
  - 勉強会の満足度は毎回90%以上を維持しており、学習会後の補修では、さらに深い知識の共有や、その日の疑問を解消していました
- 現在では、自社システムのコンテナ・Kubernetes化が進んでおり、その移行時の支援や課題解決を行っています
- また、SE(Sales Engineer)や営業の技術支援も行っており、コンテナ・Kubernetesの導入時の課題解決や、上記の学習コンテンツを使用したクライアントへの技術サポートもしております
  - 技術支援では、コンテナ・Kuberentes以外にも、CI/CDやObservabilityなどのツールの導入支援も併せて行っています

| 項目                | 内容    |
| :----------------- | :------ |
| プロジェクト規模       | 約 20 名 (内チーム: 2名)  |
| 役割 | 機能検討、設計、コーディング、その他、調査、研究など |
| 業務内容 | Kubernetes as a Service (KaaS) 開発 |
| 使用した技術 | VMware vSphere, CloudStack, GitHub Actions, Fleet, Docker, Kubernetes, Golang|

- 私が関わっているプロジェクトは、OSSのクラウドプラットフォームであるCloudStackでKubernetesを使用できるように以下のコンポーネントの各種機能や実装に関する調査・研究を行っています
  - CSI Driver
  - Cloud Controller Manager
  - Ingress Controller

{{< admonition question "CloudStackにもKubernetesを動かすAPIが提供されているけどなんで？" true>}}
CloudStackには、Kubernetesを構築する機能を有していますが、自社のセキュリティ要件に満たないため、独自に実装しました
{{< /admonition >}}

- そのため、Kubernetesのバージョンアップに伴う内部コンポーネントなどの修正などは、実際にOSSなどを読み解くことで自分たちのコンポーネントに反映させています
- その他にも、ユーザー体験向上のために、以下のような自社独自のコンポーネントを開発しています
  - [addon-manager](https://github.com/kubernetes/kubernetes/tree/master/cluster/addons/addon-manager)の内製による自動アップデート機能の提供
    - 顧客クラスターに導入することで、自社コンポーネントの更新を自動化することを実現しています
    - また、Addonを定期的に取得することもできます
    - 上記のコンポーネントを使用するためのマニフェストを管理するサーバーを設置しており、各環境、各バージョンごとに沿ったマニフェストを取得することが可能です
  - Migration機能
    - クラスターの直接操作でしか変更できないような対応を自動で行ってくれる機能
  - [Cluster Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler)の提供
    - 弊社ではRancherをベースにGUIの提供を行っているため、Rancherの仕様に沿ったサービスの提供を行っています
    - Cluster Autoscalerは各プロバイダーには存在している機能ですが、Rancher社から提供されていないため、OSSとして提供されているコードを参考に独自に実装を行いました
  - プライベートクラウド
    - vSphereをベースにKubernetesを構築しているので、上記とはまた異なるリソースを独自で用意してユーザーに提供しています
- 非常に多くのKubernetesバージョンをサポート・管理しているため、「マニフェストの変更差分などを検知することが難しい」という課題がついて回ります
  - そのため、CIで変更差分を出力するようなスクリプトを実装することで、解決しています
- また、CD([Fleet](https://fleet.rancher.io/))も併せて実装することで、活発的に開発が行えるように整備しています
- 以上のことから、Kubernetesを「利用する」のではなく、「利用してもらう」ための開発を行っており、他の人に比べ内部の実装についての知見が豊富であると自負しています

### パペルック株式会社 (2021/02 ~ 2021/08)

| 項目                | 内容    |
| :----------------- | :------ |
| プロジェクト規模 | 約 2 名  |
| 役割 | テックリード、機能検討、設計、コーディング、レビュー |
| 業務内容 | 自社の商品発注管理システムの開発・運用 |
| 使用した技術 | Google Cloud, Cloud Build, Docker, Shopify, Golang, MySQL, Redis |

- 私が入社するまでは、商品発注管理はすべて手動で行われており、その業務が他の従業の生産性を著しく低下させていました
- そのため、業務効率の向上やヒューマンエラー対策も兼ねて、システムの開発を行いました
- 開発者が私しかいなかったという点と、素早い提供を要求されたため、 Google Cloud内で完結するサービスの運用を考え、開発を勧めました
- 具体的な開発内容は以下の通りです
  - GolangでのAPI開発
    - Frameworkは使用せず、標準パッケージですべて実装
  - Google Cloud内で完結するサービスの運用
  - CloudBuild + CloudRunでのCI/CDの構築、および開発サイクルの加速化
  - 自社で使用しているECプラットフォーム（Shopify）との連携
- 上記の開発を行うことで、以前に比べ大幅に業務効率が上昇し、かつヒューマンエラーによる手戻りの時間も大幅に削減することができました

| 項目                | 内容    |
| :----------------- | :------ |
| プロジェクト規模       | 個人開発 |
| 役割 | 機能検討、設計、コーディング、クライアントとの仕様検討、および交渉 |
| 業務内容 | 中国、韓国 EC サイトと自社サービスとの連携システムの開発・運用 |
| 使用した技術 | Google Cloud, Cloud Build, Docker, Shopify, Golang, MySQL, BigQuery |

- 中国・韓国のECサイトと提携を結んでおり、それらのECサイトの商品を国内で展開するための連携システムの開発をおこなっていました
- それらの連携はGo言語を使って、以下の機能を作成しました
  - APIの作成
  - バッチ処理の作成
  - Webhookの実装
- 日々多くの商品が登録されるため、Goroutineを使用して、1日あたり2~3万件の登録・更新処理を高速におこなうことができました
- また、Goroutine内でレスポンスの整形やBigQueryへの登録を最適化に取り組んだことで、データの情報をGUIなどでも可視化できるようにして、非エンジニアでもどのような商品があるのかを確認しやすいようにしました
  - 登録結果などはSlackとのWebhook連携を導入して検知しており、エラー発生時なども早期に検知できるようにしました
- これらの経験を通じて、効率的なシステム開発と運用における実践的なスキルを磨くことができました
- この経験から柔軟な発想と問題解決能力を持ち、チームとの協力を通じて目標の達成に取り組むことができると考えています

| 項目                | 内容    |
| :----------------- | :------ |
| 役割 | 社内インフラの管理、整備 |
| 業務内容 | 社内のネットワーク管理、およびPCなどの資産管理、およびスマートロックの導入 |

- 社内のネットワーク整備がまったくされていなかったため、社内のネットワークの安定化に尽力しました
- 具体的には以下の整備を行いました
  - Wi-FiルータやLANケーブルなどの交換
  - ネットワークセキュリティの設定の堅牢化
- また、PCなどの資産管理なども杜撰であったため、管理番号の付与や初期セットアップの手順などのドキュメントを提供しました
- さらに、スマートロックの導入により社内自体のセキュリティも堅牢化しました

### 株式会社ビデオマーケット (2019/04 ~ 2021/01)

| 項目                | 内容    |
| :----------------- | :------ |
| プロジェクト規模       | 約 20 名 (内チーム: 4名) |
| 役割 | APIの機能検討・設計・コーディング・レビュー、Kubernetes環境の構築・レビュー、監視ツールの導入、CI/CDの導入 |
| 業務内容 | 配信サービス内の再生基盤のリニューアル |
| 使用した技術 | Google Cloud, Circle CI, Golang, PHP, Python, Redis |

- 動画再生の基盤としてPHPを採用していましたが、機能が増えるたびに暫定対応で耐え凌いでいた結果、異なるバージョンが複数実行されている状況でした
- そのため、既存で動いているPHPの再生基盤をGo言語へリプレイスすることにしました
- リプレイスを機に、これまで自社サーバでモノリスで管理されていたAPIたちを、Kubernetesを採用しコンテナ化とマイクロサービス化の両方を実現しました
- 当時、私はGo言語もKubernetesに関しても知識は未熟であり、一から学習をして、プロジェクト内で開発を行いました
  - 最終的には開発の主力として、全体的なリードをする形になりました
- はじめてKubernetesでの運用を試みたが、以下のような多くのエコシステムを導入し、これまでの課題を解決することができました
  - [Kustomize](https://kustomize.io/)などのマニフェスト管理ツールを用いることで、マニフェストの管理コストの削減を実現
  - サービスメッシュ（[Istio](https://istio.io/)）を活用し、マイクロサービス間のセキュアな通信を実現
  - [Grafana](https://grafana.com/), [Prometheus](https://prometheus.io/)などを用いたモニタリングの実現
  - [Locust](https://locust.io/)を用いた負荷試験の実現

## 業務外活動

### 技術関連

#### テックカンファレンスの運営 (CloudNative Days) (2021/11 - 現在)

- 日本最大級のクラウドネイティブ・テックカンファレンスに実行委員として参画しています
- これまで以下のカンファレンスにてObservabilityチームリーダーを牽引しています
  - [Observability Conference 2022 by CloudNative Days](https://event.cloudnativedays.jp/o11y2022)
  - [CloudNative Security Conference 2022 by CloudNative Days](https://event.cloudnativedays.jp/cnsec2022)
  - [CloudNative Days Tokyo 2022](https://event.cloudnativedays.jp/cndt2022)
  - [CI/CD Conference 2023 by CloudNative Days](https://event.cloudnativedays.jp/cicd2023)

#### [株式会社Relie](https://re-lie.com/) (2021/07, 2022/01 - 現在)

- 友人が起業した会社のサービス開発のバックエンド、インフラ全般をサポートしています
- また、現在では技術コーチとして社内のエンジニアの育成、および教育を行っています

| 項目                | 内容    |
| :----------------- | :------ |
| 案件名       | eSportの総合プラットフォームの開発 |
| 業務内容 | APIの設計・開発・レビュー、DBの構築、マイグレーションの自動化、インフラ環境の構築・運用・保守 |
| 使用技術 | Golang, Google Cloud (GAE, CloudSQL, BigQuery) |

| 項目                | 内容    |
| :----------------- | :------ |
| 案件名       | 技術コーチなどの社内のエンジニアリング支援 |
| 業務内容 | 技術研修の実施、プロダクトの技術的課題解決の支援、クラウド技術や、CI/CDの導入支援 |
| 使用技術 | PHP, AWS, GitHub Actions |

#### [株式会社GiGs](https://gigsinc.jp/) (2019/07 - 2019/11: 5 ヶ月)

- 友人から起業した企業のサービスの開発の一部を開発・サポートを行いました

| 項目                | 内容    |
| :----------------- | :------ |
| 案件名       | 音声プラットフォームの開発 |
| 業務内容 | 独自メディア再生プレイヤーの設計、実装、テスト |
| 使用技術 | CentOS, HTML, CSS, JavaScript |

#### [株式会社ライズアース](https://riseearth.co.jp/) (2017/10 - 2017/12: 3 ヶ月)

- 友人から紹介を受けたスタートアップ企業のLPの作成から公開、運用をすべて行いました

| 項目                | 内容    |
| :----------------- | :------ |
| 案件名       | LP サイトの作成 |
| 業務内容 | WordPress の構築・運用・保守、LP サイトの作成 |
| 使用技術 | CentOS, WordPress, PHP, JavaScript, CSS, MySQL |

### その他

#### DJ, VJとしての活動 (2019 - 現在)

- 2019年から関西でDJ活動をスタートし、2021年から`BigBaby`として都内のナイトクラブを中心に活動しています
- DJとして培った豊富な音楽知識とスキルを活用し、ジャンルにとらわれないVJスタイルで「五感を刺激する」空間を作り上げ、観客を魅了しています
- 現在は都内のクラブで活動の幅を広げています
- 各現場で海外アーティストのVJも担当しており、これから注目のVJとして評価されています

ー出演経験ー

- CLUB
  - [CÉ LA VI Tokyo](https://www.celavi.com/ja/tokyo/)（東京・渋谷）
  - [WOMB](https://www.womb.co.jp/)（東京・渋谷）
  - [Zouk Tokyo](https://www.zoukgrouptky.com/ja/)（東京・銀座）
  - [YOKOHAMA COAST garage+](https://gp.yokohama-coast.com/)
  - ZEUS Tokyo（東京・六本木）※閉店
- FESTIVAL
  - [SONIC MANIA 2023](https://www.summersonic.com/sonicmania/)（千葉・幕張メッセ）

