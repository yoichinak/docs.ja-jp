---
title: インターフェイス - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: ce3cb95617c87d1bf66879f4a2432b4de4ac40f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586463"
---
# <a name="interface-c-reference"></a>インターフェイス (C# リファレンス)

インターフェイスには、[メソッド](../../programming-guide/classes-and-structs/methods.md)、[プロパティ](../../programming-guide/classes-and-structs/properties.md)、[イベント](../../programming-guide/events/index.md)、[インデクサー](../../programming-guide/indexers/index.md)のシグネチャのみが含まれています。 インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。 次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。

使用例を含む詳細については、「[インターフェイス](../../programming-guide/interfaces/index.md)」を参照してください。

## <a name="example"></a>例

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。

- [メソッド](../../programming-guide/classes-and-structs/methods.md)

- [プロパティ](../../programming-guide/classes-and-structs/using-properties.md)

- [インデクサー](../../programming-guide/indexers/using-indexers.md)

- [イベント](event.md)

インターフェイスは、1 つ以上の基底インターフェイスから継承できます。

基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。

インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。 明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。

明示的なインターフェイスの実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。

## <a name="example"></a>例

ここでは、インターフェイスの実装例を示します。 この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。 `IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [参照型](reference-types.md)
- [インターフェイス](../../programming-guide/interfaces/index.md)
- [プロパティの使用](../../programming-guide/classes-and-structs/using-properties.md)
- [インデクサーの使用](../../programming-guide/indexers/using-indexers.md)
- [class](class.md)
- [struct](struct.md)
- [インターフェイス](../../programming-guide/interfaces/index.md)
