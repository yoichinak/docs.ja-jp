---
title: dynamic - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: c8748f1869e8e2d5246910fac0100a6c70790579
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306647"
---
# <a name="dynamic-c-reference"></a>dynamic (C# リファレンス)

`dynamic` 型を使用すると、コンパイル時の型チェックをバイパスする処理が可能になります。 代わりに、演算は実行時に解決されます。 `dynamic` 型により、Office オートメーション API などの COM API、IronPython ライブラリなどの動的 API、および HTML ドキュメント オブジェクト モデル (DOM: Document Object Model) へのアクセスが容易になります。

ほとんどの環境で、`dynamic` 型は `object` 型のように動作します。 ただし、`dynamic` 型の式を含む演算はコンパイラによって解決または型チェックされません。 コンパイラは演算に関する情報をまとめてパッケージ化します。その情報が後で実行時に演算を評価するために使用されます。 このプロセスの過程で、`dynamic` 型の変数は `object` 型の変数にコンパイルされます。 そのため、`dynamic` 型はコンパイル時にのみ存在し、実行時には存在しません。

`dynamic` 型の変数と `object` 型の変数の違いを次に示します。 コンパイル時に各変数の型を確認するには、`WriteLine` ステートメントの `dyn` または `obj` にマウス ポインターを置きます。 IntelliSense 機能によって、`dyn` には **dynamic**、`obj` には **object** が表示されます。

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

`WriteLine` ステートメントは `dyn` および `obj` の実行時の型を表示します。 その時点では、両方が同じ整数型を持ちます。 次の出力が生成されます。

`System.Int32`

`System.Int32`

コンパイル時の `dyn` と `obj` の違いを確認するには、前の例の宣言と `WriteLine` ステートメントの間に次の 2 行を追加します。

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 式 `obj + 3` に整数およびオブジェクトを追加しようとしたことに対してコンパイル エラーが報告されます。 ただし、`dyn + 3` に関するエラーは報告されません。 `dyn` を含む式はコンパイル時にはチェックされません。これは、`dyn` の型が `dynamic` であるためです。

## <a name="context"></a>コンテキスト

次の状況では、`dynamic` キーワードを直接記述するか、構築型のコンポーネントとして記述できます。

- 宣言では、プロパティ、フィールド、インデクサー、パラメーター、戻り値、ローカル変数、または型制約として記述できます。 次のクラス定義はさまざまな宣言で `dynamic` を使用します。

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- 明示的な型変換で、変換先の型として記述できます。

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- `is` 演算子または `as` 演算子の右側、`typeof` への引数など、型が値として機能するコンテキストでは構築型の一部として記述できます。 たとえば、次の式では `dynamic` を使用できます。

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a>例

さまざまな宣言で `dynamic` を使用する例を次に示します。 また、`Main` メソッドで、コンパイル時の型チェックと実行時の型チェックの違いを確認できます。

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

使用例を含む詳細については、「[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [dynamic 型の使用](../../programming-guide/types/using-type-dynamic.md)
- [object](object.md)
- [is](../operators/type-testing-and-conversion-operators.md#is-operator)
- [as](../operators/type-testing-and-conversion-operators.md#as-operator)
- [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator)
- [方法: パターン マッチング、as 演算子、is 演算子を使用して安全にキャストする](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [チュートリアル: 動的オブジェクトの作成と使用](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
