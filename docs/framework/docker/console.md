---
title: Docker でのコンソール アプリケーションの実行
description: 既存の .NET Framework コンソール アプリケーションを Windows Docker コンテナーで実行する方法について説明します。
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: da3c814e2ae3ae646072deaf7aa932272160ce49
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611498"
---
# <a name="running-console-applications-in-windows-containers"></a>Windows コンテナーでのコンソール アプリケーションの実行

コンソール アプリケーションは、状態の単純なクエリから、実行時間の長いドキュメント イメージ処理タスクまで、さまざまな目的で使用されます。 いずれの場合にも、これらのアプリケーションを起動およびスケーリングする機能は、ハードウェアの取得、起動時間、または複数インスタンスの実行による制約を受けます。

Docker コンテナーと Windows Server コンテナーを使用するようにコンソール アプリケーションを移行すると、これらのアプリケーションをクリーンな状態から起動でき、操作を実行してからクリーンにシャットダウンできます。 このトピックでは、コンソール アプリケーションを Windows ベースのコンテナーに移行し、PowerShell スクリプトを使用してこのアプリケーションを起動するために必要な手順を示します。

サンプルのコンソール アプリケーションは、引数 (この場合は質問) を受け取ってランダムな回答を返す単純な例です。 この例では、`customer_id` を受け取ってその税金を処理したり、`image_url` 引数に対してサムネイルを作成したりできます。

回答に加えて、`Environment.MachineName` が応答に追加されており、アプリケーションの実行をローカルで行う場合と Windows コンテナーで行う場合の違いが示されます。 アプリケーションをローカルで実行する場合はローカル コンピューター名が返され、Windows コンテナーで実行する場合はコンテナーのセッション ID が返されます。

[完全な例](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator)は、GitHub の dotnet/samples リポジトリにあります。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

アプリケーションをコンテナーに移行する作業を開始する前に、いくつかの Docker 用語を理解しておく必要があります。

> [!NOTE]
> *Docker イメージ*は、オペレーティング システム (OS)、システム コンポーネント、アプリケーションなど、実行中のコンテナー用の環境を定義する読み取り専用のテンプレートです。

Docker イメージの重要な特徴の 1 つは、イメージが基本イメージから構成されることです。 新しい各イメージが、特徴の小さなセットを既存のイメージに追加します。

> [!NOTE]
> *Docker コンテナー*は、イメージの実行インスタンスです。

さまざまなコンテナーで同じイメージを実行することで、アプリケーションをスケーリングします。
概念的には、複数のホストで同じアプリケーションを実行する場合に似ています。

