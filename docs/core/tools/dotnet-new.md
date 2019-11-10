---
title: dotnet new コマンド
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420474"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。

## <a name="synopsis"></a>構文

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>説明

`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。

このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。

## <a name="arguments"></a>引数

`TEMPLATE`

コマンドが呼び出されたときにインスタンス化するテンプレート。 各テンプレートには、渡すことができるオプションが存在する場合があります。 詳細については、[テンプレートのオプション](#template-options)を参照してください。

`TEMPLATE` の値が「**テンプレート**」列または「**短い形式の名前**」列のテキストと完全に一致しない場合、それら 2 つの列で部分文字列一致が実行されます。

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。 次の表は、.NET Core SDK 2.2.100 にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

| テンプレート                                    | 短い形式の名前        | 言語     | Tags                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| コンソール アプリケーション                          | `console`         | [C#], F#, VB | Common/Console                        |
| クラス ライブラリ                                | `classlib`        | [C#], F#, VB | Common/Library                        |
| 単体テスト プロジェクト                            | `mstest`          | [C#], F#, VB | Test/MSTest                           |
| NUnit 3 テスト プロジェクト                         | `nunit`           | [C#], F#, VB | Test/NUnit                            |
| NUnit 3 テスト項目                            | `nunit-test`      | [C#], F#, VB | Test/NUnit                            |
| xUnit テスト プロジェクト                           | `xunit`           | [C#], F#, VB | Test/xUnit                            |
| Razor ページ                                   | `page`            | [C#]         | Web/ASP.NET                           |
| MVC ViewImports                              | `viewimports`     | [C#]         | Web/ASP.NET                           |
| MVC ViewStart                                | `viewstart`       | [C#]         | Web/ASP.NET                           |
| ASP.NET Core 空                           | `web`             | [C#], F#     | Web/Empty                             |
| ASP.NET Core Web アプリ (モデル ビュー コントローラー) | `mvc`             | [C#], F#     | Web/MVC                               |
| ASP.NET Core Web アプリ                         | `webapp`、 `razor` | [C#]         | Web/MVC/Razor Pages                   |
| Angular 付きの ASP.NET Core                    | `angular`         | [C#]         | Web/MVC/SPA                           |
| React.js 付きの ASP.NET Core                   | `react`           | [C#]         | Web/MVC/SPA                           |
| React.js および Redux 付きの ASP.NET Core         | `reactredux`      | [C#]         | Web/MVC/SPA                           |
| Razor クラス ライブラリ                          | `razorclasslib`   | [C#]         | Web/Razor/Library/Razor Class Library |
| ASP.NET Core Web API                         | `webapi`          | [C#], F#     | Web/WebAPI                            |
| global.json file                             | `globaljson`      |              | 構成                                |
| NuGet 構成                                 | `nugetconfig`     |              | 構成                                |
| Web 構成                                   | `webconfig`       |              | 構成                                |
| ソリューション ファイル                                | `sln`             |              | ソリューション                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。 次の表は、.NET Core SDK 2.1.300 にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

| テンプレート                                    | 短い形式の名前      | 言語     | Tags                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| コンソール アプリケーション                          | `console`       | [C#], F#, VB | Common/Console                        |
| クラス ライブラリ                                | `classlib`      | [C#], F#, VB | Common/Library                        |
| 単体テスト プロジェクト                            | `mstest`        | [C#], F#, VB | Test/MSTest                           |
| xUnit テスト プロジェクト                           | `xunit`         | [C#], F#, VB | Test/xUnit                            |
| Razor ページ                                   | `page`          | [C#]         | Web/ASP.NET                           |
| MVC ViewImports                              | `viewimports`   | [C#]         | Web/ASP.NET                           |
| MVC ViewStart                                | `viewstart`     | [C#]         | Web/ASP.NET                           |
| ASP.NET Core 空                           | `web`           | [C#], F#     | Web/Empty                             |
| ASP.NET Core Web アプリ (モデル ビュー コントローラー) | `mvc`           | [C#], F#     | Web/MVC                               |
| ASP.NET Core Web アプリ                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| Angular 付きの ASP.NET Core                    | `angular`       | [C#]         | Web/MVC/SPA                           |
| React.js 付きの ASP.NET Core                   | `react`         | [C#]         | Web/MVC/SPA                           |
| React.js および Redux 付きの ASP.NET Core         | `reactredux`    | [C#]         | Web/MVC/SPA                           | 
| Razor クラス ライブラリ                          | `razorclasslib` | [C#]         | Web/Razor/Library/Razor Class Library |
| ASP.NET Core Web API                         | `webapi`        | [C#], F#     | Web/WebAPI                            |
| global.json file                             | `globaljson`    |              | 構成                                |
| NuGet 構成                                 | `nugetconfig`   |              | 構成                                |
| Web 構成                                   | `webconfig`     |              | 構成                                |
| ソリューション ファイル                                | `sln`           |              | ソリューション                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。 次の表は、.NET Core SDK 2.0.0 にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

| テンプレート                                    | 短い形式の名前    | 言語     | Tags                |
|----------------------------------------------|---------------|--------------|---------------------|
| コンソール アプリケーション                          | `console`     | [C#], F#, VB | Common/Console      |
| クラス ライブラリ                                | `classlib`    | [C#], F#, VB | Common/Library      |
| 単体テスト プロジェクト                            | `mstest`      | [C#], F#, VB | Test/MSTest         |
| xUnit テスト プロジェクト                           | `xunit`       | [C#], F#, VB | Test/xUnit          |
| ASP.NET Core 空                           | `web`         | [C#], F#     | Web/Empty           |
| ASP.NET Core Web アプリ (モデル ビュー コントローラー) | `mvc`         | [C#], F#     | Web/MVC             |
| ASP.NET Core Web アプリ                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| Angular 付きの ASP.NET Core                    | `angular`     | [C#]         | Web/MVC/SPA         |
| React.js 付きの ASP.NET Core                   | `react`       | [C#]         | Web/MVC/SPA         |
| React.js および Redux 付きの ASP.NET Core         | `reactredux`  | [C#]         | Web/MVC/SPA         |
| ASP.NET Core Web API                         | `webapi`      | [C#], F#     | Web/WebAPI          |
| global.json file                             | `globaljson`  |              | 構成              |
| NuGet 構成                                 | `nugetconfig` |              | 構成              |
| Web 構成                                   | `webconfig`   |              | 構成              |
| ソリューション ファイル                                | `sln`         |              | ソリューション            |
| Razor ページ                                   | `page`        |              | Web/ASP.NET         |
| MVC ViewImports                              | `viewimports` |              | Web/ASP.NET         |
| MVC ViewStart                                | `viewstart`   |              | Web/ASP.NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。 次の表は、.NET Core SDK 1.0.1 にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

| テンプレート            | 短い形式の名前    | 言語 | Tags           |
|----------------------|---------------|----------|----------------|
| コンソール アプリケーション  | `console`     | [C#], F# | Common/Console |
| クラス ライブラリ        | `classlib`    | [C#], F# | Common/Library |
| 単体テスト プロジェクト    | `mstest`      | [C#], F# | Test/MSTest    |
| xUnit テスト プロジェクト   | `xunit`       | [C#], F# | Test/xUnit     |
| ASP.NET Core 空   | `web`         | [C#]     | Web/Empty      |
| ASP.NET Core Web アプリ | `mvc`         | [C#], F# | Web/MVC        |
| ASP.NET Core Web API | `webapi`      | [C#]     | Web/WebAPI     |
| NuGet 構成         | `nugetconfig` |          | 構成         |
| Web 構成           | `webconfig`   |          | 構成         |
| ソリューション ファイル        | `sln`         |          | ソリューション       |

---

## <a name="options"></a>オプション

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

`--dry-run`

指定されたコマンドが実行されてテンプレートが作成された場合に起きることの概要が表示されます。

`--force`

既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-i|--install <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。 テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。 既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。 「[使用例](#examples)」のセクションで、例をご覧ください。

カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#|VB}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

> [!NOTE]
> 一部のシェルは `#` を特殊文字として解釈します。 そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`--nuget-source`

