---
title: Windows で .NET for Apache Spark アプリケーションをデバッグする
description: Windows で .NET for Apache Spark アプリケーションをデバッグする方法について学習します。
ms.date: 08/15/2019
ms.topic: how-to
ms.custom: mvc
ms.openlocfilehash: 08142bd45c475ddd131053213ebdea5f843fa736
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667670"
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