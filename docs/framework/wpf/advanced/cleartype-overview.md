---
title: ClearType の概要
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: b76c0cb04e5de498374cbf28c8813fe5c95d41ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186165"
---
# <a name="cleartype-overview"></a>ClearType の概要
このトピックでは、 で使用されているマイクロソフトの ClearType[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テクノロジの概要について説明します。  

<a name="overview"></a>
## <a name="technology-overview"></a>テクノロジの概要  
 ClearType は、ラップトップの画面、ポケット PC 画面、フラット パネル モニターなどの既存の LCD (液晶ディスプレイ) 上のテキストの読みやすさを向上させるマイクロソフトが開発したソフトウェア テクノロジです。  ClearType は、LCD 画面の各ピクセルの縦色のストライプ要素に個別にアクセスすることで機能します。 ClearType 以前は、コンピュータが表示できる最小レベルの詳細は 1 ピクセルでしたが、LCD モニタで ClearType を実行すると、幅のピクセルのほんの一部の小さなテキストの機能を表示できるようになりました。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。  
  
 利用可能な ClearType[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、最新世代の ClearType で、Windows グラフィックス デバイス インターフェイス (GDI) で見つかったバージョンよりもいくつかの改善を行っています。  
  
<a name="sub-pixel_positioning"></a>
## <a name="sub-pixel-positioning"></a>サブピクセル ポジショニング  
 以前のバージョンの ClearType に比べて大幅に改善されたのが、サブピクセルの位置決めの使用です。 GDI に見られる ClearType 実装とは異なり[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、ClearType を使用すると、ピクセルの開始境界だけでなく、ピクセル内でグリフを開始できます。 グリフの配置の解像度が上がることにより、グリフの間隔や比率の正確さや一貫性が増します。  
  
 次の 2 つの例は、サブピクセル ポジショニングを使用した場合にサブピクセル境界でグリフを開始できることを示しています。 左側の例は、サブピクセルの位置を採用していない以前のバージョンの ClearType レンダラを使用してレンダリングされます。 右側の例は、サブピクセルの位置を使用して、新しいバージョンの ClearType レンダラを使用してレンダリングされます。 右側のイメージの **e** と **l** が、それぞれ異なるサブピクセルから開始しているために若干異なってレンダリングされていることに注意してください。 グリフ イメージはハイ コントラストであるため、テキストを標準サイズで画面に表示したときは、この違いはわかりません。 これは、ClearType に組み込まれている洗練されたカラー フィルタリングが原因でしか可能にないためです。  
  
 ![2 つのバージョンの ClearType を使用して表示されるテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType の以前のバージョンと新しいバージョンを使用して表示されるテキスト  
  
 次の 2 つの例では、以前の ClearType レンダラーの出力と新しいバージョンの ClearType レンダラーを比較します。 右側に示したサブピクセル ポジショニングでは、画面上の文字の間隔が大きく改善されています。特に、サブピクセル 1 個とピクセル 1 個の差がグリフの幅に占める割合の大きい、小さなサイズの場合によくわかります。 2 番目のイメージの方が、文字の間隔が均等に近くなっています。 テキストの画面の全体的な外観にサブピクセルの位置を配置することの累積利点は大幅に増加し、ClearType 技術の大幅な進化を表します。  
  
 ![以前のバージョンの ClearType を使用して表示されるテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
ClearType の以前のバージョンと新しいバージョンを使用したテキスト  
  
<a name="y-direction_antialiasing"></a>
## <a name="y-direction-antialiasing"></a>Y 方向のアンチエイリアシング  
 ClearType のもう 1[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]つの改善点は、y 方向アンチエイリアシングです。 Y 方向アンチエイリアシングを使用しない GDI の ClearType は、x 軸の解像度は向上しますが、Y 軸では解像度が向上しません。 緩やかな曲線部分の上下では、境界がギザギザになって読みにくくなります。  
  
 次の例では、y 方向のアンチエイリアシングを使用しない場合の効果を示します。 この場合、文字の上下で境界がギザギザになっていることがよくわかります。  
  
 ![緩やかな曲線上にギザギザした境界が付いたテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
緩やかな曲線上にギザギザした境界が付いたテキスト  
  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in では、Y 方向レベルでアンチエイリアシングを行い、ギザギザのエッジを滑らかにします。 これは、東アジア言語を読みやすくするために特に重要です。これらの言語の表意文字では、緩やかな曲線の量が水平方向と垂直方向でほぼ同じであるからです。  
  
 次の例では、y 方向のアンチエイリアシングの効果を示します。 この場合、文字の上下の曲線が滑らかに表示されています。  
  
 ![ClearType の y 方向アンチエイリアシングを適用したテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
<a name="hardware_acceleration"></a>
## <a name="hardware-acceleration"></a>ハードウェアの高速化  
 ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] in は、パフォーマンスを向上させ、CPU の負荷とシステム メモリの要件を減らすために、ハードウェア アクセラレーションを利用できます。 グラフィックス カードのピクセル シェーダとビデオ メモリを使用することで、ClearType は、特にアニメーションを使用する場合に、テキストのレンダリングを高速化します。  
  
 での入力[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を解除しても、システム全体の ClearType 設定は変更されません。 Windows で ClearType[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を無効にすると、アンチエイリアスがグレースケール モードに設定されます。 また、ClearType では[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、[クリアタイプ チューナー PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)の設定は変更されません。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のアーキテクチャ設計における決定事項の 1 つに、解像度に依存しないレイアウトによる高解像度 DPI モニターのサポート向上があります。高解像度モニターの普及は進みつつあるからです。 この決定を受けて、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ではエイリアス化されたテキスト レンダリングや、一部の東アジア言語フォントのビットマップをサポートしないことになりました。これらはどちらも解像度に依存するためです。  
  
<a name="further_information"></a>
## <a name="further-information"></a>詳細情報  
 [ClearType の情報](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>関連項目

- [ClearType レジストリの設定](cleartype-registry-settings.md)
