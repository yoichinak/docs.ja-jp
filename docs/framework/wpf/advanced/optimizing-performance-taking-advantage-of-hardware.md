---
title: パフォーマンスの最適化:ハードウェアの活用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: a47a4aae785d817904c30fe7c865a1c033eb3cca
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709221"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>パフォーマンスの最適化:ハードウェアの活用
の内部アーキテクチャに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、ハードウェアとソフトウェアという2つのレンダリングパイプラインがあります。 このトピックでは、アプリケーションのパフォーマンスの最適化に関する意思決定に役立つ、これらのレンダリングパイプラインについて説明します。  
  
## <a name="hardware-rendering-pipeline"></a>ハードウェアレンダリングパイプライン  
 パフォーマンスを判断[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]するうえで最も重要な要因の1つは、レンダリングが制限されており、レンダリングする必要があるピクセルが多いほど、パフォーマンスコストが高くなることです。 ただし、グラフィックス処理装置 (GPU) にオフロードできるレンダリングが多いほど、パフォーマンスが向上します。 アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ハードウェアレンダリングパイプラインは、microsoft directx バージョン7.0 以上をサポートするハードウェアで microsoft directx 機能を最大限に活用します。 Microsoft DirectX バージョン7.0 および PixelShader 2.0 以降の機能をサポートするハードウェアでは、さらに最適化を行うことができます。  
  
## <a name="software-rendering-pipeline"></a>ソフトウェアレンダリングパイプライン  
 ソフトウェア[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レンダリングパイプラインは、完全に CPU にバインドされています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、CPU の SSE および SSE2 命令セットを利用して、最適化された、完全な機能を備えたソフトウェアラスタライザーを実装します。 ソフトウェアへのフォールバックは、ハードウェアレンダリングパイプラインを使用してアプリケーションの機能をレンダリングできないときにシームレスに実行されます。  
  
 ソフトウェアモードで表示するときに発生する最大のパフォーマンスの問題は、塗りつぶし速度に関連しています。これは、レンダリングするピクセル数として定義されています。 ソフトウェアレンダリングモードのパフォーマンスに懸念がある場合は、ピクセルが再描画される回数を最小限に抑えるようにしてください。 たとえば、青色の背景を持つアプリケーションがあり、それによって少し透明な画像がレンダリングされる場合、アプリケーションのすべてのピクセルが2回レンダリングされます。 その結果、背景が青しかない場合と比べて、イメージでアプリケーションをレンダリングするのに2倍の時間がかかります。  
  
### <a name="graphics-rendering-tiers"></a>グラフィックスの描画層  
 アプリケーションが実行されるハードウェア構成を予測することは、非常に困難な場合があります。 ただし、アプリケーションが異なるハードウェアで実行されているときに機能をシームレスに切り替えることができるように設計を検討することもできます。これにより、さまざまなハードウェア構成を最大限に活用することができます。  
  
 これを実現する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ために、には、実行時にシステムのグラフィックス機能を決定する機能が用意されています。 グラフィックス機能を決定するには、ビデオカードを3つのレンダリング機能層の1つとして分類します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが表示機能層に対してクエリを実行できるようにする API を公開します。 アプリケーションは、ハードウェアでサポートされているレンダリング層に応じて、実行時にさまざまなコードパスを取得できます。  
  
 描画層に最も影響を与えるグラフィックス ハードウェアの機能:  
  
- **ビデオ RAM** グラフィックス ハードウェアのビデオ メモリの量で、グラフィックスの構築に利用できるバッファーのサイズと数が決まります。  
  
- **ピクセル シェーダー** ピクセル シェーダーは、ピクセル単位で効果を計算するグラフィックス処理機能です。 表示されるグラフィックスの解像度によっては、各表示フレームの処理に数百万単位のピクセルが必要になることがあります。  
  
- **頂点シェーダー** 頂点シェーダーは、オブジェクトの頂点データに数学演算を実行するグラフィックス処理機能です。  
  
- **マルチテクスチャ サポート** マルチテクスチャ サポートとは、3D グラフィックス オブジェクトにブレンド操作を実行するとき、2 つ以上の異なるテクスチャを適用できる機能のことです。 マルチテクスチャ サポートの度合いは、グラフィックス ハードウェア上のマルチテクスチャ ユニットの数で決まります。  
  
 ピクセルシェーダー、頂点シェーダー、およびマルチテクスチャ機能は、特定の DirectX バージョンレベルを定義するために使用されます。これは、の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]さまざまなレンダリング層を定義するために使用されます。  
  
 グラフィックス ハードウェアの機能により [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのレンダリング能力が決まります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] システムには次の 3 つの描画層があります。  
  
- **描画層 0** グラフィックス ハードウェアの高速化はありません。 DirectX のバージョンレベルがバージョン7.0 未満です。  
  
- **描画層 1**部分的なグラフィックスハードウェアの高速化。 DirectX のバージョンレベルは、バージョン7.0 以降で、バージョン**9.0 よりも**前のバージョンです。  
  
- **描画層 2** ほとんどのグラフィックス機能でグラフィックス ハードウェア高速が利用されます。 DirectX のバージョンレベルは、バージョン9.0 以上です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]描画層の詳細については、「[グラフィックスの描画層](graphics-rendering-tiers.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [データ バインディング](optimizing-performance-data-binding.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
