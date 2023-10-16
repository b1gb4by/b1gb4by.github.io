# Kubernetes初学者ロードマップ


Kubernetesをはじめて学ぶ方に向けて、ロードマップを作成してみました。

これから学んでいく第一歩として、参考にしていただければと思います。
<!--more-->

## はじめに

本ページは、筆者がまったくの知見のない初学者がKubernetesを学習し、利用していく上で必要な知識やスキルの習得方法を示したものです。

そのため、本ページでは概要や用語の説明などは行いません。

また、本ページの指針をすべて達成することでKubernetesのすべてを網羅し、**完全に理解**できる訳ではありません。

必要な知識が必要な場合は個人で別途で調査、理解をする必要があることをあらかじめ、ご了承ください。

## そもそも Kubernetes とは？

![k8s-logo](k8s-logo.webp)

### Kubernetes の読み方

Kubernetesは、**クバネティス**、**クバネテス**、**クーべネティス**と呼び方はさまざまありますが、読み方は人それぞれです。

また、`K8s`と略されることもあります。

{{< admonition question "Kubernetesの読み方について" true>}}
**Kubernetes**（希: `κυβερνήτης`, `koo-ber-nay'-tace`, クベルネテス）は、ギリシャ語で**航海長**または**水先案内人**を意味し、サイバネティクス（人工頭脳学）の語源でもある

引用: <https://ja.wikipedia.org/wiki/Kubernetes>
{{< /admonition >}}

### 何をしているの？

Kubernetesは、コンテナをデプロイできる基盤となるソフトウェアであり、コンテナオーケストレーターの1つです。