Docker アーキテクチャの詳細については、Docker サイトの「[Docker Overview](https://docs.docker.com/engine/understanding-docker/)」 (Docker の概要) を参照してください。

コンソール アプリケーションの移行には、次のいくつかの手順を要します。

1. [アプリケーションのビルド](#building-the-application)
1. [イメージの Dockerfile の作成](#creating-the-dockerfile)
1. [Docker コンテナーをビルドして実行するプロセス](#creating-the-image)

## <a name="prerequisites"></a>必須コンポーネント

Windows コンテナーは、[Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) または [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) でサポートされています。

> [!NOTE]
>Windows Server 2016 を使用している場合、Docker for Windows インストーラーによってこの機能は有効にならないので、コンテナーを手動で有効にする必要があります。 OS に対してすべての更新プログラムが実行されていることを確認してから、「[Container Host Deployment](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server)」 (コンテナー ホストの展開) の記事にある説明に従って、コンテナーおよび Docker 機能をインストールします。

Windows コンテナーをサポートするには、Docker for Windows バージョン 1.12 Beta 26 以降が必要になります。 既定では、Docker は Linux ベースのコンテナーを有効にします。Windows コンテナーに切り替えるには、システム トレイで Docker アイコンを右クリックし、**[Switch to Windows containers]** (Windows コンテナーに切り替え) を選択します。 Docker は変更プロセスを実行します。この際、再起動が必要になる場合があります。

![Windows コンテナーのメニュー オプションのスクリーンショット。](./media/console/windows-container-option.png)

## <a name="building-the-application"></a>アプリケーションのビルド

通常、コンソール アプリケーションは、インストーラー、FTP、またはファイル共有の展開を通して配布されます。 コンテナーへの展開時には、資産をコンパイルし、Docker イメージを作成するときに使用できる場所にステージングする必要があります。

サンプル アプリケーションを次に示します。[ConsoleRandomAnswerGenerator](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator)

*build.ps1*<sup>[[source]](https://github.com/dotnet/samples/blob/master/framework/docker/ConsoleRandomAnswerGenerator/ConsoleRandomAnswerGenerator/build.ps1)</sup> で、スクリプトは資産のビルド タスクを実行するために、[MSBuild](/visualstudio/msbuild/msbuild) を使用してアプリケーションをコンパイルします。 必要な資産を最終処理するために MSBuild に渡されるいくつかのパラメーターがあります。 コンパイルするプロジェクト ファイルまたはソリューションの名前、出力の場所、および構成 (Release または Debug) です。

`Invoke-MSBuild` への呼び出しで、`OutputPath` は **publish** に設定され、`Configuration` は **Release** に設定されます。

```powershell
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Dockerfile の作成
コンソールの .NET Framework アプリケーションに使用される基本イメージは `microsoft/windowsservercore` であり、[Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/) で一般公開されています。 この基本イメージには、Windows Server 2016、.NET Framework 4.6.2 の最小限のインストールが含まれており、Windows コンテナーの基本 OS イメージとして機能します。

```Dockerfile
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```

Dockerfile の最初の行は、[`FROM`](https://docs.docker.com/engine/reference/builder/#/from) 命令を使用して基本イメージを指定します。 次に、ファイル内の [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) は、**publish** フォルダーからコンテナーのルート フォルダーにアプリケーション資産をコピーします。最後に、イメージの [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) を設定することで、これがコンテナーの開始時に実行されるコマンドまたはアプリケーションであることを示します。

## <a name="creating-the-image"></a>イメージの作成

Docker イメージを作成するには、*build.ps1* スクリプトに次のコードを追加します。 スクリプトを実行すると、「[アプリケーションのビルド](#building-the-application)」セクションで定義した MSBuild からコンパイルされた資産を使用して、`console-random-answer-generator` イメージが作成されます。

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

PowerShell コマンド プロンプトから、`.\build.ps1` を使用してスクリプトを実行します。

ビルドが完了したら、コマンドラインまたは PowerShell プロンプトから `docker images` コマンドを使用します。イメージが作成され、実行できる状態であることがわかります。

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>コンテナーの実行

コンテナーは、コマンドラインから Docker コマンドを使用して起動できます。

```
docker run console-random-answer-generator "Are you a square container?"
```

出力は次のようになります。

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

PowerShell から `docker ps -a` コマンドを実行すると、コンテナーがまだ存在することがわかります。

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago
```

STATUS 列は、"約 1 分前" にアプリケーションが完了しており、シャットダウンできることを示しています。 このコマンドを 100 回実行すれば、実行する作業のない 100 個のコンテナーが静的な状態で残ります。 最初のシナリオでは、理想的な操作は、作業を実行してからシャットダウンまたはクリーンアップを行うことでした。 そのワークフローを実行するには、`--rm` オプションを `docker run` コマンドに追加することで、`Exited` シグナルを受け取ったらすぐにコンテナーが削除されるようにします。

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

このオプションを指定してコマンドを実行してから、`docker ps -a` コマンドの出力を見ると、コンテナー ID (`Environment.MachineName`) が一覧に表示されていません。

### <a name="running-the-container-using-powershell"></a>PowerShell を使用したコンテナーの実行

サンプル プロジェクト ファイルには、PowerShell を使用して引数を受け入れるアプリケーションを実行する方法の例として、*run.ps1* も含まれています。

実行するには、PowerShell を開き、次のコマンドを使用します。

```powershell
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>まとめ

Dockerfile を追加し、アプリケーションを発行するだけで、.NET Framework コンソール アプリケーションをコンテナー化できます。これにより、アプリケーション コードを全く変更せずに、複数のインスタンス、クリーンな起動と停止、および Windows Server 2016 のより多くの機能を実行することができます。
