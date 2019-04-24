---
title: '方法: (Visual Basic) がブロックされないようにするカスタム イベントを宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 6eea47ea2c8aee697eb34ca904dad22ca88e6ce4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821258"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>方法: (Visual Basic) がブロックされないようにするカスタム イベントを宣言します。
その 1 つのイベント ハンドラーが後続のイベント ハンドラーをブロックしない必要がある場合は、いくつかの状況にがあります。 カスタム イベントは、そのイベント ハンドラーを非同期的に呼び出すイベントを許可します。  
  
 既定では、イベントの宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーを順番に結合するマルチキャスト デリゲートです。 つまり、1 つのハンドラーが完了に長時間を受け取る場合、ブロック、その他のハンドラーが完了するまで。 (正常に動作するイベント ハンドラーは、時間のかかるまたはブロックしている可能性がある操作を実行する必要があることはありません)。  
  
 Visual Basic ではイベントの既定の実装を使用する代わりに、イベント ハンドラーを非同期的に実行するのにカスタム イベントを使用できます。  
  
## <a name="example"></a>例  
 この例で、`AddHandler`アクセサーの各ハンドラーのデリゲートの追加、`Click`イベントを<xref:System.Collections.ArrayList>に格納されている、`EventHandlerList`フィールド。  
  
 コードが発生の場合、`Click`イベント、`RaiseEvent`アクセサーが非同期的を使用してすべてのイベント ハンドラー デリゲートを呼び出す、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>メソッド。 そのメソッドでは、ワーカー スレッドで各ハンドラーが呼び出され、ハンドラーは、互いをブロックできませんので、すぐに返します。  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [方法: カスタム イベントを宣言してメモリを節約する](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
