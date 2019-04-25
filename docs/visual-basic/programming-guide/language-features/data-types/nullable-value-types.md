---
title: Null 許容値型の Visual Basic
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
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008229"
---
# <a name="nullable-value-types-visual-basic"></a>null 許容値型 (Visual Basic)

特定の状況で定義されている値を含まない値の型を操作することがあります。 たとえば、データベース内のフィールドは、意味のある割り当てられた値を持つと、値が割り当てられる必要があるとを区別する必要があります。 値の型は、通常の値または null 値のいずれかを拡張できます。 このような拡張機能が呼び出された、 *null 許容型*します。

各 null 許容型がジェネリックから構築された<xref:System.Nullable%601>構造体。 作業に関連するアクティビティを追跡するデータベースを検討してください。 次の例を構築する null 許容`Boolean`を入力し、その型の変数を宣言します。 次の 3 つの方法では、宣言を記述できます。

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

変数`ridesBusToWork`の値を保持できる`True`、@property `False`、またはすべてに値がありません。 初期の既定値はありません値、ここで可能性があることについては、いないまだに対して取得されたこの人。 これに対し、`False`情報が取得され、ユーザーが仕事のバスをオーバーライドしていないことを意味する可能性があります。

Null 許容型変数とプロパティを宣言することができ、null 許容型の要素を含む配列を宣言することができます。 プロシージャを宣言するには、パラメーターとして null 許容型とから null 許容型を返すことができます、`Function`プロシージャ。

など、配列参照型で null 許容型を構築することはできません、 `String`、またはクラス。 基になる型は、値型である必要があります。 詳細については、「 [Value Types and Reference Types](value-types-and-reference-types.md)」を参照してください。

## <a name="using-a-nullable-type-variable"></a>Null 許容型の変数を使用します。

Null 許容型の最も重要なメンバーは、その<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>プロパティ。 Null 許容型では、変数の<xref:System.Nullable%601.HasValue%2A>変数が定義されている値を格納するかどうかがわかります。 場合<xref:System.Nullable%601.HasValue%2A>は`True`から値を読み取ることができます<xref:System.Nullable%601.Value%2A>します。 なお両方<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>は`ReadOnly`プロパティ。

### <a name="default-values"></a>既定値

Null 許容型を持つ変数を宣言するときにその<xref:System.Nullable%601.HasValue%2A>プロパティの既定値を持つ`False`します。 つまり、既定では変数がない、基になる値型の既定値ではなく、定義済みの値。 次の例では、変数`numberOfChildren`最初に定義されていない値、場合でも、既定値の`Integer`型は 0 です。

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null 値は、定義されていないか不明な値を示すために役立ちます。 場合`numberOfChildren`として宣言されていた`Integer`情報が現在使用できないことを示す可能性のある値がなくなる。

### <a name="storing-values"></a>値を格納します。

通常の方法で変数または null 許容型のプロパティ値を格納します。 次の例では、変数に値を代入`numberOfChildren`前の例で宣言します。

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

変数または null 許容型のプロパティ値が定義されている場合、値を割り当てる必要があるの初期状態に戻すことが発生することができます。 変数またはプロパティを設定して、これを行う`Nothing`、次の例を示しています。

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> 割り当てることができます`Nothing`、null 許容型の変数にテストできない`Nothing`等号 (=) を使用しています。 等号を使用する比較`someVar = Nothing`、常に評価`Nothing`します。 変数をテストする<xref:System.Nullable%601.HasValue%2A>プロパティ`False`、またはテストを使用して、`Is`または`IsNot`演算子。

### <a name="retrieving-values"></a>値を取得します。

Null 許容型の変数の値を取得する必要があります初めてテストしたその<xref:System.Nullable%601.HasValue%2A>プロパティに値があることを確認します。 値を読み取るしようとする場合と<xref:System.Nullable%601.HasValue%2A>は`False`、Visual Basic をスロー、<xref:System.InvalidOperationException>例外。 次の例は、変数を読み取り、推奨される方法を示しています。`numberOfChildren`前の例です。

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Null 許容型を比較します。

Null 許容と`Boolean`の変数のブール式で使用、結果があります`True`、 `False`、または`Nothing`します。 次に、真理値表の`And`と`Or`します。 `b1`と`b2`これで 3 つの値がある 9 つの組み合わせを評価します。

|B1|B2|b1 および b2|b1 または b2|
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

ブール値変数または式の値が`Nothing`はどちらも`true`も`false`します。 例を次に示します。

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

この例で`b1 And b2`に評価される`Nothing`します。 結果として、`Else`句が各実行`If`ステートメントと、出力は次のように。

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` `OrElse`、最初の評価が、2 番目のオペランドを評価する必要がありますショート サーキット評価を使用する`Nothing`します。

## <a name="propagation"></a>伝達

算術演算子、比較、shift キー、または型の操作のオペランドの一方または両方が null 許容の場合は、操作の結果も null 値には。 両方のオペランドが値ではない`Nothing`の場合も同じように、オペランドの基になる値で、操作を実行、null 許容型。 次の例では、変数`compare1`と`sum1`は暗黙的に型指定されます。 上にマウス ポインターを置くと場合、コンパイラがその両方の null 許容型を推論することが表示されます。

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

1 つまたは両方のオペランドの値がある場合`Nothing`、結果になります`Nothing`します。

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Null 許容型のデータを使用します。

データベースは、null 許容型を使用する最も重要な場所の 1 つです。 すべてのデータベース オブジェクトが現在 null 許容型をサポートしますが、デザイナーで生成されたテーブル アダプターの操作を行います。 参照してください[null 許容型のサポートを TableAdapter](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)します。

## <a name="see-also"></a>関連項目

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Null 許容型の使用](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [データの種類](index.md)
- [値型と参照型](value-types-and-reference-types.md)
- [トラブルシューティング (データ型)](troubleshooting-data-types.md)
- [TableAdapters を使用してデータセットを入力する](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If 演算子](../../../language-reference/operators/if-operator.md)
- [ローカル型の推論](../variables/local-type-inference.md)
- [Is 演算子](../../../language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../language-reference/operators/isnot-operator.md)