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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345147"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>方法: カスタム イベントを宣言してブロックを回避する (Visual Basic)
There are several circumstances when it is important that one event handler not block subsequent event handlers. Custom events allow the event to call its event handlers asynchronously.  
  
 By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers. This means that if one handler takes a long time to complete, it blocks the other handlers until it completes. (Well-behaved event handlers should never perform lengthy or potentially blocking operations.)  
  
 Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.  
  
## <a name="example"></a>例  
 In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.  
  
 When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method. That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
