---
title: Visual Studio Tools for Windows 上の Docker
description: Visual Studio 2017 バージョン 15.7 以降で使用可能な Docker ツールの説明を取得します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 78ea3e553e4e449b307bc3585ed66fa48d2c0d8e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680361"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Windows 上の Visual Studio 2017 での Docker ツールの使用

Visual Studio 2017 バージョン 15.7 以降に含まれる Docker ツールを使用する場合、開発者のワークフローは Visual Studio Code と Docker CLI を使用すると似ています (実際には、その同じ Docker CLI) に基づいてが容易に開始、プロセスを簡略化し、生産性の向上は、ビルド、実行、およびタスクを構成します。 実行して、通常を使用してコンテナーをデバッグ`F5`と`Ctrl+F5`Visual Studio からのキー。 そのコンテナーが同じで定義されている場合でも、ソリューション全体をデバッグできます`docker-compose.yml`ソリューション レベルでのファイル。

## <a name="configure-your-local-environment"></a>ローカル環境を構成します。

Docker for Windows の最新バージョンでは、これまでにアプリケーションを開発 Docker、次の参照で説明したように、セットアップは簡単なためより簡単になります。

> [!Docker for Windows をインストールする方法についてに移動する情報] (<https://docs.docker.com/docker-for-windows/>)。

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017 での docker サポート

Docker のサポートをプロジェクトに追加することの 2 つのレベルがあります。 ASP.NET Core プロジェクトで、追加、 `Dockerfile` Docker サポートを有効にすると、プロジェクト ファイル。 次のレベルは、追加コンテナー オーケストレーションのサポート、 `Dockerfile` (まだ存在しない) 場合は、プロジェクトに、`docker-compose.yml`ソリューション レベルでのファイル。 Visual Studio 2017 バージョン 15.0 を 15.7 で既定で、Docker Compose を使用して、コンテナー オーケストレーションのサポートが追加されます。 コンテナー オーケストレーションのサポートは、15.8 またはそれ以降の Visual Studio 2017 バージョンにオプトイン機能です。 後で、バージョン 15.8 Docker Compose と Service Fabric のサポートします。

**追加 > Docker サポート**と**追加 > コンテナー オーケストレーター サポート**コマンドにある ASP.NET Core プロジェクトのプロジェクト ノードの右クリック メニュー (またはコンテキスト メニュー) で**ソリューション エクスプ ローラー**ように、図 4-31。

![Visual Studio での Docker サポート メニュー オプションを追加します。](./media/add-docker-support-menu.png)

**図 4-31**。 Visual Studio 2017 のプロジェクトに Docker サポートの追加

### <a name="add-docker-support"></a>Docker サポートを追加します。

選択して、既存の ASP.NET Core プロジェクトに Docker サポートを追加することができます**追加** > **Docker サポート**で**ソリューション エクスプ ローラー**します。 選択して、プロジェクトの作成時に Docker サポートを有効することも**Docker サポートを有効にする**で、**新しい ASP.NET Core Web アプリケーション**クリックした後に表示されたダイアログ ボックス**ok**で、**新しいプロジェクト** ダイアログ ボックスで、図 4-32 を示すようにします。

![Visual Studio での新しい ASP.NET Core web アプリの Docker サポートを有効にします。](./media/enable-docker-support-visual-studio.png)

**図 4-32**。 Visual Studio 2017 でプロジェクトの作成時に Docker サポートを有効にします。

Docker サポートを有効にすると、Visual Studio の追加、 *Dockerfile*ファイルをプロジェクトにします。

> [!NOTE]
> 図 4-33 に示すように ASP.NET プロジェクト (.NET Framework、.NET Core プロジェクトではなく) プロジェクトの作成時に Docker Compose のサポートが有効、コンテナー オーケストレーションのサポートも追加されます。

![Docker を有効にする ASP.NET プロジェクトのサポートの構成](media/enable-docker-compose-support.png)

**図 4-33**。 Visual Studio 2017 での ASP.NET プロジェクトの Docker Compose のサポートを有効にします。

### <a name="add-container-orchestration-support"></a>コンテナー オーケストレーションのサポートを追加します。

マルチ コンテナー ソリューションを作成する場合は、コンテナー オーケストレーションのサポートをプロジェクトに追加します。 これにより、実行およびで同じ定義している場合、コンテナー (ソリューション全体) のグループを同時にデバッグ*docker compose.yml*ファイル。

コンテナー オーケストレーションのサポートを追加するには、ソリューションまたはプロジェクトのノードを右クリックし**ソリューション エクスプ ローラー**、選択**追加 > コンテナー オーケストレーション サポート**します。 クリックして**Docker Compose**または**Service Fabric**コンテナーを管理します。

プロジェクトに追加の Dockerfile を参照してくださいコンテナー オーケストレーションのサポートをプロジェクトに追加した後、 **docker compose**でソリューションに追加されたフォルダー**ソリューション エクスプ ローラー**ように、図 4-34。

![Visual Studio でソリューション エクスプ ローラーでの docker ファイル](media/docker-support-solution-explorer.png)

**図 4-34**します。 Visual Studio 2017 でのソリューション エクスプ ローラーでの docker ファイル

場合*docker compose.yml*が既に存在する Visual Studio に必要な構成コードの行を追加するだけです。

## <a name="configure-docker-tools"></a>Docker ツールを構成します。

メイン メニューで、次のように選択します。**ツール > オプション**、展開と**コンテナー ツール > 設定**します。 コンテナーのツールの設定が表示されます。

![Visual Studio Docker ツールの表示オプション。プロジェクトの読み込みに必要な Docker イメージを自動的にプル、コンテナーをバック グラウンドで自動的に起動、ソリューションを閉じるには、上のコンテナーを自動的に強制終了および SSL 証明書を信頼する側の入力を促しません。](./media/visual-studio-docker-tools-options.png)

**図 4-35**します。 Docker Tools のオプション

次の表は、これらのオプションを設定する方法を決定するのに役立ちます。

| 名前 | 既定の設定 | 対象 | 説明 |
| -----|:---------------:|:----------:| ----------- |
| プロジェクトの読み込みで必要な Docker イメージを自動的にプルします。 | オン | Docker Compose | プロジェクトを読み込むときのパフォーマンスを高める Visual Studio は、イメージが既にダウンロードしてコードを実行する準備ができたら、ダウンロード処理中にまたは、バック グラウンドで Docker プルの操作が開始されます。 プロジェクトをロードする場合だけ、コードを参照するには、これをオフにできます必要はありません、コンテナー イメージをダウンロードしないようにする場合。 |
| コンテナーをバック グラウンドで自動的に開始します。 | オン | Docker Compose | もう一度パフォーマンスを向上させる Visual Studio によりコンテナーとボリューム マウント ビルドおよびコンテナーを実行する場合に対応。 コンテナーが作成されたときを制御するには、これをオフにします。 |
| 自動的に強制終了のコンテナー ソリューションを閉じる | オン | Docker Compose | コンテナー ソリューションを閉じるか、Visual Studio の終了後も引き続き実行に、ソリューションが希望される場合は、これをオフにします。 |
| Localhost SSL 証明書を信頼する側は表示しません | オフ | ASP.NET Core 2.1 プロジェクト | Localhost SSL 証明書が信頼されていない場合は、Visual Studio は必要ない限り、このチェック ボックスをオンになって、プロジェクトを実行するたびと求められます。 |

> [!WARNING]
> Localhost SSL 証明書は信頼されず、プロンプトを抑制するボックスをチェックする場合は、アプリまたはサービスの実行時に HTTPS web 要求が失敗します。 その場合は、オフにして、**を求めない** チェック ボックスは、プロジェクトを実行し、プロンプトでの信頼関係を示します。

> [!情報] での Visual Studio Tools for Docker の使用、サービスの実装の詳細については、次の記事を参照します。
>
>ローカル Docker コンテナーでアプリをデバッグするには。 <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Visual Studio を使用してコンテナー レジストリに ASP.NET コンテナーをデプロイします。 <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[前へ](docker-apps-inner-loop-workflow.md)
>[次へ](set-up-windows-containers-with-powershell.md)
