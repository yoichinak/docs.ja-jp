---
title: '方法: 影付きテキストを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776817"
---
# <a name="how-to-create-text-with-a-shadow"></a>方法: 影付きテキストを作成する
このセクションの例で、表示されるテキストに影を付ける方法を紹介します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Effects.DropShadowEffect>オブジェクトでは、さまざまなドロップ シャドウ効果を作成できます。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]オブジェクト。 テキストにドロップ シャドウ効果を適用した例を次に示します。 この場合、影はソフト シャドウです。つまり、影の色がぼやけています。  
  
 ![テキストの影のぼかしを&#61;0.25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 設定して影の幅を制御することができます、<xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>プロパティ。 値`4.0`4 ピクセルの影の幅を示します。 ぼかしを制御する、または変更することで、シャドウのぼかし、<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティ。 値`0.0`ぼかしはありません。 ソフト シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  これらのシャドウ効果を通過しない、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキスト レンダリング パイプライン。 結果として、これらの効果の利用時、ClearType が無効になります。  
  
 テキストにハード シャドウ効果を適用した例を次に示します。 この場合、影はぼかされません。  
  
 ![テキストの影のぼかしを&#61;0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 ハード シャドウを作成するには設定して、<xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>プロパティを`0.0`、ぼかし効果が使用されていないことを示します。 影の方向を制御するには変更することによって、<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティ。 このプロパティの方向性のある値を設定間の角度に`0`と`360`します。 次の図の方向値、<xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>プロパティの設定。  
  
 ![シャドウの DropShadow 度の設定](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 ハード シャドウを付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>ぼかし効果を使用する  
 A<xref:System.Windows.Media.Effects.BlurBitmapEffect>テキスト オブジェクトの後ろに配置できる影のような効果を作成するために使用できます。 テキストに適用されたぼかしビットマップ効果は、全方向に均等にテキストをぼかします。  
  
 テキストにぼかし効果が適用されている例を次に示します。  
  
 ![BlurBitmapEffect を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 ぼかし効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>TranslateTransform を使用する  
 A<xref:System.Windows.Media.TranslateTransform>テキスト オブジェクトの後ろに配置できる影のような効果を作成するために使用できます。  
  
 次のコード例では、<xref:System.Windows.Media.TranslateTransform>テキストのオフセット。 この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。  
  
 ![TranslateTransform を使用するテキスト シャドウ](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 TranslateTransform を利用して影のような効果を付ける方法を次のコード例に示します。  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