もともとはGoogleのコンテナ盤である[**Borg**](https://research.google/pubs/pub49065/)をベースにしたOSSであり、2014年6月にローンチされました。

現在は [**Cloud Native Computing Foundation (CNCF)**](https://www.cncf.io/) によって管理されているGA Projectの1つです。

{{< admonition question "CNCFとは？" false>}}
**CNCF**は、Cloud Nativeなシステムを推進するために2015年に創設されたLinux Foundation傘下の非営利団体の1つです。
{{< /admonition >}}

## 学習ロードマップ

本題の学習のロードマップについてですが、個人的には以下の通りに学習を進めて行くのが良いと考えています。

![k8s-loadmap](loadmap.drawio.png)

### Step1. コンテナの基礎理解

Kubernetesを理解する上で、非常に密な関係性にあるのが**コンテナ**です。

まずは、コンテナについて理解を深めることが最重要になります。コンテナを理解している場合は、このステップはスキップしても良いでしょう。

理解がないままKubernetesを理解を深めること困難です。まずは、コンテナの理解を深めしょう。

コンテナと言っても、コンテナを動かすエンジンは複数種類あるので、まずは`Docker`に焦点をあてて、学習を進めて行きます。

#### Step1 を学ぶポイント

- コンテナとは何なのか？
- コンテナと仮想化の違いは？
- Dockerfileの記述方法
- Dockerの操作方法
  - イメージのビルド
  - イメージのプッシュ
  - コンテナの起動

### Step2. Kubernetes の基礎理解

コンテナの基礎を理解した後は、Kubernetesの基礎を理解しましょう。

Kubernetesを動かす前にまずは知識としてインプットしていくのが良いでしょう。

#### Step2 を学ぶポイント

- Kubernetesで実現できること
  - また、それがなぜ必要とされているのか
  - Kubernetesを使うメリット
- APIリソース群の理解
- `kubectl` の使用方法

### Step3. Kubernetes の利用

コンテナやKubernetesの基礎的な部分を理解した後は、実際にKubernetesを触ってみましょう。

実際にKubernetesを動かして、体系的に学ぶようにすることで理解を深めていきます。

Step1, Step2でインプットした知識を、きちんとアウトプットしていくことで**ラーニングサイクル**を回すようにしましょう。

#### Step3 を学ぶポイント

- Kubernetesの一連の動作を試してみる
  - クラスターの作成
  - アプリケーションの操作（`kubectl`での操作）
    - デプロイ
    - 探索
    - 公開
    - スケーリング
    - アップデート

### Step4. エコシステムの利用

Kubernetesには多くのエコシステムが提供されています。

エコシステムを活用することで、Kubernetesはより真価を発揮します。

また、本番環境などで運用する際、CI/CDや監視、ログ収集、セキュリティなど考慮する点が多く存在します。

エコシステムを利用することで、それらの課題を解決できます。

{{< admonition question "エコシステムとは？" true>}}
元々は生態系の用語であり、あるエリア（地域や空間など）の生命体が互いに依存しながら生態を維持する関係の様子を表します。 ここでは、Kubernetesを支えるツール群のことを指しています。
{{< /admonition >}}

#### Step4 を学ぶポイント

- Kubernetesを運用する上でどのような点を考慮する必要があるのか
- どのようなエコシステムがあるのか

### Step5. 内部ツールの理解・実装

しかし、実際にマネージドクラウド（AWS, Google Cloud, Azureなど）で運用する場合、あまり気にする必要はありません。

個人でKubernetesのコントローラーなどを開発していきたい方はStep5に挑戦してみましょう。

なお、Kubernetes関連の周辺ツールは、Go言語で書かれている事が多いです。

Go言語をはじめて触る方は、後日記載予定の「Go言語学習ロードマップ」をご覧いただければと思います。

#### Step5 を学ぶポイント

- カスタムコントローラーの基礎の理解
- 公開されているカスタムコントローラー群の理解
- カスタムコントローラーの実装、動作検証

## オススメの書籍、文献など

ここでは、ロードマップにそって学習を行う上で著者自身がお薦めする書籍や、文献などを紹介します

### 書籍

- [仕組みと使い方がわかるDocker＆Kubernetesのきほんのきほん](https://amzn.asia/d/gnG5rrm)
  - 対象
    - Step1, Step2
  - コンテナにはじめて触れる方やバックエンドの技術に詳しくない方でもLinuxの知識や、サーバの基礎なども併せて記載されているため読みやすいです
  - イラストも多く、視覚的に知識をインプットできます
- [Docker コンテナ開発・環境構築の基本](https://amzn.asia/d/bfLkWr2)
  - 対象
    - Step1, Step2
  - コンテナを体系的に学ぶことができます
  - コンテナを用いたCI/CD、アプリケーションの運用方法も基本から記載されています
- [イラストでわかるDockerとKubernetes](https://amzn.asia/d/4yGWPsU)
  - 対象
    - Step1, Step2
  - DockerやKubernetesの知識を有していない場合はまずこれを読んだほうがイメージはつかみやすいかと思います
    - 概要がメインなので、サラッと読むには良いと思います
- [Kubernetes完全ガイド（第2版）](https://amzn.asia/d/08N3hn5)
  - 対象
    - Step2, Step3
  - 一番時初めにこの書籍から読み始めるのは少し難易度が高いため、上記の書籍を読んでから読むと良いです
  - Kubernetesに関する知識が網羅的にまとめられています
  - Kubernetesを使用していて、困った時にリファレンスとしても活用できます
- [Kubernetes CI/CD パイプラインの実装](https://amzn.asia/d/7JkcyEf)
  - 対象
    - Step4
  - 題名の通り、CI/CDのパイプラインを構築について詳細に記されている
- [Docker/Kubernetes 開発・運用のためのセキュリティ実践ガイド](https://amzn.asia/d/36ET8Vt)
  - 対象
    - Step3, Step4
  - DockerやKubernetesの知識はある程度有していないと読むのは難しいと思います
  - Kubernetes上での開発、運用視点からのセキュリティ対策についてまとめられていています
- [Kubernetesの知識地図 —— 現場での基礎から本番運用まで](https://amzn.asia/d/36oRtHP)
  - 対象
    - Step3, Step4
  - Kubernetesの基礎から本番運用のベストプラクティスまで、押さえておきたい情報源を第一線のエンジニアが厳選してくれています
  - 進化を続けるKubernetesと幅広いエコシステムについての知識をこの一冊で身につけられます
- [実践入門 Kubernetes カスタムコントローラーへの道](https://amzn.asia/d/9fHk2VU)
  - 対象
    - Step5
  - Kubernetesで拡張機能（カスタムコントローラー）を開発する入門です
  - Kubernetesを利用するだけの方はあまり作成しないかもしれないですが、Kubernetesに拡張機能を追加したい方は読んでみると良いと思います
- [Kubernetes ネットワーク 徹底解説](https://zenn.dev/taisho6339/books/fc6facfb640d242dc7ec)
  - 対象
    - Step5
  - Kubernetesのネットワークの実現方法について説明されています
  - TCP/IPは知っているが、Kubernetesのネットワークの実現方法は知らない人向けに、噛み砕いて体系的に説明してくれています

### e-Learning

#### Katacoda

- [Katakoda](https://www.katacoda.com/)は、ブラウザ環境で学習が行えるプラットフォームです
- コンテナ周辺の技術などのトレーニングが公開されており、すべてブラウザ環境でコマンド、ターミナル環境が提供されているため、環境構築などの手間などなく学習を行うことができます

#### Kubernetes 学習とトレーニング (Microsoft)

- Microsoft社が提供している、トレーニングになります
- 動画ベースで各項目を説明しており、Kubernetes基本を理解すると共に、さまざまなKubernetesの機能などについても解説してくれています
- トレーニングは、[こちら](https://azure.microsoft.com/ja-jp/resources/kubernetes-learning-and-training/#overview)から受講できます

#### つくって学ぶ Kubebuilder

- [@zoetrope](https://github.com/zoetrope?tab=repositories)さんによって提供されている学習コンテンツになります
- Kubebuilderと呼ばれるフレームワークを使用して、Kubernetesを拡張するためのカスタムコントローラー/オペレーターを開発するため方法を解説されています
- Step5に進まれた方は、この記事を読んでカスタムコントローラー/オペレーターの開発手法を理解すると良いと思います

## その他

### 情報収集

Kubernetesの情報を収集する際には基本的には以下を使用しています

- [Kubernetes Official](https://kubernetes.io/)
  - [Document](https://kubernetes.io/docs/home/)
  - [Reference](https://kubernetes.io/docs/reference/)
  - [Blog](https://kubernetes.io/blog/)
- [GitHub](https://github.com/kubernetes)
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes)
- News
  - [KubeWeekly](https://us10.campaign-archive.com/home/?u=3885586f8f1175194017967d6&id=11c1b8bcb2)
  - [Kubernetes Podcast](https://kubernetespodcast.com/)
  - [Kubernetes on Medium](https://medium.com/tag/kubernetes/latest)

### コミュニティの参加

#### Kubernetes Slack

- KubernetesのSlackになります（Joinは[こちら](http://slack.k8s.io/)からできます）
  - すでにJoin済みの場合は、[こちら](https://kubernetes.slack.com/)からサインインできます
- はじめて参加する方は以下のチャンネルに参加すると良いと思います。
  - `#jp-users`
  - `#jp-events`
  - `#jp-dev`
  - `#jp-mentoring`
  - `#jp-users-novice`
  - `#kubernetes-doc-ja`
- 初学者の方で質問などを行いたい場合は、`jp-users-novice`で聞いてみると良いでしょう

### 勉強会など

#### [Kubernetes Meetup Tokyo](https://k8sjp.connpass.com/)

- 国内では最大のKubernetesの勉強会になります
- 過去の勉強会の動画は[こちら](https://www.youtube.com/c/KubernetesMeetupTokyo)から見ることができます

#### [Kubernetes Meetup Novice](https://k8s-novice-jp.connpass.com/)

- 「まだ、学び始めたばっかりだけど発表してみたい」という方向けの勉強会になります
- 過去の勉強会の動画は[こちら](https://www.youtube.com/channel/UC4EPkXFGaMA_BZ0N6unnQIAz)から見ることができます

#### [Kubernetes 変更内容共有会](https://kubernetes-updates.connpass.com/)

- Kubernetesのバージョンアップごとの変更内容で重要な部分や、興味深いポイントを紹介してくれる勉強会になります
- Kubernetesのバージョンに追従してくためにこちらの勉強会を活用してみても良いと思います
- 過去の勉強会の動画は[こちら](https://www.youtube.com/channel/UC9bxCiEy9Nocy5UQHfG_6Yw)から見ることができます

#### Kubernetes Internal

- Kubernetesをより深く掘り下げ、その他の周辺ツールなどの実装や設計などについて情報交換、交流をするための勉強会です
- 現在は、「kubenews」が毎週開催されています
- 過去の勉強会の動画は[こちら](https://www.youtube.com/channel/UCpkd51NdxThtTSR3L6T83fw)から見ることができます

#### [OCHa(Oracle Cloud Hangout cafe) Cafe](https://ochacafe.connpass.com/)

- Kubernetes以外にクラウドネイティブな技術全般について発信しています
- 過去の勉強会の動画は[こちら](https://www.youtube.com/c/JapanOracleDevelopers)から見ることができます

#### [KubeConn + CloudNativeConn](https://www.cncf.io/kubecon-cloudnativecon-events/)

- KubeCon + CloudNativeConは、Cloud Native Computing Foundation (CNCF) の主力カンファレンスカンファレンスとして開催されています
- Kubernetesのみならず、クラウドネイティブに関するコミュニティが一同に集結し、クラウドネイティブな技術の教育と進歩を推進しています

#### [Cloud Native Days](https://cloudnativedays.connpass.com/)

- 日本最大級のクラウドネイティブ・テックカンファレンスを開催しています
- 過去のカンファレンスの動画は[こちら](https://www.youtube.com/channel/UCMBw1Z3fmhe-2l-iq2p4rNw)から見ることができます

### 資格

Kubernetesでは、Linux FoundationとCloud Native Computing Foundation (CNCF) が行っている試験が一番有名だと思います

#### [CKA (Certified Kubernetes Administrator)](https://training.linuxfoundation.org/ja/certification/certified-kubernetes-administrator-cka/)

- Kubernetesの基本的な機能に加え、基盤自体の運用方法やトラブルシュートなどの理解が求められます
- Kubernetesの基盤開発者向けの試験になります

#### [CKAD (Certified Kubernetes Application Developer)](https://training.linuxfoundation.org/ja/certification/certified-kubernetes-application-developer-ckad/)

- CKAと比べ、アプリケーション開発者向けの試験になります
- Kubernetesの基本的な機能に加え、Kubernetesをアプリをデプロイ・運用する基盤として十分に利用できるスキルがあるかが求められます

#### [CKS (Certified Kubernetes Security Specialist)](https://training.linuxfoundation.org/ja/certification/certified-kubernetes-security-specialist/)

- CKAの試験をさらにセキュリティに焦点を当てた試験となります

{{< admonition warning "CKAを受けるための注意点" true>}}
この試験を受けるには、事前にCKAに合格している必要があります。
{{< /admonition >}}

#### [KCNA (Kubernetes and Cloud Native Associate)](https://training.linuxfoundation.org/ja/certification/kubernetes-and-cloud-native-associate-kcna-jp/)

- Kubernetesと広範なクラウド ネイティブ エコシステムのエントリー レベルの知識とスキルをテストになります
- このテストでは以下のような知識が問われます
  - 基本的な`kubectl`コマンドを使用してアプリケーションをデプロイする方法
  - Kubernetesのアーキテクチャ（コンテナ、ポッド、ノード、クラスター）
  - クラウドネイティブランドスケープやプロジェクトの理解（ストレージ、ネットワーク、GitOps、サービスメッシュ）
  - クラウドネイティブセキュリティの原則の理解など

## まとめ

- 今回は、Kubernetesの学習ロードマップを考えてまとめてみました
- 筆者自身もKubernetesを触り始めてまだ日が浅いため、上記のものを参考に日々精進しています
- これをきっかけに一人でも多くの方がKubernetesに興味をもっていただけることを切に願います

