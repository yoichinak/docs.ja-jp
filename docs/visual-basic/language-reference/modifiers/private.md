---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819478"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素に内に含まれる任意の型を含む、宣言のコンテキストからのみアクセスできることを指定します。  
  
## <a name="remarks"></a>コメント  
 プログラミング要素は、独自の機能または機密データを含む、通常はできるだけ厳密にへのアクセスを制限します。 最大の制限は、モジュール、クラス、またはそれへのアクセスを定義する構造のみを許可することで実現します。 この方法で要素へのアクセスを制限するために宣言できます`Private`します。  

> [!NOTE]
> 使用することも、[Private Protected](private-protected.md)メンバーにそのクラス内、および、含んでいるアセンブリにある派生クラスからアクセスできるよう、アクセス修飾子。

## <a name="rules"></a>ルール  

-   **宣言コンテキスト。** `Private` は、モジュール レベルでのみ使用できます。 これは、意味の宣言のコンテキストを`Private`要素は、モジュール、クラス、または構造体にある必要があるあり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** 宣言コンテキスト内ですべてのコードがアクセスできるその`Private`要素。 これには、入れ子になったクラスまたは列挙型の代入式などの包含の種類の中でコードが含まれます。 宣言コンテキストの外側でコードがアクセスできない、`Private`要素。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードが呼び出される*アクセス修飾子*します。 アクセス修飾子の比較は、次を参照してください。[アクセス レベルを Visual Basic で](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
 `Private` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
