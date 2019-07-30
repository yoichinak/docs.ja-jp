---
title: ClearType の概要
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], ClearType technology
- ClearType [WPF], technology
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
ms.openlocfilehash: c9d86cadd5f2115d0214d9a1b1dce7e6682341e0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629731"
---
# <a name="cleartype-overview"></a>ClearType の概要
このトピックでは、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]で検出された Microsoft の ClearType テクノロジの概要について説明します。  

<a name="overview"></a>   
## <a name="technology-overview"></a>テクノロジの概要  
 ClearType は、によって[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]開発されたソフトウェアテクノロジで、ラップトップの画面、Pocket PC の画面、フラットパネルモニターなど、既存の lcd (液晶ディスプレイ) でのテキストの読みやすさを向上させます。  ClearType は、LCD 画面のすべてのピクセルで個々の垂直色のストライプ要素にアクセスすることによって機能します。 ClearType より前は、コンピューターが表示できる最小の詳細レベルは1ピクセルですが、LCD モニターで ClearType が実行されているため、テキストの特徴をピクセルの幅で表示できるようになりました。 解像度が上がるとテキスト表示の微細部の鮮明度が高くなるため、長時間にわたって読んでも苦になりません。  
  
 で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用できる cleartype は、最新世代の cleartype であり、で検出された[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)]バージョンに対していくつかの機能強化が行われています。  
  
<a name="sub-pixel_positioning"></a>   
## <a name="sub-pixel-positioning"></a>サブピクセル ポジショニング  
 以前のバージョンの ClearType よりも大幅に改善された点は、サブピクセルの配置を使用することです。 で[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]見つかった cleartype の実装とは異なり、の[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] cleartype では、ピクセルの開始境界だけでなく、ピクセル内でもグリフを開始できます。 グリフの配置の解像度が上がることにより、グリフの間隔や比率の正確さや一貫性が増します。  
  
 次の 2 つの例は、サブピクセル ポジショニングを使用した場合にサブピクセル境界でグリフを開始できることを示しています。 左側の例は、サブピクセルの配置を使用していない以前のバージョンの ClearType レンダラーを使用してレンダリングされます。 右側の例は、サブピクセルの配置を使用して、新しいバージョンの ClearType レンダラーを使用してレンダリングされます。 右側のイメージの **e** と **l** が、それぞれ異なるサブピクセルから開始しているために若干異なってレンダリングされていることに注意してください。 グリフ イメージはハイ コントラストであるため、テキストを標準サイズで画面に表示したときは、この違いはわかりません。 これは、ClearType に組み込まれている高度な色のフィルター処理が原因でのみ可能です。  
  
 ![2 つのバージョンの ClearType で表示されるテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk_mmgraphics_text_cleartype_overview_01")  
ClearType の以前のバージョンと新しいバージョンを使用して表示されるテキスト  
  
 次の2つの例では、以前の ClearType レンダラーの出力を、新しいバージョンの ClearType レンダラーと比較しています。 右側に示したサブピクセル ポジショニングでは、画面上の文字の間隔が大きく改善されています。特に、サブピクセル 1 個とピクセル 1 個の差がグリフの幅に占める割合の大きい、小さなサイズの場合によくわかります。 2 番目のイメージの方が、文字の間隔が均等に近くなっています。 テキスト画面の全体的な外観に対するサブピクセルポジショニングの累積的な利点は、大幅に増加し、ClearType テクノロジの大幅な進化を表しています。  
  
 ![以前のバージョンの ClearType で表示されるテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk_mmgraphics_text_cleartype_overview_02")  
ClearType の以前のバージョンと新しいバージョンを使用したテキスト  
  
<a name="y-direction_antialiasing"></a>   
## <a name="y-direction-antialiasing"></a>Y 方向のアンチエイリアシング  
 で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の ClearType のもう1つの改良点は、y 方向のアンチエイリアシングです。 Y 方向の[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]アンチエイリアシングを使用しないの ClearType では、y 軸ではなく x 軸での解像度が向上しています。 緩やかな曲線部分の上下では、境界がギザギザになって読みにくくなります。  
  
 次の例では、y 方向のアンチエイリアシングを使用しない場合の効果を示します。 この場合、文字の上下で境界がギザギザになっていることがよくわかります。  
  
 ![浅い曲線上にギザギザした端のテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk_mmgraphics_text_cleartype_overview_03")  
緩やかな曲線上にギザギザした境界が付いたテキスト  
  
 の ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、y 方向レベルでアンチエイリアシングを使用して、ギザギザした端を滑らかにします。 これは、東アジア言語を読みやすくするために特に重要です。これらの言語の表意文字では、緩やかな曲線の量が水平方向と垂直方向でほぼ同じであるからです。  
  
 次の例では、y 方向のアンチエイリアシングの効果を示します。 この場合、文字の上下の曲線が滑らかに表示されています。  
  
 ![ClearType の y&#45;方向のアンチ&#45;エイリアシングを含むテキスト](./media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk_mmgraphics_text_cleartype_overview_04")  
ClearType の y 方向アンチエイリアシングを適用したテキスト  
  
<a name="hardware_acceleration"></a>   
## <a name="hardware-acceleration"></a>ハードウェアの高速化  
 の ClearType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、ハードウェアの高速化を利用してパフォーマンスを向上させ、CPU の負荷とシステムメモリの要件を減らすことができます。 グラフィックスカードのピクセルシェーダーとビデオメモリを使用することにより、特にアニメーションが使用される場合に、ClearType によってテキストのレンダリングが高速になります。  
  
 の cleartype [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、システム全体の cleartype 設定は変更されません。 で[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ClearType を無効[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]にすると、アンチエイリアシングがグレースケールモードに設定されます。 また、の[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] cleartype では、 [cleartype チューナー PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)の設定は変更されません。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のアーキテクチャ設計における決定事項の 1 つに、解像度に依存しないレイアウトによる高解像度 DPI モニターのサポート向上があります。高解像度モニターの普及は進みつつあるからです。 この決定を受けて、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ではエイリアス化されたテキスト レンダリングや、一部の東アジア言語フォントのビットマップをサポートしないことになりました。これらはどちらも解像度に依存するためです。  
  
<a name="further_information"></a>   
## <a name="further-information"></a>詳細情報  
 [ClearType の情報](https://www.microsoft.com/typography/ClearTypeInfo.mspx)  
  
 [ClearType Tuner PowerToy](https://www.microsoft.com/typography/ClearTypePowerToy.mspx)  
  
## <a name="see-also"></a>関連項目

- [ClearType レジストリの設定](cleartype-registry-settings.md)
