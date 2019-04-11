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
ms.openlocfilehash: 49318059435c5f5669510f7cf3fb7c93a4bc05e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137437"
---
# <a name="optimizing-performance-object-behavior"></a>パフォーマンスの最適化:オブジェクトの動作
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトに固有の動作を理解することは、機能とパフォーマンスのバランスを見極めるうえで役に立ちます。  

<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>オブジェクトのイベント ハンドラーを削除しないとオブジェクトが維持される可能性がある  
 オブジェクトがそのイベントに渡すデリゲートは、事実上そのオブジェクトへの参照です。 このため、イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。 オブジェクトのイベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。 不要なオブジェクトが残っていると、アプリケーションのメモリ使用量が増加します。 これは、オブジェクトが論理ツリーやビジュアル ツリーのルートである場合には特に重要になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ソースとリスナー間でオブジェクトの有効期間の関係が追跡する困難な状況で役に立ちますイベントの弱いイベント リスナー パターンについて説明します。 一部の既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントはこのパターンを使用します。 カスタム イベントを持つオブジェクトを実装する場合に、このパターンが役に立つこともあります。 詳細については、「[弱いイベント パターン](weak-event-patterns.md)」を参照してください。  
  
 CLR プロファイラーや作業セット ビューアーなど、特定のプロセスのメモリ使用量に関する情報を入手できるツールもいくつかあります。 CLR プロファイラーには、割り当てられた型のヒストグラム、割り当てグラフと呼び出しグラフ、さまざまなジェネレーションのガベージ コレクションとその結果のマネージド ヒープの状態を示す時系列、メソッドごとの割り当てとアセンブリの読み込みを示す呼び出しツリーなど、非常に便利な割り当てプロファイルのビューがいくつか含まれています。 詳細については、「[.NET Framework デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=117435)」を参照してください。  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>依存関係プロパティと依存関係オブジェクト  
 一般の依存関係プロパティへのアクセス、<xref:System.Windows.DependencyObject>にアクセスするよりも低速でない、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティ。 プロパティ値の設定には多少のパフォーマンス オーバーヘッドがありますが、値の取得は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティから取得する場合と同じくらい高速です。 この小さなパフォーマンス オーバーヘッドがある代わりに、依存関係プロパティでは、データ バインディング、アニメーション、継承、スタイル設定などの堅牢な機能がサポートされています。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty の最適化  
 アプリケーションで依存関係プロパティを定義するときには注意が必要です。 場合、<xref:System.Windows.DependencyProperty>に影響しか表示されないその他のメタデータ オプションではなく型のメタデータ オプションなど<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、そのメタデータをオーバーライドすることでようマークする必要があります。 プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。  
  
 すべてのプロパティ変更が実際に測定、配置、描画に影響するわけではない場合は、測定、配置、描画の各パスを、プロパティ変更ハンドラーによって手動で無効にした方が効率的な場合もあります。 たとえば、設定した制限値より値が大きい場合にのみ背景を再描画する場合は、 設定した制限値を値が超えていた場合にのみプロパティ変更ハンドラーで描画を無効にします。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty を継承可能にするとパフォーマンスへの負荷が発生する  
 既定では、登録した依存関係プロパティは継承不可になります。 ただし、プロパティはどれでも明示的に継承可能にすることができます。 この機能は便利ですが、プロパティを継承可能にすると、プロパティの無効化の時間が増加して、パフォーマンスに影響します。  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler は慎重に使用する  
 呼び出し中に<xref:System.Windows.EventManager.RegisterClassHandler%2A>のインスタンス状態を保存することがでくことが重要では、すべてのインスタンスでは、パフォーマンスの問題が発生することができます、ハンドラーが呼び出されることに注意してください。 のみを使用して、<xref:System.Windows.EventManager.RegisterClassHandler%2A>アプリケーションに必要なインスタンスの状態を保存することです。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>DependencyProperty の既定値は登録時に設定する  
 作成するときに、<xref:System.Windows.DependencyProperty>へのパラメーターとして渡される既定のメタデータを使用して設定すると、既定値が必要な<xref:System.Windows.DependencyProperty.Register%2A>のメソッド、 <xref:System.Windows.DependencyProperty>。 コンストラクターや要素の各インスタンスでプロパティ値を設定するのではなく、この方法を使用するようにしてください。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register を使用して PropertyMetadata の値を設定する  
 作成するときに、 <xref:System.Windows.DependencyProperty>、設定のオプションがある、<xref:System.Windows.PropertyMetadata>いずれかを使用して、<xref:System.Windows.DependencyProperty.Register%2A>または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッド。 オブジェクトを呼び出す静的コンス トラクターを持つでした<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>、この最適なソリューションではないと、パフォーマンスに影響します。 最適なパフォーマンスを設定、<xref:System.Windows.PropertyMetadata>呼び出し中に<xref:System.Windows.DependencyProperty.Register%2A>します。  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable オブジェクト  
 A<xref:System.Windows.Freezable>は 2 つの状態を持つオブジェクトの特殊な型です: 非フリーズし、フリーズします。 可能な場合は常にオブジェクトを固定するようにすると、アプリケーションのパフォーマンスが向上し、作業セットを縮小できます。 詳細については、「[Freezable オブジェクトの概要](freezable-objects-overview.md)」を参照してください。  
  
 各<xref:System.Windows.Freezable>が、<xref:System.Windows.Freezable.Changed>が変更されるたびに発生するイベントです。 ただし、変更通知はアプリケーションのパフォーマンスに影響を与えます。  
  
 各例を次に示します<xref:System.Windows.Shapes.Rectangle>切り替わり<xref:System.Windows.Media.Brush>オブジェクト。  
  
 [!code-csharp[Performance#PerformanceSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のイベント ハンドラーを提供、<xref:System.Windows.Media.SolidColorBrush>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントが無効にするには、<xref:System.Windows.Shapes.Rectangle>オブジェクトの<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティ。 ここでは、毎回、<xref:System.Windows.Media.SolidColorBrush>起動する必要がありますその<xref:System.Windows.Freezable.Changed>イベントごとにコールバック関数を呼び出す必要があります<xref:System.Windows.Shapes.Rectangle>-大幅なパフォーマンス ペナルティを適用するこれらのコールバック関数の呼び出しが蓄積されます。 さらに、この時点でハンドラーを追加または削除すると、アプリケーションでリスト全体を検査しなければならなくなるため、パフォーマンスに大きく影響します。 アプリケーションのシナリオが変化しない場合、 <xref:System.Windows.Media.SolidColorBrush>、維持するためのコストを支払うこと<xref:System.Windows.Freezable.Changed>イベント ハンドラーが不必要にします。  
  
 固定、<xref:System.Windows.Freezable>変更通知の維持にリソースを費やす必要がなくなったために、パフォーマンスが向上することができます。 次の表は、簡単なサイズ<xref:System.Windows.Media.SolidColorBrush>ときにその<xref:System.Windows.Freezable.IsFrozen%2A>プロパティに設定されて`true`ではない場合に比べて、します。 これは 1 つのブラシを適用することを前提としています、 <xref:System.Windows.Shapes.Shape.Fill%2A> 10 プロパティ<xref:System.Windows.Shapes.Rectangle>オブジェクト。  
  
|**状態**|**サイズ**|  
|---------------|--------------|  
|固定されています。 <xref:System.Windows.Media.SolidColorBrush>|212 バイト|  
|固定されていません。 <xref:System.Windows.Media.SolidColorBrush>|972 バイト|  
  
 この概念の例を次のコード サンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>固定されていない Freezable の Changed ハンドラーによってオブジェクトが維持される可能性がある  
 オブジェクトが渡されるデリゲートを<xref:System.Windows.Freezable>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントは、事実上そのオブジェクトへの参照。 そのため、<xref:System.Windows.Freezable.Changed>イベント ハンドラーは維持オブジェクト予想よりも長い期間。 リッスンするように登録されているオブジェクトのクリーンアップを実行するときに、<xref:System.Windows.Freezable>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントでは、オブジェクトを解放する前にそのデリゲートを削除するために不可欠です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フック<xref:System.Windows.Freezable.Changed>イベント内部的にします。 なるすべての依存関係プロパティなど、<xref:System.Windows.Freezable>値がリッスンするよう<xref:System.Windows.Freezable.Changed>イベントに自動的にします。 <xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを<xref:System.Windows.Media.Brush>、この概念を示します。  
  
 [!code-csharp[Performance#PerformanceSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 割り当てると、`myBrush`に`myRectangle.Fill`、指すデリゲート、<xref:System.Windows.Shapes.Rectangle>オブジェクトに追加されます、<xref:System.Windows.Media.SolidColorBrush>オブジェクトの<xref:System.Windows.Freezable.Changed>イベント。 このため、次のコードを使用しても、`myRect` は実際にはガベージ コレクションの対象にはなりません。  
  
 [!code-csharp[Performance#PerformanceSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 ここで`myBrush`保持しながら`myRectangle`アライブにコールバックが発生したときに、その<xref:System.Windows.Freezable.Changed>イベント。 割り当てて`myBrush`を<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティの新しい<xref:System.Windows.Shapes.Rectangle>を別のイベント ハンドラーが追加されるだけです`myBrush`します。  
  
 この種のオブジェクトをクリーンアップする推奨される方法は、削除する、<xref:System.Windows.Media.Brush>から、<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティで、削除はさらに、<xref:System.Windows.Freezable.Changed>イベント ハンドラー。  
  
 [!code-csharp[Performance#PerformanceSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>ユーザー インターフェイスの仮想化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] バリエーションも提供します、<xref:System.Windows.Controls.StackPanel>自動的に「仮想化する」データ バインド子コンテンツ要素。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、オブジェクトのサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel> (によって提供される機能を使用して<xref:System.Windows.Controls.VirtualizingPanel>) 表示されている項目を計算し、連携、<xref:System.Windows.Controls.ItemContainerGenerator>から、 <xref:System.Windows.Controls.ItemsControl> (など<xref:System.Windows.Controls.ListBox>または<xref:System.Windows.Controls.ListView>) だけ表示される項目の要素を作成します。  
  
 パフォーマンスの最適化の一環として、これらの項目のビジュアル オブジェクトは、画面に表示される場合にのみ生成または維持されます。 既にコントロールの表示可能領域にないビジュアル オブジェクトは削除される可能性があります。 これをデータの仮想化と混同しないようにしてください。データの仮想化では、すべてのデータ オブジェクトがローカル コレクションに存在するのではなく、データ オブジェクトが必要に応じてストリームされます。  
  
 次の表は、経過時間を追加して、5000 のレンダリング<xref:System.Windows.Controls.TextBlock>要素を<xref:System.Windows.Controls.StackPanel>と<xref:System.Windows.Controls.VirtualizingStackPanel>します。 このシナリオでは、測定値を表すテキスト文字列をアタッチするまでの時間、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ItemsControl>パネル要素がテキスト文字列を表示する場合にオブジェクト。  
  
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
