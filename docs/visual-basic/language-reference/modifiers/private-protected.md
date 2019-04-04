---
title: Private Protected (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376391"
---
# <a name="private-protected-visual-basic"></a>Private Protected (Visual Basic)

キーワード組み合わせ `Private Protected` はメンバー アクセス修飾子です。 A`Private Protected`メンバーがアクセスできるは、外側のクラスから派生した型と、含まれるクラスのすべてのメンバーによっては、含んでいるアセンブリが見つかった場合にのみです。

指定できます`Private Protected`クラスのメンバーにのみ適用することはできません`Private Protected`構造体のメンバーに構造体は継承できないためです。

`Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。 これを使用する Visual Basic プロジェクトに次の要素を追加することができます (\*.vbproj) ファイル。 Visual Basic 15.5 いる限り、またはそれ以降は、システムにインストールされているが、最新バージョンの Visual Basic コンパイラでサポートされているすべての言語機能を活用することができます。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

詳細については、[Visual Basic の言語バージョンを設定](../../language-reference/configure-language-version.md)を参照してください。

> [!NOTE]
> Visual Studio での F1 ヘルプを選択する`private protected`のいずれかのヘルプを提供します。[プライベート](private.md)または[保護](protected.md)します。 IDE では、複合語ではなく、カーソルの下の 1 つのトークンを取得します。

## <a name="rules"></a>ルール

- **宣言コンテキスト。** 使用することができます`Private Protected`クラス レベルでのみです。 これは、意味の宣言のコンテキストを`Protected`要素は、クラスでなければなりませんし、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

## <a name="behavior"></a>動作

- **アクセス レベルです。** クラスのすべてのコードは、その要素にアクセスできます。 基本クラスから派生し、同じアセンブリに含まれているすべてのクラスでコードがすべてにアクセスできる、`Private Protected`基底クラスの要素。 基本クラスを基底クラスから派生し、別のアセンブリに含まれているすべてのクラスでのコードでアクセスできませんただし、`Private Protected`要素。

- **アクセス修飾子。** アクセス レベルを指定するキーワードが呼び出される*アクセス修飾子*します。 アクセス修飾子の比較は、[アクセス レベルを Visual Basic で](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。

`Private Protected` 修飾子は、次のコンテキストで使用できます。

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)の入れ子になったクラス

- [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)デリゲートのクラスで入れ子になった

- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)列挙型のクラスで入れ子になった

- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)インターフェイスのクラスで入れ子になった

- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)

- [ステートメントの構造体](../../../visual-basic/language-reference/statements/structure-statement.md)クラスで入れ子になった構造体

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>関連項目

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
