---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: ba09bdbc35779afba3dd24f6352cb99a49f931c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583050"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
変数またはプロパティを読み取ることができても書き込まれないことを指定します。

## <a name="remarks"></a>Remarks

## <a name="rules"></a>ルール

- **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。 つまり、`ReadOnly` 要素の宣言コンテキストはクラス、構造体、またはモジュールである必要があり、ソースファイル、名前空間、またはプロシージャにすることはできません。

- **結合された修飾子。** 同じ宣言内の `Static` と共に `ReadOnly` を指定することはできません。

- **値の割り当て。** @No__t_0 プロパティを使用するコードでは、値を設定できません。 ただし、基になるストレージにアクセスできるコードは、いつでも値を割り当てたり、変更したりできます。

     @No__t_0 変数に値を割り当てることができるのは、その宣言、またはそれが定義されているクラスまたは構造体のコンストラクター内でのみです。

## <a name="when-to-use-a-readonly-variable"></a>ReadOnly 変数を使用する場合

[Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)を使用して定数値を宣言し、割り当てることができない場合があります。 たとえば、`Const` ステートメントでは、割り当てたいデータ型が受け入れられない場合や、コンパイル時に定数式を使用して値を計算できない場合があります。 コンパイル時に値がわからない場合もあります。 このような場合は、`ReadOnly` 変数を使用して定数値を保持できます。

> [!IMPORTANT]
> 変数のデータ型が配列やクラスインスタンスなどの参照型である場合、変数自体が `ReadOnly` 場合でも、そのメンバーを変更できます。 次に例を示します。

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

初期化されると、`characterArray()` が指す配列は、"x"、"y"、および "z" を保持します。 変数 `characterArray` が `ReadOnly` ので、初期化後に値を変更することはできません。つまり、新しい配列を割り当てることはできません。 ただし、1つまたは複数の配列メンバーの値を変更できます。 プロシージャ `ChangeArrayElement` の呼び出しの後、`characterArray()` が指す配列は、"x"、"M"、および "z" を保持します。

これは、プロシージャパラメーターを[ByVal](byval.md)に宣言するのと似ています。これにより、プロシージャが呼び出し元の引数自体を変更するのではなく、メンバーを変更することができます。

## <a name="example"></a>例

次の例では、従業員が雇用された日付の `ReadOnly` プロパティを定義します。 クラスは `Private` 変数として内部的にプロパティ値を格納します。クラス内のコードだけがその値を変更できます。 ただし、プロパティは `Public`、クラスにアクセスできるすべてのコードでプロパティを読み取ることができます。

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

`ReadOnly` 修飾子は、次のコンテキストで使用できます。

- [Dim ステートメント](../statements/dim-statement.md)
- [Property ステートメント](../statements/property-statement.md)

## <a name="see-also"></a>関連項目

- [WriteOnly](writeonly.md)
- [キーワード](../keywords/index.md)
