---
title: '方法: ListView のカスタム表示モードを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 609781e9ac2db9c9beef049886617e541199e5dd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374766"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>方法: ListView のカスタム表示モードを作成する
この例は、カスタムを作成する方法を示しています。<xref:System.Windows.Controls.ListView.View%2A>のモードを<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="example"></a>例  
 使用する必要があります、<xref:System.Windows.Controls.ViewBase>クラス用のカスタム ビューを作成するときに、<xref:System.Windows.Controls.ListView>コントロール。 次の例では、呼び出される表示モード`PlainView`から派生、<xref:System.Windows.Controls.ViewBase>クラス。  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 カスタム ビューには、スタイルを適用するには、使用、<xref:System.Windows.Style>クラス。 次の例では、定義、<xref:System.Windows.Style>の`PlainView`表示モード。 前の例では、このスタイルが設定の値として、<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>プロパティに対して定義されている`PlainView`します。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 カスタム表示モードでは、データのレイアウトを定義するには、定義、<xref:System.Windows.DataTemplate>オブジェクト。 次の例では、定義、<xref:System.Windows.DataTemplate>データを表示する使用できる、`PlainView`表示モード。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 次の例は、定義する方法を示します、<xref:System.Windows.ResourceKey>の`PlainView`表示モードを使用する、<xref:System.Windows.DataTemplate>前の例で定義されています。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A<xref:System.Windows.Controls.ListView>設定した場合、コントロールがカスタム ビューを使用できます、<xref:System.Windows.Controls.ListView.View%2A>プロパティをリソース キー。 次の例は、指定する方法を示します`PlainView`の表示モードとして、<xref:System.Windows.Controls.ListView>します。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 サンプル全体については、[ListView で複数のビュー (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)または[複数 Views(Visual Basic) で ListView](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [方法トピック](listview-how-to-topics.md)
- [ListView の概要](listview-overview.md)
- [GridView の概要](gridview-overview.md)
