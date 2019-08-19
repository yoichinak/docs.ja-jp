---
title: Apache Spark アプリケーション用の .NET を Databricks にデプロイする
description: Apache Spark アプリケーション用の .NET を Databricks にデプロイする方法について説明します。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "69576969"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>Apache Spark アプリケーション用の .NET を Databricks にデプロイする

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Databricks にデプロイする方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * Microsoft の Spark を準備します。
> * Spark .NET アプリを発行する
> * アプリを Databricks にデプロイする
> * アプリの実行

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、次の手順を実行します。

* [DATABRICKS CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)をダウンロードします。
* [Install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)をローカルコンピューターにダウンロードします。 これは、後で Apache Spark 依存ファイル用の .NET を Spark クラスターのワーカーノードにコピーするために後で使用するヘルパースクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft spark**は、spark クラスターの個々のワーカーノードに存在するバックエンドコンポーネントです。 C# Udf (ユーザー定義関数) を実行する場合、Spark は、.net CLR を起動して udf を実行する方法を理解する必要があります。 **Microsoft spark**は、この機能を有効にするクラスのコレクションを spark に提供します。

1. クラスターにデプロイする[Microsoft Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、を`.NET for Apache Spark v0.1.0`使用`netcoreapp2.1`する場合は、 [linux-x64-0.1.0](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)をダウンロードする必要があります。これは、次のようになります。

2. クラスター `Microsoft.Spark.Worker.<release>.tar.gz`からアクセスできる分散ファイルシステム (たとえば、DBFS) にアップロードして[install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)します。

## <a name="prepare-your-net-for-apache-spark-app"></a>Apache Spark アプリ用の .NET を準備する

1. [入門](get-started.md)チュートリアルに従ってアプリをビルドします。

2. Spark .NET アプリを自己完結型として発行します。

   Linux では、次のコマンドを実行できます。

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. パブリッシュ`<your app>.zip`されたファイルのを生成します。

   Linux では、を使用して`zip`次のコマンドを実行できます。

   ```bash
   zip -r <your app>.zip .
   ```

4. クラスターがアクセスできる分散ファイルシステム (たとえば、DBFS) に次のコードをアップロードします。

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`:この jar は、 [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   * `<your app>.zip`
   * 各実行プログラムの作業ディレクトリに配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (アプリが依存しているユーザー定義関数またはライブラリを含む Dll など)。

## <a name="deploy-to-databricks"></a>Databricks のデプロイする

[Databricks](https://databricks.com)は、Apache Spark を使用してクラウドベースのビッグデータ処理を提供するプラットフォームです。

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/)と[AWS Databricks](https://databricks.com/aws)は Linux ベースです。 そのため、Databricks へのアプリのデプロイに関心がある場合は、アプリに互換性が .NET Standard こと、および[.Net Core コンパイラ](https://dotnet.microsoft.com/download)を使用してアプリをコンパイルすることを確認してください。

Databricks を使用すると、既存のアクティブなクラスターに Apache Spark アプリ用の .NET を送信したり、ジョブを起動するたびに新しいクラスターを作成したりすることができます。 そのためには、Apache Spark アプリ用の .NET を送信する前に、 **Microsoft の Spark**をインストールする必要があります。

### <a name="deploy-microsoftsparkworker"></a>Microsoft Spark をデプロイする

この手順は、クラスターに対して1回のみ必要です。

1. [Db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)と install-worker.sh [](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
)をローカルコンピューターにダウンロードします。

2. Db-init.sh を変更して、クラスターにダウンロードしてインストールするのリリースをポイントします。

3. [DATABRICKS CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)をインストールします。

4. Databricks CLI の認証の詳細を[設定](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication)します。

5. 次のコマンドを使用して、ファイルを Databricks クラスターにアップロードします。

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Databricks ワークスペースにアクセスします。 左側のメニューから **[クラスター]** を選択し、 **[クラスターの作成]** を選択します。

7. クラスターを適切に構成したら、 **Init スクリプト**を設定し、クラスターを作成します。

   ![スクリプトアクションの画像](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>アプリの実行 

または`set JAR` `spark-submit`を使用して、ジョブを Databricks に送信できます。

### <a name="use-set-jar"></a>JAR の設定を使用する

[SET JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job)を使用すると、既存のアクティブなクラスターにジョブを送信できます。

#### <a name="one-time-setup"></a>1回限りのセットアップ

1. Databricks クラスターに移動し、左側のメニューから **[ジョブ]** を選択します。 次に、 **[JAR の設定]** を選択します。

2. 適切な`microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`ファイルをアップロードします。

3. パラメーターを適切に設定します。

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. 前のセクションで、 **Init スクリプト**を作成した既存のクラスターを指すように**クラスター**を構成します。

#### <a name="publish-and-run-your-app"></a>アプリを発行して実行する

1. [DATABRICKS CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)を使用して、Databricks クラスターにアプリケーションをアップロードします。

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. この手順が必要なのは、アプリアセンブリ (たとえば、ユーザー定義関数を含む Dll) を各**Microsoft Spark. Worker**の作業ディレクトリに配置する必要がある場合のみです。

   - アプリケーションアセンブリを Databricks クラスターにアップロードする
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - アプリの依存関係のパスをポイントして Databricks クラスターにアップロードするには、 [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh)の [アプリの依存関係] セクションのコメントを解除し、変更します。
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - クラスターを再起動します。

3. Databricks ワークスペースで Databricks クラスターにアクセスします。 **[ジョブ]** でジョブを選択し、 **[今すぐ実行]** を選択してジョブを実行します。

### <a name="use-spark-submit"></a>Spark 送信の使用

[Spark submit](https://spark.apache.org/docs/latest/submitting-applications.html)コマンドを使用すると、新しいクラスターにジョブを送信できます。

1. [ジョブを作成](https://docs.databricks.com/user-guide/jobs.html)し、 **[spark-submit の構成]** を選択します。

2. 次`spark-submit`のパラメーターを使用してを構成します。

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Databricks ワークスペースで Databricks クラスターにアクセスします。 **[ジョブ]** でジョブを選択し、 **[今すぐ実行]** を選択してジョブを実行します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Databricks にデプロイしました。 Databricks の詳細については、Azure Databricks のドキュメントを参照してください。

> [!div class="nextstepaction"]
> [Azure Databricks のドキュメント](https://docs.microsoft.com/azure/azure-databricks/)
