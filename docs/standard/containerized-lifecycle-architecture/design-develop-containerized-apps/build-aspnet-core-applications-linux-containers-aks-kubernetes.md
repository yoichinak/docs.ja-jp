---
title: Linux コンテナーと AKS/Kubernetes クラスターにデプロイされた ASP.NET Core 2.1 アプリケーションを構築します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052756"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>AKS/Kubernetes オーケストレーターに Linux コンテナーとして展開されている ASP.NET Core 2.1 アプリケーションを構築します。

Azure Kubernetes サービス (AKS) は、Azure の管理された Kubernetes オーケストレーション サービスをコンテナーのデプロイと管理を簡略化します。

AKS の主な機能は次のとおりです。

- Azure でホストされるコントロール プレーンは、
- 自動アップグレード
- 自己復旧機能
- ユーザー構成可能なスケーリング
- 開発者とクラスター オペレーターの両方に簡単なユーザー エクスペリエンス。

次の例では、Linux で実行され、開発が完了、Azure では、AKS クラスターを展開する ASP.NET Core 2.1 アプリケーションの作成を探索する Visual Studio 2017 を使用します。

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>Visual Studio 2017 を使用して ASP.NET Core 2.1 のプロジェクトの作成

ASP.NET Core は、Microsoft と GitHub の .NET コミュニティによって管理される汎用的な開発プラットフォームです。 クロスプラット フォーム、Windows、macOS および Linux をサポートしていると、デバイス、クラウド、および埋め込み/iot のシナリオで使用できます。

この例では、サンプルを作成する追加に関する知識は不要であるため、Visual Studio の Web API テンプレートに基づいている単純なプロジェクトを使用します。 のみ、ASP.NET Core 2.1 のテクノロジを使用して、REST API を使用した小規模なプロジェクトを実行するすべての要素を含む標準のテンプレートを使用してプロジェクトを作成する必要があるとします。

![ASP.NET Core Web アプリケーションを選択すると、Visual Studio で新しいプロジェクト ウィンドウを追加します。](media/create-aspnet-core-application.png)

**図 4 ~ 36**します。 ASP.NET Core アプリケーションを作成します。

Visual Studio でサンプル プロジェクトを作成するには、選択**ファイル** > **新規** > **プロジェクト**を選択、 **Web**プロジェクトの後に、左側のウィンドウで種類**ASP.NET Core Web アプリケーション**します。

Visual Studio には、web プロジェクト用のテンプレートが一覧表示します。 たとえば、次のように選択します。 **API** ASP.NET Web API アプリケーションを作成します。

ASP.NET Core 2.1 をフレームワークとして選択したことを確認します。 .NET core 2.1 Visual Studio 2017 の最新バージョンに含まれるとは自動的にインストールして構成する Visual Studio 2017 をインストールするときにします。

![API オプションを選択して、ASP.NET Core Web アプリケーションの種類を選択するための visual Studio のダイアログ。](media/create-web-api-application.png)

**図 4-37**します。 ASP.NET CORE 2.1 を選択し、Web API プロジェクトの種類

以前のバージョンの .NET Core を使っている場合は、ダウンロードしてからバージョン 2.1 のインストール<https://www.microsoft.com/net/download/core#/sdk>します。

Docker サポートを追加するには、プロジェクトの作成時またはその後、ようにすることができます「docker 化」、プロジェクト、いつでもできます。 プロジェクトの作成後に、Docker サポートを追加するには、ソリューション エクスプ ローラーでプロジェクト ノードを右クリックして**追加** > **Docker サポート**コンテキスト メニュー。

![既存のプロジェクトに Docker サポートを追加するコンテキスト メニュー オプション:(プロジェクト) を右クリックして > 追加 > Docker のサポート。](media/add-docker-support-to-project.png)

**図 4-38**します。 既存のプロジェクトに Docker サポートの追加

Docker のサポートを追加を完了するには、Windows または Linux を選択できます。 この場合は、選択**Linux**AKS は (2018 年末) としての Windows コンテナーをサポートしないためです。

![Dockerfile のターゲット OS を選択するオプションのダイアログ。](media/select-linux-docker-support.png)

**図 4-39**します。 Linux コンテナーを選択します。

簡単な手順では、Linux コンテナーで実行されている ASP.NET Core 2.1 アプリケーションがあります。

ご覧のように、Visual Studio 2017 と Docker の統合は完全に達成するため、開発者の生産性です。

使用してアプリケーションを実行するようになりました、 **F5**キーまたはを使用して、**再生**ボタンをクリックします。

使用してイメージを一覧表示、プロジェクトを実行した後、`docker images`コマンド。 表示する必要があります、`mssampleapplication`イメージは、プロジェクトを Visual Studio 2017 での自動配置によって作成します。

```console
docker images
```

![Docker images コマンドをからの出力をコンソールには、一覧が表示されます。リポジトリ、タグ、イメージ ID、作成済み (日)、およびサイズ。](media/docker-images-command.png)

