---
title: dotnet help コマンド
description: dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503731"
---
# <a name="dotnet-help-reference"></a>dotnet help リファレンス

**この記事の対象:** ✔️ .NET Core 2.0 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet help` - 指定したコマンドについて、より詳細なドキュメントがオンラインで表示されます。

## <a name="synopsis"></a>構文

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>説明

`dotnet help` コマンドは、docs.microsoft.com で、指定したコマンドに関する詳細情報のリファレンス ページを開きます。

## <a name="arguments"></a>引数

- **`COMMAND_NAME`**

  .NET Core CLI コマンドの名前です。 有効な CLI コマンドの一覧については、[CLI コマンド](index.md#cli-commands)を参照してください。

## <a name="options"></a>オプション

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

## <a name="examples"></a>使用例

- ドキュメントの [dotnet new](dotnet-new.md) コマンドに関するページを開きます。

  ```dotnetcli
  dotnet help new
  ```
