---
title: '方法: イベント ハンドラーでソース要素を検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 8c1ff53e5af1ddfda17328291c5e22b57a8fe0e2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359468"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>方法: イベント ハンドラーでソース要素を検索する
この例では、イベント ハンドラーでソース要素を検索する方法を示します。  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>分離コード ファイルで宣言されているイベント ハンドラー。 ハンドラーがアタッチされているボタンをクリックすると、ハンドラーは、プロパティ値を変更します。 ハンドラー コードを使用して、<xref:System.Windows.RoutedEventArgs.Source%2A>のルーティング イベントのデータを変更するイベントの引数で報告されるプロパティ、<xref:System.Windows.FrameworkElement.Width%2A>プロパティ値、<xref:System.Windows.RoutedEventArgs.Source%2A>要素。  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.RoutedEventArgs>
- [ルーティング イベントの概要](routed-events-overview.md)
- [方法トピック](events-how-to-topics.md)