インストール中に使用する NuGet ソースを 1 つ指定します。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

`--type`

使用可能な種類に基づいて、テンプレートをフィルター処理します。 定義済みの値は、"project"、"item"、または "other" です。

`-u|--uninstall <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。 `<PATH|NUGET_ID>` 値を除外すると、現在インストールされているすべてのテンプレート パックとそれらに関連付けられているテンプレートが表示されます。

> [!NOTE]
> `PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。 たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。
> また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--force`

既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-i|--install <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。 テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。 既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。 「[使用例](#examples)」のセクションで、例をご覧ください。

カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#|VB}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

> [!NOTE]
> 一部のシェルは `#` を特殊文字として解釈します。 そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`--nuget-source`

インストール中に使用する NuGet ソースを 1 つ指定します。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

`--type`

使用可能な種類に基づいて、テンプレートをフィルター処理します。 定義済みの値は、"project"、"item"、または "other" です。

`-u|--uninstall <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。

> [!NOTE]
> `PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。 たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。
> また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--force`

既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-i|--install <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。 テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。 既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。 「[使用例](#examples)」のセクションで、例をご覧ください。

カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#|VB}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

> [!NOTE]
> 一部のシェルは `#` を特殊文字として解釈します。 そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

`--type`

使用可能な種類に基づいて、テンプレートをフィルター処理します。 定義済みの値は、"project"、"item"、または "other" です。

