---
title: new 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 409a5307eaacd2eac865e2882cc7228521260dbe
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421876"
---
# <a name="new-operator-c-reference"></a>new 演算子 (C# リファレンス)

オブジェクトを作成し、コンストラクターを呼び出すために使用します。 次に例を示します。

```csharp
Class1 obj  = new Class1();
```

匿名型のインスタンスの作成にも使用します。

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

`new` 演算子は値型のパラメーターなしのコンストラクターの呼び出しにも使用します。 次に例を示します。

```csharp
int i = new int();
```

上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。 このステートメントは次のステートメントと同じ効果があります。

```csharp
int i = 0;
```

既定値の一覧については、「[既定値の一覧表](default-values-table.md)」を参照してください。

すべての値型には暗黙的にパラメーターなしのパブリック コンストラクターがあるため、[構造体](struct.md) に対して既定のコンストラクターを宣言するとエラーになります。 パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。

構造体などの値型オブジェクトと、クラスなどの参照型オブジェクトは両方とも自動的に破棄されますが、値型オブジェクトは含まれているコンテキストが破棄されたときに破棄され、参照型オブジェクトはそれに対する最後の参照が削除された後、ガベージ コレクターによって随時破棄されます。 ファイル ハンドルなどのリソース、またはネットワーク接続を含む型の場合、格納されているリソースができるだけ早く解放されるように、決定的なクリーンアップを使用することをお勧めします。 詳細については、「[using ステートメント](using-statement.md)」を参照してください。

`new` 演算子はオーバーロードできません。

`new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。

## <a name="example"></a>例

次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。 既定値と代入値が表示されます。

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

この例では、文字列の既定値は `null` です。 このため、文字列の既定値は表示されません。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../language-reference/index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [new](new.md)
- [匿名型](../../programming-guide/classes-and-structs/anonymous-types.md)
