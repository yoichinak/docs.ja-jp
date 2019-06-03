---
title: 整数型の一覧表 - C# リファレンス
ms.custom: seodec18
description: 組み込み C# 整数型の概要
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: b4a3a46ba98c0c621b747284ce39e03d68a5b62d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421738"
---
# <a name="integral-types-table-c-reference"></a>整数型の一覧表 (C# リファレンス)

次の表は、単純型のサブセットである、整数型のサイズと範囲を示しています。  
  
|型|範囲|サイズ|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 ～ 127|符号付き 8 ビット整数|  
|[byte](byte.md)|0 ～ 255|符号なし 8 ビット整数|  
|[char](char.md)|U+0000 ～ U+ffff|Unicode 16 ビット文字|  
|[short](short.md)|-32,768 ～ 32,767|符号付き 16 ビット整数|  
|[ushort](ushort.md)|0 ～ 65,535|符号なし 16 ビット整数|  
|[int](int.md)|-2,147,483,648 ～ 2,147,483,647|符号付き 32 ビット整数|  
|[uint](uint.md)|0 ～ 4,294,967,295|符号なし 32 ビット整数|  
|[long](long.md)|-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807|符号付き 64 ビット整数|  
|[ulong](ulong.md)|0 ～ 18,446,744,073,709,551,615|符号なし 64 ビット整数|  

## <a name="remarks"></a>解説
  
整数リテラルで表される値が <xref:System.UInt64.MaxValue?displayProperty=nameWithType> を超えると、コンパイル エラー [CS1021](../../misc/cs1021.md) が発生します。

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> 構造体を使用して、任意の大きさを持つ符号付き整数を表します。
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [浮動小数点型の一覧表](floating-point-types-table.md)
- [既定値の一覧表](default-values-table.md)
- [数値結果テーブルの書式設定](formatting-numeric-results-table.md)
- [組み込み型の一覧表](built-in-types-table.md)
- [.NET における数値](../../../standard/numerics.md)
