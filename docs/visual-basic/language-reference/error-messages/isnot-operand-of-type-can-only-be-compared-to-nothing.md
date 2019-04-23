---
title: "'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: f19b8cd5f80ba9fd6d1f5a9162b04ee409e24e28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311891"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます
式に null 許容型として宣言された変数が以外に比較`Nothing`を使用して、`IsNot`演算子。  
  
 **エラー ID:** BC32128  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `Nothing` 演算子を使用して、Null 許容型を `IsNot` 以外の式と比較するには、次の例に示すように、Null 許容型に対して `GetType` メソッドを呼び出し、その結果を式と比較します。  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>関連項目

- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
