---
title: Apache Spark アプリケーション用の .NET を Amazon EMR Spark にデプロイする
description: Apache Spark アプリケーション用の .NET を Amazon EMR Spark にデプロイする方法について説明します。
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 5414bc20de3bb90a5d2144bd006d1b859e184a39
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "69576929"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a>Apache Spark アプリケーション用の .NET を Amazon EMR Spark にデプロイする

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Amazon EMR Spark にデプロイする方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * Microsoft の Spark を準備します。
> * Spark .NET アプリを発行する
> * アプリを Amazon EMR Spark にデプロイする
> * アプリの実行

## <a name="prerequisites"></a>前提条件

開始する前に、次の手順を実行します。

* [AWS CLI](https://aws.amazon.com/cli/)をダウンロードします。
* [Install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)をローカルコンピューターにダウンロードします。 これは、後で Apache Spark 依存ファイル用の .NET を Spark クラスターのワーカーノードにコピーするために後で使用するヘルパースクリプトです。

## <a name="prepare-worker-dependencies"></a>ワーカーの依存関係を準備する

**Microsoft spark**は、spark クラスターの個々のワーカーノードに存在するバックエンドコンポーネントです。 C# Udf (ユーザー定義関数) を実行する場合、Spark は、.net CLR を起動して udf を実行する方法を理解する必要があります。 **Microsoft spark**は、この機能を有効にするクラスのコレクションを spark に提供します。

1. クラスターにデプロイする[Microsoft Spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp リリースを選択します。

   たとえば、を`.NET for Apache Spark v0.1.0`使用`netcoreapp2.1`する場合は、 [linux-x64-0.1.0](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)をダウンロードする必要があります。これは、次のようになります。

2. クラスター `Microsoft.Spark.Worker.<release>.tar.gz`からアクセスできる分散ファイルシステム (S3 など) にアップロードして[install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)します。

## <a name="prepare-your-net-for-apache-spark-app"></a>Apache Spark アプリ用の .NET を準備する

1. [入門](get-started.md)チュートリアルに従ってアプリをビルドします。

2. Spark .NET アプリを自己完結型として発行します。

   Linux で次のコマンドを実行します。

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. パブリッシュ`<your app>.zip`されたファイルのを生成します。

   を使用して`zip`Linux で次のコマンドを実行します。

   ```bash
   zip -r <your app>.zip .
   ```

4. 次の項目を、クラスターがアクセスできる分散ファイルシステム (S3 など) にアップロードします。

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`:この jar は、 [Microsoft Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet パッケージの一部として含まれており、アプリのビルド出力ディレクトリに併置されています。
   * `<your app>.zip`
   * 各実行プログラムの作業ディレクトリに配置されるファイル (依存関係ファイルや、すべてのワーカーからアクセスできる共通データなど) またはアセンブリ (アプリが依存しているユーザー定義関数またはライブラリを含む Dll など)。

## <a name="deploy-to-amazon-emr-spark"></a>Amazon EMR Spark にデプロイする

[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html)は、AWS でのビッグデータフレームワークの実行を簡略化する、管理されたクラスタープラットフォームです。

> [!NOTE] 
> Amazon EMR Spark は Linux ベースです。 そのため、Amazon EMR Spark へのアプリのデプロイに関心がある場合は、アプリに互換性が .NET Standard こと、および[.Net Core コンパイラ](https://dotnet.microsoft.com/download)を使用してアプリをコンパイルすることを確認してください。

### <a name="deploy-microsoftsparkworker"></a>Microsoft Spark をデプロイする

この手順は、クラスターの作成時にのみ必要です。

`install-worker.sh` [ブートストラップアクション](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)を使用して、クラスターの作成中に実行します。

AWS CLI を使用して、Linux で次のコマンドを実行します。

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a>アプリの実行

Amazon EMR Spark でアプリを実行する方法には、spark submit と Amazon EMR の2つの方法があります。

### <a name="use-spark-submit"></a>Spark 送信の使用

[Spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html)コマンドを使用して、Apache Spark ジョブ用の .Net を Amazon Emr spark に送信できます。

1. `ssh`をクラスター内のいずれかのノードにインポートします。

2. `spark-submit` を実行します。

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a>Amazon EMR の手順を使用する

[Amazon EMR の手順](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html)を使用すると、emr クラスターにインストールされている Spark フレームワークにジョブを送信できます。

AWS CLI を使用して、Linux で次のコマンドを実行します。

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Apache Spark アプリケーション用の .NET を Amazon EMR Spark にデプロイしました。 .NET for Apache Spark プロジェクトの例については、GitHub を引き続きご使用ください。

> [!div class="nextstepaction"]
> [Apache Spark サンプル用 .NET](https://github.com/dotnet/spark/tree/master/examples)
