---
title: Protected (Visual Basic)
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
ms.openlocfilehash: 88e13fcd03c6a10cf1450cec90f9ca60aedc3eb1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819165"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
1 つまたは複数のプログラミング要素が宣言されていることを指定するメンバー アクセス修飾子は、独自のクラス内または派生クラスからのみアクセスできます。  
  
## <a name="remarks"></a>Remarks  
 クラスで宣言されたプログラミング要素が機密データまたは制限付きのコードを格納することもありますし、要素へのアクセスを制限します。 ただし、クラスが継承可能でないと、派生クラスの階層が期待どおり場合、これらの派生クラスのデータまたはコードにアクセスするために必要な場合があります。 このような場合は、基底クラスとすべての派生クラスの両方にアクセスできる要素をします。 この方法で要素へのアクセスを制限するために宣言できます`Protected`します。  

> [!NOTE]
> `Protected`アクセス修飾子は、その他の 2 つの修飾子と組み合わせることができます。
> - [Protected Friend](protected-friend.md)修飾子は、クラス メンバーを同じアセンブリのクラスが定義されていると、派生クラスからそのクラス内からアクセスできます。 
> - [Private Protected](private-protected.md)修飾子により、クラス メンバー アクセス、含んでいるアセンブリ内でのみ、派生型です。
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Protected`クラス レベルでのみです。 これは、意味の宣言のコンテキストを`Protected`要素は、クラスでなければなりませんし、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。  

## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** クラスのすべてのコードは、その要素にアクセスできます。 すべての基本クラスから派生したクラス内のコードにアクセスできます、`Protected`基底クラスの要素。 これは、派生のすべてのジェネレーションに当てはまります。 これは、クラスにアクセスできることを意味`Protected`基底クラスの基底クラスの要素。  
  
     保護されたアクセスは、スーパー セットまたはサブセットのフレンド アクセスではありません。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードが呼び出される*アクセス修飾子*します。 アクセス修飾子の比較は、次を参照してください。[アクセス レベルを Visual Basic で](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
 `Protected` 修飾子は、次のコンテキストで使用できます。  
  
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
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
