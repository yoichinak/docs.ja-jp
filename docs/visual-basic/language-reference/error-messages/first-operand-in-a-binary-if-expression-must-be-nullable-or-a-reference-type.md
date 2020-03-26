---
title: バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249527"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
式`If`は、2 つまたは 3 つの引数を受け取ることができます。 2 つの引数だけを送信する場合、最初の引数は参照型または null 許容値型である必要があります。 最初の引数が`Nothing`以外の値に評価される場合は、その値が返されます。 最初の引数が`Nothing`に評価されると、2 番目の引数が評価され、返されます。  
  
 たとえば、次のコードには、引数`If`が 3 つ、引数が 2 つある式が 2 つ含まれています。 式は、同じ値を計算して返します。  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 次の式がこのエラーを引き起こします。  
  
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
  
- 最初の引数が null 許容値型または参照型になるようにコードを変更できない場合は、3 つの引数を持`If`つ式または`If...Then...Else`ステートメントに変換することを検討してください。  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>関連項目

- [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
