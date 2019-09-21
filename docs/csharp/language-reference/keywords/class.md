---
title: class キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 0c4fc9645e43f23e340804b46bbe8a5faa19525d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922387"
---
# <a name="class-c-reference"></a>class (C# リファレンス)

クラスは、次の例に示すように、キーワード `class` を使用して宣言します。

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>解説

C# では、単一継承のみを使用できます。 つまり、クラスは 1 つの基底クラスの実装だけを継承できます。 ただし、クラスは複数のインターフェイスを実装できます。 クラスの継承とインターフェイスの実装の例を次の表に示します。

|継承|例|
|-----------------|-------------|
|なし|`class ClassA { }`|
|Single|`class DerivedClass: BaseClass { }`|
|なし。2 つのインターフェイスを実装|`class ImplClass: IFace1, IFace2 { }`|
|1 つ。1 つのインターフェイスを実装|`class ImplDerivedClass: BaseClass, IFace1 { }`|

名前空間内で直接宣言され、他のクラスに入れ子にされていないクラスは、[public](./public.md) または [internal](./internal.md) のいずれかです。 クラスは既定で `internal` です。

クラスのメンバー (入れ子にされているクラスを含む) は [public](public.md)、[protected internal](protected-internal.md)、[protected](protected.md)、[internal](internal.md)、[private](private.md)、または [private protected](private-protected.md) のいずれかとして宣言することができます。 メンバーは既定で `private` です。

詳細については、「[アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。

型パラメーターを持つジェネリック クラスを宣言することができます。 詳細については、「[ジェネリック クラス](../../programming-guide/generics/generic-classes.md)」を参照してください。

クラスには、次のメンバーの宣言を含めることができます。

- [コンストラクター](../../programming-guide/classes-and-structs/constructors.md)

- [定数](../../programming-guide/classes-and-structs/constants.md)

- [フィールド](../../programming-guide/classes-and-structs/fields.md)

- [ファイナライザー](../../programming-guide/classes-and-structs/destructors.md)

- [メソッド](../../programming-guide/classes-and-structs/methods.md)

- [プロパティ](../../programming-guide/classes-and-structs/properties.md)

- [インデクサー](../../programming-guide/indexers/index.md)

- [演算子](../operators/index.md)

- [イベント](../../programming-guide/events/index.md)

- [デリゲート](../../programming-guide/delegates/index.md)

- [クラス](../../programming-guide/classes-and-structs/classes.md)

- "[インターフェイス](../../programming-guide/interfaces/index.md)"

- [構造体](../../programming-guide/classes-and-structs/structs.md)

- [列挙型](../../programming-guide/enumeration-types.md)

## <a name="example"></a>例

ここでは、クラスのフィールド、コンストラクター、メソッドの宣言例を示します。 また、オブジェクト インスタンスの作成とインスタンス データの出力の例も示します。 次の例では、2 つのクラスが宣言されています。 最初の `Child` クラスには、2 つのプライベート フィールド (`name` と `age`)、2 つのパブリック コンストラクター、および 1 つのパブリック メソッドがあります。 2 番目のクラスである `StringTest` は、`Main`の格納に使用されます。

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>説明

前の例で、プライベート フィールド (`name` および `age`) にアクセスできるのは、`Child` クラスのパブリック メソッドだけであることに注意してください。 たとえば、次のステートメントを使用して `Main` メソッドから子の名前を印刷することはできません。

```csharp
Console.Write(child1.name);   // Error
```

`Main` から `Child`のプライベート メンバーへのアクセスは、`Main` がそのクラスのメンバーである場合にのみ可能です。

アクセス修飾子を指定せずにクラス内で宣言された型は既定で `private` になります。そのため、キーワードが削除されてもこの例のデータ メンバーは `private` です。

最後に、パラメーターなしのコンストラクターを使って作成したオブジェクト (`child3`) の `age` フィールドが、既定で 0 に初期化されていることに注意してください。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [参照型](./reference-types.md)
