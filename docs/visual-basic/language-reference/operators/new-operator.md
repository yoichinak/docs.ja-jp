---
title: New 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: dda23ef3ff49bd32474f39f5ae1807e57bdc2a62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980465"
---
# <a name="new-operator-visual-basic"></a>New 演算子 (Visual Basic)
導入されています、 `New` 、新しいオブジェクト インスタンスを作成する句が、型パラメーターにコンス トラクター制約を指定または識別、`Sub`クラスのコンス トラクターと手順。  
  
## <a name="remarks"></a>Remarks  
 代入ステートメントの宣言で、`New`句は、定義済みクラスのインスタンスを作成できますを指定する必要があります。 つまり、クラスが呼び出し元のコードにアクセスできる 1 つまたは複数のコンス トラクターを公開する必要があります。  
  
 使用することができます、`New`宣言ステートメントまたは代入ステートメントの句。 ステートメントを実行すると、指定した引数を渡さず、指定したクラスの適切なコンス トラクターを呼び出します。 次の例では、これを示しますのインスタンスを作成、`Customer`を 2 つのコンス トラクターを持つクラス、もう 1 つはパラメーターはとらず文字列パラメーターを受け取る。  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 配列は、クラスであるため`New`次の例に示すように、配列の新しいインスタンスを作成することができます。  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 共通言語ランタイム (CLR) がスローされます、<xref:System.OutOfMemoryException>エラーの新しいインスタンスを作成する十分なメモリがある場合。  
  
> [!NOTE]
>  `New`キーワードが指定された型が、アクセス可能なパラメーターなしのコンス トラクターを公開する必要がありますを指定する型パラメーター リストで使用もします。 型パラメーターや制約の詳細については、次を参照してください。[型リスト](../../../visual-basic/language-reference/statements/type-list.md)します。  
  
 クラスのコンス トラクターのプロシージャを作成するには、設定の名前、`Sub`する手順、`New`キーワード。 詳細については、次を参照してください。[オブジェクトの有効期間。オブジェクトの作成し、破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。  
  
 キーワード `New` は次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目
- <xref:System.OutOfMemoryException>
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [オブジェクトの有効期間:オブジェクトを作成および破棄する方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
