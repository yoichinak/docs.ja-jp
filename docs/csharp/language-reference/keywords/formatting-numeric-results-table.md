---
title: 数値結果テーブルの書式設定 - C# リファレンス
ms.custom: seodec18
description: C# の標準の数値書式指定文字列について説明します
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 0f2b5bc54a0e9055d64a95dc229eaadf66687b43
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421968"
---
# <a name="formatting-numeric-results-table-c-reference"></a>数値結果テーブルの書式設定 (C# リファレンス)

次の表は、数値結果の書式を設定するためにサポートされている書式指定子を示しています。 最後の列の書式設定後の結果は、"en-US"<xref:System.Globalization.CultureInfo> に対応します。

|書式指定子|説明|使用例|結果|  
|----------------------|-----------------|--------------|------------|  
|C または c|通貨|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D または d|Decimal (10 進数型)|`string s = $"{25:D5}";`|00025|  
|E または e|指数|`string s = $"{250000:E2}";`|2.50E+005|  
|F または f|固定小数点|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G または g|全般|`string s = $"{2.5:G}";`|2.5|  
|N または n|数字|`string s = $"{2500000:N}";`|2,500,000.00|  
|P または p|パーセント|`string s = $"{0.25:P}";`|25.00%|  
|R または r|ラウンドトリップ|`string s = $"{2.5:R}";`|2.5|  
|X または x|16 進数|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>解説

書式指定子を使用して、書式設定文字列を作成します。 書式設定文字列は `Axx` 形式になります。

- `A` は書式指定子であり、数値に適用される書式設定の種類を制御します。
- `xx` は精度指定子であり、書式設定後の結果の桁数に影響します。 精度指定子の値は 0 から 99 の範囲です。

10 進数 ("D"または"d") と 16 進数 ("X"または"x") の形式指定子は、整数型でのみサポートされます。 ラウンドト リップ ("R"または"r") 書式指定子は、<xref:System.Single>、 <xref:System.Double> 型と <xref:System.Numerics.BigInteger> 型でのみサポートされます。

標準の数値書式指定文字列は、以下をサポートしています。

- 全数値型の `ToString` メソッドの一部のオーバーロード。 たとえば、<xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> メソッドおよび <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> メソッドに数値書式指定文字列を指定できます。

- .NET の[複合書式設定機能](../../../standard/base-types/composite-formatting.md)。たとえば <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドでサポートされます。

- [挿入文字列](../tokens/interpolated.md)。

詳細については、「[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [型の書式設定](../../../standard/base-types/formatting-types.md)
- [複合書式指定](../../../standard/base-types/composite-formatting.md)
- [文字列補間](../tokens/interpolated.md)
- [string](string.md)