`-u|--uninstall <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。

> [!NOTE]
> ソース `PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。 たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、 *./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。 また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。
> 
> テンプレートのアンインストールに必要な `PATH` または `NUGET_ID` 引数を決定できない場合、引数なしで `dotnet new --uninstall` を実行するとインストールされているすべてのテンプレートと、それをアンインストールするために必要な引数が一覧表示されます。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。 `dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

> [!NOTE]
> 一部のシェルは `#` を特殊文字として解釈します。 そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

---

## <a name="template-options"></a>テンプレート オプション

プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。 コア テンプレートの場合、次のオプションが追加されています。

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

**console**

`--langVersion <VERSION_NUMBER>` - 作成されたプロジェクト ファイルの `LangVersion` プロパティを設定します。 たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。 F# に対してはサポートされません。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**angular、react、reactredux**

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

`--no-https` - プロジェクトは HTTPS を必要としません。 このオプションは、`IndividualAuth` または `OrganizationalAuth` が使用されない場合にのみ適用されます。

**razorclasslib**

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**classlib**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: .NET Core クラス ライブラリを作成するには `netcoreapp2.2`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。 既定値は `netstandard2.0` です。

`--langVersion <VERSION_NUMBER>` - 作成されたプロジェクト ファイルの `LangVersion` プロパティを設定します。 たとえば、C# 7.3 を使うには `--langVersion 7.3` を使います。 F# に対してはサポートされません。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mstest, xunit**

`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**nunit**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 既定値は `netcoreapp2.1` です。

`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**page**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

`-np|--no-pagemodel` - PageModel なしでページを作成します。

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

**web**

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

`--no-https` - プロジェクトは HTTPS を必要としません。 このオプションは、`IndividualAuth` または `OrganizationalAuth` が使用されない場合にのみ適用されます。

**mvc、webapp**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `Individual` - 個別認証です。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `MultiOrg` - 複数のテナントに対する組織認証です。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証または `MultiOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `/signin-oidc` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--no-https` - プロジェクトは HTTPS を必要としません。 `app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。 このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証または `SingleOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--no-https` - プロジェクトは HTTPS を必要としません。 `app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。 このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**globaljson**

