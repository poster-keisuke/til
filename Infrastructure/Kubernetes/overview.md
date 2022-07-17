## Kubernetesとは

[Kubernetes Overview](Infrastructure/Kubernetes/images/overview.png)

Kubernetesはコンテナのオーケストラレーションツールである

`kubectl` コマンドを使ってコンテナを操作する

## Clusterとは

マスターコンポーネントのセットでシステム全体とコンテナを管理する。
KubernetesがPod内のコンテナをスケジュールできるマシンのグループ。
クラスタ内のマシンはノードと呼ばれる。

## Pod

最小デプロイ単位で、クラスタの実行プロセスのこと。
また、1つ以上のコンテナのグループを指す。
通常一つのPodに1つのコンテナだが、複数のコンテナを持つことも可能。

各Podには固有のIPを持つ。

Pod内のコンテナはローカルホストでの通信が可能。

PodはリリースのたびにIPアドレスが変わる。

## Deployment

同じPodのレプリカのグループ。
ノードのいずれかで障害が起こったときに、対応できる。

DeploymentのPodを一般公開するには、ロードバランサー(Service)を追加して、固定IPアドレスにアクセスする。

## Service

一連のPodをグループ化して安定したエンドポイントを提供するもの。
