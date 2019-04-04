---
title: '方法: テキストに変換を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: be0b6a0bbe927f248be434afd15dde6a66791fe6
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2019
ms.locfileid: "58126124"
---
# <a name="how-to-apply-transforms-to-text"></a>方法: テキストに変換を適用する
変換を利用すると、アプリケーションのテキストの表示を変えることができます。 次の例のテキストの表示に影響を与えるさまざまな種類の描画変換を使用して、<xref:System.Windows.Controls.TextBlock>コントロール。  
  
## <a name="example"></a>例  
 次は、x と y の 2 次元平面に指定した点を中心にテキストを回転させた例です。  
  
 ![RotateTransform を使用して回転したテキスト](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 次のコード例では、<xref:System.Windows.Media.RotateTransform>テキストを回転させます。 <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 の値は要素を時計回りに 90 度回転します。  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 テキストの 2 行目を x 軸に沿って 150% 拡大し、3 行目を y 軸に沿って 150% 拡大した例を次に示します。  
  
 ![ScaleTransform を使用してスケールされたテキスト](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 次のコード例では、<xref:System.Windows.Media.ScaleTransform>を元のサイズからスケールのテキスト。  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  テキストの拡大縮小は、テキストのフォント サイズを増やすことと同じではありません。 フォント サイズは、サイズを変えても最良の解像度が得られるように、互いに依存せずに計算されます。 一方で、テキストの拡大縮小では、元のサイズのテキストの比率が維持されます。  
  
 x 軸に沿って傾斜させたテキストの例を次に示します。  
  
 ![SkewTransform を使用して傾斜させたテキスト](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 次のコード例では、<xref:System.Windows.Media.SkewTransform>テキストを傾斜させる。 傾斜はスキューと呼ばれることもありますが、一様でない方法で座標空間を拡大する変換です。 この例では、2 つのテキスト文字列が x 座標に沿って -30° と 30° とに傾斜します。  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 次の例では、x 軸と y 軸に沿ってテキストが変換または移動されます。  
  
 ![TranslateTransform を使用するテキスト オフセット](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 次のコード例では、<xref:System.Windows.Media.TranslateTransform>テキストのオフセット。 この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>シャドウ効果を提供するための豊富な機能を提供します。 詳細については、[テキスト シャドウを伴って作成](how-to-create-text-with-a-shadow.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [アニメーションをテキストに適用する](how-to-apply-animations-to-text.md)
