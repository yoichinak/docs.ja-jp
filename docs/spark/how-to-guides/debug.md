---
title: Windows で .NET for Apache Spark アプリケーションをデバッグする
description: Windows で .NET for Apache Spark アプリケーションをデバッグする方法について学習します。
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206148"
---
# <a name="debug-a-net-for-apache-spark-application"></a>.NET for Apache Spark アプリケーションをデバッグする

この使い方では、Windows 上で .NET for Apache Spark アプリケーションと Scala コードをデバッグするために実行する必要があるコマンドが提供されます。

## <a name="debug-your-application"></a>アプリケーションをデバッグする

新しいコマンド プロンプト ウィンドウを開いて、次を実行します。

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

このコマンドを実行すると、次の出力が表示されます。

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

このデバッグモードでは、`DotnetRunner` によって .NET アプリケーションが起動されることはありませんが、接続されるまで待機します。 このコマンド プロンプト ウィンドウは開いたままにしておきます。

これで、任意のデバッガーを使用して .NET アプリケーションを実行し、アプリケーションをデバッグできるようになりました。

## <a name="debug-scala-code"></a>Scala コードをデバッグする

`DotnetRunner` や `DotnetBackendHandler` などの Scala 側のコードをデバッグする必要がある場合は、次のコマンドを実行します。

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

コマンドを実行した後、[Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) を使用して実行中のプロセスにデバッガーを追加します。

## <a name="next-steps"></a>次の手順

* [.NET for Apache Spark の概要](../tutorials/get-started.md)
* [.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする](../tutorials/hdinsight-deployment.md)
* [.NET for Apache Spark アプリケーションを Databricks にデプロイする](../tutorials/databricks-deployment.md)
* [.NET for Apache Spark アプリケーションを Amazon EMR Spark にデプロイする](../tutorials/amazon-emr-spark-deployment.md)
