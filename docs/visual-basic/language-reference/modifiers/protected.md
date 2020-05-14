---
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 740c998b8a6ccc6798bce37e9b08e408dac7c17d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351299"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

1 つ以上の宣言されたプログラミング要素を指定するメンバー アクセス修飾子は、独自のクラス内から、または派生クラスからのみアクセスできます。

## <a name="remarks"></a>Remarks

場合によっては、クラスで宣言されたプログラミング要素に機密データまたは制限コードが含まれていて、要素へのアクセスを制限する必要があります。 ただし、クラスが継承可能であり、派生クラスの階層を想定している場合は、これらの派生クラスがデータまたはコードにアクセスする必要がある場合があります。 このような場合は、基底クラスとすべての派生クラスの両方から要素にアクセスできるようにする必要があります。 この方法で要素へのアクセスを制限するには、`Protected` を使用して宣言できます。

> [!NOTE]
> `Protected` アクセス修飾子は、次の 2 つの修飾子と組み合わせることができます。
>
> - [Protected Friend](protected-friend.md) 修飾子は、クラス メンバーに、クラス内、派生クラス、およびクラスが定義されている同じアセンブリからアクセスできるようにします。
> - [Private Protected](private-protected.md) 修飾子は、派生型によってクラス メンバーにアクセスできるようにしますが、その包含アセンブリ内に限られます。

## <a name="rules"></a>ルール

**宣言コンテキスト。** `Protected` は、クラス レベルでのみ使用できます。 つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

## <a name="behavior"></a>動作

- **アクセス レベル。** クラス内のすべてのコードで、その要素にアクセスできます。 基底クラスから派生するすべてのクラスのコードで、基底クラスのすべての `Protected` 要素にアクセスできます。 これは、派生のすべての世代に当てはまります。 これは、クラスが基底クラスの基底クラスの `Protected` 要素にアクセスでき、以下同様に続くことを意味します。

     保護されたアクセスは、フレンド アクセスのスーパーセットまたはサブセットではありません。

- **アクセス修飾子。** アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。 アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

`Protected` 修飾子は、次のコンテキストで使用できます。

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

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
