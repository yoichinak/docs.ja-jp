---
title: NotOverridable
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
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351444"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
派生クラス内のプロパティまたはプロシージャをオーバーライドできないことを示します。  
  
## <a name="remarks"></a>Remarks  
 `NotOverridable` 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。 詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。  
  
 `Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。 プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。  
  
 オーバーライドできない要素は、*シールド*要素と呼ばれることもあります。  
  
 `NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 `NotOverridable` は、別のプロパティまたはプロシージャをオーバーライドするプロパティまたはプロシージャでのみ、つまり `Overrides` との組み合わせでのみ指定できます。  
  
## <a name="combined-modifiers"></a>結合された修飾子  
 `Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。  
  
 同じ宣言内で `NotOverridable` を `MustOverride`、`Overridable`、または `Shared` と共に指定することはできません。  
  
## <a name="usage"></a>使用方法  
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
