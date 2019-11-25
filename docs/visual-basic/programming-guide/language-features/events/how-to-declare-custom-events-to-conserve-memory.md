---
title: '方法: カスタム イベントを宣言してメモリを節約する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345132"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)
There are several circumstances when it is important that an application keep its memory usage low. Custom events allow the application to use memory only for the events that it handles.  
  
 By default, when a class declares an event, the compiler allocates memory for a field to store the event information. If a class has many unused events, they needlessly take up memory.  
  
 Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.  
  
## <a name="example"></a>例  
 In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use. The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.  
  
 All events in the class use the `Events` field to keep track of what methods are handling each event.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.EventHandlerList>
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [方法: カスタム イベントを宣言してブロックを回避する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
