---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 52fdbfa3b0cd79cc9714a13a75716829163e45f6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967374"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素にその宣言を含むアセンブリ内からのみアクセスできることを指定します。  
  
## <a name="remarks"></a>コメント  
 多くの場合、クラスとそれらを宣言するコンポーネントによってだけでなく、アセンブリ全体で使用される構造体などのプログラミング要素にします。 ただし、(たとえば、アプリケーションが専用) 場合、アセンブリ外部のコードでアクセスできるようにする必要があります。 この方法で要素へのアクセスを制限する場合は、使用して宣言できます、`Friend`修飾子。  
  
 その他のクラス、構造、およびモジュールを同じコンパイルでコード アセンブリはすべてにアクセスできる、`Friend`そのアセンブリ内の要素。  
  
 `Friend` アクセスは、アプリケーションのプログラミング要素の任意のレベルでは多くの場合と`Friend`インターフェイス、モジュール、クラスまたは構造のレベルで既定のアクセス。  
  
 使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。 宣言コンテキストはそのため、`Friend`ソース ファイル、名前空間、インターフェイス、モジュール、クラスまたは構造体を要素として使用することがあります。 プロシージャをすることはできません。  

> [!NOTE]
> 使用することも、 [Protected Friend](protected-friend.md)アクセス修飾子、クラス メンバーに、派生クラスとクラスが定義されている同じアセンブリからそのクラス内からアクセスできるようします。 使用して、同じアセンブリ内の派生クラスからそのクラス内からのメンバーへのアクセスを制限する、[Private Protected](private-protected.md)アクセス修飾子。

 比較について`Friend`および他のアクセス修飾子を参照してください[アクセス レベルを Visual Basic で](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
> [!NOTE]
>  別のアセンブリがフレンド アセンブリ、型とメンバーとしてマークされているすべてのアクセスを許可するかを指定することができます`Friend`します。 詳細については、[Friend アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)に関するページを参照してください。  
  
## <a name="example"></a>例  
 次のクラスは、`Friend`修飾子を特定のメンバーへのアクセスに同じアセンブリ内の他のプログラミング要素を許可します。  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>使用法  
 使用することができます、`Friend`これらのコンテキストでの修飾子。  
  
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
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
