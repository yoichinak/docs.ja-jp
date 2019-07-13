---
title: 型パラメーターは修飾子として使用できません。
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: ba7348ae50965ffcf2719b20934451916c8fa95a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923722"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>型パラメーターは修飾子として使用できません。
プログラミング要素は、型パラメーターを含む修飾文字列で修飾されます。  
  
 型パラメーターは、ジェネリック型が構築されるときに指定する型の要件を表します。 特定の定義された型は表しません。 修飾文字列には、コンパイル時に定義されている要素のみを含める必要があります。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **エラー ID:** BC32098  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 修飾文字列から型パラメーターを削除するか、定義された型に置き換えます。  
  
2. 修飾されているプログラミング要素の検索に構築された型を使用する必要がある場合は、プログラム ロジックの追加を使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
