---
title: パフォーマンスの最適化:アプリケーション リソース
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 362d0f0fd3282365e5e05dcd43c49a9fd2ddc9a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139426"
---
# <a name="optimizing-performance-application-resources"></a>パフォーマンスの最適化:アプリケーション リソース
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同様に型指定された要素の間で一貫性のある外観や動作をサポートできるように、アプリケーションのリソースを共有することができます。 このトピックでは、この領域に役立ついくつかの推奨事項が、アプリケーションのパフォーマンスを向上します。  
  
 リソースについて詳しくは、「[XAML リソース](xaml-resources.md)」をご覧ください。  
  
## <a name="sharing-resources"></a>リソースの共有  
 アプリケーションがカスタム コントロールを使用して、内のリソースを定義するかどうか、 <xref:System.Windows.ResourceDictionary> (または XAML リソース ノード)、いずれかを定義することでリソースをお勧め、<xref:System.Windows.Application>または<xref:System.Windows.Window>オブジェクト レベル、またはの既定のテーマで定義しますカスタム コントロール。 カスタム コントロールのリソースを定義する<xref:System.Windows.ResourceDictionary>でそのコントロールのすべてのインスタンスのパフォーマンスに影響が課せられます。 たとえば、カスタム コントロールのリソース定義の一部と、カスタム コントロールの多くのインスタンスとして定義されているブラシの負荷の高い操作では、場合によっては、アプリケーションのワーキング セットは大幅に長くなります。  
  
 このポイントを示すためには、次のことを検討してください。 たとえば、カード ゲームを使用して、開発している[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 ほとんどのカード ゲームでは、それぞれ異なる面を 52 枚のカードが必要です。 カードのカスタム コントロールを実装して、カードのカスタム コントロールのリソースで (それぞれを表すカードの面) 52 のブラシを定義します。 メインのアプリケーションでは、最初にこのカードのカスタム コントロールの 52 のインスタンスを作成します。 カードのカスタム コントロールの各インスタンスの 52 のインスタンスを生成する<xref:System.Windows.Media.Brush>52 * 52 の合計を提供するオブジェクト、<xref:System.Windows.Media.Brush>アプリケーション内のオブジェクト。 カードのカスタム コントロールのリソースが不足ブラシを移動することによって、<xref:System.Windows.Application>または<xref:System.Windows.Window>オブジェクト レベル、または、カスタム コントロールの既定のテーマでの定義 52 ブラシを共有しているようになりましたので、アプリケーションのワーキング セットを削減します。カードのコントロールの 52 のインスタンス。  
  
## <a name="sharing-a-brush-without-copying"></a>コピーすることがなく、ブラシの共有  
 同じを使用して複数の要素があれば<xref:System.Windows.Media.Brush>オブジェクトでブラシをリソースとして定義しではなく、ブラシにインラインで定義する参照[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]します。 このメソッドは 1 つのインスタンスが作成され、ブラシにインラインで定義する一方、再利用する[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]の各要素の新しいインスタンスを作成します。  
  
 次のマークアップ例では、この点を示します。  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>使用可能な場合は、静的なリソース  
 静的リソースは、定義済みのリソースへの参照を検索することで、任意の XAML プロパティ属性の値を提供します。 そのリソースの検索の動作は、コンパイル時参照に似ています。  
  
 動的リソースは、その一方で、最初のコンパイル中に一時的な式を作成を要求されたリソースの値が実際にオブジェクトを構築するために必要になるまで遅延リソースを参照します。 そのリソースの検索の動作は、パフォーマンスに影響は、実行時参照に似ています。 必要な場合にのみ動的リソースを使用して、アプリケーションで可能な限り、静的なリソースを使用します。  
  
 次のマークアップ例では、両方の種類のリソースの使用を示します。  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [テキスト](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
