---
title: シャドウとオーバーライドの違い
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345416"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>シャドウとオーバーライドの違い (Visual Basic)
When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class. Shadowing and overriding are both available for this purpose.  
  
## <a name="comparison"></a>条件式  
 Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another. But there are significant differences between the two.  
  
 The following table compares shadowing with overriding.  
  
||||  
|---|---|---|  
|Point of comparison|シャドウ|Overriding|  
|目的|Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class|Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup>|  
|Redefined element|Any declared element type|Only a procedure (`Function`, `Sub`, or `Operator`) or property|  
|Redefining element|Any declared element type|Only a procedure or property with the identical calling sequence<sup>1</sup>|  
|Access level of redefining element|Any access level|Cannot change access level of overridden element|  
|Readability and writability of redefining element|Any combination|Cannot change readability or writability of overridden property|  
|Control over redefining|Base class element cannot enforce or prohibit shadowing|Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`|  
|Keyword usage|`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup>|`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class|  
|Inheritance of redefining element by classes deriving from your derived class|Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup>|Overriding element inherited by further derived classes; overridden element still overridden|  
  
 <sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type. You cannot override a procedure with a property, or the other way around. You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.  
  
 <sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use. If you ignore the warning, the shadowing mechanism is used.  
  
 <sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited. For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.  
  
## <a name="guidelines"></a>ガイドライン  
 You normally use overriding in the following cases:  
  
- You are defining polymorphic derived classes.  
  
- You want the safety of having the compiler enforce the identical element type and calling sequence.  
  
 You normally use shadowing in the following cases:  
  
- You anticipate that your base class might be modified and define an element using the same name as yours.  
  
- You want the freedom of changing the element type or calling sequence.  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [方法: 自分で宣言した変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [方法: 派生クラスによって非表示になっている変数にアクセスする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
