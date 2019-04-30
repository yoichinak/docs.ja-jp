---
title: 基本型
description: 使用される基本的な基本的な型を検出、F#言語。
ms.date: 07/09/2018
ms.openlocfilehash: 74a276792e2566b8f18b87f4bdcfb923b713b9c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959116"
---
# <a name="basic-types"></a>基本的な型

このトピックでは、F# 言語で定義されている基本的な型を使用します。 これらの型は、最も基本的な F# でほぼすべての F# プログラムの基礎を形成します。 .NET プリミティブ型のスーパー セットです。

|型|.NET 型|説明|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|有効な値は、`true` と `false` です。|
|`byte`|<xref:System.Byte>|0 から 255 の値です。|
|`sbyte`|<xref:System.SByte>|-128 から 127 の値です。|
|`int16`|<xref:System.Int16>|-32768 から 32767 の値です。|
|`uint16`|<xref:System.UInt16>|0 から 65535 の値です。|
|`int`|<xref:System.Int32>|-2,147, 483,648 から 2,147, 483,647 の値です。|
|`uint32`|<xref:System.UInt32>|0 から 4,294,967,295 の値です。|
|`int64`|<xref:System.Int64>|9,223,372,036,854,775,807-9,223,372,036,854,775,808 から値です。|
|`uint64`|<xref:System.UInt64>|0 から 18,446,744,073,709,551,615 の値です。|
|`nativeint`|<xref:System.IntPtr>|符号付き整数としてのネイティブ ポインターです。|
|`unativeint`|<xref:System.UIntPtr>|符号なし整数としてのネイティブ ポインターです。|
|`char`|<xref:System.Char>|Unicode 文字の値。|
|`string`|<xref:System.String>|Unicode テキスト。|
|`decimal`|<xref:System.Decimal>|浮動小数点、少なくとも 28 の有効桁数を持つデータ型です。|
|`unit`|該当なし|実際の値がないことを示します。 型が示される 1 つだけの仮引数の値を持つ`()`します。 単位の値、`()`値が必要なが実際の値が使用可能なまたは意味のプレース ホルダーとして使用されます。|
|`void`|<xref:System.Void>|ないことを示します型または値。|
|`float32`, `single`|<xref:System.Single>|32 ビット浮動小数点型。|
|`float`, `double`|<xref:System.Double>|64 ビット浮動小数点型。|

> [!NOTE]
> 使用して、64 ビット整数型の整数が大きすぎると計算を行うことができます、 [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型。 `bigint` 基本的な型であるとは見なされません省略形は`System.Numerics.BigInteger`します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)