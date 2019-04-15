---
title: Protected Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151776"
---
# <a name="protected-friend-visual-basic"></a>Protected Friend (Visual Basic)

キーワード組み合わせ `Protected Friend` はメンバー アクセス修飾子です。 両方を設定する[フレンド](friend.md)アクセスと[Protected](protected.md)および派生クラス独自のクラスからは、同じアセンブリ内の任意の場所からアクセスできるように、宣言された要素へのアクセス。 指定できます`Protected Friend`クラスのメンバーにのみ適用することはできません`Protected Friend`構造体のメンバーに構造体は継承できないためです。

> [!NOTE]
> Visual Studio での F1 ヘルプを選択する`protected friend`のいずれかのヘルプを提供します。[保護](protected.md)または[フレンド](friend.md)します。 IDE では、複合語ではなく、カーソルの下の 1 つのトークンを取得します。

## <a name="rules"></a>ルール

- **宣言コンテキスト。** 使用することができます`Protected Friend`クラス レベルでのみです。 これは、意味の宣言のコンテキストを`Protected`要素は、クラスでなければなりませんし、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。 

## <a name="see-also"></a>関連項目

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [プロテクト](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [プライベート](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
