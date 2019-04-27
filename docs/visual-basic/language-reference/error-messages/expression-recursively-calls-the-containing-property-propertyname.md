---
title: 式は、含んでいるプロパティ '<propertyname>' を再帰的に呼び出します。
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: a758d05cca5ca71943b0ef08184aef5b2c457739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802350"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>式を再帰的には、包含するプロパティを呼び出す '\<propertyname >'
内のステートメント、`Set`プロパティ定義のプロシージャは、プロパティの名前に、値を格納します。  
  
 プロパティの値を保持するための推奨アプローチが定義するには、`Private`プロパティのコンテナーに変数を両方で使用、`Get`と`Set`プロシージャ。 `Set`プロシージャこれで受信した値を格納し、`Private`変数。  
  
 `Get`プロシージャと同様に動作を`Function`プロシージャ、プロパティ名に値を代入し、発生してコントロールを返すため、`End Get`ステートメント。 ただしを含めるにはお勧め、`Private`変数の値として、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。  
  
 `Set`プロシージャと同様に動作を`Sub`プロシージャで、値は返されません。 そのため、プロシージャまたはプロパティ名には内で特別な意味がない、`Set`して、プロシージャに値を格納ことはできません。  
  
 次の例は、推奨されるアプローチを続けて、このエラーを引き起こす可能性のある方法を示しています。  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42026  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   前の例に示すように推奨されるアプローチを使用するプロパティの定義を書き直してください。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
