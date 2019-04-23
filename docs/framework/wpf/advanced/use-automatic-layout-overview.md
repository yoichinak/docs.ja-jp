---
title: 自動レイアウトの使用の概要
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 5df6d39bef137bd4005316eac252ca0952df5e7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098781"
---
# <a name="use-automatic-layout-overview"></a>自動レイアウトの使用の概要
このトピックで作成する方法に関する開発者向けのガイドラインは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ローカライズ可能なアプリケーション[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]します。 以前は、UI のローカライズは時間のかかるプロセスでした。 各言語 UI が変更するには、ピクセル単位で調整が必要です。 今日は、適切な設計とコーディング標準、[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]ローカライザーがあるサイズ変更や、実行する位置を変更できるように構築できます。 簡単にサイズ変更や位置が変更された可能性のあるアプリケーションを作成する方法は、自動レイアウトをという名前を使用して実現できます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションの設計。  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>自動レイアウトを使用する利点  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プレゼンテーション システムは強力で柔軟なさまざまな言語の要件に合わせて調整できるアプリケーションの要素をレイアウトする機能を提供します。 次の一覧は、自動レイアウトの利点の一部を示しています。  

-   任意の言語で UI を表示します。  

-   テキストの翻訳後のコントロールの位置とサイズを再調整する必要性が軽減されます。  
  
-   ウィンドウのサイズを再調整する必要性を軽減します。  

-   UI のレイアウトは、任意の言語で正しく表示します。  

-   ローカリゼーションは、文字列の翻訳より若干高であるポイントに削減できます。  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>自動レイアウトとコントロール  
 自動レイアウトには、コントロールのサイズを自動的に調整するアプリケーションができるようにします。 たとえば、文字列の長さに合わせてコントロールを変更できます。 この機能により、ローカライザーに文字列を変換するには不要になった、翻訳されたテキストに合わせてコントロールのサイズを変更する必要があります。 次の例では、英語コンテンツをボタンを作成します。  
  
 [!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 例をスペイン語のボタンのために実行する必要がある、テキストを変更します。 例えば以下のようにします。  
  
 [!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 次の図は、コード サンプルの出力を示しています。  
  
 ![テキストの言語が異なる同じボタン](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>自動レイアウトとコーディング標準  
 自動レイアウトのアプローチを使用するには、一連のコーディングし設計標準と完全にローカライズ可能な UI を生成するために規則が必要です。 次のガイドライン、自動レイアウトのコーディングが容易になります。  

**絶対位置を使用しないでください。**

- 使用しない<xref:System.Windows.Controls.Canvas>のため、絶対に要素を配置します。

- 使用<xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.StackPanel>、および<xref:System.Windows.Controls.Grid>コントロールを配置します。

パネルのさまざまな種類の詳細については、次を参照してください。[パネルの概要](../controls/panels-overview.md)します。

**ウィンドウの固定サイズを設定しないでください。**

- <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType> を使用してください。 例:

   [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**追加します。 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- 追加、<xref:System.Windows.FrameworkElement.FlowDirection%2A>アプリケーションのルート要素にします。

   WPF には、水平方向をサポートする便利な方法、双方向、および垂直方向のレイアウトが用意されています。 プレゼンテーションのフレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A>レイアウトを定義するプロパティを使用できます。 フロー方向パターンは次のとおりです。
   
     - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb)-ラテン語や東アジア言語などのための横書きレイアウト。
     
     - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb)-アラビア語やヘブライ語などの双方向。

**物理フォントではなく複合フォントを使用します。**

- 複合のフォントを含む、<xref:System.Windows.Controls.Control.FontFamily%2A>プロパティはローカライズする必要はありません。

- 開発者では、次のフォントのいずれかを使用したり、独自に作成することができます。

   - グローバル ユーザー インターフェイス
   - グローバル San Serif
   - グローバル Serif

**Xml:lang を追加します。**

- 追加、`xml:lang`など、UI のルート要素に属性`xml:lang="en-US"`英語版のアプリケーション。

- 複合フォントを使用しているため`xml:lang`を使用するフォントを確認するには、多言語シナリオをサポートするには、このプロパティを設定します。

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>自動レイアウトとグリッド  
 <xref:System.Windows.Controls.Grid>要素は、開発者が要素を配置するため、自動レイアウト用に便利です。 A<xref:System.Windows.Controls.Grid>コントロールの列と行の並べ替え方法を使用して、その子要素間で使用可能な領域を配布します。 UI 要素が複数のセルにまたがることができます、グリッド内にグリッドを作成できます。 グリッドを作成し、複雑な UI を配置することができるため便利です。 次の例では、グリッドを使用したいくつかのボタンとテキストの位置を示します。 セルの幅と高さに設定されている通知<xref:System.Windows.GridUnitType.Auto>。 したがって、イメージ付きのボタンを含むセルを画像に合わせて調整します。  

 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 次の図は、前のコードによって生成されるグリッドを示します。  
  
 ![グリッドの例](./media/glob-grid.png "glob_grid")  
グリッド  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>自動レイアウトと IsSharedSizeScope プロパティを使用してグリッド  
 A<xref:System.Windows.Controls.Grid>要素がコンテンツに合わせて調整されるコントロールを作成する、ローカライズ可能なアプリケーションで役に立ちます。 ただし、たい場コンテンツに関係なく特定のサイズを維持するコントロール。 たとえば、"OK"があれば、「キャンセル」と「参照」おそらくたくないボタンのサイズをコンテンツに合わせてボタン。 この場合、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType>添付プロパティは複数の grid 要素間で同じサイズの変更を共有するために便利です。 次の例は、列と行の複数の間でデータをサイズ変更を共有する方法を示します<xref:System.Windows.Controls.Grid>要素。  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **注**完全なコード サンプルでは、次を参照してください[共有サイズ設定プロパティの間でグリッド。](../controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>関連項目

- [WPF のグローバリゼーション](globalization-for-wpf.md)
- [自動レイアウトを使用してボタンを作成する](how-to-use-automatic-layout-to-create-a-button.md)
- [自動レイアウト用のグリッドを使用する](how-to-use-a-grid-for-automatic-layout.md)
