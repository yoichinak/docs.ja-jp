---
title: dotnet help コマンド
description: dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。
ms.date: 08/08/2019
ms.openlocfilehash: e76f858f2529afc50646473f1aab9d52730cff16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990460"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

**この記事の対象: ✓** .NET Core 2.0 SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>name

`dotnet help` - 指定したコマンドについて、より詳細なドキュメントがオンラインで表示されます。

## <a name="synopsis"></a>構文

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>説明

`dotnet help` コマンドは、docs.microsoft.com で、指定したコマンドに関する詳細情報のリファレンス ページを開きます。

## <a name="arguments"></a>引数

* **`COMMAND_NAME`**

  .NET Core CLI コマンドの名前です。 有効な CLI コマンドの一覧については、[CLI コマンド](index.md#cli-commands)を参照してください。

## <a name="options"></a>オプション

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

## <a name="examples"></a>使用例

* ドキュメントの [dotnet new](dotnet-new.md) コマンドに関するページを開きます。

  ```console
  dotnet help new
  ```
