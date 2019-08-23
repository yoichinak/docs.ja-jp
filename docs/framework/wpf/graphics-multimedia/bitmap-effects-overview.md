---
title: ビットマップ効果の概要
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: f2fa42d5d63cad6a71efd259416dad3416bf2d72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935300"
---
# <a name="bitmap-effects-overview"></a>ビットマップ効果の概要
ビットマップ効果を使用すると、デザイナーと開発者は、レンダリングされた Windows Presentation Foundation (WPF) コンテンツに視覚効果を適用できます。 たとえば、ビットマップ効果を使用すると、イメージまた<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>はボタンに効果またはぼかし効果を簡単に適用できます。  
  
> [!IMPORTANT]
> .NET Framework 4 <xref:System.Windows.Media.Effects.BitmapEffect>以降では、クラスは互換性のために残されています。 <xref:System.Windows.Media.Effects.BitmapEffect>クラスを使用しようとすると、互換性のために残されている例外が発生します。 クラスの代わり<xref:System.Windows.Media.Effects.BitmapEffect>に使用できない<xref:System.Windows.Media.Effects.Effect>ものは、クラスです。 ほとんどの場合、 <xref:System.Windows.Media.Effects.Effect>クラスは非常に高速です。  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF のビットマップ効果  
 ビットマップ効果 (<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクト) は、単純なピクセル処理操作です。 ビットマップ効果は、を<xref:System.Windows.Media.Imaging.BitmapSource>入力として受け取り、ぼかし<xref:System.Windows.Media.Imaging.BitmapSource>やドロップシャドウなどの効果を適用した後に新しいを生成します。 各ビットマップ効果は、の<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>ようなフィルター処理プロパティを制御できるプロパティを公開します。  
  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、特殊なケースとして、や<xref:System.Windows.Controls.TextBox>などの<xref:System.Windows.Controls.Button>ライブ<xref:System.Windows.Media.Visual>オブジェクトのプロパティとして効果を設定できます。 ピクセル処理は、実行時に適用されてレンダリングされます。 この場合、レンダリング<xref:System.Windows.Media.Visual>時に、は自動的に<xref:System.Windows.Media.Imaging.BitmapSource>等価のに変換され、への<xref:System.Windows.Media.Effects.BitmapEffect>入力として出力されます。 出力は、オブジェクト<xref:System.Windows.Media.Visual>の既定のレンダリング動作に代わるものです。 このため、オブジェクトは、視覚エフェクトが適用されている場合に、ビジュアルにハードウェアアクセラレータが適用されないようにするためだけに、ビジュアルをソフトウェアでレンダリングすることになります。 <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>フォーカスのないオブジェクトをシミュレートします。  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>オブジェクトの周囲に色のハローを作成します。  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>オブジェクトの背後に影を作成します。  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>指定された曲線に従ってイメージの表面を生成するベベルを作成します。  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>のバンプマッピングを作成し<xref:System.Windows.Media.Visual>て、人工光源の奥行とテクスチャの印象を与えます。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、ソフトウェア モードでレンダリングされます。 効果を適用するオブジェクトも、ソフトウェアでレンダリングされます。 大きなビジュアルにビットマップ効果を使うとき、またはビットマップ効果のプロパティをアニメーション化するときに、パフォーマンスが最も低下します。 このような方法ではビットマップ効果をまったく使ってはならないということではありませんが、注意を払い、十分にテストを行って、ユーザー エクスペリエンスが期待どおりになることを確認する必要があります。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、部分信頼の実行をサポートしていません。 ビットマップ効果を使うには、アプリケーションが完全な信頼のアクセス許可を持つ必要があります。  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>効果を適用する方法  
 <xref:System.Windows.Media.Effects.BitmapEffect>はの<xref:System.Windows.Media.Visual>プロパティです。 <xref:System.Windows.Controls.Button>したがって<xref:System.Windows.Controls.Image> 、、<xref:System.Windows.UIElement>、、などのビジュアルに効果を適用することは、プロパティを設定するのと同じように簡単です。 <xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.UIElement.BitmapEffect%2A>1つ<xref:System.Windows.Media.Effects.BitmapEffect>のオブジェクトに設定することも、 <xref:System.Windows.Media.Effects.BitmapEffectGroup>オブジェクトを使用して複数の効果を連鎖させることもできます。  
  
 次の例は、の<xref:System.Windows.Media.Effects.BitmapEffect> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を適用する方法を示しています。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 次の例は、を<xref:System.Windows.Media.Effects.BitmapEffect>コードに適用する方法を示しています。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.DockPanel>またはなど<xref:System.Windows.Controls.Canvas>のレイアウトコンテナーにが適用されると、そのすべての子要素を含む要素またはビジュアルのビジュアルツリーに効果が適用されます。<xref:System.Windows.Media.Effects.BitmapEffect>  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>カスタム効果の作成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、マネージド [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで使うことができるカスタム効果を作成するためのアンマネージド インターフェイスも提供されています。 カスタム ビットマップ効果の作成に関する参考資料については、「[Unmanaged WPF Bitmap Effect](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)」(アンマネージ WPF ビットマップ効果) ドキュメントをご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [アンマネージ WPF ビットマップ効果](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [イメージングの概要](imaging-overview.md)
- [セキュリティ](../security-wpf.md)
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [2D グラフィックスとイメージング](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
