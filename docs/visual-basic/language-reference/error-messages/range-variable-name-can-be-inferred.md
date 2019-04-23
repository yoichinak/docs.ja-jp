---
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: a0b5633bb0efb3c67f73810552ef9a14ac3d0c70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331651"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
LINQ クエリでは、1 つまたは複数の引数を受け取るプログラミング要素が含まれます。 コンパイラは、そのプログラミング要素の範囲変数を推論できません。  
  
 **エラー ID:** BC36599  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 次のコードに示すように、プログラミングの要素に明示的な変数名を指定します。  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
