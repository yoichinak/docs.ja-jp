---
title: 匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: b798f296b62b51de34a7ec5ce5a8b608273f5748
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819230"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます
複雑な式から匿名型メンバーの名前を推論することはできません。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 ソースから匿名型ができ、メンバーの名前と型を推論することはできませんの詳細については、次を参照してください。[方法。匿名型の宣言におけるプロパティ名と型を推論](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)します。  
  
 **エラー ID:** BC36556  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   次のコードに示すように、メンバー名に式を割り当てます。  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>関連項目

- [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [方法: 匿名型の宣言におけるプロパティ名と型を推論します。](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
