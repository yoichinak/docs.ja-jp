---
title: ScrollViewer の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186985"
---
# <a name="scrollviewer-overview"></a>ScrollViewer の概要
ユーザー インターフェイス内のコンテンツは、多くの場合、コンピューター画面の表示領域よりも大きいです。 この<xref:System.Windows.Controls.ScrollViewer>コントロールは、アプリケーションのコンテンツのスクロールを有効にする[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]便利な方法を提供します。 このトピックでは、<xref:System.Windows.Controls.ScrollViewer>この要素を紹介し、いくつかの使用例を示します。  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>ScrollViewer コントロール  
 アプリケーションで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スクロールを可能にする 2 つの定義済み<xref:System.Windows.Controls.Primitives.ScrollBar>要素<xref:System.Windows.Controls.ScrollViewer>があります: と . コントロール<xref:System.Windows.Controls.ScrollViewer>は、スクロール可能な領域<xref:System.Windows.Controls.Primitives.ScrollBar>に他の表示可能な要素を表示<xref:System.Windows.Controls.Panel>するために、水平方向および垂直方向の要素とコンテンツ コンテナー (要素など) をカプセル化します。 コンテンツのスクロールに要素を使用するには、<xref:System.Windows.Controls.Primitives.ScrollBar>カスタム オブジェクトを作成する必要があります。 ただし、機能をカプセル化<xref:System.Windows.Controls.ScrollViewer>する複合コントロールであるため、この要素自体を<xref:System.Windows.Controls.Primitives.ScrollBar>使用できます。  
  
 コントロール<xref:System.Windows.Controls.ScrollViewer>は、マウス コマンドとキーボード コマンドの両方に応答し、あらかじめ指定された増分でコンテンツをスクロールする多数のメソッドを定義します。 イベントを<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>使用して、状態の変化を<xref:System.Windows.Controls.ScrollViewer>検出できます。  
  
 A<xref:System.Windows.Controls.ScrollViewer>は 1 つの子<xref:System.Windows.Controls.Panel>(通常は要素の<xref:System.Windows.Controls.Panel.Children%2A>コレクションをホストできる要素) しか持てなさがありません。 プロパティ<xref:System.Windows.Controls.ContentPresenter.Content%2A>は、 の唯一の<xref:System.Windows.Controls.ScrollViewer>子を定義します。  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>物理スクロールと論理スクロール  
 物理スクロールは、定義済みの物理インクリメント(通常ピクセル単位で宣言されている値) でコンテンツをスクロールするために使用します。 論理スクロールは、論理ツリーの次の項目にスクロールするために使用します。 物理的なスクロールは、ほとんどの<xref:System.Windows.Controls.Panel>要素の既定のスクロール動作です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は両方の種類のスクロールをサポートしています。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo インターフェイス  
 インターフェイス<xref:System.Windows.Controls.Primitives.IScrollInfo>は、または派生コントロール内のメインスクロール<xref:System.Windows.Controls.ScrollViewer>領域を表します。 インターフェイスは、物理的なインクリメントではなく、論理ユニットでスクロール<xref:System.Windows.Controls.Panel>する必要がある要素によって実装できるスクロールプロパティとメソッドを定義します。 のインスタンス<xref:System.Windows.Controls.Primitives.IScrollInfo>を派生<xref:System.Windows.Controls.Panel>にキャストし、そのスクロール メソッドを使用すると、ピクセル単位ではなく、子コレクションの次の論理ユニットにスクロールする便利な方法が提供されます。 既定では、コントロール<xref:System.Windows.Controls.ScrollViewer>は物理単位によるスクロールをサポートします。  
  
 <xref:System.Windows.Controls.StackPanel>実装<xref:System.Windows.Controls.VirtualizingStackPanel><xref:System.Windows.Controls.Primitives.IScrollInfo>とネイティブの両方が論理スクロールをサポートしています。 論理スクロールをネイティブにサポートするレイアウト コントロールの場合でも、<xref:System.Windows.Controls.Panel>ホスト要素を a<xref:System.Windows.Controls.ScrollViewer>にラップし、プロパティを に<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>`false`設定することで、物理的なスクロールを実現できます。  
  
 のインスタンスをキャストし、インターフェイスで定義されたコンテンツ<xref:System.Windows.Controls.Primitives.IScrollInfo>スクロール<xref:System.Windows.Controls.StackPanel>メソッド (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>および<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) を使用する方法を次のコード例に示します。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer 要素の定義と使用  
 テキストと四角形を<xref:System.Windows.Controls.ScrollViewer>含むウィンドウに を作成する例を次に示します。 <xref:System.Windows.Controls.Primitives.ScrollBar>要素は必要な場合にのみ表示されます。 ウィンドウのサイズを変更すると、<xref:System.Windows.Controls.Primitives.ScrollBar><xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A>要素は表示され、プロパティ<xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>の値が更新されたため、非表示になります。  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>ScrollViewer のスタイル設定  
 Windows プレゼンテーションファンデーションのすべてのコントロールと<xref:System.Windows.Controls.ScrollViewer>同様に、コントロールの既定のレンダリング動作を変更するためにスタイルを設定できます。 コントロールのスタイル設定の詳細については、「[スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)」を参照してください。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>ドキュメントの改ページ調整  
 ドキュメントのコンテンツでは、スクロールする代わりに、改ページ調整をサポートするドキュメントのコンテナーを選択します。 <xref:System.Windows.Documents.FlowDocument>は、複数ページにわたってコンテンツの改ページをサポートする<xref:System.Windows.Controls.FlowDocumentPageViewer>、表示コントロール内でホストされるように設計されたドキュメント用であり、スクロールの必要を防ぎます。 <xref:System.Windows.Controls.DocumentViewer>は、従来のスクロール<xref:System.Windows.Documents.FixedDocument>を使用して表示領域の領域外のコンテンツを表示するコンテンツを表示するためのソリューションを提供します。  
  
 ドキュメント形式とプレゼンテーション オプションの詳細については、「[WPF のドキュメント](../advanced/documents-in-wpf.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [方法 : スクロール ビューアーを作成する](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF のドキュメント](../advanced/documents-in-wpf.md)
- [ScrollBar のスタイルとテンプレート](scrollbar-styles-and-templates.md)
- [コントロール](../advanced/optimizing-performance-controls.md)
