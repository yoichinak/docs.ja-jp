---
title: ビットマップ効果の概要
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 1866ba7a5419ea435a56daa63f94122d3b83473e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166895"
---
# <a name="bitmap-effects-overview"></a>ビットマップ効果の概要
ビットマップ効果は、デザイナーを有効にして、視覚効果を適用する開発者が Windows Presentation Foundation (WPF) をコンテンツのレンダリングします。 ビットマップ効果を簡単に適用することを許可するなど、<xref:System.Windows.Media.Effects.DropShadowBitmapEffect>効果またはぼかし効果をイメージやボタン。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]以降、<xref:System.Windows.Media.Effects.BitmapEffect>クラスは廃止されています。 使用しようとする場合、<xref:System.Windows.Media.Effects.BitmapEffect>クラス、廃止例外が発生します。 旧式でない代わりに、<xref:System.Windows.Media.Effects.BitmapEffect>クラスは、<xref:System.Windows.Media.Effects.Effect>クラス。 ほとんどの場合、<xref:System.Windows.Media.Effects.Effect>クラスが大幅に高速です。  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>WPF のビットマップ効果  
 ビットマップ効果 (<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクト) 簡単なピクセル処理操作が。 ビットマップ効果は、<xref:System.Windows.Media.Imaging.BitmapSource>として、入力、新しい生成<xref:System.Windows.Media.Imaging.BitmapSource>ぼかしやドロップ シャドウなどの効果を適用した後。 各ビットマップ効果など、フィルター処理のプロパティを制御できるプロパティを公開する<xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A>の<xref:System.Windows.Media.Effects.BlurBitmapEffect>します。  
  
 特殊なケースとしての[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、効果として設定できるプロパティでライブ<xref:System.Windows.Media.Visual>などのオブジェクトを<xref:System.Windows.Controls.Button>または<xref:System.Windows.Controls.TextBox>します。 ピクセル処理は、実行時に適用されてレンダリングされます。 レンダリング時にこの場合、<xref:System.Windows.Media.Visual>に自動的に変換されます、<xref:System.Windows.Media.Imaging.BitmapSource>同等への入力として渡すは、 <xref:System.Windows.Media.Effects.BitmapEffect>。 出力の置換、<xref:System.Windows.Media.Visual>オブジェクトの既定のレンダリング動作します。 これは、ため<xref:System.Windows.Media.Effects.BitmapEffect>オブジェクトが効果を適用するときに、ビジュアルでハードウェア アクセラレータのみつまりなしをソフトウェアでレンダリングするビジュアルを強制します。  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> 焦点のずれたに表示されるオブジェクトをシミュレートします。  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> オブジェクトの周囲に色の付いた光輪を作成します。  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> オブジェクトの後ろに影を作成します。  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> 指定した曲線に従ってイメージの表面を浮き上がらせるベベルを作成します。  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> バンプ マッピングを作成、<xref:System.Windows.Media.Visual>人工的な光源から奥行きとテクスチャの印象を与える。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、ソフトウェア モードでレンダリングされます。 効果を適用するオブジェクトも、ソフトウェアでレンダリングされます。 大きなビジュアルにビットマップ効果を使うとき、またはビットマップ効果のプロパティをアニメーション化するときに、パフォーマンスが最も低下します。 このような方法ではビットマップ効果をまったく使ってはならないということではありませんが、注意を払い、十分にテストを行って、ユーザー エクスペリエンスが期待どおりになることを確認する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のビットマップ効果は、部分信頼の実行をサポートしていません。 ビットマップ効果を使うには、アプリケーションが完全な信頼のアクセス許可を持つ必要があります。  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>効果を適用する方法  
 <xref:System.Windows.Media.Effects.BitmapEffect> プロパティは、<xref:System.Windows.Media.Visual>します。 などのビジュアル、効果の適用そのため、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Image>、 <xref:System.Windows.Media.DrawingVisual>、または<xref:System.Windows.UIElement>プロパティの設定と同じくらい簡単です。 <xref:System.Windows.UIElement.BitmapEffect%2A> 1 つに設定することができます<xref:System.Windows.Media.Effects.BitmapEffect>を使用してオブジェクトまたは複数の効果をチェーンできる、<xref:System.Windows.Media.Effects.BitmapEffectGroup>オブジェクト。  
  
 次の例では、適用する方法、<xref:System.Windows.Media.Effects.BitmapEffect>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 次の例では、適用する方法、<xref:System.Windows.Media.Effects.BitmapEffect>コード。  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  ときに、<xref:System.Windows.Media.Effects.BitmapEffect>などレイアウト コンテナーに適用される<xref:System.Windows.Controls.DockPanel>または<xref:System.Windows.Controls.Canvas>、要素またはビジュアルを含むすべての子要素のビジュアル ツリーに効果を適用します。  
  
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
