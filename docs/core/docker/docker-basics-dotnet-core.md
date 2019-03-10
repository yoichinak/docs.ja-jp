---
title: Docker を使用してアプリをコンテナー化する
description: このチュートリアルでは、基本的な .NET Core アプリケーションを作成し、Docker を使用してコンテナー化する方法について説明します。
ms.date: 10/11/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: addaabb41e57e03a5cf4ec5b2fa3b8b4f3089b32
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372920"
---
# <a name="how-to-containerize-a-net-core-application"></a>.NET Core アプリケーションをコンテナー化する方法

このチュートリアルでは、Docker コンテナー ビルドと .NET Core アプリケーションの展開タスクについて学習します。 [Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)では [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)を使用してアプリを簡単にビルドし、[Docker イメージ](https://docs.docker.com/glossary/?term=image)としてパッケージ化します。 これらのイメージは [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 形式で記述され、[階層型コンテナー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)に展開され、実行されます。

このチュートリアルを通して、以下のことを学びます。

> [!div class="checklist"]
> * Dockerfile の作成方法
> * .NET Core アプリの作成方法
> * Docker コンテナーにアプリを展開する方法

## <a name="net-core-easiest-way-to-get-started"></a>.NET Core:入門として最も簡単な方法

Docker イメージを作成する前に、コンテナー化するアプリケーションを用意する必要があります。 それは Linux、MacOS、Windows で作成できます。 これを行う最も迅速かつ簡単な方法は、.NET Core を利用することです。

.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。

Windows コンテナーと Linux コンテナーの両方を[マルチアーキテクチャ ベース タグ](https://github.com/dotnet/announcements/issues/14)でビルドできます。

## <a name="your-first-net-core-docker-app"></a>初めての .NET Core Docker アプリ

### <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには、次のものが必要です。

#### <a name="net-core-sdk"></a>.NET Core SDK

* [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) 以降をインストールします。

.NET Core 2.1 がサポートされているオペレーティング システムの完全なリスト、サポートが終了した OS、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.1 - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」 (.NET Core 2.1 - サポートされる OS のバージョン) を参照してください。

* コード エディターをまだインストールしていなければ、お気に入りのエディターをインストールしてください。

> [!TIP]
> コード エディターをインストールする必要がありますか。 [Visual Studio Code](https://code.visualstudio.com/download) を試してください。

#### <a name="installing-docker-client"></a>Docker クライアントをインストールする

[Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) 以降の Docker クライアントをインストールします。

Docker クライアントがインストール可能な OS:

* Linux ディストリビューション

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/)

### <a name="create-a-net-core-21-console-app-for-dockerization"></a>Docker で動作させるために .NET Core 2.1 コンソール アプリを作成する

コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。 作成したフォルダーに移動し、次のコマンドを入力します。

```console
dotnet new console
dotnet run
```

簡単に説明します。

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。  また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。

   `Hello.csproj`:

   プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。

   * `OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。
   * `TargetFramework` タグは、対象の .NET 実装を指定します。 高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作で指定したフレームワークにビルドできます。 このチュートリアルでは、.NET Core 2.1 のためにビルドします。

   `Program.cs`:

   プログラムは `using System` で始まります。 これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。 `System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。

   次に、`Hello` という名前空間を定義します。 名前空間は必要なものに変更できます。 `Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。 この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。 今回の例では、"Hello World!" とだけ記述されます。 記述するだけです。

   **dotnet new** で [`dotnet restore`](../tools/dotnet-restore.md) コマンドが実行されます。 **dotnet restore** は [NuGet](https://www.nuget.org/) (.NET パッケージ マネージャー) 呼び出しによって依存関係ツリーを復元します。
   NuGet は次のタスクを実行します。
   * *Hello.csproj* ファイルを分析します。
   * ファイルの依存関係をダウンロードします (またはコンピューター キャッシュから取得します)。
   * *obj/project.assets.json* ファイルを記述します。

   *project.assets.json* ファイルは、NuGet の依存関係グラフ、バインディング解決、その他のアプリ メタデータをすべて揃えたものです。 この必須ファイルは、ソース コードを正しく処理するために、[`dotnet build`](../tools/dotnet-build.md) や [`dotnet run`](../tools/dotnet-run.md) など、他のツールで使用されます。

2. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) は [`dotnet build`](../tools/dotnet-build.md) を呼び出してビルドの成功を確認し、それから `dotnet <assembly.dll>` を呼び出してアプリケーションを実行します。

    ```console
    $ dotnet run

    Hello World!
    ```

    高度なシナリオについては、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。

## <a name="dockerize-the-net-core-application"></a>.NET Core アプリケーションを Docker で動作させる

Hello .NET Core コンソール アプリがローカルで正常に実行されます。 それでは先に進み、アプリをビルドし、Docker で実行します。

### <a name="your-first-dockerfile"></a>初めての Dockerfile

テキスト エディターを開き、始めましょう。 引き続き、アプリをビルドした Hello ディレクトリから作業します。

Linux コンテナーまたは [Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/)の次の Docker 命令を新しいファイルに追加します。 完了したら、Hello ディレクトリのルートに **Dockerfile** として保存します。拡張子は付けません。場合によっては、ファイルの種類を `All types (*.*)` か、それと同様のものに設定する必要があります。

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Dockerfile ファイルには、順次実行される Docker ビルド命令が含まれています。

最初の命令は [**FROM**](https://docs.docker.com/engine/reference/builder/#from) のはずです。 この命令は新しいビルド ステージを初期化し、残りの命令のベース イメージを設定します。 マルチアーキテクチャ タグは、Docker for Windows [コンテナー モード](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)に基づき、Windows コンテナーまたは Linux コンテナーをプルします。 今回の例のベース イメージは microsoft/dotnet リポジトリの 2.1-sdk イメージです。

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

[**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) 命令は残りの命令、RUN、CMD、ENTRYPOINT、COPY、ADD Dockerfile の作業ディレクトリを設定します。 ディレクトリが存在しなければ、作成されます。 今回、WORKDIR がアプリ ディレクトリに設定されています。

```Dockerfile
WORKDIR /app
```

[**COPY**](https://docs.docker.com/engine/reference/builder/#copy) 命令はソース パスから新しいファイルまたはディレクトリをコピーし、それをターゲットのコンテナー ファイルシステムに追加します。 この命令により、C# プロジェクトがコンテナーにコピーされます。

```Dockerfile
COPY *.csproj ./
```

[**RUN**](https://docs.docker.com/engine/reference/builder/#run) 命令は現在のイメージに加えて新しい層でコマンドを実行し、結果をコミットします。 結果のコミットされたイメージは、Dockerfile の次の手順に使用されます。 **dotnet restore** を実行し、C# プロジェクト ファイルの必要な依存関係を取得します。

```Dockerfile
RUN dotnet restore
```

この **COPY** 命令は、コンテナーの残りのファイルを新しい[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)にコピーします。

```Dockerfile
COPY . ./
```

この **RUN** 命令でアプリが公開されます。 [**dotnet publish**](../tools/dotnet-publish.md) コマンドはアプリケーションをコンパイルし、プロジェクト ファイルに指定されているその依存関係を読み通し、結果的に生成された一連のファイルをディレクトリに公開します。 今回のアプリは **Release** 構成で公開され、既定のディレクトリに出力されます。

```Dockerfile
RUN dotnet publish -c Release -o out
```

[**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) 命令では、コンテナーを実行可能ファイルとして実行できます。

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

これで次のような Dockerfile が用意されました。

* アプリをイメージにコピーする
* アプリの依存関係をイメージにコピーする
* 実行可能ファイルとして実行できるようにアプリをビルドする

### <a name="build-and-run-the-hello-net-core-app"></a>Hello .NET Core アプリをビルドして実行する

#### <a name="essential-docker-commands"></a>基本的 Docker コマンド

次の Docker コマンドは不可欠です。

* [docker build](https://docs.docker.com/engine/reference/commandline/build/)
* [docker run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>ビルドして実行する

Dockerfile を記述しました。これで、Docker はアプリをビルドし、コンテナーを実行します。

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

`docker build` コマンドからの出力は、次のコンソール出力と同じようなものになります。

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

この出力からわかるように、Docker エンジンは Dockerfile を利用してコンテナーをビルドしました。

`docker run` コマンドからの出力は、次のコンソール出力と同じようなものになります。

```console
Hello World!
```

おめでとうございます!  今回の成果:
> [!div class="checklist"]
> * ローカル .NET Core アプリを作成しました
> * Dockerfile を作成し、最初のコンテナーをビルドしました
> * Docker で動作させるアプリをビルドし、実行しました

## <a name="next-steps"></a>次の手順

次の手順としては以下のものを用意しています。

* [.NET Docker イメージの入門動画](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio、Docker、Azure コンテナーのインスタンスの併用の利点](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [Docker for Azure クイックスタート](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Docker for Azure でアプリをデプロイする](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。

## <a name="docker-images-used-in-this-sample"></a>このサンプルで使用されている Docker イメージ

次の Docker イメージはこのサンプルで使用されています

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>関連資料

* [.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [Windows コンテナー上の Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET Framework Docker サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [DockerHub の ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/)
* [.NET Core アプリケーションを Docker で動作させる - Docker チュートリアル](https://docs.docker.com/engine/examples/dotnetcore/)
* [Visual Studio Docker ツールの使用](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure Container Registry から Azure Container Instances に Docker イメージを配置する](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)