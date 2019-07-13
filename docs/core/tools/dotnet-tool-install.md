---
title: dotnet tool install コマンド
description: dotnet tool install コマンドでは、使用しているマシンに指定された .NET Core グローバル ツールをインストールします。
ms.date: 05/29/2018
ms.openlocfilehash: 1348eb1165c77376a885fdcbf094bd17b2aa3514
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563705"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>name

`dotnet tool install` - 使用しているマシンに指定された [.NET Core グローバル ツール](global-tools.md)をインストールします。

## <a name="synopsis"></a>構文

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>説明

`dotnet tool install` コマンドでは、使用しているマシンに .NET Core グローバル ツールをインストールするための手段を提供します。 コマンドを使用するには、`--global` オプションを使用してユーザー全体のインストールを指定するか、`--tool-path` オプションを使用してツールをインストールするパスを指定する必要があります。

グローバル ツールは、`-g` (または `--global`) オプションを指定した場合、既定では次のディレクトリにインストールされます。

| OS          | パス                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>引数

`PACKAGE_NAME`

インストールする .NET Core グローバル ツールを含む、NuGet パッケージの名前または ID。

## <a name="options"></a>オプション

`--add-source <SOURCE>`

インストール時に使用するために追加の NuGet パッケージ ソースを追加します。

`--configfile <FILE>`

使用する NuGet 構成 (*nuget.config*) ファイル。

`--framework <FRAMEWORK>`

ツールをインストールする[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。 既定では、.NET Core SDK は最適なターゲット フレームワークの選択を試みます。

`-g|--global`

ユーザー全体のインストールを指定します。 `--tool-path` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--tool-path <PATH>`

グローバル ツールをインストールする場所を指定します。 PATH は絶対パスでも相対パスでもかまいません。 PATH が存在しない場合、コマンドではパスの作成を試みます。 `--global` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--global` オプションを指定する必要があります。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`--version <VERSION_NUMBER>`

インストールするツールのバージョン。 既定では、安定した最新バージョンのパッケージがインストールされます。 このオプションを使用して、プレビューまたは古いバージョンのツールをインストールします。

## <a name="examples"></a>使用例

既定の場所に [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。

`dotnet tool install -g dotnetsay`

特定の Windows フォルダーに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。

`dotnet tool install dotnetsay --tool-path c:\global-tools`

特定の Linux/macOS フォルダーに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。

`dotnet tool install dotnetsay --tool-path ~/bin`

バージョン 2.0.0 の [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>関連項目

- [.NET Core グローバル ツール](global-tools.md)
