---
title: Null 許容型の推論はこのコンテキストではサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249501"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Null 許容型の推論はこのコンテキストではサポートされていません
値型と構造体は null 許容として宣言できます。  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 ただし、null 許容宣言と型の推論を組み合わせて使用することはできません。 次の例では、このエラーが発生します。  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **エラー ID:** BC36629  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 変数を`As`null 許容値型として宣言するには、句を使用します。  
  
## <a name="see-also"></a>関連項目

- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
