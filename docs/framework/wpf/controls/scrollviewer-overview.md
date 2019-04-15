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
ms.openlocfilehash: a3302d9c360b0918a1fce956af3e3aa14f29361b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212428"
---
# <a name="scrollviewer-overview"></a>ScrollViewer の概要
ユーザー インターフェイス内のコンテンツは、多くの場合、コンピューター画面の表示領域よりも大きいです。 <xref:System.Windows.Controls.ScrollViewer>コントロール内のコンテンツのスクロールを有効にする便利な手段を提供する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション。 このトピックでは、<xref:System.Windows.Controls.ScrollViewer>要素と、いくつかの使用例を提供します。  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer コントロール  
 スクロールを有効にする 2 つの定義済みの要素がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション:<xref:System.Windows.Controls.Primitives.ScrollBar>と<xref:System.Windows.Controls.ScrollViewer>します。 <xref:System.Windows.Controls.ScrollViewer>コントロールに水平スクロール バーと垂直方向がカプセル化します<xref:System.Windows.Controls.Primitives.ScrollBar>要素およびコンテンツ コンテナー (など、<xref:System.Windows.Controls.Panel>要素)、スクロール可能な領域に表示されるその他の要素を表示するためにします。 使用するには、カスタム オブジェクトを構築する必要があります、<xref:System.Windows.Controls.Primitives.ScrollBar>要素コンテンツのスクロールします。 ただし、使用することができます、<xref:System.Windows.Controls.ScrollViewer>単独の要素、複合コントロールであるカプセル化<xref:System.Windows.Controls.Primitives.ScrollBar>機能します。  
  
 <xref:System.Windows.Controls.ScrollViewer>コントロールがマウスとキーボードの両方のコマンドに応答して、あらかじめ決められたインクリメントでコンテンツをスクロールするために多数のメソッドを定義します。 使用することができます、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>で変更を検出するイベントを<xref:System.Windows.Controls.ScrollViewer>状態。  
  
 A<xref:System.Windows.Controls.ScrollViewer>通常 1 つの子をしか、<xref:System.Windows.Controls.Panel>要素をホストできる、<xref:System.Windows.Controls.Panel.Children%2A>要素のコレクション。 <xref:System.Windows.Controls.ContentPresenter.Content%2A>プロパティ定義の唯一の子、<xref:System.Windows.Controls.ScrollViewer>します。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>物理スクロールと論理スクロール  
 物理スクロールは、定義済みの物理インクリメント(通常ピクセル単位で宣言されている値) でコンテンツをスクロールするために使用します。 論理スクロールは、論理ツリーの次の項目にスクロールするために使用します。 ほとんどの既定のスクロール動作は、物理スクロール<xref:System.Windows.Controls.Panel>要素。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 両方の種類のスクロールをサポートしています。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo インターフェイス  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイス内のメインのスクロール領域を表す、<xref:System.Windows.Controls.ScrollViewer>または派生コントロール。 スクロールのプロパティとメソッドを実装できるインターフェイスを定義します<xref:System.Windows.Controls.Panel>物理インクリメントではなく、論理ユニットのスクロールを必要とします。 インスタンスにキャスト<xref:System.Windows.Controls.Primitives.IScrollInfo>を派生する<xref:System.Windows.Controls.Panel>ピクセル インクリメントではなく、子のコレクションでは、次の論理ユニットにスクロールする便利な方法を提供し、そのスクロール メソッドを使用しているとします。 既定で、<xref:System.Windows.Controls.ScrollViewer>コントロールは、物理単位でスクロールをサポートしています。  
  
 <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>両方実装<xref:System.Windows.Controls.Primitives.IScrollInfo>論理スクロールをネイティブでサポートしているとします。 ホストをラップすることによって、物理スクロールを実現するレイアウトをネイティブ サポート論理スクロールをコントロールにはまだできます<xref:System.Windows.Controls.Panel>内の要素を<xref:System.Windows.Controls.ScrollViewer>と設定、<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>プロパティを`false`します。  
  
 次のコード例は、のインスタンスにキャストする方法を示します<xref:System.Windows.Controls.Primitives.IScrollInfo>を<xref:System.Windows.Controls.StackPanel>コンテンツ スクロール メソッドを使用して (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>と<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) インターフェイスによって定義されています。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>ScrollViewer 要素の定義と使用  
 次の例では、作成、<xref:System.Windows.Controls.ScrollViewer>ウィンドウにいくつかのテキストと四角形が含まれています。 <xref:System.Windows.Controls.Primitives.ScrollBar> 要素は、必要ながときにのみ表示されます。 ウィンドウのサイズを変更するときに、<xref:System.Windows.Controls.Primitives.ScrollBar>要素の表示し、非表示の更新された値によって、<xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A>と<xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>プロパティ。  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>ScrollViewer のスタイル設定  
 Windows Presentation foundation のすべてのコントロールと同様、<xref:System.Windows.Controls.ScrollViewer>コントロールの既定のレンダリング動作を変更するにはスタイルを設定できます。 コントロールのスタイル設定の詳細については、「[スタイルとテンプレート](styling-and-templating.md)」を参照してください。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>ドキュメントの改ページ調整  
 ドキュメントのコンテンツでは、スクロールする代わりに、改ページ調整をサポートするドキュメントのコンテナーを選択します。 <xref:System.Windows.Documents.FlowDocument> などの表示コントロール内でホストされるように設計されたドキュメントが<xref:System.Windows.Controls.FlowDocumentPageViewer>、スクロールの必要をなくし、複数のページ コンテンツの改ページ調整をサポートします。 <xref:System.Windows.Controls.DocumentViewer> 表示するため、ソリューションを提供します。<xref:System.Windows.Documents.FixedDocument>コンテンツで、従来のスクロールを使用して、表示領域の領域外のコンテンツを表示します。  
  
 ドキュメント形式とプレゼンテーション オプションの詳細については、「[WPF のドキュメント](../advanced/documents-in-wpf.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [方法: スクロール ビューアーを作成します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF のドキュメント](../advanced/documents-in-wpf.md)
- [ScrollBar のスタイルとテンプレート](scrollbar-styles-and-templates.md)
- [コントロール](../advanced/optimizing-performance-controls.md)
