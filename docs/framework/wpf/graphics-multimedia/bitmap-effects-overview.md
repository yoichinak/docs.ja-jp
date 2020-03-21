---
title: ビットマップ効果の概要
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187000"
---
# <a name="bitmap-effects-overview"></a>ビットマップ効果の概要
ビットマップ効果を使用すると、デザイナーや開発者は、レンダリングされた Windows プレゼンテーション ファンデーション (WPF) コンテンツに視覚効果を適用できます。 たとえば、ビットマップ効果を使用すると、イメージやボタン<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>に効果やぼかし効果を簡単に適用できます。  
  
> [!IMPORTANT]
> NET Framework 4 以降では、<xref:System.Windows.Media.Effects.BitmapEffect>クラスは廃止されています。 <xref:System.Windows.Media.Effects.BitmapEffect>クラスを使用しようとすると、古い例外が発生します。 クラスに代わる非廃止の<xref:System.Windows.Media.Effects.BitmapEffect>代替クラスは<xref:System.Windows.Media.Effects.Effect>クラスです。 ほとんどの場合、クラスは<xref:System.Windows.Media.Effects.Effect>大幅に高速化されます。  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>WPF のビットマップ効果  
 ビットマップ効果(<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクト)は、単純なピクセル処理操作です。 ビットマップ効果は、入力<xref:System.Windows.Media.Imaging.BitmapSource>として使用され、ぼかしや<xref:System.Windows.Media.Imaging.BitmapSource>ドロップシャドウなどの効果を適用した後に新しいエフェクトを生成します。 各ビットマップ効果は、 の場合など、フィルター処理プロパティを制御できる<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>プロパティ<xref:System.Windows.Media.Effects.BlurBitmapEffect>を公開します。  
  
 特殊なケースとして、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で の効果は、<xref:System.Windows.Media.Visual><xref:System.Windows.Controls.Button>または<xref:System.Windows.Controls.TextBox>などのライブ オブジェクトのプロパティとして設定できます。 ピクセル処理は、実行時に適用されてレンダリングされます。 この場合、レンダリング時に a<xref:System.Windows.Media.Visual>は<xref:System.Windows.Media.Imaging.BitmapSource>自動的に同等の値に変換され、 への入力として供給<xref:System.Windows.Media.Effects.BitmapEffect>されます。 出力は、オブジェクトの<xref:System.Windows.Media.Visual>既定のレンダリング動作を置き換えます。 このため<xref:System.Windows.Media.Effects.BitmapEffect>、オブジェクトは、効果が適用されたときにビジュアルにハードウェアアクセラレーションを適用しない、ソフトウェアでのみレンダリングするようにビジュアルを強制します。  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>フォーカスが合っていないように見えるオブジェクトをシミュレートします。  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>オブジェクトの周囲に色のハローが作成されます。  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>オブジェクトの背後に影を作成します。  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>指定した曲線に従ってイメージのサーフェスを上げるベベルを作成します。  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>は、人工光源からの深<xref:System.Windows.Media.Visual>さとテクスチャの印象を与えるために、のバンプマッピングを作成します。  
  
> [!NOTE]
> WPF ビットマップ効果はソフトウェア モードでレンダリングされます。 効果を適用するオブジェクトも、ソフトウェアでレンダリングされます。 大きなビジュアルにビットマップ効果を使うとき、またはビットマップ効果のプロパティをアニメーション化するときに、パフォーマンスが最も低下します。 このような方法ではビットマップ効果をまったく使ってはならないということではありませんが、注意を払い、十分にテストを行って、ユーザー エクスペリエンスが期待どおりになることを確認する必要があります。  
  
> [!NOTE]
> WPF ビットマップ効果は、部分信頼の実行をサポートしていません。 ビットマップ効果を使うには、アプリケーションが完全な信頼のアクセス許可を持つ必要があります。  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>効果を適用する方法  
 <xref:System.Windows.Media.Effects.BitmapEffect>は のプロパティ<xref:System.Windows.Media.Visual>です。 したがって<xref:System.Windows.Controls.Button>、 、 <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.DrawingVisual>、 、または<xref:System.Windows.UIElement>などのビジュアルに効果を適用する方法は、プロパティを設定するのと同じくらい簡単です。 <xref:System.Windows.UIElement.BitmapEffect%2A>1 つの<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクトに設定することも、オブジェクトを使用して複数の効果を<xref:System.Windows.Media.Effects.BitmapEffectGroup>連鎖することもできます。  
  
 次の例は、 を適用する<xref:System.Windows.Media.Effects.BitmapEffect>方法[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を示しています。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 次の例は、コード内でを<xref:System.Windows.Media.Effects.BitmapEffect>適用する方法を示しています。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.DockPanel>などの<xref:System.Windows.Controls.Canvas>レイアウト<xref:System.Windows.Media.Effects.BitmapEffect>コンテナーに a が適用されると、その効果は、要素またはビジュアルのビジュアル ツリー (子要素の全要素を含む) に適用されます。  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>カスタム効果の作成  
 WPF には、マネージ WPF アプリケーションで使用できるカスタム効果を作成するためのアンマネージ インターフェイスも用意されています。 カスタム ビットマップ効果の作成に関する参考資料については、「[Unmanaged WPF Bitmap Effect](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)」(アンマネージ WPF ビットマップ効果) ドキュメントをご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [アンマネージ WPF ビットマップ効果](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [イメージングの概要](imaging-overview.md)
- [セキュリティ](../security-wpf.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
