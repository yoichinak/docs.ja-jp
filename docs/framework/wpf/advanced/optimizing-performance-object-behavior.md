---
title: 'パフォーマンスの最適化 : オブジェクトの動作'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 67184db7fc1459e83ac7b1e6ff09ef56e43f0ca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187073"
---
# <a name="optimizing-performance-object-behavior"></a>パフォーマンスの最適化 : オブジェクトの動作
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトに固有の動作を理解することは、機能とパフォーマンスのバランスを見極めるうえで役に立ちます。  

<a name="Not_Removing_Event_Handlers"></a>
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>オブジェクトのイベント ハンドラーを削除しないとオブジェクトが維持される可能性がある  
 オブジェクトがそのイベントに渡すデリゲートは、事実上そのオブジェクトへの参照です。 このため、イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。 オブジェクトのイベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。 不要なオブジェクトが残っていると、アプリケーションのメモリ使用量が増加します。 これは、オブジェクトが論理ツリーやビジュアル ツリーのルートである場合には特に重要になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって導入される弱いイベント リスナー パターンは、ソースとリスナーのオブジェクト有効期間の関係の追跡が困難な場合に役に立ちます。 一部の既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントはこのパターンを使用します。 カスタム イベントを持つオブジェクトを実装する場合に、このパターンが役に立つこともあります。 詳細については、「[弱いイベント パターン](weak-event-patterns.md)」を参照してください。  
  
 CLR プロファイラーや作業セット ビューアーなど、特定のプロセスのメモリ使用量に関する情報を入手できるツールもいくつかあります。 CLR プロファイラーには、割り当てられた型のヒストグラム、割り当てグラフと呼び出しグラフ、さまざまなジェネレーションのガベージ コレクションとその結果のマネージド ヒープの状態を示す時系列、メソッドごとの割り当てとアセンブリの読み込みを示す呼び出しツリーなど、非常に便利な割り当てプロファイルのビューがいくつか含まれています。 詳しくは、「[パフォーマンス](https://docs.microsoft.com/previous-versions/aa497289(v=msdn.10))」をご覧ください。  
  
<a name="DPs_and_Objects"></a>
## <a name="dependency-properties-and-objects"></a>依存関係プロパティと依存関係オブジェクト  
 一般に、a<xref:System.Windows.DependencyObject>の依存関係プロパティへのアクセスは、CLR プロパティへのアクセスよりも遅くはありません。 プロパティ値を設定する場合のパフォーマンスのオーバーヘッドは少ないですが、値を取得する速度は、CLR プロパティから値を取得するのと同じくらい速いです。 この小さなパフォーマンス オーバーヘッドがある代わりに、依存関係プロパティでは、データ バインディング、アニメーション、継承、スタイル設定などの堅牢な機能がサポートされています。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty の最適化  
 アプリケーションで依存関係プロパティを定義するときには注意が必要です。 などの他<xref:System.Windows.DependencyProperty>のメタデータ オプションではなく、レンダー タイプのメタデータ オプション<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>にのみ影響する場合は、メタデータをオーバーライドしてそのようにマークする必要があります。 プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。  
  
 すべてのプロパティ変更が実際に測定、配置、描画に影響するわけではない場合は、測定、配置、描画の各パスを、プロパティ変更ハンドラーによって手動で無効にした方が効率的な場合もあります。 たとえば、設定した制限値より値が大きい場合にのみ背景を再描画する場合は、 設定した制限値を値が超えていた場合にのみプロパティ変更ハンドラーで描画を無効にします。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty を継承可能にするとパフォーマンスへの負荷が発生する  
 既定では、登録した依存関係プロパティは継承不可になります。 ただし、プロパティはどれでも明示的に継承可能にすることができます。 この機能は便利ですが、プロパティを継承可能にすると、プロパティの無効化の時間が増加して、パフォーマンスに影響します。  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler は慎重に使用する  
 呼び<xref:System.Windows.EventManager.RegisterClassHandler%2A>出しによってインスタンスの状態を保存できますが、すべてのインスタンスでハンドラが呼び出され、パフォーマンスの問題が発生する可能性があることに注意してください。 アプリケーションで<xref:System.Windows.EventManager.RegisterClassHandler%2A>インスタンスの状態を保存する必要がある場合にのみ使用します。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>DependencyProperty の既定値は登録時に設定する  
 既定値を必要<xref:System.Windows.DependencyProperty>とする を作成する場合は、 のメソッドにパラメーターとして渡される既定の<xref:System.Windows.DependencyProperty.Register%2A>メタデータを使用して値<xref:System.Windows.DependencyProperty>を設定します。 コンストラクターや要素の各インスタンスでプロパティ値を設定するのではなく、この方法を使用するようにしてください。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register を使用して PropertyMetadata の値を設定する  
 を作成する<xref:System.Windows.DependencyProperty>際に、<xref:System.Windows.PropertyMetadata><xref:System.Windows.DependencyProperty.Register%2A>または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドを使用して を設定するオプションがあります。 オブジェクトには静的コンストラクターを呼び出す<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>場合がありますが、これは最適なソリューションではなく、パフォーマンスに影響します。 最高のパフォーマンスを得るために<xref:System.Windows.PropertyMetadata>は、呼び<xref:System.Windows.DependencyProperty.Register%2A>出し中に を に設定します。  
  
<a name="Freezable_Objects"></a>
## <a name="freezable-objects"></a>Freezable オブジェクト  
 A<xref:System.Windows.Freezable>は、フリーズ解除とフリーズの 2 つの状態を持つ特殊なタイプのオブジェクトです。 可能な場合は常にオブジェクトを固定するようにすると、アプリケーションのパフォーマンスが向上し、作業セットを縮小できます。 詳細については、「[Freezable オブジェクトの概要](freezable-objects-overview.md)」を参照してください。  
  
 それぞれに<xref:System.Windows.Freezable>、<xref:System.Windows.Freezable.Changed>変更されるたびに発生するイベントがあります。 ただし、変更通知はアプリケーションのパフォーマンスに影響を与えます。  
  
 それぞれが<xref:System.Windows.Shapes.Rectangle>同じ<xref:System.Windows.Media.Brush>オブジェクトを使用する次の例を考えてみます。  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Media.SolidColorBrush>オブジェクトの<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを無効にするために、オブジェクトの<xref:System.Windows.Freezable.Changed>イベントのイベント ハンドラーを<xref:System.Windows.Shapes.Rectangle>提供します。 この場合、イベント<xref:System.Windows.Media.SolidColorBrush>を発生<xref:System.Windows.Freezable.Changed>させるたびに、コールバック関数を呼<xref:System.Windows.Shapes.Rectangle>び出す必要があります。 さらに、この時点でハンドラーを追加または削除すると、アプリケーションでリスト全体を検査しなければならなくなるため、パフォーマンスに大きく影響します。 アプリケーション シナリオで<xref:System.Windows.Media.SolidColorBrush>を変更しない場合は、イベント ハンドラを不必要に<xref:System.Windows.Freezable.Changed>保守するコストを支払います。  
  
 a<xref:System.Windows.Freezable>を凍結すると、変更通知の維持にリソースを費やす必要がなくなるため、パフォーマンスが向上します。 次の表は、プロパティ<xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Freezable.IsFrozen%2A>が に設定されている場合の単純な`true`サイズを示しています。 これは、10<xref:System.Windows.Shapes.Rectangle>個のオブジェクト<xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティに 1 つのブラシを適用することを前提としています。  
  
|**状態**|**サイズ**|  
|---------------|--------------|  
|冷凍<xref:System.Windows.Media.SolidColorBrush>|212 バイト|  
|非凍結<xref:System.Windows.Media.SolidColorBrush>|972 バイト|  
  
 この概念の例を次のコード サンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>固定されていない Freezable の Changed ハンドラーによってオブジェクトが維持される可能性がある  
 オブジェクトが<xref:System.Windows.Freezable>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントに渡すデリゲートは、実質的にそのオブジェクトへの参照です。 したがって、<xref:System.Windows.Freezable.Changed>イベント ハンドラーは、オブジェクトを予想よりも長く存続させることができます。 オブジェクトの<xref:System.Windows.Freezable><xref:System.Windows.Freezable.Changed>イベントをリッスンするために登録されているオブジェクトのクリーンアップを実行する場合、オブジェクトを解放する前にそのデリゲートを削除することが重要です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、イベントを<xref:System.Windows.Freezable.Changed>内部的にフックします。 たとえば、値として受け取る<xref:System.Windows.Freezable>すべての依存関係プロパティは、イベント<xref:System.Windows.Freezable.Changed>を自動的にリッスンします。 この<xref:System.Windows.Shapes.Shape.Fill%2A>概念を示す<xref:System.Windows.Media.Brush>プロパティは、 を使用します。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myBrush`の代入`myRectangle.Fill`で、<xref:System.Windows.Shapes.Rectangle>オブジェクトを指し示すデリゲートがオブジェクトの<xref:System.Windows.Media.SolidColorBrush><xref:System.Windows.Freezable.Changed>イベントに追加されます。 このため、次のコードを使用しても、`myRect` は実際にはガベージ コレクションの対象にはなりません。  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 この場合`myBrush`、まだ生き`myRectangle`続けており、<xref:System.Windows.Freezable.Changed>イベントを発生させるときにコールバックします。 new<xref:System.Windows.Shapes.Rectangle>の<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティ`myBrush`に割り当てると、単に別のイベント`myBrush`ハンドラが に追加されることに注意してください。  
  
 これらの種類のオブジェクトをクリーンアップする推奨される方法は、<xref:System.Windows.Media.Brush><xref:System.Windows.Shapes.Shape.Fill%2A>プロパティからを削除することです。 <xref:System.Windows.Freezable.Changed>  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>
## <a name="user-interface-virtualization"></a>ユーザー インターフェイスの仮想化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、データ バインド子<xref:System.Windows.Controls.StackPanel>コンテンツを自動的に 「仮想化」する要素のバリエーションも提供します。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、オブジェクトのサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel>( によって提供される<xref:System.Windows.Controls.VirtualizingPanel>機能を通じて ) は、<xref:System.Windows.Controls.ItemContainerGenerator>表示可能<xref:System.Windows.Controls.ItemsControl>な項目を<xref:System.Windows.Controls.ListBox>計算<xref:System.Windows.Controls.ListView>し、 ( または など ) から 、 を使用して、可視項目の要素のみを作成します。  
  
 パフォーマンスの最適化の一環として、これらの項目のビジュアル オブジェクトは、画面に表示される場合にのみ生成または維持されます。 既にコントロールの表示可能領域にないビジュアル オブジェクトは削除される可能性があります。 これをデータの仮想化と混同しないようにしてください。データの仮想化では、すべてのデータ オブジェクトがローカル コレクションに存在するのではなく、データ オブジェクトが必要に応じてストリームされます。  
  
 次の表は、 と に 5000<xref:System.Windows.Controls.TextBlock>個の<xref:System.Windows.Controls.StackPanel>要素を追加および<xref:System.Windows.Controls.VirtualizingStackPanel>レンダリングする経過時間を示しています。 このシナリオでは、測定は、パネル要素がテキスト文字列を表示する時間に<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A><xref:System.Windows.Controls.ItemsControl>オブジェクトのプロパティにテキスト文字列をアタッチする時間を表します。  
  
|**ホスト パネル**|**レンダリング時間 (ミリ秒)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [テキスト](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
