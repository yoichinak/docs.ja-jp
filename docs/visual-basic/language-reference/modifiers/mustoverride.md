---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: f5932b28c4664dd59dad829228f2186e78108af5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661241"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
プロパティまたはプロシージャは、このクラスで実装されていませんしを使用する派生クラスでオーバーライドされる必要がありますを指定します。  
  
## <a name="remarks"></a>Remarks  
 `MustOverride` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。 プロパティまたはプロシージャを指定する`MustOverride`クラスのメンバーである必要があり、そのクラスをマークする必要があります[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)します。  
  
## <a name="rules"></a>ルール  
  
- **不完全な宣言です。** 指定すると`MustOverride`、任意の追加のプロパティまたはプロシージャのコード行をしない指定しないでも、 `End Function`、 `End Property`、または`End Sub`ステートメント。  
  
- **結合された修飾子。** 指定することはできません`MustOverride`と共に`NotOverridable`、 `Overridable`、または`Shared`同じ宣言内。  
  
- **シャドウとオーバーライドします。** シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。 詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)します。  
  
- **代替条件です。** オーバーライドで以外は使用できませんを要素とも呼ばれます、*純粋仮想*要素。  
  
 `MustOverride` 修飾子は、次のコンテキストで使用できます。  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
