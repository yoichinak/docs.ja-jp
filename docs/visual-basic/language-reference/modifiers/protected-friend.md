---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351315"
---
# <a name="protected-friend-visual-basic"></a>Protected Friend (Visual Basic)

キーワード組み合わせ `Protected Friend` はメンバー アクセス修飾子です。 宣言された要素に対して、[Friend](friend.md) アクセスと [Protected](protected.md) アクセスの両方が許可されるため、同じアセンブリ内の任意の場所から、それらの独自のクラスから、および派生クラスから、それらにアクセスできます。 `Protected Friend` は、クラスのメンバーに対してのみ指定できます。構造体は継承できないため、構造体のメンバーに `Protected Friend` を適用することはできません。

> [!NOTE]
> Visual Studio で、`protected friend` に対して F1 ヘルプを選択すると、[protected](protected.md) または [friend](friend.md) のヘルプが表示されます。 IDE では、複合語ではなくカーソルの下にある 1 つのトークンが選択されます。

## <a name="rules"></a>ルール

**宣言コンテキスト。** `Protected Friend` は、クラス レベルでのみ使用できます。 つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

## <a name="see-also"></a>関連項目

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