**図 4-40**します。 Docker イメージの表示

## <a name="register-the-solution-in-the-azure-container-registry"></a>Azure Container registry のソリューションを登録します。

このような任意の Docker レジストリにイメージをアップロード[Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/)または Docker Hub、イメージは、そのレジストリから AKS クラスターにデプロイできるようにします。 ここでは、Azure Container Registry にイメージをアップロードしています。

### <a name="create-the-image-in-release-mode"></a>リリース モードでイメージを作成します。

今すぐにイメージを作成します**リリース**モード (実稼働の準備) を変更することで**リリース**図 4-41、およびアプリケーションを実行する前に行ったように示すようにします。

![VS でオプションをリリース モードでビルドするツールバーです。](media/select-release-mode.png)

**図 4-41**します。 リリース モードを選択します。

実行する場合、`docker image`コマンドを作成するには、1 つの両方のイメージが表示されます`debug`およびその他の`release`モード。

### <a name="create-a-new-tag-for-the-image"></a>イメージの新しいタグを作成します。

各コンテナー イメージをタグが付けられる必要があります、`loginServer`レジストリの名前。 このタグは、ルーティング、イメージ レジストリにコンテナー イメージをプッシュするときに使用されます。

表示することができます、 `loginServer` Azure Container Registry からの情報を受け取り、Azure portal から名前

![右上の Azure コンテナー レジストリ名のブラウザー ビュー。](media/loginServer-name.png)

**図 4-42**します。 レジストリの名前のビュー

または、次のコマンドを実行します。

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![上記のコマンドから出力コンソール。](media/az-cli-loginServer-name.png)

**図 4-43**します。 PowerShell を使用して、レジストリの名前を取得します。

どちらの場合は、名前を取得します。 この例では`mssampleacr.azurecr.io`します。

ようになりましたことができますタグを付けること、イメージを最新のイメージ (リリース イメージ) の場合は、コマンドを使用。

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

実行後、`docker tag`コマンドでのイメージを一覧表示、`docker images`コマンドを新しいタグを持つイメージが表示されます。

![Docker イメージのコマンドからの出力をコンソール。](media/tagged-docker-images-list.png)

**図 4-44**します。 タグが付けられたイメージの表示

### <a name="push-the-image-into-the-azure-acr"></a>Azure の ACR にイメージをプッシュします。

次のコマンドを使用して、Azure の ACR にイメージをプッシュします。

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

このコマンドがかかるイメージのアップロード プロセスでフィードバックが用意されています。

![Docker push コマンドからの出力をコンソール: 各レイヤーの文字ベースの進行状況バーが表示されます。](media/uploading-image-to-acr.png)

**図 4-45**します。 ACR にイメージをアップロードします。

後述する結果が完了すると、プロセスを取得する必要があります。

![完了したら、すべてのレイヤーまたはノードを示す docker push コマンドから出力コンソール。](media/uploading-docker-images-complete.png)

**図 4-46**します。 ノードのビュー

次の手順では、AKS の Kubernetes クラスターにコンテナーをデプロイします。 そのためには、ファイルが必要です。 (**.yml ファイルをデプロイする**)、次を含みます。

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Kubernetes を使用した展開の詳細については、次を参照してください。 <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

これで、使用してデプロイする準備はほとんど**Kubectl**、まず、このコマンドを使用して AKS クラスターに資格情報を取得する必要がありますが。

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![上記のコマンドから出力コンソール:現在のコンテキストで/root/.kube/config としてマージ"MSSampleK8Cluster](media/getting-aks-credentials.png)

**図 4-47**します。 資格情報を取得します。

次に、使用、`kubectl create`展開を起動するコマンド。

```console
kubectl create -f mssample-deploy.yml
```

![上記のコマンドからの出力をコンソール: 展開"mssamplesbook"を作成します。 サービス「mssample kub-アプリ」を作成します。](media/kubectl-create-command.png)

**図 4-48**します。 Kubernetes へのデプロイします。

デプロイが完了したら、次のコマンドで一時的にアクセスできるローカル プロキシを使用した Kubernetes コンソールにアクセスできます。

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

Url にアクセスして`http://127.0.0.1:8001`します。

![展開、ポッド、レプリカ セット、およびサービスを表示、Kubernetes ダッシュ ボードのブラウザー ビュー。](media/kubernetes-cluster-information.png)

**図 4 ~ 49**します。 Kubernetes クラスターの情報を表示します。

Linux コンテナーと AKS の Kubernetes クラスターを使用して Azure にデプロイされたアプリケーションをする必要があります。 Azure portal から取得できるサービスのパブリック IP を参照するアプリにアクセスできます。

> [!NOTE]
> セクションでこのサンプルの AKS クラスターを作成する方法を確認できます[ **Deploy Azure Kubernetes Service (AKS) を**](deploy-azure-kubernetes-service.md)このガイドにします。

>[!div class="step-by-step"]
>[前へ](set-up-windows-containers-with-powershell.md)
>[次へ](../docker-devops-workflow/index.md)
