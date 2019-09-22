---
title: dotnet tool update コマンド
description: dotnet tool update コマンドは、マシン上の指定された .NET Core グローバル ツールを更新します。
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117529"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>name

`dotnet tool update` - マシン上の指定された [.NET Core グローバル ツール](global-tools.md) を更新します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>説明

`dotnet tool update` コマンドは、マシン上の指定された .NET Core グローバル ツールをパッケージの最新の安定バージョンに更新するための手段を提供します。 このコマンドは、ツールをアンインストールして再インストールして、効果的に更新します。 コマンドを使用するには、`--global` オプションを使用してユーザー全体のインストールからツールを更新することを指定するか、`--tool-path` オプションを使用してツールがインストールされている場所へのパスを指定する必要があります。

## <a name="arguments"></a>引数

`PACKAGE_NAME`

更新する .NET Core グローバル ツールが格納されている NuGet パッケージの名前または ID。 パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。

## <a name="options"></a>オプション

`--add-source <SOURCE>`

インストール時に使用するために追加の NuGet パッケージ ソースを追加します。

`--configfile <FILE>`

使用する NuGet 構成 (*nuget.config*) ファイル。

`--framework <FRAMEWORK>`

ツールを更新する[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。

`-g|--global`

更新プログラムがユーザー全体のツール用であることを指定します。 `--tool-path` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--tool-path <PATH>`

グローバル ツールがインストールされている場所を指定します。 パスは絶対パスでも相対パスでもかまいません。 `--global` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--global` オプションを指定する必要があります。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

## <a name="examples"></a>使用例

[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。

`dotnet tool update -g dotnetsay`

特定の Windows フォルダーに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。

`dotnet tool update dotnetsay --tool-path c:\global-tools`

特定の Linux/macOS フォルダーに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>関連項目

- [.NET Core グローバル ツール](global-tools.md)
