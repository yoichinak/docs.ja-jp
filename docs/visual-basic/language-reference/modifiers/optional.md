---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820790"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
プロシージャが呼び出されたときにプロシージャの引数を省略できますを指定します。  
  
## <a name="remarks"></a>Remarks  
 オプションのパラメーターごとに、そのパラメーターの既定値として定数式を指定する必要があります。 式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)値のデータ型の既定値は、パラメーターの既定値として使用されます。  
  
 パラメーター リストには、オプションのパラメーターが含まれています、それに続くすべてのパラメーターは省略可能な必要があります。  
  
 `Optional` 修飾子は、次のコンテキストで使用できます。  
  
-   [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  省略可能なパラメーターの有無、プロシージャを呼び出すときに、位置または名前で引数を渡すことができます。 詳細については、次を参照してください。[位置と名前による引数を渡す](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)します。  
  
> [!NOTE]
>  オーバー ロードを使用して、省略可能なパラメーターを持つプロシージャを定義することもできます。 1 つの省略可能なパラメーターがある場合、プロシージャ、ないおよびパラメーターを受け取るいずれかの 2 つのオーバー ロードされたバージョンを定義できます。 詳細については、「 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、省略可能なパラメーターを持つプロシージャを定義します。  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>例  
 次の例では、位置によって渡される引数と名前によって渡される引数は、プロシージャを呼び出す方法を示します。 プロシージャが、2 つの省略可能なパラメーター。  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>関連項目

- [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)
- [省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
