---
title: パフォーマンスの最適化:オブジェクトの動作
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
ms.openlocfilehash: 025c8691eb1aaf9483a222530a5590670ede486b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400466"
---
# <a name="optimizing-performance-object-behavior"></a>パフォーマンスの最適化:オブジェクトの動作
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトに固有の動作を理解することは、機能とパフォーマンスのバランスを見極めるうえで役に立ちます。  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>オブジェクトのイベント ハンドラーを削除しないとオブジェクトが維持される可能性がある  
 オブジェクトがそのイベントに渡すデリゲートは、事実上そのオブジェクトへの参照です。 このため、イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。 オブジェクトのイベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。 不要なオブジェクトが残っていると、アプリケーションのメモリ使用量が増加します。 これは、オブジェクトが論理ツリーやビジュアル ツリーのルートである場合には特に重要になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって導入される弱いイベント リスナー パターンは、ソースとリスナーのオブジェクト有効期間の関係の追跡が困難な場合に役に立ちます。 一部の既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントはこのパターンを使用します。 カスタム イベントを持つオブジェクトを実装する場合に、このパターンが役に立つこともあります。 詳細については、「[弱いイベント パターン](weak-event-patterns.md)」を参照してください。  
  
 CLR プロファイラーや作業セット ビューアーなど、特定のプロセスのメモリ使用量に関する情報を入手できるツールもいくつかあります。 CLR プロファイラーには、割り当てられた型のヒストグラム、割り当てグラフと呼び出しグラフ、さまざまなジェネレーションのガベージ コレクションとその結果のマネージド ヒープの状態を示す時系列、メソッドごとの割り当てとアセンブリの読み込みを示す呼び出しツリーなど、非常に便利な割り当てプロファイルのビューがいくつか含まれています。 詳細については、「[.NET Framework デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=117435)」を参照してください。  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>依存関係プロパティと依存関係オブジェクト  
 一般に、の依存関係プロパティへの<xref:System.Windows.DependencyObject>アクセスは、CLR プロパティにアクセスする場合よりも遅くなりません。 プロパティ値を設定する場合、パフォーマンスのオーバーヘッドはわずかですが、値を取得することは、CLR プロパティから値を取得するのと同じくらい高速です。 この小さなパフォーマンス オーバーヘッドがある代わりに、依存関係プロパティでは、データ バインディング、アニメーション、継承、スタイル設定などの堅牢な機能がサポートされています。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty の最適化  
 アプリケーションで依存関係プロパティを定義するときには注意が必要です。 が、などの他のメタデータオプション<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>ではなく、render 型のメタデータオプションにのみ影響を与える場合は、そのメタデータをオーバーライドすることによって、それをマークする必要があります。<xref:System.Windows.DependencyProperty> プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。  
  
 すべてのプロパティ変更が実際に測定、配置、描画に影響するわけではない場合は、測定、配置、描画の各パスを、プロパティ変更ハンドラーによって手動で無効にした方が効率的な場合もあります。 たとえば、設定した制限値より値が大きい場合にのみ背景を再描画する場合は、 設定した制限値を値が超えていた場合にのみプロパティ変更ハンドラーで描画を無効にします。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty を継承可能にするとパフォーマンスへの負荷が発生する  
 既定では、登録した依存関係プロパティは継承不可になります。 ただし、プロパティはどれでも明示的に継承可能にすることができます。 この機能は便利ですが、プロパティを継承可能にすると、プロパティの無効化の時間が増加して、パフォーマンスに影響します。  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler は慎重に使用する  
 を呼び<xref:System.Windows.EventManager.RegisterClassHandler%2A>出すと、インスタンスの状態を保存できますが、すべてのインスタンスでハンドラーが呼び出されることに注意してください。これにより、パフォーマンスの問題が発生する可能性があります。 アプリケーションで<xref:System.Windows.EventManager.RegisterClassHandler%2A>インスタンスの状態を保存する必要がある場合にのみ使用してください。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>DependencyProperty の既定値は登録時に設定する  
 既定値を<xref:System.Windows.DependencyProperty>必要とするを作成する場合は、の<xref:System.Windows.DependencyProperty.Register%2A> <xref:System.Windows.DependencyProperty>メソッドにパラメーターとして渡される既定のメタデータを使用して、値を設定します。 コンストラクターや要素の各インスタンスでプロパティ値を設定するのではなく、この方法を使用するようにしてください。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register を使用して PropertyMetadata の値を設定する  
 を作成<xref:System.Windows.DependencyProperty>するときに、メソッド<xref:System.Windows.DependencyProperty.Register%2A>または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドの<xref:System.Windows.PropertyMetadata>いずれかを使用してを設定するオプションがあります。 オブジェクトはを呼び出す<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>ための静的コンストラクターを持つことができますが、これは最適なソリューションではなく、パフォーマンスに影響します。 最適なパフォーマンスを得るに<xref:System.Windows.PropertyMetadata>は、の<xref:System.Windows.DependencyProperty.Register%2A>呼び出し中にを設定します。  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable オブジェクト  
 <xref:System.Windows.Freezable> オブジェクトは、非フリーズとフリーズの 2 つの状態を持つ特殊な型です。 可能な場合は常にオブジェクトを固定するようにすると、アプリケーションのパフォーマンスが向上し、作業セットを縮小できます。 詳細については、「[Freezable オブジェクトの概要](freezable-objects-overview.md)」を参照してください。  
  
 各<xref:System.Windows.Freezable>には<xref:System.Windows.Freezable.Changed> 、変更されるたびに発生するイベントがあります。 ただし、変更通知はアプリケーションのパフォーマンスに影響を与えます。  
  
 それぞれ<xref:System.Windows.Shapes.Rectangle>が同じ<xref:System.Windows.Media.Brush>オブジェクトを使用する次の例を考えてみます。  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 既定では[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、は、オブジェクトの<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティ<xref:System.Windows.Media.SolidColorBrush>を無効<xref:System.Windows.Freezable.Changed> <xref:System.Windows.Shapes.Rectangle>にするために、オブジェクトのイベントのイベントハンドラーを提供します。 この場合、が<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.Changed>イベントを起動するたびに、それぞれ<xref:System.Windows.Shapes.Rectangle>のコールバック関数を呼び出す必要があります。これらのコールバック関数呼び出しを蓄積すると、パフォーマンスが大幅に低下します。 さらに、この時点でハンドラーを追加または削除すると、アプリケーションでリスト全体を検査しなければならなくなるため、パフォーマンスに大きく影響します。 アプリケーションのシナリオによってが<xref:System.Windows.Media.SolidColorBrush>変更されない場合は、イベントハンドラー <xref:System.Windows.Freezable.Changed>を不必要に維持するコストを支払う必要があります。  
  
 を固定<xref:System.Windows.Freezable>すると、変更通知の保持にリソースを費やす必要がなくなるため、パフォーマンスが向上します。 次の表は、 <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Freezable.IsFrozen%2A>プロパティがに`true`設定されている場合の単純なのサイズを示していますが、それ以外の場合はと比較しています。 これは、10個<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>のオブジェクトのプロパティに1つのブラシを適用することを前提としています。  
  
|**状態**|**Size**|  
|---------------|--------------|  
|れ<xref:System.Windows.Media.SolidColorBrush>|212 バイト|  
|凍結されていない<xref:System.Windows.Media.SolidColorBrush>|972 バイト|  
  
 この概念の例を次のコード サンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>固定されていない Freezable の Changed ハンドラーによってオブジェクトが維持される可能性がある  
 オブジェクトがオブジェクトの<xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed>イベントに渡すデリゲートは、事実上、そのオブジェクトへの参照です。 そのため<xref:System.Windows.Freezable.Changed> 、イベントハンドラーはオブジェクトを予想よりも長く保持できます。 オブジェクトの<xref:System.Windows.Freezable> <xref:System.Windows.Freezable.Changed>イベントをリッスンするように登録されているオブジェクトのクリーンアップを実行する場合は、オブジェクトを解放する前にそのデリゲートを削除することが不可欠です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、イベント<xref:System.Windows.Freezable.Changed>を内部でフックします。 たとえば、値<xref:System.Windows.Freezable>として使用されるすべての依存関係プロパティ<xref:System.Windows.Freezable.Changed>は、イベントを自動的にリッスンします。 <xref:System.Windows.Shapes.Shape.Fill%2A> を<xref:System.Windows.Media.Brush>受け取るプロパティは、この概念を示しています。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 へ`myBrush` <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.SolidColorBrush>の割り当てでは、オブジェクトを指すデリゲートがオブジェクトの<xref:System.Windows.Freezable.Changed>イベントに追加されます。 `myRectangle.Fill` このため、次のコードを使用しても、`myRect` は実際にはガベージ コレクションの対象にはなりません。  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 この場合`myBrush` 、は引き続き alive `myRectangle`を維持し、 <xref:System.Windows.Freezable.Changed>イベントが発生したときにコールバックします。 新しい`myBrush` <xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティにを割り当てると、単に別のイベントハンドラーがに`myBrush`追加されることに注意してください。 <xref:System.Windows.Shapes.Rectangle>  
  
 これらの種類のオブジェクトをクリーンアップするには、 <xref:System.Windows.Media.Brush> <xref:System.Windows.Shapes.Shape.Fill%2A>プロパティからを削除することをお勧めします。これ<xref:System.Windows.Freezable.Changed>により、イベントハンドラーが削除されます。  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>ユーザー インターフェイスの仮想化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]また、は、 <xref:System.Windows.Controls.StackPanel>データバインドされた子コンテンツを自動的に "仮想化する" 要素のバリエーションも提供します。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、オブジェクトのサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel><xref:System.Windows.Controls.VirtualizingPanel>(によって提供される機能を使用) によって、 <xref:System.Windows.Controls.ItemsControl>表示可能な項目が計算され、 <xref:System.Windows.Controls.ListBox>から (または<xref:System.Windows.Controls.ListView>など) のを使用して、 <xref:System.Windows.Controls.ItemContainerGenerator>表示される項目の要素のみが作成されます。  
  
 パフォーマンスの最適化の一環として、これらの項目のビジュアル オブジェクトは、画面に表示される場合にのみ生成または維持されます。 既にコントロールの表示可能領域にないビジュアル オブジェクトは削除される可能性があります。 これをデータの仮想化と混同しないようにしてください。データの仮想化では、すべてのデータ オブジェクトがローカル コレクションに存在するのではなく、データ オブジェクトが必要に応じてストリームされます。  
  
 次の表は、5000 <xref:System.Windows.Controls.TextBlock>要素を<xref:System.Windows.Controls.StackPanel>と<xref:System.Windows.Controls.VirtualizingStackPanel>に追加して表示する経過時間を示しています。 このシナリオでは、測定値は、テキスト文字列を<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl>オブジェクトのプロパティにアタッチしてから、パネル要素にテキスト文字列が表示されるまでの時間を表します。  
  
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
- [Text](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
