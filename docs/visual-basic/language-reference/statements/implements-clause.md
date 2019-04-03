---
title: Implements 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 05de1d9f8966c17d84deba34f27819cce4aff3fe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832620"
---
# <a name="implements-clause-visual-basic"></a>Implements 句 (Visual Basic)
クラスまたは構造体のメンバーがインターフェイスで定義されているメンバーの実装を提供することを示します。  
  
## <a name="remarks"></a>Remarks  
`Implements`キーワードがないと同じ、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)します。 使用する、`Implements`クラスまたは構造体は、1 つまたは複数のインターフェイスを実装および使用する各メンバーに対して、指定のステートメント、`Implements`インターフェイスとメンバーを指定するキーワードを実装します。

含めることはクラスまたは構造体、インターフェイスを実装する場合、`Implements`ステートメントの直後に、 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)または[Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)、およびすべてのメンバーを実装する必要がありますインターフェイスによって定義されます。

## <a name="reimplementation"></a>再実装  
派生クラスでは、基底クラスが実装済みインターフェイスのメンバーを再実装できます。 これは、次の点で基底クラスのメンバーのオーバーライドとは異なります。

- 基底クラスのメンバーがある必要はありません[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)実装するためにします。
- 別の名前を持つメンバーを再実装できます。

`Implements`キーワードは、次のコンテキストで使用できます。
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
