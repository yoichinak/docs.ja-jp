---
title: struct - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 77d5c83dd4c81b96bc62ace6e609db8bc411dc41
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093163"
---
# <a name="struct-c-reference"></a>struct (C# リファレンス)

`struct` 型は、通常、関連する変数 (四角形の座標やインベントリ内の項目の特性など) の小さなグループをカプセル化するのに使用される値型です。 次の例に単純な構造体の宣言を示します。

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Remarks

構造体には、[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)、[定数](../../programming-guide/classes-and-structs/constants.md)、[フィールド](../../programming-guide/classes-and-structs/fields.md)、[メソッド](../../programming-guide/classes-and-structs/methods.md)、[プロパティ](../../programming-guide/classes-and-structs/properties.md)、[インデクサー](../../programming-guide/indexers/index.md)、[演算子](../operators/index.md)、[イベント](../../programming-guide/events/index.md)、および[入れ子にされた型](../../programming-guide/classes-and-structs/nested-types.md)を含めることができます。ただし、複数のメンバーが必要な場合は、代わりに型をクラスに変更することを検討してください。

例については、「[構造体の使用](../../programming-guide/classes-and-structs/using-structs.md)」を参照してください。

構造体はインターフェイスを実装できますが、別の構造体から継承することはできません。 そのため、構造体メンバーを `protected` として宣言することはできません。

詳細については、「[構造体](../../programming-guide/classes-and-structs/structs.md)」を参照してください。

## <a name="examples"></a>使用例

例と詳細については、「[構造体の使用](../../programming-guide/classes-and-structs/using-structs.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

例については、「[構造体の使用](../../programming-guide/classes-and-structs/using-structs.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# キーワード](index.md)
- [値型](../builtin-types/value-types.md)
- [class](class.md)
- [interface](interface.md)
- [クラスと構造体](../../programming-guide/classes-and-structs/index.md)
