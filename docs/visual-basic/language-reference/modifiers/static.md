---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f1031fe005a2fc264b50116b8ea3311dc7065dbc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647637"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
1 つまたは複数のローカル変数が存在し、宣言されているプロシージャの終了後、最新の値を保持し続けることを指定します。  
  
## <a name="remarks"></a>Remarks  
 通常、プロシージャ内のローカル変数は、プロシージャを停止すると、すぐに存在しなくなります。 静的変数は引き続き存在し、最新の値を保持します。 コードは、プロシージャを呼び出し、次回は、変数が再初期化されていないとに割り当てられている最新の値をそのまま保持します。 静的変数で定義されているクラスまたはモジュールの有効期間が存在し続けます。  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** 使用することができます`Static`ローカル変数に対してのみです。 これは、意味の宣言コンテキスト、`Static`変数は、プロシージャまたはプロシージャでは、ブロックする必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールにすることはできません。  
  
     使用することはできません`Static`構造プロシージャ内にあります。  
  
- データ型`Static`ローカル変数を推論することはできません。 詳細については、次を参照してください。[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
- **結合された修飾子。** 指定することはできません`Static`と共に`ReadOnly`、 `Shadows`、または`Shared`同じ宣言内。  
  
## <a name="behavior"></a>動作  
 静的変数を宣言する場合、`Shared`プロシージャ、静的変数の 1 つだけコピーは、アプリケーション全体で使用します。 呼び出す、`Shared`クラスを使用してプロシージャ名、クラスのインスタンスを指す変数ではなく。  
  
 ないプロシージャ内で静的変数を宣言すると`Shared`、のみ、変数の 1 つのコピーが、クラスのインスタンスごとに表示します。 クラスの特定のインスタンスを指す変数を使用して、非共有プロシージャを呼び出します。  
  
## <a name="example"></a>例  
 次の例は、`Static` の使い方を示しています。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`変数`totalSales`0 に 1 回だけ初期化されます。 入力するたびに`updateSales`、`totalSales`まだ最新の値を計算しました。  
  
 `Static`修飾子は、このコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Visual Basic での有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
