---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816883"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
同じ名前のプロパティまたは派生クラス内のプロシージャによってオーバーライドできるプロパティまたはプロシージャを指定します。  
  
## <a name="remarks"></a>Remarks  
 `Overridable`修飾子は派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾子が、プロパティまたはメソッドを派生クラスでオーバーライドされるを防ぎます。  詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 場合、`Overridable`または`NotOverridable`修飾子が指定されていない、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドは、基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定値は`Overridable`。 それ以外は`NotOverridable`します。  
  
 継承された要素を再定義するためにオーバーライドまたはシャドウできますが、2 つのアプローチの重要な違いがあります。 詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)します。  
  
 オーバーライド可能な要素として呼ば、*仮想*要素。 ということもありますが、オーバーライドできますが、する必要はありません、*具象*要素。  
  
 `Overridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。  
  
## <a name="combined-modifiers"></a>修飾子の組み合わせ  
 指定することはできません`Overridable`または`NotOverridable`の`Private`メソッド。  
  
 指定することはできません`Overridable`と共に`MustOverride`、 `NotOverridable`、または`Shared`同じ宣言内。  
  
 オーバーライドする要素は暗黙的にオーバーライド可能であるため、`Overridable` と `Overrides` を結合することはできません。  
  
## <a name="usage"></a>使用法  
 `Overridable` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [修飾子](../../../visual-basic/language-reference/modifiers/index.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
