---
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 344a813907483dcb0e9f531b54db68a88d77f3dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842383"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
LINQ クエリでは、1 つまたは複数の引数を受け取るプログラミング要素が含まれます。 コンパイラは、そのプログラミング要素の範囲変数を推論できません。  
  
 **エラー ID:** BC36599  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  次のコードに示すように、プログラミングの要素に明示的な変数名を指定します。  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
