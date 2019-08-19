---
title: Apache Spark 用 .NET の概要
description: Windows で .NET Core を使用して Apache Spark アプリ用 .NET を実行する方法について説明します。
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7ce7d7aec6c15385d3d797d5a548519eea33b764
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "69577009"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>チュートリアル:Apache Spark 用 .NET の概要

このチュートリアルでは、Windows で .NET Core を使用して Apache Spark アプリ用の .NET を実行する方法について説明します。

このチュートリアルでは、次の作業を行う方法について説明します。

> [!div class="checklist"]
> * Apache Spark 用に .NET 用の Windows 環境を準備する
> * **Microsoft Spark**をダウンロードします。
> * Apache Spark アプリケーション用の単純な .NET をビルドして実行する

## <a name="prepare-your-environment"></a>環境を準備する

開始する前に、コマンドラインから、 `dotnet`、 `java` `mvn`、 `spark-shell`を実行できることを確認してください。 環境が既に準備されている場合は、次のセクションに進むことができます。 コマンドのいずれかまたはすべてを実行できない場合は、次の手順に従います。

1. [.Net Core 2.1 x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)をダウンロードしてインストールします。 SDK をインストールすると`dotnet` 、ツールチェーンがパスに追加されます。 PowerShell コマンド`dotnet --version`を使用して、インストールを確認します。

2. 最新の更新プログラムを使用して、 [Visual studio 2017](https://www.visualstudio.com/downloads/)または[visual studio 2019](https://visualstudio.microsoft.com/vs/preview/)をインストールします。 Community、Professional、または Enterprise を使用できます。 コミュニティのバージョンは無料です。

   インストール中に次のワークロードを選択します。
      * .NET デスクトップ開発
          * すべての必須コンポーネント
          * .NET Framework 4.6.1 開発ツール
      * .NET Core クロスプラットフォームの開発
          * すべての必須コンポーネント

3. [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)をインストールします。

    * オペレーティングシステムに適したバージョンを選択します。 たとえば、Windows x64 コンピューターの場合は、 **jdk-8u201-windows-x64**を選択します。
    * PowerShell コマンド`java -version`を使用して、インストールを確認します。

4. [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)をインストールします。
    * [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip)をダウンロードします。
    * ローカルディレクトリに抽出します。 たとえば、`c:\bin\apache-maven-3.6.0\` のようにします。
    * Apache Maven を[PATH 環境変数](https://www.java.com/en/download/help/path.xml)に追加します。 に`c:\bin\apache-maven-3.6.0\`抽出した場合は、を`c:\bin\apache-maven-3.6.0\bin`パスに追加します。
    * PowerShell コマンド`mvn -version`を使用して、インストールを確認します。

5. [Apache Spark 2.3 以降](https://spark.apache.org/downloads.html)をインストールします。 Apache Spark 2.4 以降はサポートされていません。
    * [Apache Spark 2.3](https://spark.apache.org/downloads.html)以降をダウンロードし、 [7-zip](https://www.7-zip.org/)や[WinZip](https://www.winzip.com/)などのツールを使用してローカルフォルダーに抽出します。 たとえば、に`c:\bin\spark-2.3.2-bin-hadoop2.7\`抽出することができます。
    * [PATH 環境変数](https://www.java.com/en/download/help/path.xml)に Apache Spark を追加します。 に`c:\bin\spark-2.3.2-bin-hadoop2.7\`抽出した場合は、を`c:\bin\spark-2.3.2-bin-hadoop2.7\bin`パスに追加します。
    * という名前`SPARK_HOME`の[新しい環境変数](https://www.java.com/en/download/help/path.xml)を追加します。 に`C:\bin\spark-2.3.2-bin-hadoop2.7\`抽出した場合は`C:\bin\spark-2.3.2-bin-hadoop2.7\` 、変数の**値**にを使用します。
    * コマンドラインから実行`spark-shell`できることを確認します。

6. [Winutils](https://github.com/steveloughran/winutils)をセットアップします。
    * Winutils [リポジトリ](https://github.com/steveloughran/winutils)から winutils バイナリをダウンロードします。 Spark ディストリビューションがコンパイルされた Hadoop のバージョンを選択します。 たとえば、 **Spark 2.3.2**には**2.7.1**を使用します。 Hadoop のバージョンは、Spark インストールフォルダー名の最後に注釈が付けられます。
    * Winutilsバイナリを任意のディレクトリに保存します。 たとえば、`c:\hadoop\bin` のようにします。
    * を`HADOOP_HOME`指定せず`bin`に、 **winutils**を含むディレクトリを反映するように設定します。 たとえば、`c:\hadoop` のようにします。
    * PATH 環境変数を含める`%HADOOP_HOME%\bin`ように設定します。

次のセクションに進む前`dotnet`に、 `mvn`コマンド`spark-shell`ラインから、、を実行`java`できることを再度確認します。

## <a name="download-the-microsoftsparkworker-release"></a>Microsoft の Spark. ワーカーリリースのダウンロード

1. .NET for Apache Spark GitHub リリースページからローカルコンピューターに、 [Microsoft Spark. ワーカー](https://github.com/dotnet/spark/releases)リリースをダウンロードします。 たとえば、というパス`c:\bin\Microsoft.Spark.Worker\`にダウンロードできます。

2. という名前`DotnetWorkerPath`の[新しい環境変数](https://www.java.com/en/download/help/path.xml)を作成し、これをダウンロードして、 **Microsoft の Spark**を展開したディレクトリに設定します。 たとえば、`c:\bin\Microsoft.Spark.Worker` のようにします。

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Apache Spark GitHub リポジトリ用の .NET の複製

次の[GitBash](https://gitforwindows.org/)コマンドを使用して、Apache Spark リポジトリ用の .net をコンピューターに複製します。

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Apache Spark アプリ用の .NET を作成する

1. **Visual Studio**を開き、**ファイル > 新しいプロジェクトの作成 > コンソールアプリ (.net Core)** の順に移動します。 アプリケーションに**HelloSpark**という名前を指定します。

2. [Microsoft Spark NuGet パッケージ](https://www.nuget.org/profiles/spark)をインストールします。 NuGet パッケージのインストールの詳細については、「 [Nuget パッケージをインストールするさまざまな方法](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package)」を参照してください。

3. **ソリューションエクスプローラー**で、 **Program.cs**を開き、次C#のコードを記述します。

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. ソリューションをビルドします。

## <a name="run-your-net-for-apache-spark-app"></a>.NET for Apache Spark アプリを実行する

1. **PowerShell**を開き、ディレクトリをアプリが格納されているフォルダーに変更します。

   ```powershell
   cd <your-app-output-directory>
   ```

2. 次の内容を使用して、" **people. json** " という名前のファイルを作成します。

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

おめでとうございます! Apache Spark アプリ用の .NET の作成と実行が正常に完了しました。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * Apache Spark 用に .NET 用の Windows 環境を準備する
> * **Microsoft Spark**をダウンロードします。
> * Apache Spark アプリケーション用の単純な .NET をビルドして実行する

詳細については、「リソース」ページを参照してください。
> [!div class="nextstepaction"]
> [Apache Spark リソース用 .NET](../resources/index.md)
