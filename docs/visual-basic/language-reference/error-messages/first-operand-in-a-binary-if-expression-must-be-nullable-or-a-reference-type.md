---
title: バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 32ff0adca9d35e6b5439ae06be85414924dac2e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838626"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
`If`式が 2 つまたは 3 つの引数を受け取ることができます。 2 つの引数を送信すると、最初の引数は、参照型または null 許容型でする必要があります。 最初の引数の評価が何も以外の場合`Nothing`、その値が返されます。 最初の引数が評価された場合`Nothing`、2 番目の引数が評価され、返されます。  
  
 たとえば、次のコードには 2 つ`If`で 3 つの引数と 2 つの引数の式。 式を計算し、同じ値を返します。  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 次の式では、このエラーが発生します。  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **エラー ID:** BC33107  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   最初の引数が null 許容型または参照型であるようにコードを変更することはできない場合、は、3 つの引数に変換することを検討してください`If`式、または、`If...Then...Else`ステートメント。  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>関連項目

- [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
