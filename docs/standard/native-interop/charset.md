---
title: 文字セットとマーシャリング - .NET
description: CharSet の値によって、.NET でデータをネイティブ コードにマーシャリングする方法がどのように変わるかについて説明します。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c50c58ad639b1efb29c13e5124fe3c32e8af96fc
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063334"
---
# <a name="charsets-and-marshaling"></a>文字セットとマーシャリング

`char` 値、`string` オブジェクト、および `System.Text.StringBuilder` オブジェクトのマーシャリング方法は、P/Invoke または構造体どちらかの `CharSet` フィールド値によって変わります。 P/Invoke の `CharSet` を設定するには、P/Invoke を宣言するときに <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> フィールドを設定します。 構造体の `CharSet` を設定するには、構造体宣言の <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> フィールドを設定します。 これらの属性フィールドが設定されていない場合、言語コンパイラによって使用する `CharSet` が決まります。 C# と VB は既定で <xref:System.Runtime.InteropServices.CharSet.Ansi> 文字セットを使用します。

次の表は、各文字セット間のマッピングと、その文字セットを使ってマーシャリングした場合に文字または文字列がどのように表現されるかを示しています。

| `CharSet` の値 | Windows            | Unix 上での .NET Core 2.2 以前 | Unix 上での .NET Core 3.0 以降および Mono |
|-----------------|--------------------|-----------------------------------|------------------------------------------|
| Ansi            | `char` (ANSI)      | `char` (UTF-8)                    | `char` (UTF-8)                           |
| Unicode         | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char16_t` (UTF-16)                      |
| 自動            | `wchar_t` (UTF-16) | `char16_t` (UTF-16)               | `char` (UTF-8)                           |

文字セットを選択するときは、必ずネイティブ表現で期待される表現を必ず把握しておいてください。
