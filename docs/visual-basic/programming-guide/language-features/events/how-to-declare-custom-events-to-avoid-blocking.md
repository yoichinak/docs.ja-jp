---
title: '方法: カスタム イベントを宣言してブロックを回避する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345147"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)
場合によっては、あるイベント ハンドラーにより後続のイベント ハンドラーがブロックされないようにする必要があります。 カスタム イベントを使用すると、イベントでそのイベント ハンドラーを非同期的に呼び出すことができます。  
  
 既定では、イベント宣言用のバッキングストア フィールドは、すべてのイベント ハンドラーを連続的にまとめたマルチキャスト デリゲートになります。 つまり、あるハンドラーの完了までに長時間かかる場合、他のハンドラーはこのハンドラーが完了するまでブロックされます。 (動作が適切なイベント ハンドラーであれば、実行時間が長期間にわたったり、操作をブロックする可能性が出たりすることはありません。)  
  
 Visual Basic に備わっている既定のイベント実装ではなく、カスタム イベントを使用することで、イベント ハンドラーを非同期的に実行できます。  
  
## <a name="example"></a>例  
 次の例では、`EventHandlerList` フィールドに格納されている <xref:System.Collections.ArrayList> に対して、`AddHandler` アクセサーで `Click` イベントの各ハンドラーのデリゲートを追加しています。  
  
 コードで `Click` イベントが発生すると、`RaiseEvent` アクセサーにより、すべてのイベント ハンドラーのデリゲートが <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> メソッドで非同期的に呼び出されます。 このメソッドは各ハンドラーをワーカー スレッドで呼び出してすぐに返すため、ハンドラーどうしがブロックし合うことはありません。  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
