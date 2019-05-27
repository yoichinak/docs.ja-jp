---
title: 列挙型ではなく列挙型クラスを使用する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | enum のいくつかの制限を解決する方法として、代わりに Enumeration クラスを使用する方法を説明します。
ms.date: 10/08/2018
ms.openlocfilehash: 10b4c2f7b9f079ed535111e65b8154791f6575cd
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003836"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>enum 型の代わりに Enumeration クラスを使用する

[列挙型](../../../../docs/csharp/language-reference/keywords/enum.md) (省略形も同じ *列挙型*) は、整数型を包む薄い言語ラッパーです。 閉じた値のセットから 1 つの値を格納するときに、列挙型の使用を制限することができます。 サイズ (小、中、大) に基づく分類は良い一例です。 制御フローまたはより堅牢な抽象化のために列挙型を使用すると、[コードの臭い](https://deviq.com/code-smells/)になることがあります。 このような用法は、列挙型の値を検査する多くの制御フロー ステートメントでは脆弱なコードにつながります。

代わりに、オブジェクト指向言語の豊富な機能をすべて使用できる列挙型クラスを作成する方法があります。

ただし、これは重要な話題ではなく、多くの場合は、好みに応じてわかりやすくするために通常の[列挙型](../../../csharp/language-reference/keywords/enum.md)を使用することができます。 いずれにしても、Enumeration クラスを使用するとビジネス関連の概念に対する関連性が強くなります。

## <a name="implement-an-enumeration-base-class"></a>Enumeration 基底クラスを実装する

eShopOnContainers 内の注文マイクロサービスは、次の例のように、列挙型基底クラスの実装サンプルを提供しています。

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

次の `CardType` : `Enumeration` クラスに関しては、このクラスを任意のエンティティまたは値オブジェクトの型として使用できます。

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>その他の技術情報

- **列挙型は悪 — 更新** \
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- **Daniel Hardman。列挙型で広がる病気 — そしてその治療方法** \
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- **Jimmy Bogard。列挙型クラス** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith。C# の列挙型の代替** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs。** eShopOnContainers の基底列挙型クラス \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**。 eShopOnContainers のサンプル列挙型クラス。 \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- **SmartEnum**. Ardalis - .NET で厳密に型指定されたスマートな列挙型を生成するためのクラス。 \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[前へ](implement-value-objects.md)
>[次へ](domain-model-layer-validations.md)
