---
title: 'パフォーマンスの最適化 : その他の推奨事項'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186302"
---
# <a name="optimizing-performance-other-recommendations"></a>パフォーマンスの最適化 : その他の推奨事項
<a name="introduction"></a> このトピックでは、「[WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)」セクションのトピックで説明されている推奨事項を補足するパフォーマンスに関する推奨事項について取り上げます。  
  
 このトピックには、次のセクションが含まれます。  
  
- [ブラシの Opacity と要素の Opacity](#Opacity)  
  
- [オブジェクトへの移動](#Navigation_Objects)  
  
- [大きな 3D サーフェイスのヒット テスト](#Hit_Testing)  
  
- [CompositionTarget.Rendering イベント](#CompositionTarget_Rendering_Event)  
  
- [ScrollBarVisibility=Auto は使用しない](#Avoid_Using_ScrollBarVisibility)  
  
- [Font Cache サービスの構成による起動時間の短縮](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>ブラシの Opacity と要素の Opacity  
 を<xref:System.Windows.Media.Brush>使用して 要素の<xref:System.Windows.Shapes.Shape.Fill%2A>を<xref:System.Windows.Shapes.Shape.Stroke%2A>設定する場合は、要素の<xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType><xref:System.Windows.UIElement.Opacity%2A>プロパティを設定するよりも、値を設定することをおし。 要素の<xref:System.Windows.UIElement.Opacity%2A>プロパティを変更すると、一時的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]なサーフェスが作成される場合があります。  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>オブジェクトへの移動  
 オブジェクト<xref:System.Windows.Navigation.NavigationWindow>は、主に<xref:System.Windows.Window>集約とジャーナルによって、コンテンツ ナビゲーションのサポートを使用してオブジェクトを<xref:System.Windows.Navigation.NavigationService>派生および拡張します。 のクライアント領域は、統一<xref:System.Windows.Navigation.NavigationWindow>リソース識別子 (URI) またはオブジェクトのいずれかを指定して更新できます。 この両方の方法を次のサンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 各<xref:System.Windows.Navigation.NavigationWindow>オブジェクトには、そのウィンドウにユーザーのナビゲーション履歴を記録するジャーナルがあります。 履歴の目的の 1 つは、ユーザーが自分の来た道を戻れるようにすることです。  
  
 統一リソース識別子 (URI) を使用してナビゲートする場合、ジャーナルは統一リソース識別子 (URI) 参照のみを格納します。 したがって、ページに戻るたびにそのページが動的に再構築されることになり、ページの複雑さによってはかなりの時間がかかることもあります。 この場合、履歴の格納の負荷は低い反面、ページの再構築にかかる時間が長くなる可能性があります。  
  
 オブジェクトを使用して移動した場合は、オブジェクトのビジュアル ツリー全体が履歴に格納されます。 したがって、ページに戻るたびにページを再構築する必要はなく、ページがすぐに描画されます。 この場合、履歴の格納の負荷は高くなりますが、ページの再構築にかかる時間は短くて済みます。  
  
 オブジェクトを<xref:System.Windows.Navigation.NavigationWindow>使用する場合は、ジャーナリング・サポートがアプリケーションのパフォーマンスにどのような影響を与えるのかを念頭に置く必要があります。 詳細については、「ナビゲーションの[概要](../app-development/navigation-overview.md)」を参照してください。  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>大きな 3D サーフェイスのヒット テスト  
 大きな 3D サーフェイスのヒット テストは、CPU 消費の面でパフォーマンスへの影響が非常に大きくなります。 3D サーフェイスがアニメーション化されている場合には特にその傾向が強くなります。 そのようなサーフェイスでヒット テストを行う必要がない場合は、ヒット テストを無効にしてください。 から<xref:System.Windows.UIElement>派生したオブジェクトは、プロパティを に設定することで<xref:System.Windows.UIElement.IsHitTestVisible%2A>ヒット`false`テストを無効にすることができます。  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>CompositionTarget.Rendering イベント  
 イベント<xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType>が連続[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的にアニメーション化します。 このイベントを使用する場合は、毎回デタッチしてください。  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>ScrollBarVisibility=Auto は使用しない  
 可能な限り、<xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType>`HorizontalScrollBarVisibility`プロパティの値を`VerticalScrollBarVisibility`使用しないでください。 これらのプロパティは、<xref:System.Windows.Controls.RichTextBox>および<xref:System.Windows.Controls.ScrollViewer>オブジェクト<xref:System.Windows.Controls.TextBox>に対して定義され、オブジェクトの添付<xref:System.Windows.Controls.ListBox>プロパティとして定義されます。 代わりに、 <xref:System.Windows.Controls.ScrollBarVisibility> <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>、 <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>、<xref:System.Windows.Controls.ScrollBarVisibility.Visible>または に設定します。  
  
 この<xref:System.Windows.Controls.ScrollBarVisibility.Auto>値は、スペースが限られており、必要な場合にのみスクロールバーを表示する必要がある場合に使用されます。 たとえば、数百行のテキストを<xref:System.Windows.Controls.ScrollBarVisibility><xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.TextBox>含むのとは対照的に、この値を 30 項目の 1 つの値で使用すると便利です。  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Font Cache サービスの構成による起動時間の短縮  
 WPF フォント キャッシュ サービスは、WPF アプリケーション間でフォント データを共有します。 最初に実行する WPF アプリケーションは、サービスがまだ実行されていない場合に、このサービスを開始します。 Windows Vista を使用している場合は、"Windows プレゼンテーション基盤 (WPF) フォント キャッシュ 3.0.0.0" サービスを "手動" (既定) から "自動 (遅延開始)" に設定して、WPF アプリケーションの初期起動時間を短縮できます。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [テキスト](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [アニメーションのヒントとテクニック](../graphics-multimedia/animation-tips-and-tricks.md)
