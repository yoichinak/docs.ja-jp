---
title: .NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする
description: .NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする方法を説明します。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2e8da5497035a83fde75bf91a7d21437d510b480
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117979"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする

このチュートリアルでは、.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
>
> * Microsoft.Spark.Worker を準備する
> * Spark .NET アプリを発行する
> * アプリを Azure HDInsight にデプロイする
> * アプリの実行

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、以下を行います。

* [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をダウンロードします。
* [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) をお使いのローカル コンピューターにダウンロードします。 これは、後で .NET for Apache Spark の依存ファイルを Spark クラスターのワーカー ノードにコピーするために使用するヘルパー スクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft.Spark.Worker** は、Spark クラスターの個々のワーカー ノードに存在するバックエンド コンポーネントです。 C# UDF (ユーザー定義関数) を実行する場合、.NET CLR を起動して UDF を実行する方法を Spark が理解している必要があります。 **Microsoft.Spark.Worker** により、この機能を有効にするクラスのコレクションが Spark に提供されます。

1. お使いのクラスターにデプロイされる [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、`netcoreapp2.1` を使用する `.NET for Apache Spark v0.1.0` が必要な場合は、[Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz) をダウンロードします。

2. クラスターからアクセスできる分散ファイル システム (HDFS、WASB、ADLS など) に、`Microsoft.Spark.Worker.<release>.tar.gz` と [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) をアップロードします。

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

4. クラスターからアクセスできる分散ファイル システム (HDFS、WASB、ADLS など) に、次をアップロードします。

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`:この jar は、[Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   * `<your app>.zip`
   * 各 Executor の作業ディレクトリ内に配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (`app` が依存しているユーザー定義関数またはライブラリを含む DLL など)。

## <a name="deploy-to-azure-hdinsight-spark"></a>Azure HDInsight Spark にデプロイする

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) は、ユーザーが Azure で Spark クラスターを起動して構成できるようにするための、Microsoft による Apache Spark のクラウドへの実装です。 HDInsight Spark クラスターを使用して、[Azure Storage](https://azure.microsoft.com/services/storage/) または [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2) に格納されているデータを処理できます。

> [!NOTE]
> Azure HDInsight Spark は Linux ベースです。 Azure HDInsight Spark へのアプリのデプロイに関心がある場合は、アプリが .NET Standard と互換性があることと、アプリのコンパイルに [.NET Core コンパイラ](https://dotnet.microsoft.com/download)を使用していることを確認してください。

### <a name="deploy-microsoftsparkworker"></a>Microsoft.Spark.Worker をデプロイする

この手順は、クラスターに対して 1 回のみ必要です。

[HDInsight スクリプト アクション](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を使用して、クラスターで `install-worker.sh` を実行します。

|設定|[値]|
|-------|-----|
|スクリプトの種類|カスタム|
|name|Microsoft.Spark.Worker をインストールする|
|Bash スクリプト URI|`install-worker.sh` のアップロード先の URI。 たとえば、`abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|ノードの種類|ワーカー|
|パラメーター|`install-worker.sh` のパラメーター。 たとえば、`install-worker.sh` を Azure Data Lake Gen 2 にアップロードした場合、これは `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin` になります。|

![スクリプト アクションの画像](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>アプリの実行

`spark-submit` または Apache Livy を使用して、ジョブを Azure HDInsight に送信できます。

### <a name="use-spark-submit"></a>spark-submit を使用する

[spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) コマンドを使用して、.NET for Apache Spark ジョブを Azure HDInsight に送信できます。
 
1. クラスター内のいずれかのヘッド ノードに `ssh` で接続します。

1. `spark-submit` を実行します。

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Apache Livy を使用する

[Apache Livy](https://livy.incubator.apache.org/) (Apache Spark REST API) を使用して、.NET for Apache Spark ジョブを Azure HDInsight Spark クラスターに送信することができます。 詳細については、[Apache Livy を使用したリモート ジョブ](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface) に関するページを参照してください。

Linux では、`curl` を使用して次のコマンドを実行できます。

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイしました。 HDInsight の詳細については、Azure HDInsight のドキュメントに進んでください。

> [!div class="nextstepaction"]
> [Azure HDInsight のドキュメント](https://docs.microsoft.com/azure/hdinsight/)
