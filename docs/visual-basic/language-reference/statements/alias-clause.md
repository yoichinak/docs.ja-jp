---
title: Alias 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 84c8f39e632eebbe5382492669820910b38bc360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053354"
---
# <a name="alias-clause-visual-basic"></a>Alias 句 (Visual Basic)
外部プロシージャにその DLL 内の別の名前があることを示します。  
  
## <a name="remarks"></a>Remarks  
 `Alias`キーワードは、このコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 次の例では、 `Alias` advapi32.dll、内の関数の名前を指定するキーワードが使用される`GetUserNameA`、その`getUserName`の代わりにこの例では使用します。 関数`getUserName`sub で呼び出される`getUser`、現在のユーザーの名前が表示されます。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
