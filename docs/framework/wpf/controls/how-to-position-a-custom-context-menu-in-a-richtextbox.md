---
title: '方法: カスタム コンテキスト メニューを RichTextBox に配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: abb5bbb5d5a537b14f334782e87fa7caf0c7976f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367879"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>方法: カスタム コンテキスト メニューを RichTextBox に配置する
この例のカスタム コンテキスト メニューを配置する方法を示しています、<xref:System.Windows.Controls.RichTextBox>します。  
  
 **RichTextBox** のカスタム コンテキスト メニューを実装する場合、コンテキスト メニューの配置の処理を行う必要があります。  既定では、**RichTextBox** の中央でカスタム コンテキスト メニューが開きます。  
  
## <a name="example"></a>例  
 既定の配置動作を上書きするには、追加のリスナーを<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント。  次の例では、プログラムによってこれを実行する方法を説明します。  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>例  
 次の例は、対応する実装を示します<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント リスナー。  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>関連項目
- [RichTextBox の概要](richtextbox-overview.md)
- [TextBox の概要](textbox-overview.md)
