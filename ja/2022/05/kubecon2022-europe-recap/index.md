# KubeCon + CloudNativeCon Europe 2022 Recap for Security


先日開催された、「KubeCon + CloudNativeCon Europe 2022」でセキュリティをメインに個人的に興味をもったセッションを共有します.

<!--more-->

## KubeCon + CloudNativeCon とは？

KubeCon + CloudNativeCon は、クラウドネイティブコンピューティングに関する最大のオープンソースカンファレンスになります.

[Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) の主力のカンファレンスとして開催され、主要な OSS およびクラウドネイティブコミュニティが一同に集結して、 情報共有を行っています.

先日は、スペインのバレンシアで 5/16 - 20 の 5 日間、開催されました. (前夜祭が 2 日間、本祭が 3 日間という感じ)

## 選んだセッションの背景

- 今回は、セキュリティ関連をメインに取り上げました
  - 個人的に好きだから
  - マネージドを使っている場合、意識することも少ないが、管理している場合は意識する必要があるため

## 興味を持ったセッション

### Trampoline Pods Node to Admin PrivEsc Built Into Popular K8s Platforms

{{< youtube PGsJ4QTlKlQ >}}

- [概要](https://kccnceu2022.sched.com/event/ytlb/trampoline-pods-node-to-admin-privesc-built-into-popular-k8s-platforms-yuval-avrahami-shaul-ben-hai-palo-alto-networks?iframe=no&w=100%&sidebar=yes&bg=no)
- 発表概要
  - `Trampoline Pods` ついて
  - マネージドクラウドなどにおける、`Trampoline Pods` の調査結果の報告と、それに関する対策
  - Cilium を用いたデモ
  - `rbac-police`について

#### Trampoline Pods

- 業務に必要な特権を持つが、特権を昇格させるための跳躍台として使われる可能性のあるポッドのことを指す
  - ノードが不正を行った場合、クラスタに対して壊滅的な攻撃を行い、場合によっては完全にクラスタを乗っ取ってしまうほど強力である

#### rbac-police

- [rbac-police](https://github.com/PaloAltoNetworks/rbac-police) とは、Palo Alt Networks 社が開発しているツール
- Kubernetes クラスタ内の `ServiceAccounts`、`Pod`、`Node` の RBAC パーミッションを取得し、Rego で記述されたポリシーを使って評価する
- デフォルトで 20 個のポリシーが定義されている
  - Rego で書かれたポリシーは[こちら](https://github.com/PaloAltoNetworks/rbac-police/tree/main/lib)を見ると良い

#### 所感

- マネージドクラウドで Kubernetes を使うのまずいのか？
  - そういうわけではない
  - 今回取り上げた DaemonSet などは既に存在しない
    - いくつかのプラットフォームでは、すでに強力な DaemonSet が削除されている
    - Google はブログで、どのように対策を行っているかをまとめてくれている
      - [Privileged pod escalations in Kubernetes and GKE](https://security.googleblog.com/2022/05/privileged-pod-escalations-in.html)
- どう対策するべきなのか
  - Least-Privileged
    - `namespace/resourceNames` に対するパーミッションのスコープを設定
  - Track the powerful permissions & pods in your cluster / project
    - 要求内容を文書化
  - Isolate powerful pods from untrusted / publicly-exposed ones
    - Scheduling constraints: `Taints` & `Tolerations`, `Node Affinity`, `PodAntiAffinity`
  - Remove powerful DaemonSets
    - 特権的な機能を `non-DaemonSet`, `controlPlane` に移動
    - コアオブジェクトへの書き込み権限を最小化し、状態を `CRDs`, `ConfigMap` に格納
    - すべてを捨てるか、何も捨てないかではな
  - Restrain powerful permissions
    - OPA Gatekeeper などによる誤用の防止・検出
- 詳しい調査報告は、[こちら](https://www.paloaltonetworks.com/resources/whitepapers/kubernetes-privilege-escalation-excessive-permissions-in-popular-platforms)で確認できる

### How Attackers Use Exposed Prometheus Server to Exploit Kubernetes Clusters

{{< youtube 5cbbm_L6n7w >}}

- [概要](https://kccnceu2022.sched.com/event/ytmB/how-attackers-use-exposed-prometheus-server-to-exploit-kubernetes-clusters-david-de-torres-huerta-miguel-hernandez-sysdig?iframe=no&w=100%&sidebar=yes&bg=no)
- 発表概要
  - Kubernetes におけるフィンガープリントについて
  - Kubernetes の野放しな部分
    - Kubernetes UI
  - Prometheus の野放しな部分
    - Basic 認証の使用を許可 (推奨) しているが、デフォルトでは有効ではない点
    - オープンエンドポイントをインターネットに公開する行為
  - 実際にフィンガープリントを行うシナリオ

#### なぜ、Kubernetes のフィンガープリントを気にするのか

- ここで言うフィンガープリントとは
  - Kubernetes を使う上で存在する、様々な情報のことを指している
- 攻撃をするにも、まずは侵入したいターゲットについて、できる限り多くの情報を収集する
  - クラスタ内のバージョン情報
    - CVE や脆弱性に対応することができ、それを利用することで悪用可能
  - アプリケーション、ツール、アーキテクチャに関する情報
    - 競合他社に利用可能

#### 所感

- 以下のことは大前提
  - [Kubernetes security best practices](https://sysdig.com/learn-cloud-native/kubernetes-security/kubernetes-security-101/)に従おう
  - Prometheus を使用してすべてを監視しようね
- Prometheus はメトリクスを収集するツールだけではないということを再認識
  - Prometheus は多彩なメトリクスを取得することができるということを理解しておく必要がある
  - 使う人間が攻撃者の場合、Prometheus を使いそれぞれのケースに応じたテクニックを駆使する
- 新たな脆弱性とは、常に戦い続けなければならない
  - また、インサイダーに対する対策も必要

### Securing Kubernetes Applications by Crafting Custom Seccomp Profiles

{{< youtube alx38YdvvzA >}}

- [概要](https://kccnceu2022.sched.com/event/ytml/securing-kubernetes-applications-by-crafting-custom-seccomp-profiles-sascha-grunert-red-hat?iframe=no&w=100%&sidebar=yes&bg=no)
- 発表概要
  - Kubernetes における `seccomp` についての簡単な歴史
  - 手作業でカスタム `seccomp` プロファイルを作成する
  - 手動で行っていた作業を自動化する
  - デフォルトでより安全な Kubernetes の明るい未来

#### seccomp とは

- `secure computing mode` の略
- Linux カーネル上でアプリケーションのサンドボックスメカニズムを提供するためのセキュアコンピューティングの機能
  - 許可されたシステムコールのリストを制限することにより、アプリケーションのセキュリティを向上させることが可能
  - システムコールルールにヒットした場合のさまざまなアクションをサポート
- Kubernetes にはかなり前に追加されている
  - `containerd`,`CRI-O`, `docker (shim)` のようなコンテナランタイムによって選択されるデフォルトプロファイルをサポート
- seccomp に関する参考資料
  - [コンテナセキュリティにおける権限制御 〜Seccomp とかよくわからんけどとりあえずこれくらいはやっておこう〜](https://speakerdeck.com/mochizuki875/container-seccomp)
  - [seccomp について学ぼう](https://w-tl00.hatenablog.com/entry/2019/12/19/221815)

#### 所感

- SeccompDefault を、Kubernetes `v1.25.0` でベータ版を卒業させたい熱量を感じた
  - `v1.24.0` のベータ版機能はデフォルトではもう有効になっていないため
    - これに関しては、公式の[ブログ](https://kubernetes.io/blog/2022/05/16/volume-populators-beta/)を参照
  - この機能を安定版へ移行することで、Kubernetes のセキュリティが向上する
- 手動で生成する手順などはやったことがないから、個人的にはいい勉強だった

## その他のセッション

### Secure Multi User HPC Jobs in Kubernetes with Kyverno

{{< youtube MpbxRL8XPJ8 >}}

- [概要](https://kccnceu2022.sched.com/event/ytws/lightning-talk-secure-multi-user-hpc-jobs-in-kubernetes-with-kyverno-trey-dockendorf-ohio-supercomputer-center?iframe=no)

#### Kyverno とは

- [Kyverno](https://kyverno.io/) は、ポリシーエンジンの一種
- OpenPolicyAgent との違い
  - Rego のような特別な言語を用いずにポリシーを定義できる
    - YAML での定義
    - Kubernetes ネイティブなツールといえる

