---
title: 構造体の変数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816331"
---
# <a name="structure-variables-visual-basic"></a>構造体の変数 (Visual Basic)
構造体を作成すると、その型と、プロシージャ レベルとモジュール レベル変数を宣言できます。 たとえば、コンピューター システムに関する情報を記録する構造体を作成できます。 次に例を示します。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 型の変数を宣言できます。 次の例を示します。  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  クラスとモジュールで宣言された構造体を使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)パブリック アクセスに既定値。 構造体をプライベートにする場合を使用して宣言確認、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード。  
  
## <a name="access-to-structure-values"></a>構造体の値へのアクセス  
 割り当てし、構造体変数の要素から値を取得に設定し、オブジェクトのプロパティを取得するときに使用同じ構文を使用します。 メンバー アクセス演算子を配置する (`.`) 構造体の変数名と要素名の間。 次の例では、要素型として以前に宣言された変数の`systemInfo`します。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>構造体の変数の代入  
 両方とも同じ構造体型の場合は、別に 1 つの変数を割り当てることもできます。 これにより、1 つの構造体のすべての要素がもう一方で対応する要素にコピーされます。 次の例を示します。  
  
```  
yourSystem = mySystem  
```  
  
 構造体の要素など、参照型では、かどうか、 `String`、 `Object`、またはデータへのポインター、配列をコピーします。 前の例では場合、`systemInfo`のポインターが前の例をコピーした場合、オブジェクト変数が含まれていた`mySystem`に`yourSystem`、アクセスするときに、1 つの構造をオブジェクトのデータの変更が有効になるとその他の構造をします。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [方法: 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
