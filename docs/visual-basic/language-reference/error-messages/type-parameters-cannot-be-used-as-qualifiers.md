---
title: 型パラメーターは修飾子として使用できません。
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592135"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>型パラメーターは修飾子として使用できません。
プログラミング要素は、型パラメーターを含む修飾文字列で修飾されます。  
  
 型パラメーターは、ジェネリック型が構築されるときに指定される型の要件を表します。 定義されている特定の型を表していません。 修飾文字列には、コンパイル時に定義された要素のみを含める必要があります。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **エラー ID:** BC32098  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 修飾文字列から型パラメーターを削除するか、定義された型で置き換えます。  
  
2. 構築された型を使用して、修飾するプログラミング要素を見つける必要がある場合は、追加のプログラムロジックを使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
