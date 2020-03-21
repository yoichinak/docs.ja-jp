---
title: '方法 : 影付きテキストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186842"
---
# <a name="how-to-create-text-with-a-shadow"></a>方法 : 影付きテキストを作成する
このセクションの例で、表示されるテキストに影を付ける方法を紹介します。  
  
## <a name="example"></a>例  
 オブジェクト<xref:System.Windows.Media.Effects.DropShadowEffect>を使用すると、オブジェクトに対してさまざまなドロップ シャドウ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]効果を作成できます。 テキストにドロップ シャドウ効果を適用した例を次に示します。 この場合、影はソフト シャドウです。つまり、影の色がぼやけています。  
  
 ![ソフトネス&#61;のテキストシャドウ 0.25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 プロパティを設定すると、影の幅を<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>制御できます。 の値は`4.0`、4 ピクセルのシャドウ幅を示します。 プロパティを変更することで、影の柔らかさやぼかしを<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>コントロールできます。 の値は`0.0`ぼかしがないことを示します。 ソフト シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> これらのシャドウ効果は、テキスト レンダリング[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]パイプラインを通過しません。 結果として、これらの効果の利用時、ClearType が無効になります。  
  
 テキストにハード シャドウ効果を適用した例を次に示します。 この場合、影はぼかされません。  
  
 ![ソフトネス&#61; 0 のテキストシャドウ](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 プロパティを<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>`0.0`に設定して、ハード シャドウを作成できます。 プロパティを変更することで、影の方向を<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>制御できます。 このプロパティの方向値を と の`0``360`間の程度に設定します。 次の図は、プロパティ設定の方向<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>値を示しています。  
  
 ![シャドウの DropShadow 度の設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 ハード シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>ぼかし効果を使用する  
 A<xref:System.Windows.Media.Effects.BlurBitmapEffect>を使用すると、テキスト オブジェクトの背後に配置できる影のような効果を作成できます。 テキストに適用されたぼかしビットマップ効果は、全方向に均等にテキストをぼかします。  
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 ぼかし効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>TranslateTransform を使用する  
 A<xref:System.Windows.Media.TranslateTransform>を使用すると、テキスト オブジェクトの背後に配置できる影のような効果を作成できます。  
  
 次のコード例では、<xref:System.Windows.Media.TranslateTransform>を使用してテキストをオフセットします。 この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。  
  
 ![TranslateTransform を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 TranslateTransform を利用して影のような効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
