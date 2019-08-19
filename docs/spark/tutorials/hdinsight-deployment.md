---
title: Apache Spark アプリケーション用の .NET を Azure HDInsight にデプロイする
description: Apache Spark アプリケーション用の .NET を HDInsight にデプロイする方法について説明します。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4769c194520790ce217d46d1d3197b20742d4f1a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "69576949"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Apache Spark アプリケーション用の .NET を Azure HDInsight にデプロイする

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Azure HDInsight にデプロイする方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * Microsoft の Spark を準備します。
> * Spark .NET アプリを発行する
> * アプリを Azure HDInsight にデプロイする
> * アプリの実行

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、次の手順を実行します。

* [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/)をダウンロードします。
* [Install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)をローカルコンピューターにダウンロードします。 これは、後で Apache Spark 依存ファイル用の .NET を Spark クラスターのワーカーノードにコピーするために後で使用するヘルパースクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft spark**は、spark クラスターの個々のワーカーノードに存在するバックエンドコンポーネントです。 C# Udf (ユーザー定義関数) を実行する場合、Spark は、.net CLR を起動して udf を実行する方法を理解する必要があります。 **Microsoft spark**は、この機能を有効にするクラスのコレクションを spark に提供します。

1. クラスターにデプロイする[Microsoft Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、を`.NET for Apache Spark v0.1.0`使用`netcoreapp2.1`する場合は、 [linux-x64-0.1.0](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)をダウンロードする必要があります。これは、次のようになります。

2. クラスター `Microsoft.Spark.Worker.<release>.tar.gz`からアクセスできる分散ファイルシステム (HDFS、 [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 、adls など) にアップロードして、そのファイルをアップロードします。

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

4. クラスターからアクセス可能な分散ファイルシステム (HDFS、ADLS、ADLS など) に以下をアップロードします。

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar` :この jar は、 [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   * `<your app>.zip`
   * 各実行プログラムの作業ディレクトリに配置されるファイル (依存関係ファイルや、 `app`すべてのワーカーがアクセスできる共通のデータなど) またはアセンブリ (ユーザー定義関数またはが依存するライブラリを含む dll など)。

## <a name="deploy-to-azure-hdinsight-spark"></a>Azure HDInsight Spark に配置する

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview)は、クラウドで Apache Spark の Microsoft による実装であり、ユーザーは Azure で Spark クラスターを起動して構成することができます。 HDInsight Spark クラスターを使用して、 [Azure Storage](https://azure.microsoft.com/services/storage/)または[Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2)に格納されているデータを処理できます。

> [!NOTE]
> Azure HDInsight Spark は Linux ベースです。 Azure HDInsight Spark にアプリをデプロイする場合は、アプリに互換性が .NET Standard こと、および[.Net Core コンパイラ](https://dotnet.microsoft.com/download)を使用してアプリをコンパイルすることを確認してください。

### <a name="deploy-microsoftsparkworker"></a>Microsoft Spark をデプロイする

この手順は、クラスターに対して1回のみ必要です。

HDInsight `install-worker.sh`の[スクリプトアクション](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を使用して、クラスターでを実行します。

|設定|値|
|-------|-----|
|スクリプトの種類|カスタム|
|Name|Microsoft Spark をインストールします。|
|Bash スクリプト URI|アップロード`install-worker.sh`先の URI。 たとえば、`abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|ノードの種類|者|
|パラメーター|パラメーターを`install-worker.sh`にします。 たとえば、Azure Data Lake Gen 2 `install-worker.sh` `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`にアップロードした場合は、のようになります。|

![スクリプトアクションの画像](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>アプリの実行

または Apache Livy を使用して`spark-submit` 、ジョブを Azure HDInsight に送信できます。

### <a name="use-spark-submit"></a>Spark 送信の使用

[Spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html)コマンドを使用して、Apache Spark ジョブ用の .Net を Azure HDInsight に送信できます。
 
1. `ssh`クラスター内のいずれかのヘッドノードに移動します。

1. を`spark-submit`実行します。

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Apache Livy を使用する

[Apache Livy](https://livy.incubator.apache.org/)(Apache Spark REST API) を使用して、Apache Spark ジョブ用の .net を Azure HDInsight Spark クラスターに送信することができます。 詳細については、「 [Apache Livy を使用したリモートジョブ](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface)」を参照してください。

次のコマンドは、Linux でを使用`curl`して実行できます。

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Azure HDInsight にデプロイしました。 HDInsight の詳細については、Azure HDInsight のドキュメントを参照してください。

> [!div class="nextstepaction"]
> [Azure HDInsight のドキュメント](https://docs.microsoft.com/azure/hdinsight/)