`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

**console, angular, react, reactredux, razorclasslib**

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**classlib**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: .NET Core クラス ライブラリを作成するには `netcoreapp2.1`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。 既定値は `netstandard2.0` です。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mstest, xunit**

`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**globaljson**

`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。

**web**

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

`--no-https` - プロジェクトは HTTPS を必要としません。 このオプションは、`IndividualAuth` または `OrganizationalAuth` が使用されない場合にのみ適用されます。

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証または `SingleOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

`--no-https` - プロジェクトは HTTPS を必要としません。 `app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。 このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `Individual` - 個別認証です。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `MultiOrg` - 複数のテナントに対する組織認証です。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証または `MultiOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `/signin-oidc` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--exclude-launch-settings` - 生成されたテンプレートから *launchSettings.json* を除外します。

`--use-browserlink` - プロジェクトに BrowserLink を含めます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

`--no-https` - プロジェクトは HTTPS を必要としません。 `app.UseHsts` と `app.UseHttpsRedirection` は `Startup.Configure` に追加されません。 このオプションは、`Individual`、`IndividualB2C`、`SingleOrg`、または `MultiOrg` が使用されない場合にのみ適用されます。

**page**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

`-np|--no-pagemodel` - PageModel なしでページを作成します。

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

**console, angular, react, reactredux**

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**classlib**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。 既定値は `netstandard2.0` です。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mstest, xunit**

`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**globaljson**

`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。

**web**

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証または `SingleOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `Individual` - 個別認証です。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `MultiOrg` - 複数のテナントに対する組織認証です。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証または `MultiOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `/signin-oidc` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`--use-browserlink` - プロジェクトに BrowserLink を含めます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**page**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

`-np|--no-pagemodel` - PageModel なしでページを作成します。

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console、xunit、mstest、web、webapi**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` です。 既定値は `netcoreapp1.0` です。

**classlib**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。 既定値は `netstandard1.4` です。

**mvc**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` です。 既定値は `netcoreapp1.0` です。

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 値: `None` または `Individual` です。 既定値は `None` です。

`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。 値: `true` または `false` です。 既定値は `false` です。

---

## <a name="examples"></a>使用例

テンプレート名を指定することによって、C# コンソール アプリケーション プロジェクトを作成します。

`dotnet new "Console Application"`

現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。

`dotnet new console -lang F#`

指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core SDK 2.0 またはそれ以降のバージョンでのみ使用可能)。

`dotnet new classlib -lang VB -o MyLibrary`

認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC プロジェクトを作成します。

`dotnet new mvc -au None`

新しい xUnit プロジェクトを作成します。

`dotnet new xunit`

MVC に利用できるすべてのテンプレートを一覧表示します。

`dotnet new mvc -l`

部分文字列 *we* に一致するすべてのテンプレートの一覧を取得します。 完全一致が見つからないので、短い名前と名前の両方の列に対して部分文字列一致が実行されます。

`dotnet new we -l`

*ng* に一致するテンプレートの呼び出しを試みます。 一致が 1 つだけでない場合、部分的に一致するテンプレートの一覧を取得します。

`dotnet new ng`

ASP.NET Core のシングル ページ アプリケーション テンプレートのバージョン 2.0 をインストールします (コマンド オプションは .NET Core SDK 1.1 以降のバージョンでのみ使用できます):

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

SDK バージョン 2.0.0 (.NET Core SDK 2.0 以降のバージョンでのみ使用できます) を設定している現在のディレクトリ内に *global.json* を作成します。

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>関連項目

- [dotnet new のカスタム テンプレート](custom-templates.md)
- [dotnet new のカスタム テンプレートを作成する](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-template-samples GitHub リポジトリ](https://github.com/dotnet/dotnet-template-samples)
- [dotnet new で使用できるテンプレート](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
