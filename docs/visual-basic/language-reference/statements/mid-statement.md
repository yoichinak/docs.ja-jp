---
title: Mid ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: eeef4c13743b75a3d5e61ac46afb94d9ea105b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348027"
---
# <a name="mid-statement"></a>Mid ステートメント
Replaces a specified number of characters in a `String` variable with characters from another string.  
  
## <a name="syntax"></a>構文  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>指定項目  
 `Target`  
 必須です。 Name of the `String` variable to modify.  
  
 `Start`  
 必須です。 `Integer` expression. Character position in `Target` where the replacement of text begins. `Start` uses a one-based index.  
  
 `Length`  
 省略可能です。 `Integer` expression. Number of characters to replace. If omitted, all of `String` is used.  
  
 `StringExpression`  
 必須です。 `String` expression that replaces part of `Target`.  
  
## <a name="exceptions"></a>例外  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` <= 0 or `Length` < 0.|  
  
## <a name="remarks"></a>Remarks  
 The number of characters replaced is always less than or equal to the number of characters in `Target`.  
  
 Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement. These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters. 詳細については、「<xref:Microsoft.VisualBasic.Strings.Mid%2A>」を参照してください。  
  
> [!NOTE]
> The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters. It is used primarily for converting strings in double-byte character set (DBCS) applications. All Visual Basic strings are in Unicode, and `MidB` is no longer supported.  
  
## <a name="example"></a>例  
 This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>［要件］  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module:** `Strings`  
  
 **Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic の文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
