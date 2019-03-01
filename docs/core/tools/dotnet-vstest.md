---
title: dotnet vstest コマンド
description: dotnet vstest コマンドは、プロジェクトとそのすべての依存関係をビルドします。
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: d41e901f70b4a3d0647c693fdd8076f771466073
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747730"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet-vstest` - 指定されたファイルからテストを実行します。

## <a name="synopsis"></a>構文

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```
---

## <a name="description"></a>説明

`dotnet-vstest` コマンドでは、`VSTest.Console` コマンド ライン アプリケーションが実行されて、自動単体テストが実行されます。

## <a name="arguments"></a>引数

`TEST_FILE_NAMES`

指定されたアセンブリからテストを実行します。 複数のテスト アセンブリ名を指定するときは、空白で区切ります。

## <a name="options"></a>オプション

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

テストの実行時に使用される設定です。

`--Tests|/Tests:<Test Names>`

指定した値に一致する名前のテストを実行します。 複数の値を指定するときは、コンマで区切ります。

`--TestAdapterPath|/TestAdapterPath`

テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。

`--Platform|/Platform:<Platform type>`

テストの実行に使用する対象のプラットフォーム アーキテクチャです。 有効な値は `x86`、`x64`、`ARM` です。

`--Framework|/Framework:<Framework Version>`

テストの実行に使用する対象の .NET Framework バージョンです。 有効な値の例としては、`.NETFramework,Version=v4.6` や `.NETCoreApp,Version=v1.0` などがあります。 サポートされるその他の値は、`Framework40`、`Framework45`、`FrameworkCore10`、および `FrameworkUap10` です。

`--Parallel|/Parallel`

テストを並列で実行します。 既定では、コンピューター上のすべての使用可能なコアを使用できます。 runsettings ファイルの RunConfiguration ノードで MaxCpuCount プロパティを設定することにより、コア数を明示的に指定します。

`--TestCaseFilter|/TestCaseFilter:<Expression>`

指定した式に一致するテストを実行します。 `<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。 演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。 かっこ `()` はサブ式をグループ化するために使用します。

`-?|--Help|/?|/Help`

コマンドの短いヘルプを印刷します。

`--logger|/logger:<Logger Uri/FriendlyName>`

テスト結果のロガーを指定します。

* Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。 このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。 `LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

指定されたテスト コンテナーから探索されたテストをすべて一覧表示します。

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

現在のプロセスを起動する親プロセスのプロセス ID です。

`--Port|/Port:<Port>`

ソケット接続およびイベント メッセージの受信用のポートを指定します。

`--Diag|/Diag:<Path to log file>`

テスト プラットフォームの詳細ログを有効にします。 指定されたファイルにログが書き込まれます。

`--Blame|/Blame`

変更履歴モードでテストを実行します。 このオプションは、テスト ホストのクラッシュを引き起こす問題のあるテストを分離するのに役立ちます。 これは、現在のディレクトリ内に出力ファイルを *Sequence.xml* として作成します。このファイルは、クラッシュ前にテストの実行順序をキャプチャします。

`--InIsolation|/InIsolation`

分離プロセスでテストを実行します。 これにより、テストでエラーが発生しても *vstest.console.exe* プロセスが停止することは少なくなりますが、テストの実行速度は低下する可能性があります。

`@<file>`

応答ファイルを読み込んで、オプションを追加します。


`args`

アダプターに渡す追加の引数を指定します。 引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。 複数の引数を指定する場合は、空白で区切ります。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

テストの実行時に使用される設定です。

`--Tests|/Tests:<Test Names>`

指定した値に一致する名前のテストを実行します。 複数の値を指定するときは、コンマで区切ります。

`--TestAdapterPath|/TestAdapterPath`

テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。

`--Platform|/Platform:<Platform type>`

テストの実行に使用する対象のプラットフォーム アーキテクチャです。 有効な値は `x86`、`x64`、`ARM` です。

`--Framework|/Framework:<Framework Version>`

テストの実行に使用する対象の .NET Framework バージョンです。 有効な値の例としては、`.NETFramework,Version=v4.6` や `.NETCoreApp,Version=v1.0` などがあります。 サポートされる値としては、他に `Framework40`、`Framework45`、`FrameworkCore10` があります。

`--Parallel|/Parallel`

テストを並列で実行します。 既定では、コンピューター上のすべての使用可能なコアを使用できます。 runsettings ファイルの RunConfiguration ノードで MaxCpuCount プロパティを設定することにより、コア数を明示的に指定します。

`--TestCaseFilter|/TestCaseFilter:<Expression>`

指定した式に一致するテストを実行します。 `<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。 演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。 かっこ `()` はサブ式をグループ化するために使用します。

