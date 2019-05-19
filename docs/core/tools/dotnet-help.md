---
title: dotnet help コマンド
description: dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。
ms.date: 12/04/2018
ms.openlocfilehash: 8694494720cdb9a540754fdf79eeb99d5dbe61ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631976"
---
# <a name="dotnet-help-reference"></a>dotnet help reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

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
