---
title: Docker の概要
description: この記事では、.NET Core アプリケーションのコンテキストでの Docker の基本と概要について説明します。
ms.date: 11/06/2017
ms.custom: mvc, seodec18
ms.openlocfilehash: b2640a1cea4d77158b7d9ed6ec63cf36d9e1f9cd
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676279"
---
# <a name="introduction-to-net-and-docker"></a>.NET および Docker の概要

この記事では、Docker 上での .NET の使用に関する概要と概念的な基礎について説明します。

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker:アプリをパッケージ化して任意の場所で配置および実行する

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) はオープンなプラットフォームであり、開発者や管理者は[イメージ](https://docs.docker.com/glossary/?term=image)のビルド、配布、および分散アプリケーションの実行を[コンテナー](https://www.docker.com/what-container)という大まかに分けられた環境で行えます。 この手法を使用すると、開発、QA、運用環境の間でアプリケーションのライフ サイクルを効率的に管理できます。
 
[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)は [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)を使用し、アプリを [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 形式で記述されているファイルを用いて作成された [Docker イメージ](https://docs.docker.com/glossary/?term=image)として速やかにビルドしパッケージ化したうえで、[階層型コンテナー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)に配置して実行します。

独自の[階層型イメージ](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)を Dockerfile として作成することも、または[レジストリ](https://docs.docker.com/glossary/?term=registry)から [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) などの既存のものを使用することもできます。

[Docker コンテナー、イメージ、およびレジストリの相互の関係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)は、[コンテナー化されたアプリケーションやマイクロサービスの設計および構築](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)を行う際に重要となる概念です。 この手法を用いると開発および配置にかかる時間を大幅に短縮できます。

### <a name="further-reading-and-watching"></a>さらに詳しく読む (視聴する)

* [Windows ベースのコンテナー:エンタープライズ レベルの制御が可能な最新のアプリ開発。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Docker の概要](https://docs.docker.com/engine/docker-overview/)
* [Windows コンテナー上の Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Dockerfile を記述するためのベスト プラクティス](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [.NET Core アプリケーション用の Docker イメージのビルド](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>.NET Docker イメージを入手する

公式の .NET Docker イメージは Microsoft により作成および最適化されており、 Docker Hub の Microsoft リポジトリで一般公開されています。 各リポジトリには .NET のバージョンや OS のバージョンによって複数のイメージがあります。 イメージ リポジトリの多くではさまざまなタグを利用できるため、フレームワークのバージョンと OS (Linux ディストリビューションや Windows のバージョン) 両方を指定して選択できます。

## <a name="scenario-based-guidance"></a>シナリオ ベースのガイダンス

Microsoft は .NET リポジトリをきめ細かく焦点を合わせたものにしたいと考えています。これは特定のシナリオやワークロードのことを示しています。

`microsoft/aspnetcore` イメージは Docker 上の ASP.NET Core アプリに最適化されているため、コンテナーを迅速に起動できます。

.NET Core イメージ (`microsoft/dotnet`) は .NET Core をベースとしたコンソール アプリ向けです。 たとえば、バッチ プロセスや Azure WebJobs、その他のコンソールのシナリオなどでは最適化された .NET Core イメージを使用する必要があります。

Docker と .NET アプリケーションを使用する水平方向のシナリオとして最もわかりやすいのは、運用環境のデプロイとホスティングのシナリオです。 運用はシナリオのひとつに過ぎません。それ以外のシナリオも同じように有用です。 これらのシナリオは .NET に固有のものではなく、多くの開発者プラットフォームに当てはまると思われます。

* **摩擦の少ないインストール** - .NET をローカルにインストールせずに試せます。 .NET が組み込まれた Docker イメージをダウンロードするだけです。

* **コンテナーでの開発** - 一貫性のある環境で開発し、開発環境と運用環境を近づけることができます (開発者マシン上のグローバルな状態などの問題を回避できます)。 Visual Studio Tools for Docker を使用すると、Visual Studio から直接コンテナーを起動することもできます。

* **コンテナーでのテスト** - コンテナーでテストを行い、環境の構成が正しくなかったり、前回のテストからの変更が適用されていなかったりすることなどに起因するエラーを減らせます。

* **コンテナーでのビルド** - コンテナーでコードをビルドすることで、共有のビルド マシンを複数の環境用に正しく構成する必要がなくなり、その代わりとして "BYOC" (独自のコンテナーを使用) の手法に移行できます。

* **あらゆる環境で配置** - お使いのあらゆる環境からイメージを配置できます。 この手法によって、通常は外部の構成 (たとえば、挿入された環境変数など) を利用するイメージの動作が変わり、構成の違いに起因するエラーが減ります。

Docker コンテナー開発に .NET Core と .NET Framework のどちらを使用するかを判断するための一般的なガイダンスは[こちら](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)です。

### <a name="common-docker-development-scenarios"></a>Docker 開発の一般的なシナリオ

#### <a name="net-core"></a>.NET Core

**.NET Core リソース**

 関心のあるシナリオに合わせて .NET Core のサンプルを選択します。 すべてのサンプルの手順で、Windows、Linux、または macOS のホストから Windows または Linux の Docker イメージをターゲットにする方法について説明しています。

サンプルでは .NET Core 2.0 を使用しています。 Docker の[マルチ ステージ ビルド](https://github.com/dotnet/announcements/issues/18)と[マルチ アーキテクチャ タグ](https://github.com/dotnet/announcements/issues/14)が (適切な場合には) 使用されています。

* [Docker Hub 上の .NET Core イメージ](https://hub.docker.com/r/microsoft/dotnet/)

* [.NET Core アプリケーションを Docker で動作させる](https://docs.docker.com/engine/examples/dotnetcore/)

* この .NET Core の Docker サンプルでは、[.NET Core の開発プロセスにおいて Docker を使用する](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)方法を示します。 このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。

* この .NET Core の Docker サンプルでは、[運用環境用の .NET Core アプリの Docker イメージをビルドする](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)方法に関するベスト プラクティス パターンを示します。 このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。

* この [.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)では、[自己完結型の .NET Core アプリケーション](../deploying/index.md)用の Docker イメージをビルドするためのベスト プラクティス パターンを示します。 [コンテナー間で基本イメージを共有する](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)利点を得られないような、運用向けの最小コンテナーで使用します。 ただし Docker の下位レイヤーは共有可能です。

#### <a name="arm32--raspberry-pi"></a>ARM32/Raspberry Pi

* [.NET Core ランタイム ARM32 ビルドに関する告知](https://github.com/dotnet/announcements/issues/29)

* [Docker Hub の ARM32/Raspberry Pi 用 .NET Core イメージ](https://hub.docker.com/r/microsoft/dotnet/)

* [GitHub の ARM32/Raspberry Pi 用 .NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [DockerHub の .NET Framework イメージ](https://hub.docker.com/r/microsoft/dotnet-framework/)

このリポジトリには、.NET Framework のさまざまな Docker 構成を示すサンプルが保存されています。 これらのイメージを独自の Docker イメージのベースとして使用できます。

**.NET Framework 4.7**

[dotnet-framework: 4.7 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)では、[.NET Framework 4.7](../../framework/whats-new/index.md#v47) の使用方法について基礎的な "hello world" で説明します。 [.NET Framework 4.7 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile)に依存するアプリを構築して配置する方法を示します。

**.NET Framework 4.6.2**

[dotnet-framework: 4.6.2 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)では、[.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) の使用方法について基礎的な "hello world" で説明します。 [.NET Framework 4.6.2 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile)に依存するアプリを構築して配置する方法を示します。

**.NET Framework 3.5**

 [dotnet-framework:3.5 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)では、[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile) の使用方法について基礎的な "hello world" で説明します。 Docker で .NET Framework 3.5 に依存するプロジェクトを構築して配置する方法を示します。

#### <a name="aspnet-core"></a>ASP.NET Core

* [この ASP.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)は、運用向けの ASP.NET Core アプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。 このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。

* [DockerHub の ASP.NET Core イメージ](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [GitHub の ASP.NET Core イメージ](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET フレームワーク

* [DockerHub の ASP.NET フレームワーク イメージ](https://hub.docker.com/r/microsoft/aspnet/)

* [.NET Framework 4.6.2 の ASP.NET Web フォーム アプリケーションのサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [DockerHub の Windows Communication Framework (WCF) イメージ](https://hub.docker.com/r/microsoft/wcf/)

* [GitHub の Windows Communication Framework (WCF) イメージ](https://github.com/microsoft/wcf-docker)

* [完全な .NET Framework 4.6.2 を使用する Windows Communication Framework (WCF) の Docker サンプル](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>インターネット インフォメーション サーバー (IIS)

* [DockerHub のインターネット インフォメーション サーバー (IIS) イメージ](https://hub.docker.com/r/microsoft/iis/)

* [GitHub のインターネット インフォメーション サーバー (IIS) イメージ](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>その他の Microsoft スタック コンテナー イメージを操作する

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Docker クイック スタートで Linux 2017 用 Microsoft SQL Server コンテナー イメージを実行する](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [DockerHub の Linux 用 Microsoft SQL Server イメージ](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [DockerHub のWindows コンテナー用 Microsoft SQL Server Express Edition イメージ](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [DockerHub の Windows コンテナー用 Microsoft SQL Server Developer Edition イメージ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="azure-devops-services-agent"></a>Azure DevOps Services エージェント

* [DockerHub の Azure DevOps Services エージェント イメージ](https://hub.docker.com/r/microsoft/vsts-agent/)

* [GitHub の Azure DevOps Services エージェント イメージ](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux エージェント

* [Operations Management Suite (OMS) Linux エージェントの概要](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [DockerHub の Operations Management Suite (OMS) イメージ](https://hub.docker.com/r/microsoft/oms/)

* [GitHub の Operations Management Suite (OMS) イメージ](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure コマンド ライン インターフェイス (CLI)

* [DockerHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ](https://hub.docker.com/r/microsoft/azure-cli/) 

* [GitHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB Emulator (Windows コンテナーのみ)

* [DockerHub の Microsoft Azure Cosmos DB Emulator イメージ](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Microsoft Azure Cosmos DB Emulator をローカルでの開発とテストに使用する](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Docker 開発の豊かなエコシステムについて学習する

Docker プラットフォームとさまざまな Docker イメージについて学んだので、次のステップとして Docker の豊かなエコシステムについて学習しましょう。 以下のリンクでは、コンテナー開発を補完する Microsoft のツールについて説明します。

* [.NET と Docker を組み合わせて使用する](https://devblogs.microsoft.com/dotnet/using-net-and-docker-together/)
* [複数コンテナーのマイクロサービス ベース .NET アプリケーションの設計と開発](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Visual Studio Code の Docker 拡張](https://code.visualstudio.com/docs/languages/dockerfile)
* [Azure Service Fabric の使用方法を学習する](/azure/service-fabric/index)
* [Service Fabric の入門サンプル](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Windows コンテナーの利点](/virtualization/windowscontainers/about/index#video-overview)
* [Visual Studio Docker ツールの使用](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [Azure Container Registry から Azure Container Instances に Docker イメージを配置する](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio Code でのデバッグ](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [クラウドにおける Visual Studio for Mac、コンテナー、サーバーレス コードの入門](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Docker と Visual Studio for Mac の入門ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>次の手順

* [.NET Core での Docker の基礎の学習](docker-basics-dotnet-core.md)
* [.NET Core の Docker イメージのビルド](building-net-docker-images.md)
