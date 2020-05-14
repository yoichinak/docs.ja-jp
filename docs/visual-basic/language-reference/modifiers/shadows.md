---
title: Overloads
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351262"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

宣言されたプログラミング要素が、基底クラスにある、同じ名前を持つ要素、またはオーバーロードされる要素のセットを宣言し直して非表示にすることを示します。

## <a name="remarks"></a>Remarks

シャドウ (*名前による非表示*とも呼ばれます) の主な目的は、クラス メンバーの定義を保持することです。 基底クラスには、既に定義されているものと同じ名前の要素を作成する変更が含まれる場合があります。 この場合、`Shadows` 修飾子は、クラスによる参照が、新しい基底クラス要素ではなく定義したメンバーに強制的に解決されるようにします。

シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。 詳細については、「[Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。

## <a name="rules"></a>ルール

- **宣言コンテキスト。** `Shadows` は、クラス レベルでのみ使用できます。 つまり、`Shadows` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

  1 つの宣言ステートメントでは、シャドウ要素を 1 つだけ宣言できます。

- **結合された修飾子。** 同じ宣言内で `Shadows` を `Overloads`、`Overrides`、または `Static` と共に指定することはできません。

- **要素型。** 宣言された要素は、他の任意の種類の要素でシャドウできます。 別のプロパティまたはプロシージャを使用してプロパティまたはプロシージャをシャドウする場合、パラメーターと戻り値の型が基底クラスのプロパティまたはプロシージャ内のパラメーターと一致する必要はありません。

- **アクセス。** 基底クラス内のシャドウされた要素は、通常、それをシャドウする派生クラス内からは使用できません。 ただし、次の考慮事項が適用されます。

  - シャドウ要素が、それを参照するコードからアクセスできない場合、参照はシャドウされた要素に解決されます。 たとえば、`Private` 要素が基底クラスの要素をシャドウすると、`Private` 要素へのアクセス許可を持たないコードが、代わりに基底クラスの要素にアクセスします。

  - 要素をシャドウする場合でも、基底クラスの型で宣言されたオブジェクトを使用して、シャドウされた要素にアクセスできます。 また、`MyBase` を使用してアクセスすることもできます。

`Shadows` 修飾子は、次のコンテキストで使用できます。

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>関連項目

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
