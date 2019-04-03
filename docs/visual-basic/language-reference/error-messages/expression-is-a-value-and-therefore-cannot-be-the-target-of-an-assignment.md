---
title: Expression は値であるため、代入式のターゲットにすることはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826134"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expression は値であるため、代入式のターゲットにすることはできません。
ステートメントは、式に値を代入しようとします。 実行時に、書き込み可能な変数、プロパティ、または配列要素にのみ値を割り当てることができます。 次の例では、このエラーは発生する方法を示しています。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 類似した例は、プロパティおよび配列の要素に適用できます。  
  
 **間接的にアクセスします。** 値の型を間接的にアクセスでは、このエラーを生成できます。 値を設定しようとしています。 次のコード例を検討してください。<xref:System.Drawing.Point>を通じて間接的にアクセスして<xref:System.Windows.Forms.Control.Location%2A>します。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 前の例の最後のステートメントは失敗の一時的な割り当てのみを作成するため、<xref:System.Drawing.Point>によって返される構造体、<xref:System.Windows.Forms.Control.Location%2A>プロパティ。 構造体は値の型と、ステートメントの実行後、一時的な構造は保持されません。 宣言の変数を使用して、問題が解決<xref:System.Windows.Forms.Control.Location%2A>より永続的な割り当てを作成する、<xref:System.Drawing.Point>構造体。 次の例では、前の例の最後のステートメントを置き換えることができるコードを示します。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **エラー ID:** BC30068  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ステートメントは、式に値を割り当てます場合、は、書き込み可能な 1 つの変数、プロパティ、または配列要素で式を置き換えます。  
  
-   ステートメントが値型 (通常は構造体) を通じて間接的にアクセスする場合、値の型を保持する変数を作成します。  
  
-   適切な構造体 (またはその他の値の型) を変数に割り当てます。  
  
-   値を代入するのにプロパティにアクセスするのにには、変数を使用します。  
  
## <a name="see-also"></a>関連項目

- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
