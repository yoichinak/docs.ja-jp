---
title: '方法: (Visual Basic) のメモリを節約するためにカスタム イベントを宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3bd58a09d016d818c4cc88c1d2527e81a95411e6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967127"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>方法: (Visual Basic) のメモリを節約するためにカスタム イベントを宣言します。
いくつかの状況があること、アプリケーションのメモリ使用量を低く抑える必要がある場合。 カスタム イベントは、処理するイベントに対してだけメモリを使用するアプリケーションを許可します。  
  
 既定では、クラスのイベントを宣言して、コンパイラは、イベント情報を格納するフィールドのメモリを割り当てます。 クラスに使用されていない多数のイベントがある場合は、不必要が必要になるメモリ。  
  
 Visual Basic ではイベントの既定の実装を使用する代わりには、カスタム イベントを使用して、メモリ使用量をより慎重に管理することができます。  
  
## <a name="example"></a>例  
 この例で、クラスが 1 つのインスタンスを使用して、<xref:System.ComponentModel.EventHandlerList>に格納されているクラス、`Events`使用イベントについての情報を格納するためのフィールド。 <xref:System.ComponentModel.EventHandlerList>クラスは、最適化されたリスト クラスのデリゲートを保持するために設計されています。  
  
 クラスの使用中のすべてのイベント、`Events`どのような方法には、各イベントが処理を追跡するフィールド。  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.ComponentModel.EventHandlerList>
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [方法: ブロックを回避するためにカスタム イベントを宣言します。](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
