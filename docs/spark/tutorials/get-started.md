---
title: .NET for Apache Spark の概要
description: Windows で .NET Core を使用して .NET for Apache Spark アプリを実行する方法について説明します。
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577009"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>チュートリアル: .NET for Apache Spark の概要

このチュートリアルでは、Windows で .NET Core を使用して .NET for Apache Spark アプリを実行する方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * .NET for Apache Spark 用に Windows 環境を準備する
> * **Microsoft.Spark.Worker** をダウンロードする
> * .NET for Apache Spark アプリケーション用の単純な .NET をビルドして実行する

## <a name="prepare-your-environment"></a>環境を準備する

開始する前に、コマンド ラインから `dotnet`、`java`、`mvn`、`spark-shell` を実行できることを確認してください。 環境が既に準備されている場合は、次のセクションに進むことができます。 コマンドのいずれかまたはすべてを実行できない場合は、次の手順に従います。

1. [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1) をダウンロードしてインストールします。 SDK をインストールすると、`dotnet` ツールチェーンが PATH に追加されます。 PowerShell コマンド `dotnet --version` を使用して、インストールを確認します。

2. 最新の更新プログラムを使用して、[Visual Studio 2017](https://www.visualstudio.com/downloads/) または [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) をインストールします。 Community、Professional、Enterprise のいずれかを使用できます。 Community バージョンは無料です。

   インストール時に次のワークロードを選択します。
      * .NET デスクトップ開発
          * すべての必須コンポーネント
          * .NET Framework 4.6.1 開発ツール
      * .NET Core クロスプラットフォームの開発
          * すべての必須コンポーネント

3. [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) をインストールします。

    * ご使用のオペレーティング システムに適したバージョンを選択します。 たとえば、Windows x64 マシンには、**jdk-8u201-windows-x64.exe** を選択します。
    * PowerShell コマンド `java -version` を使用して、インストールを確認します。

4. [Apache Maven 3.6.0 以降](https://maven.apache.org/download.cgi)をインストールします。
    * [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip) をダウンロードします。
    * ローカル ディレクトリに抽出します。 たとえば、`c:\bin\apache-maven-3.6.0\` のようにします。
    * Apache Maven をご自分の [PATH 環境変数](https://www.java.com/en/download/help/path.xml)に追加します。 `c:\bin\apache-maven-3.6.0\` に抽出した場合は、`c:\bin\apache-maven-3.6.0\bin` を PATH に追加します。
    * PowerShell コマンド `mvn -version` を使用して、インストールを確認します。

5. [Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)をインストールします。 Apache Spark 2.4 以降はサポートされていません。
    * [Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)をダウンロードし、[7-zip](https://www.7-zip.org/) や [WinZip](https://www.winzip.com/) などのツールを使用してローカル フォルダーに抽出します。 たとえば、`c:\bin\spark-2.3.2-bin-hadoop2.7\` に抽出します。
    * Apache Spark をご自分の [PATH 環境変数](https://www.java.com/en/download/help/path.xml)に追加します。 `c:\bin\spark-2.3.2-bin-hadoop2.7\` に抽出した場合は、`c:\bin\spark-2.3.2-bin-hadoop2.7\bin` を PATH に追加します。
    * `SPARK_HOME` という[新しい環境変数](https://www.java.com/en/download/help/path.xml)を追加します。 `C:\bin\spark-2.3.2-bin-hadoop2.7\` に抽出した場合は、**変数値**に `C:\bin\spark-2.3.2-bin-hadoop2.7\` を使用します。
    * コマンド ラインから `spark-shell` を実行できることを確認します。

6. [WinUtils](https://github.com/steveloughran/winutils) を設定します。
    * [Winutils リポジトリ](https://github.com/steveloughran/winutils)から **winutils.exe** バイナリをダウンロードします。 Spark ディストリビューションをコンパイルした Hadoop のバージョンを選択します。 たとえば、**Spark 2.3.2** には **hadoop-2.7.1** を使用します。 Hadoop のバージョンは、Spark インストール フォルダー名の末尾に注釈付けされています。
    * **winutils.exe** バイナリを任意のディレクトリに保存します。 たとえば、`c:\hadoop\bin` のようにします。
    * **winutils.exe** 含むディレクトリを反映するように、`bin` なしで `HADOOP_HOME` を設定します。 たとえば、`c:\hadoop` のようにします。
    * `%HADOOP_HOME%\bin` が含まれるように PATH 環境変数を設定します。

次のセクションに進む前に、コマンド ラインから `dotnet`、`java`、`mvn`、`spark-shell` を実行できることを再度確認します。

## <a name="download-the-microsoftsparkworker-release"></a>Microsoft.Spark.Worker リリースをダウンロードする

1. .NET for Apache Spark GitHub リリース ページから、[Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) リリースをローカル コンピューターにダウンロードします。 たとえば、`c:\bin\Microsoft.Spark.Worker\` というパスにダウンロードできます。

2. `DotnetWorkerPath` という名前の[新しい環境変数](https://www.java.com/en/download/help/path.xml)を作成し、**Microsoft.Spark.Worker** をダウンロードして抽出したディレクトリに設定します。 たとえば、`c:\bin\Microsoft.Spark.Worker` のようにします。

## <a name="clone-the-net-for-apache-spark-github-repo"></a>.NET for Apache Spark GitHub リポジトリの複製

次の [GitBash](https://gitforwindows.org/) コマンドを使用して、.NET for Apache Spark リポジトリをご使用のマシンに複製します。

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>.NET for Apache Spark アプリを作成する

1. **Visual Studio** を開き、 **[ファイル]、[新しいプロジェクトの作成]、[コンソール アプリ (.NET Core)]** の順に移動します。 アプリケーションに「**HelloSpark**」という名前を付けます。

2. [Microsoft.Spark NuGet パッケージ](https://www.nuget.org/profiles/spark)をインストールします。 Nuget パッケージのインストールの詳細については、[NuGet パッケージをインストールするためのさまざまな方法](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package)に関するページを参照してください。

3. **ソリューション エクスプローラー**で、**Program.cs** を開き、次の C# コードを記述します。

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. ソリューションをビルドします。

## <a name="run-your-net-for-apache-spark-app"></a>.NET for Apache Spark アプリを実行する

1. **PowerShell** を開き、ディレクトリを、アプリが格納されているフォルダーに変更します。

   ```powershell
   cd <your-app-output-directory>
   ```

2. 次の内容を含む **people.json** という名前のファイルを作成します。

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. 次の PowerShell コマンドを使用して、アプリを実行します。

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

おめでとうございます! .NET for Apache Spark アプリの作成と実行が正常に完了しました。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * .NET for Apache Spark 用に Windows 環境を準備する
> * **Microsoft.Spark.Worker** をダウンロードする
> * .NET for Apache Spark アプリケーション用の単純な .NET をビルドして実行する

詳細については、リソースのページを参照してください。
> [!div class="nextstepaction"]
> [.NET for Apache Spark のリソース](../resources/index.md)
