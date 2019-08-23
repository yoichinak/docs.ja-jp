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
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955878"
---
# <a name="new-operator-visual-basic"></a>New 演算子 (Visual Basic)
では`New` 、新しいオブジェクトインスタンスを作成する句、型パラメーターにコンストラクター制約を指定する句、また`Sub`はプロシージャをクラスコンストラクターとして識別する句が導入されています。  
  
## <a name="remarks"></a>Remarks  
 宣言または代入ステートメント`New`では、句で、インスタンスを作成できる定義済みのクラスを指定する必要があります。 これは、クラスが、呼び出し元のコードがアクセスできる1つ以上のコンストラクターを公開する必要があることを意味します。  
  
 `New`句は、宣言ステートメントまたは代入ステートメントで使用できます。 ステートメントを実行すると、指定したクラスの適切なコンストラクターが呼び出され、指定した引数が渡されます。 次の例では、2つのコンストラクター `Customer`を持つクラスのインスタンスを作成します。1つはパラメーターを取らず、もう1つは文字列パラメーターを受け取ります。  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 配列はクラスである`New`ため、次の例に示すように、は新しい配列インスタンスを作成できます。  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 新しいインスタンスを作成するためのメモリが<xref:System.OutOfMemoryException>不足している場合は、共通言語ランタイム (CLR) によってエラーがスローされます。  
  
> [!NOTE]
> キーワード`New`は、指定された型がアクセス可能なパラメーターなしのコンストラクターを公開する必要があることを指定するために、型パラメーターリストでも使用されます。 型パラメーターと制約の詳細については、「 [Type List](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。  
  
 クラスのコンストラクタープロシージャを作成するには、 `Sub`プロシージャの名前を`New`キーワードに設定します。 詳細については[、次を参照してください。オブジェクトの有効期間:オブジェクトの作成方法と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)方法。  
  
 キーワード `New` は次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.OutOfMemoryException>
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [オブジェクトの有効期間:オブジェクトの作成方法と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
