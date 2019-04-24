---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822316"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
プロパティまたはプロシージャを派生クラスでオーバーライドできないことを指定します。  
  
## <a name="remarks"></a>Remarks  
 `NotOverridable`修飾子が、プロパティまたはメソッドを派生クラスでオーバーライドされるを防ぎます。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾子は派生クラスでオーバーライドするクラスでプロパティまたはメソッドを使用します。 詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 場合、`Overridable`または`NotOverridable`修飾子が指定されていない、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドは、基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定値は`Overridable`。 それ以外は`NotOverridable`します。  
  
 要素をオーバーライドすることはできませんとも呼ばれます、*シール*要素。  
  
 `NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 指定できる`NotOverridable`プロパティまたはとの組み合わせでのみ、つまり、別のプロパティまたはプロシージャをオーバーライドするプロシージャでのみ`Overrides`します。  
  
## <a name="combined-modifiers"></a>修飾子の組み合わせ  
 指定することはできません`Overridable`または`NotOverridable`の`Private`メソッド。  
  
 指定することはできません`NotOverridable`と共に`MustOverride`、 `Overridable`、または`Shared`同じ宣言内。  
  
## <a name="usage"></a>使用法  
 `NotOverridable` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [修飾子](../../../visual-basic/language-reference/modifiers/index.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
