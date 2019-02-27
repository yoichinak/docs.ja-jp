---
title: Docker アプリの内部ループ開発ワークフロー
description: Docker アプリケーションの開発の「内部ループ」ワークフローをについて説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1134ff439235609db840c85a1e67bc9fe4ccec84
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835682"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker アプリの内部ループ開発ワークフロー

サイクル全体の DevOps のまたがりメモリ割り当て、外側のループのワークフローをトリガーする前に、各開発者のコンピューターで、アプリ自体のコーディングや、好みの言語またはプラットフォームを使用してローカルでテストして (図 4-21) すべてが開始されます。 どのケースでも、する必要がある重要なポイントに共通どのような言語、フレームワーク、またはプラットフォームを選んでも。 この特定のワークフローで常に開発およびがローカルで Docker コンテナーをテストします。

![手順 1 - コード/実行/デバッグ](./media/image18.png)

**図 4-21** 内部ループ開発コンテキスト

コンテナーまたは Docker イメージのインスタンスは、これらのコンポーネントが含まれます。

-   (たとえば、Linux ディストリビューションまたは Windows)、オペレーティング システムの選択

- (たとえば、アプリ バイナリ) の開発者によって追加されたファイル

-   構成 (たとえば、環境の設定との依存関係)

- Docker で実行するどのようなプロセスの手順

(次のセクションで説明されている) プロセスとして Docker を使用する内部ループ開発ワークフローを設定することができます。 のみ、1 回行う必要があるため、環境を設定するには、最初の手順が含まれていないことを検討してください。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code と Docker CLI を使用して、Docker コンテナー内の 1 つのアプリの構築

アプリは、独自のサービスとその他のライブラリ (依存関係) から構成されます。

図 4-22 は、通常は各手順の詳細な説明の後に、Docker アプリを構築するときに実行するために必要な基本手順を示します。

![ワークフローの概要:手順 1 - コードでは、手順 2 - 手順 3 - の Dockerfile を記述 Dockerfile、手順 4 で定義されているイメージを作成する - 手順 5 - コンテナーの実行、docker-compose ファイルでサービスを定義または構成アプリ、手順 6 - テスト アプリ、手順 7 - が外側のループ (CI/CD パイプライン) を開始または続行 de にプッシュveloping します。](./media/image19.png)

**図 4-22** Docker CLI を使用してコンテナー化された Docker アプリケーションのライフ サイクルの高度なワークフロー

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>手順 1: Visual Studio Code でコーディングを開始し、アプリやサービスの初期ベースラインを作成します。

アプリケーションを開発する方法は、Docker を使用しないことを行う方法に似ています。 違いは、開発中に、展開しているアプリケーションまたは (Windows や Linux VM) など、ローカル環境で配置された Docker コンテナー内で実行されているサービスをテストします。

**ローカル環境の設定**

Mac および Windows 用 Docker の最新バージョンでは、これまでに、Docker アプリケーションの開発よりも簡単ですし、セットアップは簡単です。

> [!情報]
>
> Docker for Windows の設定手順については、<https://docs.docker.com/docker-for-windows/>します。
>
>Docker for Mac の設定手順については、<https://docs.docker.com/docker-for-mac/>します。

さらに、実際に Docker CLI を使用しているときにアプリケーションを開発することができるように、コード エディターが必要があります。