`-?|--Help|/?|/Help`

コマンドの短いヘルプを印刷します。

`--logger|/logger:<Logger Uri/FriendlyName>`

テスト結果のロガーを指定します。

* Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。 このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。 `LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

指定されたテスト コンテナーから探索されたテストをすべて一覧表示します。

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

現在のプロセスを起動する親プロセスのプロセス ID です。

`--Port|/Port:<Port>`

ソケット接続およびイベント メッセージの受信用のポートを指定します。

`--Diag|/Diag:<Path to log file>`

テスト プラットフォームの詳細ログを有効にします。 指定されたファイルにログが書き込まれます。

`args`

アダプターに渡す追加の引数を指定します。 引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。 複数の引数を指定する場合は、空白で区切ります。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

テストの実行時に使用される設定です。

`--Tests|/Tests:<Test Names>`

指定した値に一致する名前のテストを実行します。 複数の値を指定するときは、コンマで区切ります。

`--TestAdapterPath|/TestAdapterPath`

テストの実行では、指定されたパス (存在する場合) からカスタム テスト アダプターを使用します。

`--Platform|/Platform:<Platform type>`

テストの実行に使用する対象のプラットフォーム アーキテクチャです。 有効な値は `x86`、`x64`、`ARM` です。

`--Framework|/Framework:<Framework Version>`

テストの実行に使用する対象の .NET Framework バージョンです。 有効な値の例としては、`.NETFramework,Version=v4.6` や `.NETCoreApp,Version=v1.0` などがあります。 サポートされる値としては、他に `Framework40`、`Framework45`、`FrameworkCore10` があります。

`--Parallel|/Parallel`

テストを並列で実行します。 既定では、コンピューター上のすべての使用可能なコアを使用できます。 runsettings ファイルの RunConfiguration ノードで MaxCpuCount プロパティを設定することにより、コア数を明示的に指定します。

`--TestCaseFilter|/TestCaseFilter:<Expression>`

指定した式に一致するテストを実行します。 `<Expression>` の形式は `<property>Operator<value>[|&<Expression>]` です。この場合の演算子は `=`、`!=`、または `~` のいずれかになります。 演算子 `~` は 'contains' セマンティクスを持ち、`DisplayName` などの文字列プロパティに適用できます。 かっこ `()` はサブ式をグループ化するために使用します。

`-?|--Help|/?|/Help`

コマンドの短いヘルプを印刷します。

`--logger|/logger:<Logger Uri/FriendlyName>`

テスト結果のロガーを指定します。

* Team Foundation Server にテスト結果を発行するには、次のように `TfsPublisher` ロガー プロバイダーを使用します。

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Visual Studio テスト結果ファイル (TRX) に結果のログを書き込むには、`trx` ロガー プロバイダーを使用します。 このように切り替えることで、テスト結果ディレクトリに指定のログ ファイル名でファイルが作成されます。 `LogFileName` が指定されていない場合は、テスト結果を保持するために一意のファイル名が作成されます。

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

指定されたテスト コンテナーから探索されたテストをすべて一覧表示します。

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

現在のプロセスを起動する親プロセスのプロセス ID です。

`--Port|/Port:<Port>`

ソケット接続およびイベント メッセージの受信用のポートを指定します。

`--Diag|/Diag:<Path to log file>`

テスト プラットフォームの詳細ログを有効にします。 指定されたファイルにログが書き込まれます。

`args`

アダプターに渡す追加の引数を指定します。 引数は `<n>=<v>` 形式の名前と値のペアとして指定されます。この場合の `<n>` は引数名、`<v>` は引数値です。 複数の引数を指定する場合は、空白で区切ります。

---

## <a name="examples"></a>使用例

`mytestproject.dll` でテストを実行する:

`dotnet vstest mytestproject.dll`

`mytestproject.dll` でテストを実行し、カスタム名を持つカスタム フォルダーにエクスポートします。

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

`mytestproject.dll` と `myothertestproject.exe` でテストを実行する:

`dotnet vstest mytestproject.dll myothertestproject.exe`

`TestMethod1` テストを実行する:

`dotnet vstest /Tests:TestMethod1`

`TestMethod1` および `TestMethod2` テストを実行する:

`dotnet vstest /Tests:TestMethod1,TestMethod2`
