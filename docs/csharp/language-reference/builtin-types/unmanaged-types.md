---
title: アンマネージド型 - C# リファレンス
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512072"
---
# <a name="unmanaged-types-c-reference"></a>アンマネージド型 (C# リファレンス)

**アンマネージド型**は、参照型または構築型 (少なくとも 1 つの型引数を含む型) ではない型であり、入れ子のどのレベルにも参照型または構築型のフィールドが含まれていません。 つまり、アンマネージド型は次のいずれかになります。

- `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal`、または `bool`
- すべての[列挙](../keywords/enum.md)型
- すべての[ポインター](../../programming-guide/unsafe-code-pointers/pointer-types.md) 型
- 構築型以外の、アンマネージ型のフィールドのみを含む、ユーザー定義のすべての[構造体](../keywords/struct.md)型

C# 7.3 以降、[`unmanaged` 制約](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)を使用して、型パラメーターが非ポインターのアンマネージド型であることを指定できます。

## <a name="c-language-specification"></a>C# 言語仕様

詳しくは、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[ポインター型](~/_csharplang/spec/unsafe-code.md#pointer-types)」をご覧ください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [メモリおよびスパンに関連する型](../../../standard/memory-and-spans/index.md)
- [sizeof 演算子](../operators/sizeof.md)
- [stackalloc 演算子](../operators/stackalloc.md)
