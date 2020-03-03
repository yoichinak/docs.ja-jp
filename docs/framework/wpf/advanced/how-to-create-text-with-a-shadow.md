---
title: '方法: 影付きテキストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960440"
---
# <a name="how-to-create-text-with-a-shadow"></a>方法: 影付きテキストを作成する
このセクションの例で、表示されるテキストに影を付ける方法を紹介します。  
  
## <a name="example"></a>例  
 オブジェクトを使用すると、オブジェクトに対して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]さまざまなドロップシャドウ効果を作成できます。 <xref:System.Windows.Media.Effects.DropShadowEffect> テキストにドロップ シャドウ効果を適用した例を次に示します。 この場合、影はソフト シャドウです。つまり、影の色がぼやけています。  
  
 ![ぼかし&#61; 0.25 を使用したテキストシャドウ](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 影の幅を制御するには、 <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>プロパティを設定します。 値は、 `4.0`影の幅が4ピクセルであることを示します。 影のぼかし (ぼかし) は、 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティを変更することによって制御できます。 値がの`0.0`場合は、ぼかしがないことを示します。 ソフト シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> これらのシャドウ効果は、テキストレンダリング[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]パイプラインを通過しません。 結果として、これらの効果の利用時、ClearType が無効になります。  
  
 テキストにハード シャドウ効果を適用した例を次に示します。 この場合、影はぼかされません。  
  
 ![ぼかし&#61; 0 を使用したテキストの影](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 ハードシャドウを作成するには、 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティをに`0.0`設定します。これは、ぼかしが使用されないことを示します。 影の方向を制御するには、 <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティを変更します。 このプロパティの方向の値を、と`0` `360`の間の角度に設定します。 次の図は、 <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティ設定の方向の値を示しています。  
  
 ![シャドウの DropShadow 度の設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 ハード シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>ぼかし効果を使用する  
 は<xref:System.Windows.Media.Effects.BlurBitmapEffect> 、テキストオブジェクトの後ろに配置できる影のような効果を作成するために使用できます。 テキストに適用されたぼかしビットマップ効果は、全方向に均等にテキストをぼかします。  
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 ぼかし効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>TranslateTransform を使用する  
 は<xref:System.Windows.Media.TranslateTransform> 、テキストオブジェクトの後ろに配置できる影のような効果を作成するために使用できます。  
  
 次のコード例では<xref:System.Windows.Media.TranslateTransform> 、を使用してテキストをオフセットします。 この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。  
  
 ![TranslateTransform を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 TranslateTransform を利用して影のような効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
