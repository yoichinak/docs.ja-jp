---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0c85564503f3c83e436044cd92ee3014945f1ef3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818385"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素にアクセス制限があるないことを指定します。  
  
## <a name="remarks"></a>Remarks  
 コンポーネントまたはクラス ライブラリなどのコンポーネントのセットを公開している場合に、アセンブリと相互運用するコードでアクセスできるプログラミング要素は、通常します。 このような要素に無制限のアクセスを確保する上で宣言できます`Public`します。  
  
 パブリック アクセスは、アクセスを制限する必要がない、プログラミング要素に通常レベルです。 要素のアクセス レベルが、インターフェイス、モジュール、クラスまたは構造内で宣言されていることに注意してください。 既定値は`Public`特に宣言しない場合。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Public`モジュール、インターフェイス、または名前空間レベルでのみです。 これは、意味の宣言のコンテキストを`Public`要素は、ソース ファイル、名前空間、インターフェイス、モジュール、クラスまたは構造体にある必要があるあり、プロシージャにすることはできません。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** モジュール、クラスまたは構造体にアクセスできるすべてのコードがアクセスできるその`Public`要素。  
  
-   **既定のアクセス。** パブリック アクセスに既定のプロシージャ内のローカル変数は、それらでアクセス修飾子を使用できません。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードが呼び出される*アクセス修飾子*します。 アクセス修飾子の比較は、次を参照してください。[アクセス レベルを Visual Basic で](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
 `Public` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
