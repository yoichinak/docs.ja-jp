---
title: .NET for Apache Spark アプリケーションを Databricks にデプロイする
description: .NET for Apache Spark アプリケーションを Databricks にデプロイする方法を説明します。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 035a3c36337413153ee0370aec154d48b84a4711
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957245"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a>.NET for Apache Spark アプリケーションを Databricks にデプロイする

このチュートリアルでは、.NET for Apache Spark アプリケーションを Databricks にデプロイする方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
>
> - Microsoft.Spark.Worker を準備する
> - Spark .NET アプリを発行する
> - Databricks にアプリをデプロイする
> - アプリの実行

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、以下を行います。

- [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) をダウンロードします。
- [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) をお使いのローカル コンピューターにダウンロードします。 これは、後で .NET for Apache Spark の依存ファイルを Spark クラスターのワーカー ノードにコピーするために使用するヘルパー スクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft.Spark.Worker** は、Spark クラスターの個々のワーカー ノードに存在するバックエンド コンポーネントです。 C# UDF (ユーザー定義関数) を実行する場合、.NET CLR を起動して UDF を実行する方法を Spark が理解している必要があります。 **Microsoft.Spark.Worker** により、この機能を有効にするクラスのコレクションが Spark に提供されます。

1. お使いのクラスターにデプロイされる [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、`netcoreapp2.1` を使用する `.NET for Apache Spark v0.1.0` が必要な場合は、[Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz) をダウンロードします。

2. クラスターからアクセスできる分散ファイル システム (DBFS など) に、`Microsoft.Spark.Worker.<release>.tar.gz` と [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) をアップロードします。

## <a name="prepare-your-net-for-apache-spark-app"></a>.NET for Apache Spark アプリを準備する

1. [入門](get-started.md)チュートリアルに従ってアプリをビルドします。

2. Spark .NET アプリを自己完結型として発行します。

   Linux では、次のコマンドを実行できます。

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. 発行されたファイル用に `<your app>.zip` を生成します。

   Linux では、`zip` を使用して次のコマンドを実行できます。

   ```bash
   zip -r <your app>.zip .
   ```

4. クラスターからアクセスできる分散ファイル システム (DBFS など) に、次をアップロードします。

   - `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`:この jar は、[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   - `<your app>.zip`
   - 各 Executor の作業ディレクトリ内に配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (アプリが依存しているユーザー定義関数またはライブラリを含む DLL など)。

## <a name="deploy-to-databricks"></a>Databricks のデプロイする

[Databricks](https://databricks.com) は、Apache Spark を使用してクラウドベースのビッグ データ処理を提供するプラットフォームです。

> [!Note] 
> [Azure Databricks](https://azure.microsoft.com/services/databricks/) と [AWS Databricks](https://databricks.com/aws) は Linux ベースです。 そのため、Databricks へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに [.NET Core コンパイラ](https://dotnet.microsoft.com/download)を使用していることを確認してください。

Databricks を使用すると、.NET for Apache Spark アプリを既存のアクティブなクラスターに送信したり、ジョブを起動するたびに新しいクラスターを作成したりすることができます。 これには、.NET for Apache Spark アプリを送信する前に、**Microsoft.Spark.Worker** をインストールする必要があります。

### <a name="deploy-microsoftsparkworker"></a>Microsoft.Spark.Worker をデプロイする

この手順は、クラスターに対して 1 回のみ必要です。

1. [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) と [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) をローカル コンピューターにダウンロードします。

2. クラスターにダウンロードしてインストールする **Microsoft.Spark.Worker** リリースをポイントするように、**db-init.sh** を変更します。

3. [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) をインストールします。

4. Databricks CLI の[認証の詳細を設定](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication)します。

5. 次のコマンドを使用して、ファイルを Databricks クラスターにアップロードします。

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. Databricks ワークスペースに移動します。 左側のメニューから **[クラスター]** を選択し、 **[クラスターの作成]** を選択します。

7. クラスターを適切に構成したら、**Init スクリプト**を設定し、クラスターを作成します。

   ![スクリプト アクションの画像](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a>アプリの実行 

`set JAR` または `spark-submit` を使用して、ジョブを Databricks に送信できます。

### <a name="use-set-jar"></a>Set JAR を使用する

[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) を使用すると、既存のアクティブなクラスターにジョブを送信できます。

#### <a name="one-time-setup"></a>1 回限りのセットアップ

1. Databricks クラスターに移動し、左側のメニューから **[ジョブ]** を選択します。 次に、 **[Set JAR]** を選択します。

2. 適切な `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` ファイルをアップロードします。

3. パラメーターを適切に設定します。

   | パラメーター   | [値]                                                |
   |-------------|------------------------------------------------------|
   | Main クラス  | org.apache.spark.deploy.dotnet.DotnetRunner          |
   | 引数   | /dbfs/apps/<your-app-name>.zip <your-app-main-class> |

4. 前のセクションで、**Init スクリプト**を作成した既存のクラスターを指すように**クラスター**を構成します。

#### <a name="publish-and-run-your-app"></a>アプリを発行して実行する

1. [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) を使用して、Databricks クラスターにアプリケーションをアップロードします。

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. この手順は、アプリ アセンブリ (たとえば、ユーザー定義関数とその依存関係を含む DLL) を各 **Microsoft Spark.Worker** の作業ディレクトリに配置する必要がある場合にのみ必要です。

   - アプリケーション アセンブリを Databricks クラスターにアップロードする
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) 内のアプリの依存関係セクションをコメント解除して、ご自分のアプリの依存関係パスをポイントするように変更し、Databricks クラスターにアップロードします。
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - クラスターを再起動します。

3. Databricks ワークスペース内の Databricks クラスターに移動します。 **[ジョブ]** の下でジョブを選択し、 **[今すぐ実行]** を選択してジョブを実行します。

### <a name="use-spark-submit"></a>spark-submit を使用する

[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用すると、新しいクラスターにジョブを送信できます。

1. [ジョブを作成](https://docs.databricks.com/user-guide/jobs.html)し、 **[Configure spark-submit]\(spark-submit の構成\)** を選択します。

2. 次のパラメーターを指定して `spark-submit` を構成します。

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. Databricks ワークスペース内の Databricks クラスターに移動します。 **[ジョブ]** の下でジョブを選択し、 **[今すぐ実行]** を選択してジョブを実行します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、.NET for Apache Spark アプリケーションを Databricks にデプロイしました。 Databricks の詳細については、Azure Databricks のドキュメントに進んでください。

> [!div class="nextstepaction"]
> [Azure Databricks のドキュメント](https://docs.microsoft.com/azure/azure-databricks/)
