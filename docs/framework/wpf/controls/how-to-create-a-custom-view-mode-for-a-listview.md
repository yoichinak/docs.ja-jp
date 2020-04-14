---
title: '方法 : ListView のカスタム表示モードを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243220"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>方法: リスト ビューのカスタム ビュー モードを作成する

この例では、コントロールのカスタム<xref:System.Windows.Controls.ListView.View%2A>モードを作成<xref:System.Windows.Controls.ListView>する方法を示します。  
  
## <a name="example"></a>例  
 コントロールのカスタム<xref:System.Windows.Controls.ViewBase>ビューを作成するときには、このクラスを<xref:System.Windows.Controls.ListView>使用する必要があります。 クラスから派生したビュー モードを`PlainView`次の例に<xref:System.Windows.Controls.ViewBase>示します。  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 カスタム ビューにスタイルを適用するには、 クラス<xref:System.Windows.Style>を使用します。 次の例では、<xref:System.Windows.Style>ビュー`PlainView`モードの を定義します。 前の例では、このスタイルは、 に定義されている<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>プロパティの値として設定されています。 `PlainView`  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 カスタム ビュー モードでデータのレイアウトを定義するには、オブジェクト<xref:System.Windows.DataTemplate>を定義します。 ビュー モードでデータ<xref:System.Windows.DataTemplate>を表示するために使用できる を定義する`PlainView`例を次に示します。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 次の例は、前の例<xref:System.Windows.ResourceKey>で定義`PlainView`された を使用する<xref:System.Windows.DataTemplate>ビュー モードの を定義する方法を示しています。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <xref:System.Windows.Controls.ListView>プロパティをリソース キーに設定すると、コントロールは<xref:System.Windows.Controls.ListView.View%2A>カスタム ビューを使用できます。 次の例は、`PlainView`<xref:System.Windows.Controls.ListView>のビュー モードとして指定する方法を示しています。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 完全なサンプルについては、「[複数のビューを含むリストビュー (C#)」](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)または[「複数ビューを含むリストビュー (Visual Basic)」を参照](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [操作方法に関するトピック](listview-how-to-topics.md)
- [ListView の概要](listview-overview.md)
- [GridView の概要](gridview-overview.md)
