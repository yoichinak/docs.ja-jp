---
title: dotnet migrate コマンド
description: dotnet migrate コマンドは、プロジェクトとそのすべての依存関係を移行します。
ms.date: 05/25/2018
ms.openlocfilehash: 861cd2cb982c6f41baf00a2cbd7e04b26816af76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631944"
---
# <a name="dotnet-migrate"></a>dotnet の移行

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet migrate` - Preview 2 .NET Core プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。

## <a name="synopsis"></a>構文

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>説明

`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトを有効な .NET Core SDK 1.0 *csproj* プロジェクトに移行します。

既定では、このコマンドは、ルート プロジェクトとルート プロジェクトに含まれるすべてのプロジェクト参照を移行します。 この動作は、実行時に `--skip-project-references` オプションを使って、無効にすることができます。

移行は次のアセットで実行できます。

* 1 つのプロジェクト。移行する *project.json* ファイルを指定します。
* *global.json* ファイルで指定されているすべてのディレクトリ。*global.json* ファイルへのパスを渡します。
* *solution.sln* ファイル。ソリューションで参照されているプロジェクトを移行します。
* 特定のディレクトリのすべてのサブディレクトリ (再帰的)。

`dotnet migrate` コマンドは、`backup` ディレクトリ内に移行された *project.json* ファイルを保持します。ディレクトリが存在しない場合は作成されます。 この動作は、`--skip-backup` オプションを使ってオーバーライドされます。

既定では、移行操作は、標準出力 (STDOUT) に移行プロセスの状態を出力します。 `--report-file <REPORT_FILE>` オプションを使うと、指定したファイルに出力が保存を指定します。

`dotnet migrate` コマンドは、有効な Preview 2 *project.json* ベースのプロジェクトのみをサポートします。 つまり、DNX または Preview 1 の *project.json* ベースのプロジェクトを MSBuild/csproj プロジェクトに直接移行するためには使えません。 最初にプロジェクトを Preview 2 *project.json* ベースのプロジェクトに手動で移行し、その後で `dotnet migrate` コマンドを使ってプロジェクトを移行する必要があります。

## <a name="arguments"></a>引数

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

次のいずれかへのパスです。

* 移行する *project.json* ファイル。
* *global.json* ファイル: *global.json* で指定されているフォルダーを移行します。
* *solution.sln* ファイル: ソリューションで参照されているプロジェクトを移行します。
* 移行するディレクトリ: 移行する *project.json* ファイルを再帰的に検索して、指定したディレクトリ内に移行します。

何も指定しない場合の既定値は現在のディレクトリです。

## <a name="options"></a>オプション

`--format-report-file-json <REPORT_FILE>`

ユーザー メッセージではなく、JSON として移行レポート ファイルを出力します。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-r|--report-file <REPORT_FILE>`

移行レポートをコンソールだけでなく、ファイルに出力します。

`-s|--skip-project-references [Debug|Release]`

プロジェクト参照の移行をスキップします。 既定では、プロジェクト参照は再帰的に移行されます。

`--skip-backup`

移行が成功した後、*project.json*、*global.json*、および *\*.xproj* の `backup` ディレクトリへの移動をスキップします。

`-t|--template-file <TEMPLATE_FILE>`

移行に使用するテンプレートの csproj ファイル。 既定では、`dotnet new console` によってドロップされるテンプレートと同じテンプレートが使用されます。

`-v|--sdk-package-version <VERSION>`

移行されたアプリで参照される sdk パッケージのバージョンです。 既定値は、`dotnet new` 内の SDK のバージョンです。

`-x|--xproj-file <FILE>`

使用する xproj ファイルへのパス。 プロジェクト ディレクトリに複数の xproj がある場合に必要です。

## <a name="examples"></a>使用例

現在のディレクトリのプロジェクトとそのプロジェクト間の依存関係をすべて移行します。

`dotnet migrate`

*global.json* ファイルに含まれるすべてのプロジェクトを移行します。

`dotnet migrate path/to/global.json`

現在のプロジェクトのみを移行し、プロジェクト間 (P2P) の依存関係は移行しません。 また、特定の SDK バージョンを使います。

`dotnet migrate -s -v 1.0.0-preview4`
