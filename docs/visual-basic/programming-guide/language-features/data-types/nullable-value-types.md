---
title: null 許容値型
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249683"
---
# <a name="nullable-value-types-visual-basic"></a>null 許容値型 (Visual Basic)

特定の状況で定義された値を持たない値型を使用する場合があります。 たとえば、データベース内のフィールドでは、意味のある値を割り当てることと、値が割り当てられていないかどうかを区別する必要があります。 値型は、通常の値または null 値を使用するように拡張できます。 このような拡張は *、null 許容型*と呼ばれます。

各 null 許容値型は、ジェネリック<xref:System.Nullable%601>構造体から構築されます。 作業関連のアクティビティを追跡するデータベースを考えてみましょう。 次の例では、null 許容`Boolean`型を作成し、その型の変数を宣言します。 宣言は、次の 3 つの方法で記述できます。

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

変数`ridesBusToWork`は、 の`True`値を保持するか`False`、値をまったく保持しません。 初期値は全く値ではなく、この場合、このユーザーに関する情報がまだ取得されていない可能性があります。 対照的に`False`、情報が得られ、その人が仕事にバスに乗っていない可能性があります。

変数とプロパティを null 許容値型で宣言したり、null 許容値型の要素を持つ配列を宣言したりできます。 null 許容値型をパラメーターとしてプロシージャを宣言したり、プロシージャから null 許容値型を`Function`返したりできます。

配列、、クラスなどの参照型に null 許容型を`String`作成することはできません。 基になる型は値型である必要があります。 詳細については、「[値型と参照型](value-types-and-reference-types.md)」を参照してください。

## <a name="using-a-nullable-type-variable"></a>Null 許容型変数の使用

null 許容値型の最も重要なメンバーは<xref:System.Nullable%601.HasValue%2A>、<xref:System.Nullable%601.Value%2A>そのとプロパティです。 null 許容値型の変数の場合、<xref:System.Nullable%601.HasValue%2A>変数に定義された値が含まれているかどうかを示します。 が<xref:System.Nullable%601.HasValue%2A>`True`の場合は、 から<xref:System.Nullable%601.Value%2A>値を読み取ることができます。 両方<xref:System.Nullable%601.HasValue%2A>がプロパティ<xref:System.Nullable%601.Value%2A>であることに`ReadOnly`注意してください。

### <a name="default-values"></a>既定値

null 許容値型で変数を宣言すると、その<xref:System.Nullable%601.HasValue%2A>プロパティの既定値は`False`です。 つまり、デフォルトでは、変数には、基になる値型の既定値ではなく、定義済みの値がありません。 次の例では、型の`numberOfChildren`既定値が 0 であっても、変数には最初に値が`Integer`定義されていません。

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

null 値は、未定義または不明な値を示すのに役立ちます。 として`numberOfChildren``Integer`宣言されている場合、情報が現在利用できない可能性のある値はありません。

### <a name="storing-values"></a>値の格納

値は、一般的な方法で null 許容値型の変数またはプロパティに格納します。 次の例では、前の例で宣言`numberOfChildren`した変数に値を代入します。

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

null 許容値型の変数またはプロパティに定義値が含まれている場合、値が割り当てられていないという初期状態に戻すことができます。 これは、次の例に示すように、変数`Nothing`またはプロパティを に設定して行います。

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> null 許容値`Nothing`型の変数に代入することはできますが、等号を使用`Nothing`して変数をテストすることはできません。 等号を使用する比較、`someVar = Nothing`は常に`Nothing`に評価されます。 <xref:System.Nullable%601.HasValue%2A>の変数のプロパティ`False`をテストするか、`Is`演算子を`IsNot`使用してテストできます。

### <a name="retrieving-values"></a>値の取得

null 許容値型の変数の値を取得するには、まずそのプロパティを<xref:System.Nullable%601.HasValue%2A>テストして値が設定されていることを確認する必要があります。 のときに<xref:System.Nullable%601.HasValue%2A>値を読み取ろうとすると`False`、例外がスローされます<xref:System.InvalidOperationException>。 次の例は、前の例の変数`numberOfChildren`を読み取る推奨方法を示しています。

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Null 許容型の比較

ブール式で`Boolean`null 許容変数を使用する場合、結果`True`は`False`、 `Nothing`、または になります。 以下は、 と`And``Or`の真の表です。 3 つの値が設定されているため`b1`、評価する組み合わせは 9 つあります。 `b2`

|b1|B2|b1 と b2|b1 または b2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

ブール変数または式の値が`Nothing`の場合、値は`true`で`false`もなく、 でもありません。 各データ メンバー フィールドが JSON オブジェクトにマップされ、フィールド名がオブジェクトの "key" 部分にマップされ、"value" 部分がオブジェクトの値の部分に再帰的にマップされます。

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

この例では、`b1 And b2`に評価`Nothing`されます。 その結果、文は`Else`各`If`文で実行され、出力は次のようになります。

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`と`OrElse`は、短絡評価を使用して、最初のオペランドが に評価されたときに、2`Nothing`番目のオペランドを評価する必要があります。

## <a name="propagation"></a>伝達

算術演算、比較演算、シフト演算、または型演算のオペランドの一方または両方が NULL 許容値型である場合、演算の結果も NULL 許容値型になります。 両方のオペランドにはない`Nothing`値がある場合、演算は、どちらも null 許容値型ではないかのように、オペランドの基になる値に対して実行されます。 次の例では、変数`compare1`と`sum1`暗黙的に型指定されます。 マウス ポインターを上に置くと、コンパイラは両方の null 許容値型を推論します。

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

一方または両方の`Nothing`オペランドの値が の場合、結果は`Nothing`になります。

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Null 許容型をデータで使用する

データベースは、null 許容値型を使用する最も重要な場所の 1 つです。 現在、すべてのデータベース オブジェクトが null 許容値型をサポートしているわけではありませんが、デザイナによって生成されたテーブル アダプタはサポートしています。 [Null 許容型のテーブルアダプターのサポート](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [データ型](index.md)
- [値型と参照型](value-types-and-reference-types.md)
- [データ型のトラブルシューティング](troubleshooting-data-types.md)
- [TableAdapters を使用してデータセットを入力する](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If 演算子](../../../language-reference/operators/if-operator.md)
- [ローカル型の推論](../variables/local-type-inference.md)
- [Is 演算子](../../../language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../language-reference/operators/isnot-operator.md)
- [Null 許容値型 (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
