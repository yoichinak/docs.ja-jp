---
title: Erase ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343700"
---
# <a name="erase-statement-visual-basic"></a>Erase ステートメント (Visual Basic)
配列変数を解放し、それらの要素に使用されるメモリの割り当てを解除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>指定項目  
 `arraylist`  
 必須です。 消去する配列変数の一覧。 複数の変数を指定するときは、コンマで区切ります。  
  
## <a name="remarks"></a>Remarks  
 `Erase` ステートメントは、プロシージャ レベルでのみ使用できます。 つまり、プロシージャ内では配列を解放できますが、クラスまたはモジュール レベルでは解放できません。  
  
 `Erase` ステートメントは、各配列変数に `Nothing` を割り当てることと同じです。  
  
## <a name="example"></a>例  
 次の例では、`Erase` ステートメントを使用して 2 つの配列をクリアし、そのメモリを解放します (それぞれ 1000 および 100 ストレージ要素)。 次に、`ReDim` ステートメントを使用して、新しい配列インスタンスを 3 次元配列に割り当てます。  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>関連項目

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
