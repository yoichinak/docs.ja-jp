---
title: void - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742758"
---
# <a name="void-c-reference"></a>void (C# リファレンス)

メソッドの戻り値の型として使用した場合、`void` はメソッドが値を返さないことを指定します。

`void` は、メソッドのパラメーター リストに含めることはできません。 パラメーターを取らず、値を返さないメソッドは、次のように宣言されます。

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` は、不明な型へのポインターを宣言するために、unsafe コンテキストでも使用されます。 詳しくは、「[ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)」をご覧ください。

`void` は、.NET Framework の <xref:System.Void?displayProperty=nameWithType> 型のエイリアスです。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# キーワード](index.md)
- [参照型](reference-types.md)
- [値型](../builtin-types/value-types.md)
- [メソッド](../../programming-guide/classes-and-structs/methods.md)
- [アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)