Microsoft は、Visual Studio Code では、軽量なコード エディターは、Mac、Windows、および Linux でサポートされ、IntelliSense を提供しますです[多くの言語サポート](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、Go、Java、Ruby、Python、およびほとんど最新の言語の)[デバッグ](https://code.visualstudio.com/Docs/editor/debugging)、 [Git との統合](https://code.visualstudio.com/Docs/editor/versioncontrol)と[拡張機能のサポート](https://code.visualstudio.com/docs/extensions/overview)します。 このエディターは、Mac および Linux の開発者に最適です。 Windows でもに完全な Visual Studio アプリケーションを使用できます。

> [!情報]
>
> Visual Studio のコードを Windows、Mac、または Linux をインストールする方法の詳細についてを参照してください<https://code.visualstudio.com/docs/setup/setup-overview/>します。
>
> Docker for Mac の設定手順については、<https://docs.docker.com/docker-for-mac/>します。

Docker CLI を使用して、コード エディターを使用してコードを記述できますが、Docker 拡張機能で Visual Studio Code を使用して簡単に作成者`Dockerfile`と`docker-compose.yml`ワークスペース内のファイル。 下にある Docker CLI を使用して Docker コマンドを実行する Visual Studio コード IDE から、タスクおよびスクリプトを実行することもできます。

VS Code 用 Docker 拡張機能は、次の機能を提供します。

- 自動`Dockerfile`と`docker-compose.yml`ファイルの生成

- 構文の強調表示し、マウス ポインターのヒントの`docker-compose.yml`と`Dockerfile`ファイル

- IntelliSense (入力候補)`Dockerfile`と`docker-compose.yml`ファイル

- Lint 処理 (エラーと警告) の`Dockerfile`ファイル

- 最も一般的な Docker コマンドをコマンド パレット (F1) の統合

- イメージとコンテナーを管理するためのエクスプ ローラーの統合

- DockerHub と Azure コンテナー レジストリからイメージを Azure App Service へのデプロイします。

Docker 拡張機能のインストールに Ctrl + Shift + P キーを押して`ext install`、Marketplace 拡張機能の一覧を表示する拡張機能のインストール コマンドを実行します。 次に、入力**docker**結果をフィルター処理し、図 4-23 で示すように、Docker サポートの拡張機能を選択します。

![VS Code 用 Docker 拡張機能のビュー。](./media/image20.png)

**図 4-23**.  Visual Studio Code での Docker 拡張機能のインストール

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>手順 2: 既存のイメージ (プレーンな OS または .NET Core、Node.js、Ruby などの開発環境) に関連する DockerFile を作成します。

必要があります、`DockerFile`カスタム イメージを構築およびデプロイするコンテナーごと。 1 つのカスタム サービスのアプリが構成されている場合、1 つ必要がありますが`DockerFile`します。 場合、アプリが (マイクロ サービス アーキテクチャ) のように複数のサービスで構成される必要がありますいずれかが`Dockerfile`サービスあたり。

`DockerFile`よくアプリまたはサービスのルート フォルダーに配置され、Docker を設定して、そのアプリやサービスを実行する方法を認識できるように、必要なコマンドが含まれています。 作成することができます、`DockerFile`コードと共にプロジェクトに追加し、(node.js、.NET Core など)、または、環境に慣れていない場合、次のヒントを参照してください。

> [!TIP]
>
> 使用しているときに、Docker 拡張機能を使用することができます、`Dockerfile`と`docker-compose.yml`ファイルは、Docker コンテナーに関連します。 最終的には、このツールがなければファイルのこれらの種類を記述する可能性がありますが、学習曲線を加速する適切な開始点は、Docker 拡張機能を使用します。

図 4-24 に、docker の方法を確認できます-compose ファイルは、VS Code 用 Docker 拡張機能を使用して追加されます。

![VS Code 用 Docker 拡張機能のコンソール ビュー。](./media/image24.png)

**図 4-24** 使用して追加された docker ファイル、**ワークスペース コマンドに追加の Docker ファイル**

使用する基本の Docker イメージを指定する DockerFile を追加する場合 (などを使用して`FROM microsoft/aspnetcore`)。 任意の公式リポジトリから取得した基本イメージ上にカスタム イメージをビルドすることは、通常は、 [Docker Hub レジストリ](https://hub.docker.com/)(など、 [.NET Core のイメージ](https://hub.docker.com/r/microsoft/dotnet/)または[for Node.js](https://hub.docker.com/_/node/)).

***既存の公式 Docker イメージを使用して、***

バージョン番号を持つ言語のスタックの公式のリポジトリを使用してにより、同じ言語機能が (開発、テスト、および運用環境を含む) すべてのコンピューターで使用できます。

.NET Core コンテナー用のサンプル DockerFile を次に示します。

```Dockerfile
# Base Docker image to use  
FROM microsoft/dotnet:2.1-aspnetcore-runtime
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

この場合、イメージが、行に従って公式の ASP.NET Core Docker イメージ (Linux および Windows 用マルチ アーキテクチャ) の version 2.1 に基づきます。`FROM microsoft/dotnet:2.1-aspnetcore-runtime`します。 (詳細については、このトピックでは、次を参照してください。、 [ASP.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/aspnetcore/)ページと[.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/dotnet/)ページ)。

DockerFile では、(ポート 80) などの実行時に使用する TCP ポートをリッスンするように Docker を指示することもできます。

使用している言語とフレームワークによっては、Dockerfile に別の構成設定を指定できます。 たとえば、`ENTRYPOINT`線`["dotnet", "MySingleContainerWebApp.dll"]`.NET Core アプリケーションを実行する Docker に指示します。 SDK と .NET Core CLI を使用しているかどうか (`dotnet CLI`) をビルドする .NET アプリケーションを実行し、この設定が異なる場合がします。 ここで重要な点は、ENTRYPOINT 行とその他の設定が、アプリケーション用に選択した言語とプラットフォームに依存するです。

> [!情報]
>
> .NET Core アプリケーション用の Docker イメージの構築に関する詳細についてを参照してください<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>します。
>
> 詳細については、独自のイメージを構築するには<https://docs.docker.com/engine/tutorials/dockerimages/>します。

**マルチ アーキテクチャ イメージ リポジトリを使用します。**

リポジトリ内の 1 つのイメージ名には、Linux イメージと Windows イメージなどのプラットフォーム バリアントを含めることができます。 この機能は、複数のプラットフォーム (Linux および Windows) をカバーする 1 つのリポジトリを作成する Microsoft (基本イメージの作成者) のようなベンダーを使用できます。 たとえば、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub レジストリで利用可能なリポジトリは、同じイメージ名を使用して Linux および Windows Nano Server のサポートを提供します。

プル、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) Linux バリアントがプル Linux ホストから同じイメージ名を取得する一方、Windows ホストからのイメージのプルを Windows バリアント。

***最初から基本イメージを作成します。***

これで説明したように、最初から、独自の Docker 基本イメージを作成することができます[記事](https://docs.docker.com/engine/userguide/eng-image/baseimages/)Docker から。 このシナリオは、docker を使い始めたばかりが基本イメージの特定のビットを設定する場合は、行うことができます、最適ではない可能性があります。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>手順 3: これで、サービスを埋め込み、カスタム Docker イメージを作成します。

サービスごとにカスタム アプリを構成するには、関連するイメージを作成する必要があります。 1 つのサービスまたは web アプリのアプリが構成されている場合は、1 つのイメージを必要があります。

> [!NOTE]
>
> 「外側のループ DevOps ワークフロー」を考慮に入れてと、プッシュするたびに、ソース コードを Git リポジトリ (継続的インテグレーション) に、イメージはグローバル環境で作成できるようにから、自動化されたビルド プロセスによって、イメージを作成、ソース コードです。
>
> その外側のループのルートに、検討する前に、Docker アプリケーションが実際に正しく動作するソース管理システム (Git など) が正しく動作しないコードをプッシュしないようにすることを確認する必要があります。
>
> したがって、各開発者をローカルでテストし、完全な機能をプッシュするか、ソース管理システムに変更するまでの開発を続ける全体の内側のループ処理を行う最初が必要です。

図 4-25 に示すよう、ローカル環境と DockerFile を使用して、イメージを作成する docker ビルド コマンドを使用することができます (を実行することも`docker-compose up --build`アプリケーションがいくつかのコンテナー/サービスで構成されます)。

![進行状況をダウンロードする画像を表示、docker-compose build のコンソール出力。](./media/image25.png)

**図 4-25** Docker のビルドを実行しています。

直接実行しているのではなく、必要に応じて、 `docker build` 、プロジェクト フォルダーから最初に生成できます展開可能なフォルダー、実行を使用して、必要な .NET ライブラリと`dotnet publish`コマンドを使用し、実行`docker build`します。

この例では、Docker イメージを作成、名前を持つ`cesardl/netcore-webapi-microservice-docker:first`(`:first`は特定のバージョンのように、タグです)。 複数のコンテナーで、構成した Docker アプリケーションを作成する必要がある各カスタム イメージでは、この手順を実行できます。

既存のイメージで見つかりますローカル リポジトリ (開発用コンピューター)、docker を使用してイメージのコマンドを図 4-26 に示すようにします。

![コンソール コマンドの docker イメージを既存のイメージの表示から出力します。](./media/image26.png)

**図 4-26** Docker イメージを使用して既存のイメージを表示します。

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>手順 4: 複数のサービスで構成された Docker アプリを構築するときに docker compose.yml で、サービスを定義します。

`docker-compose.yml`ファイル、一連の手順の次のセクションで説明されている展開コマンドを使用して、構成されたアプリケーションとしてデプロイ関連のサービスを定義することができます。

そのファイルでメインまたはルート ソリューション フォルダーを作成します。このようなコンテンツが`docker-compose.yml`ファイル。

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

このケースでこのファイルは 2 つのサービスを定義します。 web サービス (カスタム サービス) と、redis サービス (一般的なキャッシュ サービス)。 各サービスは、各具象の Docker イメージを使用する必要があります、コンテナーとしてデプロイされます。 この特定の web サービスのイメージは、以下を行う必要があります。

- 現在のディレクトリに DockerFile からビルドします。

- 公開されているポート 80 をコンテナー ホスト コンピューター上でポート 81 上での転送します。

- イメージを再構築することがなく、コードを変更することができるので、コンテナー内で指定するホスト上のプロジェクト ディレクトリをマウントします。

- Redis サービスに web サービスをリンクします。

Redis サービスの使用、[最新のパブリック redis イメージ](https://hub.docker.com/_/redis/)Docker Hub レジストリからプルします。 [redis](https://redis.io/)はサーバー側アプリケーションの人気のあるキャッシュ システムです。

### <a name="step-5-build-and-run-your-docker-app"></a>手順 5: ビルドして Docker アプリの実行

アプリに 1 つのコンテナーのみがある場合だけ、Docker ホスト (VM または物理サーバー) にデプロイして実行する必要があります。 ただし、複数のサービス、アプリが構成されている場合をする必要があります*組み立てること*もします。 さまざまなオプションを見てみましょう。

***オプション a:1 つのコンテナーまたはサービスを実行します。***

次に示すように docker run コマンドを使用して、Docker イメージを実行できます。

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

この特定の展開の私たち 要求をリダイレクトする内部ポート 5000 をポート 80 に送信します。 外部ポート 80、ホスト レベルで、アプリケーションがリッスンしているようになりました。

***オプション b:構成して複数コンテナー アプリケーションの実行***

ほとんどのエンタープライズ シナリオでは、Docker アプリケーションを複数のサービスはから構成します。 このような場合は、実行することができます、`docker-compose up`が以前に作成した docker compose.yml ファイルを使用するコマンド (図 4-27)、します。 このコマンドを実行するには、すべての関連するコンテナーの構成済みのアプリケーションはデプロイします。

![コンソール出力から、docker-compose up コマンド。](./media/image27.png)

**図 4-27** "、Docker-compose up"コマンドの実行結果

実行した後`docker-compose up`、展開すると、アプリケーションとその関連コンテナー、Docker ホストに VM の表記で図 4-28 に示すようにします。

![複数コンテナー アプリケーションを実行している VM。](./media/image28.png)

**図 4-28** Docker コンテナーが展開された VM

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>手順 6: (ローカル CD VM) では、ローカルで Docker アプリケーションをテストします。

この手順は、アプリの実行内容によって異なります。

シンプルな .NET Core Web API"Hello World"を 1 つのコンテナーまたはサービスとしてデプロイされている、DockerFile で指定された TCP ポートを提供することで、サービスにアクセスするとだけです。

サービスに移動する localhost が有効でない場合は、このコマンドを使用して、マシンの IP アドレスを検索します。

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Docker ホストでは、ブラウザーを開いて、そのサイトに移動します図 4-29 に示すようにアプリ/サービスを実行して、参照してください必要があります。

![Localhost/API/値からの応答のブラウザー ビュー。](./media/image29.png)

**図 4-29** Localhost を使用してローカルで Docker アプリケーションのテスト

方法で展開されているため、ポート 80 を使用していますが、ポート 5000 に内部的にリダイレクトされていることに注意してください`docker run`、前述のようです。

これは、CURL を使用して、ターミナルから、テストできます。 図 4-30 で示すように、Windows で Docker のインストールでは、既定の IP、10.0.75.1、です。

![コンソール出力の取得から、 http://10.0.75.1/API/valuesと curl](./media/image30.png)

**図 4-30** CURL を使用してローカルの Docker アプリケーションのテスト

**Docker で実行されているコンテナーのデバッグ**

Visual Studio Code は、Node.js と .NET Core コンテナーなどの他のプラットフォームを使用している場合に、Docker のデバッグをサポートします。

デバッグすることもできます Docker でコンテナーを .NET Core または .NET Framework Visual Studio の Windows または Mac で使用する場合、次のセクションで説明されているとします。

> [!情報]
>
> Node.js の Docker コンテナーのデバッグに関する詳細については、するには<https://blog.docker.com/2016/07/live-debugging-docker/>と<https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>します。

>[!div class="step-by-step"]
>[前へ](docker-apps-development-environment.md)
>[次へ](visual-studio-tools-for-docker.md)
