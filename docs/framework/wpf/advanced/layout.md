---
title: レイアウト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: eb254503f5ce2240a03179da693c66f7ada876be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918300"
---
# <a name="layout"></a>レイアウト
このトピックでは、Windows Presentation Foundation (WPF) レイアウトシステムについて説明します。 WPF でユーザーインターフェイスを作成するには、レイアウトの計算がどのように行われるかを理解することが不可欠です。  
  
 このトピックは、次のセクションで構成されています。  
  
- [要素の境界ボックス](#LayoutSystem_BoundingBox)  
  
- [レイアウト システム](#LayoutSystem_Overview)  
  
- [子の測定と配置](#LayoutSystem_Measure_Arrange)  
  
- [パネル要素とカスタム レイアウトの動作](#LayoutSystem_PanelsCustom)  
  
- [レイアウトのパフォーマンスの考慮事項](#LayoutSystem_Performance)  
  
- [サブピクセル レンダリングとレイアウトの丸め処理](#LayoutSystem_LayoutRounding)  
  
- [次の内容](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>要素の境界ボックス  
 WPF でのレイアウトについて考えるときは、すべての要素を囲む境界ボックスについて理解しておくことが重要です。 レイアウト<xref:System.Windows.FrameworkElement>システムによって使用される各は、レイアウトにスロット分割される四角形と考えることができます。 クラス<xref:System.Windows.Controls.Primitives.LayoutInformation>は、要素のレイアウト割り当て (スロット) の境界を返します。 四角形のサイズは、使用可能な画面領域、制約のサイズ、レイアウト固有のプロパティ (余白や埋め込みなど)、および親<xref:System.Windows.Controls.Panel>要素の個々の動作を計算することによって決定されます。 レイアウトシステムは、このデータを処理することで、特定<xref:System.Windows.Controls.Panel>ののすべての子の位置を計算できます。 の<xref:System.Windows.Controls.Border>ように、親要素で定義されているサイズ設定特性は、その子に影響を与えることに注意してください。  
  
 次の図は、シンプルなレイアウトを示しています。  
  
 ![一般的なグリッドを示すスクリーンショット。境界ボックスは重ねて表示されません。](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 このレイアウトは、次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して実現できます。  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 1つ<xref:System.Windows.Controls.TextBlock>の要素が<xref:System.Windows.Controls.Grid>内でホストされます。 テキストは最初の列の左上隅にのみ表示<xref:System.Windows.Controls.TextBlock>されますが、の割り当て済み領域は実際には非常に大きくなります。 任意<xref:System.Windows.FrameworkElement>のの境界ボックスは、 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>メソッドを使用して取得できます。 <xref:System.Windows.Controls.TextBlock>要素の境界ボックスを次の図に示します。  
  
 ![TextBlock 境界ボックスが表示されていることを示すスクリーンショット。](./media/layout/visible-textblock-bounding-box.png)  
  
 黄色の四角形で示されているように、 <xref:System.Windows.Controls.TextBlock>要素に割り当てられた領域は、実際には表示されるよりもはるかに大きくなります。 追加の要素がに<xref:System.Windows.Controls.Grid>追加されると、追加される要素の型とサイズに応じて、この割り当てが縮小または拡張される可能性があります。  
  
 の<xref:System.Windows.Controls.TextBlock>レイアウトスロットは、 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>メソッドを使用し<xref:System.Windows.Shapes.Path>てに変換されます。 この方法は、要素の境界ボックスの表示に役立ちます。  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>レイアウト システム  
 簡単に言うと、レイアウトは、要素のサイズ測定、配置、および描画を繰り返す再帰的なシステムです。 具体的には、レイアウトは、要素の<xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A>コレクションのメンバーを測定および整列するプロセスについて説明します。 レイアウトは集中的なプロセスです。 コレクションが<xref:System.Windows.Controls.Panel.Children%2A>大きいほど、作成する必要がある計算の数が多くなります。 また、コレクションを所有する<xref:System.Windows.Controls.Panel>要素によって定義されたレイアウトの動作に基づいて、複雑さを導入することもできます。 など、比較的<xref:System.Windows.Controls.Panel>単純<xref:System.Windows.Controls.Canvas>なでは、より複雑<xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid>なパフォーマンスを大幅に向上させることができます。  
  
 子<xref:System.Windows.UIElement>がその位置を変更するたびに、レイアウトシステムによって新しいパスがトリガーされる可能性があります。 したがって、不要な呼び出しはアプリケーション パフォーマンスの低下につながる可能性があるため、レイアウト システムを呼び出す可能性があるイベントを理解することが重要です。 以下に、レイアウト システムが呼び出されたときに発生するプロセスについて説明します。  
  
1. 子<xref:System.Windows.UIElement>は、最初にコアプロパティを測定して、レイアウトプロセスを開始します。  
  
2. <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement> 、など、で定義されたサイズ変更プロパティが評価されます。<xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Margin%2A>  
  
3. <xref:System.Windows.Controls.Panel><xref:System.Windows.Controls.Dock>方向やスタック<xref:System.Windows.Controls.StackPanel.Orientation%2A>など、固有のロジックが適用されます。  
  
4. すべての子が測定された後にコンテンツが配置されます。  
  
5. <xref:System.Windows.Controls.Panel.Children%2A>コレクションが画面に描画されます。  
  
6. 追加<xref:System.Windows.Controls.Panel.Children%2A>がコレクションに追加された場合<xref:System.Windows.FrameworkElement.LayoutTransform%2A> 、 <xref:System.Windows.UIElement.UpdateLayout%2A>が適用された場合、またはメソッドが呼び出された場合は、プロセスが再度呼び出されます。  
  
 このプロセスとその呼び出し方法は、次のセクションで詳細に定義します。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>子の測定と配置  
 レイアウトシステムは、 <xref:System.Windows.Controls.Panel.Children%2A>コレクションのメンバーごとに、測定パスと配置パスの2つのパスを完了します。 各子<xref:System.Windows.Controls.Panel>には<xref:System.Windows.FrameworkElement.MeasureOverride%2A> 、独自<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>の特定のレイアウト動作を実現するためのメソッドとメソッドが用意されています。  
  
 メジャーパスの実行中に、 <xref:System.Windows.Controls.Panel.Children%2A>コレクションの各メンバーが評価されます。 プロセスは、メソッドの<xref:System.Windows.UIElement.Measure%2A>呼び出しで開始されます。 このメソッドは、親<xref:System.Windows.Controls.Panel>要素の実装内で呼び出されます。レイアウトを行うには、明示的に呼び出す必要はありません。  
  
 最初に、の<xref:System.Windows.UIElement>ネイティブサイズプロパティが評価されます ( <xref:System.Windows.UIElement.Visibility%2A> <xref:System.Windows.UIElement.Clip%2A>やなど)。 これにより、に`constraintSize` <xref:System.Windows.FrameworkElement.MeasureCore%2A>渡されるという名前の値が生成されます。  
  
 2番目の方法と<xref:System.Windows.FrameworkElement>して、に定義されて`constraintSize`いるフレームワークプロパティが処理され、の値に影響します。 これらの<xref:System.Windows.UIElement>プロパティは<xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>通常、<xref:System.Windows.FrameworkElement.Style%2A>、、 、など、基になるのサイズ設定特性を記述します。<xref:System.Windows.FrameworkElement.Margin%2A> これらの各プロパティは、要素を表示するために必要な領域を変更できます。 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>は、パラメーターと`constraintSize`してで呼び出されます。  
  
> [!NOTE]
> と<xref:System.Windows.FrameworkElement.Height%2A>のプロパティとの<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>間には違いがあります。<xref:System.Windows.FrameworkElement.ActualWidth%2A> たとえば<xref:System.Windows.FrameworkElement.ActualHeight%2A> 、プロパティは、他の高さ入力およびレイアウトシステムに基づく計算値です。 値は、実際のレンダリングパスに基づいてレイアウトシステム自体によって設定されます。したがって、入力の変更の基礎となる<xref:System.Windows.FrameworkElement.Height%2A>、などのプロパティの設定値よりも少し遅れが生じることがあります。  
>   
>  は<xref:System.Windows.FrameworkElement.ActualHeight%2A>計算値であるため、レイアウトシステムによるさまざまな操作の結果として、複数のまたは増分の報告される変更がある可能性があることに注意してください。 レイアウト システムが、子要素に必要な測定スペース、親要素による制約などを計算している場合があります。  
  
 メジャーパスの最終的な目標は、子が<xref:System.Windows.UIElement.DesiredSize%2A> <xref:System.Windows.FrameworkElement.MeasureCore%2A>呼び出し中に発生するを決定することです。 値は、コンテンツの<xref:System.Windows.UIElement.Measure%2A>配置パス中に使用するためにによって格納されます。 <xref:System.Windows.UIElement.DesiredSize%2A>  
  
 配置パスは、メソッドの<xref:System.Windows.UIElement.Arrange%2A>呼び出しで始まります。 配置パス中に、親<xref:System.Windows.Controls.Panel>要素は、子の境界を表す四角形を生成します。 この値は、 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>処理のためにメソッドに渡されます。  
  
 メソッド<xref:System.Windows.FrameworkElement.ArrangeCore%2A>は、子<xref:System.Windows.UIElement.DesiredSize%2A>のを評価し、表示される要素のサイズに影響する可能性のある追加の余白を評価します。 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>を生成します。これは、 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.Controls.Panel>パラメーターとしてのメソッドに渡されます。 `arrangeSize` <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>`finalSize`子のを生成します。 最後に、 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>メソッドは、余白や配置などのオフセットプロパティの最終的な評価を行い、子をレイアウトスロット内に配置します。 子は割り当てられた領域全体を埋める必要はありません (そうしない場合もよくあります)。 次に、コントロールが親<xref:System.Windows.Controls.Panel>に返され、レイアウトプロセスが完了します。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>パネル要素とカスタム レイアウトの動作  
WPF には、から<xref:System.Windows.Controls.Panel>派生する要素のグループが含まれています。 これら<xref:System.Windows.Controls.Panel>の要素により、多数の複雑なレイアウトが可能になります。 たとえば、 <xref:System.Windows.Controls.StackPanel>要素を使用すると、積み重ねる要素を簡単に実現できます。一方、を<xref:System.Windows.Controls.Canvas>使用すると、より複雑でフリーのフローレイアウトが可能になります。  
  
 次の表は、使用可能<xref:System.Windows.Controls.Panel>なレイアウト要素をまとめたものです。  
  
|パネル名|説明|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|<xref:System.Windows.Controls.Canvas>領域を基準に相対的に子要素を相対的に配置できる領域を定義します。|  
|<xref:System.Windows.Controls.DockPanel>|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|行と列で構成される柔軟性のあるグリッド領域を定義します。|  
|<xref:System.Windows.Controls.StackPanel>|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|子データコレクションを<xref:System.Windows.Controls.Panel>仮想化する要素のフレームワークを提供します。 これは抽象クラスです。|  
|<xref:System.Windows.Controls.WrapPanel>|左から右へ順に子要素を配置し、ボックスの端で改行してコンテンツを次の行へ送ります。 後続の順序は、 <xref:System.Windows.Controls.WrapPanel.Orientation%2A>プロパティの値に応じて、上から下または右から左に順番に行われます。|  
  
 定義済み<xref:System.Windows.Controls.Panel>の要素のいずれかを使用しても不可能なレイアウトを必要とするアプリケーションでは、を<xref:System.Windows.Controls.Panel>継承し、メソッド<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドをオーバーライドすることにより、カスタムレイアウト動作を実現できます。  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>レイアウトのパフォーマンスの考慮事項  
 レイアウトは再帰的なプロセスです。 <xref:System.Windows.Controls.Panel.Children%2A>コレクション内の各子要素は、レイアウトシステムの呼び出し中に処理されます。 そのため、必要ない場合はレイアウト システムをトリガーしないようにしてください。 次の考慮事項は、パフォーマンスを向上させるのに役立ちます。  
  
- どのプロパティ値の変更がレイアウト システムによる再帰的な更新を強制するかに注意してください。  
  
     レイアウト システムを初期化できる値が設定されている依存関係プロパティは、パブリック フラグでマークされます。 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>と<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>は、レイアウトシステムによって強制的に再帰的に更新されるプロパティ値の変更に役立つ手掛かりを提供します。 一般に、要素の境界ボックスのサイズに影響を与える可能性のあるプロパティでは<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 、フラグが true に設定されている必要があります。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
- 可能であれば、 <xref:System.Windows.UIElement.RenderTransform%2A> <xref:System.Windows.FrameworkElement.LayoutTransform%2A>の代わりにを使用します。  
  
     は、のコンテンツに影響を与える非常に便利な方法になります。[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.FrameworkElement.LayoutTransform%2A> ただし、変換の効果が他の要素の位置に影響を与えない場合は、を<xref:System.Windows.UIElement.RenderTransform%2A>使用することをお勧めします。これは、がレイアウトシステムを呼び出さないため<xref:System.Windows.UIElement.RenderTransform%2A>です。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>変換を適用し、影響を受ける要素の新しい位置を考慮して、再帰的なレイアウトの更新を強制的に実行します。  
  
- の不要な呼び出し<xref:System.Windows.UIElement.UpdateLayout%2A>を回避します。  
  
     メソッド<xref:System.Windows.UIElement.UpdateLayout%2A>は、レイアウトの再帰的な更新を強制的に実行するため、頻繁には必要ありません。 完全な更新が必要であると確信できる場合を除き、このメソッドの呼び出しはレイアウト システムに任せます。  
  
- 大きな<xref:System.Windows.Controls.Panel.Children%2A>コレクションを使用する場合は、通常<xref:System.Windows.Controls.StackPanel>の<xref:System.Windows.Controls.VirtualizingStackPanel>ではなくを使用することを検討してください。  
  
     子コレクションを仮想化すること<xref:System.Windows.Controls.VirtualizingStackPanel>により、は、現在親のビューポート内にあるメモリ内のオブジェクトのみを保持します。 その結果、ほとんどのシナリオでパフォーマンスが大幅に向上します。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>サブピクセル レンダリングとレイアウトの丸め処理  
 WPF グラフィックスシステムでは、デバイスに依存しない単位を使用して、解像度とデバイスに依存しないようにします。 デバイスに依存しない各ピクセルは、システムのドット/インチ (dpi) 設定に応じて自動的にスケーリングされます。 これにより、さまざまな dpi 設定に対して WPF アプリケーションの適切なスケーリングが提供され、アプリケーションが自動的に dpi に対応するようになります。  
  
 ただし、この dpi に依存しない場合は、アンチエイリアシングのために不規則なエッジレンダリングが作成できます。 これらの成果物 (通常はぼやけたエッジや半透明のエッジが見られます) は、エッジの場所がデバイス ピクセルの間ではなく、デバイス ピクセルの中間にある場合に発生します。 レイアウト システムは、レイアウトの丸め処理でこれを調整する方法を提供します。 レイアウトの丸め処理では、レイアウト システムがレイアウト パスの実行中に任意の整数以外のピクセル値を丸めます。  
  
 レイアウトの丸め処理は既定で無効になっています。 レイアウトの丸め処理を有効に<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>するに`true`は、 <xref:System.Windows.FrameworkElement>任意のでプロパティをに設定します。 これは依存関係プロパティであるため、値はビジュアル ツリー内のすべての子に反映されます。 UI 全体のレイアウトの丸め処理を有効に<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>する`true`には、ルートコンテナーのをに設定します。 例については、「<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>」を参照してください。  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>次の内容  
 要素の測定方法と配置方法を理解することが、レイアウトを理解する最初のステップです。 使用可能な<xref:System.Windows.Controls.Panel>要素の詳細については、「[パネルの概要](../controls/panels-overview.md)」を参照してください。 レイアウトに影響を与えるさまざまな配置プロパティをより理解するには、「[配置、余白、パディングの概要](alignment-margins-and-padding-overview.md)」を参照してください。 軽量のアプリケーションにまとめて配置する準備ができたら、「 [チュートリアル:初めての WPF デスクトップ](../getting-started/walkthrough-my-first-wpf-desktop-application.md)アプリケーション。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [パネルの概要](../controls/panels-overview.md)
- [配置、余白、パディングの概要](alignment-margins-and-padding-overview.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
