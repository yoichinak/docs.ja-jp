---
title: dotnet build-server コマンド
description: dotnet build-server コマンドは、ビルドによって起動されたサーバーとやり取りします。
ms.date: 04/24/2019
ms.openlocfilehash: 1c6c6dcdb53d779426daf5daa470d2ad0470a7a1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523017"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**この記事の対象: ✓** .NET Core 2.1 SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>name

`dotnet build-server` - ビルドによって起動されたサーバーとやり取りします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>コマンド

- **`shutdown`**

  dotnet から起動されるビルド サーバーをシャットダウンします。 既定では、すべてのサーバーがシャットダウンされます。

## <a name="options"></a>オプション

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--msbuild`**

  MSBuild ビルド サーバーをシャットダウンします。

- **`--razor`**

  Razor ビルド サーバーをシャットダウンします。

- **`--vbcscompiler`**

  VB/C# コンパイラ ビルド サーバーをシャットダウンします。
