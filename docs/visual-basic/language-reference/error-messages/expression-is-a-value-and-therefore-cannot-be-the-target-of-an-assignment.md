---
title: Expression は値であるため、代入式のターゲットにすることはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513033"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expression は値であるため、代入式のターゲットにすることはできません。

ステートメントが式に値を代入しようとしています。 実行時には、書き込み可能な変数、プロパティ、または配列要素にのみ値を割り当てることができます。 次の例は、このエラーがどのように発生するかを示しています。

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

同様の例は、プロパティや配列要素にも当てはまります。

**間接アクセス。** 値型を使用して間接的にアクセスすると、このエラーが発生することもあります。 を通じ<xref:System.Drawing.Point> <xref:System.Windows.Forms.Control.Location%2A>て間接的にアクセスすることによっての値を設定しようとする次のコード例について考えてみます。

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

前の例の最後のステートメントは、 <xref:System.Drawing.Point> <xref:System.Windows.Forms.Control.Location%2A>プロパティによって返される構造体の一時的な割り当てのみを作成するため、失敗します。 構造体は値型であり、ステートメントの実行後は、一時的な構造体は保持されません。 この問題を解決するには、の<xref:System.Windows.Forms.Control.Location%2A>変数を宣言して使用します。これにより、 <xref:System.Drawing.Point>構造体に対してより永続的な割り当てが作成されます。 次の例は、前の例の最後のステートメントを置き換えることができるコードを示しています。

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**エラー ID:** BC30068

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ステートメントによって式に値が割り当てられた場合は、式を1つの書き込み可能な変数、プロパティ、または配列要素に置き換えます。

- ステートメントが値型 (通常は構造体) を介して間接的にアクセスする場合は、値型を保持する変数を作成します。

- 変数に適切な構造 (またはその他の値型) を割り当てます。

- 変数を使用してプロパティにアクセスし、値を割り当てます。

## <a name="see-also"></a>関連項目

- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
