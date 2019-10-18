---
title: Protected Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524776"
---
# <a name="protected-friend-visual-basic"></a>Protected Friend (Visual Basic)

キーワード組み合わせ `Protected Friend` はメンバー アクセス修飾子です。 このクラスは、宣言された要素に対して[フレンド](friend.md)アクセスと[保護された](protected.md)アクセスの両方を実行するため、同じアセンブリ内の任意の場所、独自のクラス、および派生クラスからアクセスできます。 @No__t_0 は、クラスのメンバーに対してのみ指定できます。構造体のメンバーに `Protected Friend` を適用することはできません。構造体を継承することはできません。

> [!NOTE]
> Visual Studio では、`protected friend` で F1 ヘルプを選択すると、 [protected](protected.md)または[friend](friend.md)のヘルプが表示されます。 IDE は、複合単語ではなくカーソルの下にある1つのトークンを選択します。

## <a name="rules"></a>ルール

**宣言コンテキスト。** @No__t_0 はクラスレベルでのみ使用できます。 つまり、`Protected` 要素の宣言コンテキストはクラスである必要があり、ソースファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

## <a name="see-also"></a>関連項目

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic のアクセスレベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
