---
title: dotnet tool uninstall コマンド
description: dotnet tool uninstall コマンドは、マシン上の指定された .NET Core グローバル ツールをアンインストールします。
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680924"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>name

`dotnet tool uninstall` - マシン上の指定された [.NET Core グローバル ツール](global-tools.md)をアンインストールします。

## <a name="synopsis"></a>構文

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>説明

`dotnet tool uninstall` コマンドは、自分のマシンから .NET Core グローバル ツールをアンインストールするための手段を提供します。 コマンドを使用するには、`--global` オプションを使用してユーザー全体のツールを更新するか、`--tool-path` オプションを使用してツールがインストールされている場所へのパスを指定する必要があります。

## <a name="arguments"></a>引数

`PACKAGE_NAME`

アンインストールする .NET Core グローバル ツールを含む、NuGet パッケージの名前または ID。 パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。

## <a name="options"></a>オプション

`-g|--global`

ツールがユーザー全体のインストールから削除されることを指定します。 `--tool-path` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。

`-h|--help`

コマンドの短いヘルプを印刷します。

`--tool-path <PATH>`

グローバル ツールをアンインストールする場所を指定します。 パスは絶対パスでも相対パスでもかまいません。 `--global` オプションと組み合わせることはできません。 このオプションを指定しない場合は、`--global` オプションを指定する必要があります。

## <a name="examples"></a>使用例

[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

`dotnet tool uninstall -g dotnetsay`

特定の Windows フォルダーから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

特定の Linux/macOS フォルダーから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>関連項目

- [.NET Core グローバル ツール](global-tools.md)
