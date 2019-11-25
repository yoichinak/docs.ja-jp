---
title: 継承されたイベント ハンドラーのトラブルシューティング
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345108"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
This topic lists common issues that arise with event handlers in inherited components.  
  
## <a name="procedures"></a>手順  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Code in Event Handler Executes Twice for Every Call  
  
- An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause. The method in the base class is already associated with the event and will fire accordingly. Remove the `Handles` clause from the inherited method.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.  
  
## <a name="see-also"></a>関連項目

- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
