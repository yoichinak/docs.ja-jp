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
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209425"
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
