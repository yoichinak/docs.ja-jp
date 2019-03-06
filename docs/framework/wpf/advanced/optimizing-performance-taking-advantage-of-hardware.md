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
ms.openlocfilehash: 1e0050dbf6ec5ade22e3f09ceee66f69826e56df
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374259"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>パフォーマンスの最適化:ハードウェアの活用
内部アーキテクチャ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、2 つのレンダリング パイプライン、ハードウェアおよびソフトウェア。 このトピックでは、アプリケーションのパフォーマンスの最適化に関する決定を行うためのこれらのレンダリング パイプラインについてを説明します。  
  
## <a name="hardware-rendering-pipeline"></a>ハードウェア レンダリング パイプライン  
 決定に最も重要な要因の 1 つ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]パフォーマンスが表示範囲である、ピクセルの数が、コストが大きいほどのパフォーマンスをレンダリングする必要があります。 できるレンダリングにオフロードすることができます、ただし、 [!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)]、複数のパフォーマンス上の利点に確認できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション ハードウェア レンダリング パイプラインを最大限の活用[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]の最小値をサポートするハードウェアで機能[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]バージョン 7.0。 さらに最適化をサポートするハードウェアによって得られる[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]バージョン 7.0 と PixelShader 2.0 以降の機能です。  
  
## <a name="software-rendering-pipeline"></a>ソフトウェア レンダリング パイプライン  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ソフトウェア レンダリング パイプラインは完全に CPU バインドします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SSE 命令と SSE2 命令を利用は、最適化された、完全に機能を備えたソフトウェア ラスタライザーを実装するために、CPU で設定します。 ソフトウェアへのフォールバックは、シームレス、ハードウェア レンダリング パイプラインを使用して、アプリケーションの機能を表示することはできません。  
  
 最大のパフォーマンスの問題は発生ソフトウェア モードでのレンダリングに関連するフィル レートでレンダリングするピクセルの数として定義されている場合。 ソフトウェア レンダリング モードでのパフォーマンスに関する懸念がある場合は、ピクセルが再描画される回数を最小限にしてみてください。 たとえば、上にやや透明のイメージをレンダリングし、青色の背景を持つアプリケーションがある場合は、すべてのアプリケーションを 2 回でピクセルがレンダリングされます。 その結果がかかる 2 回青い背景のみにした場合よりも、イメージを使用してアプリケーションを表示するためにします。  
  
### <a name="graphics-rendering-tiers"></a>グラフィックスの描画層  
 アプリケーションを実行するハードウェア構成を予測する非常に困難ですがある可能性があります。 ただし、設計をシームレスに切り替える機能別のハードウェアで実行するときにそれぞれ別のハードウェア構成活用を実行できるように、アプリケーションを検討する可能性があります。  
  
 これを実現する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実行時にシステムのグラフィックス機能を判断する機能を提供します。 グラフィックス機能は、3 つの描画層の 1 つとして、ビデオ カードを分類することによって決定されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 公開、[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]描画機能層を照会するアプリケーションを利用できます。 アプリケーションは、ハードウェアでサポートされている描画層によって実行時に異なるコード パスを受け取ることができます。  
  
 描画層に最も影響を与えるグラフィックス ハードウェアの機能:  
  
-   **ビデオ RAM** グラフィックス ハードウェアのビデオ メモリの量で、グラフィックスの構築に利用できるバッファーのサイズと数が決まります。  
  
-   **ピクセル シェーダー** ピクセル シェーダーは、ピクセル単位で効果を計算するグラフィックス処理機能です。 表示されるグラフィックスの解像度によっては、各表示フレームの処理に数百万単位のピクセルが必要になることがあります。  
  
-   **頂点シェーダー** 頂点シェーダーは、オブジェクトの頂点データに数学演算を実行するグラフィックス処理機能です。  
  
-   **マルチテクスチャ サポート** マルチテクスチャ サポートとは、3D グラフィックス オブジェクトにブレンド操作を実行するとき、2 つ以上の異なるテクスチャを適用できる機能のことです。 マルチテクスチャ サポートの度合いは、グラフィックス ハードウェア上のマルチテクスチャ ユニットの数で決まります。  
  
 ピクセル シェーダー、頂点シェーダー、およびマルチ テクスチャ機能が特定の定義に使用される[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]さらに、さまざまな表示の層の定義に使用するバージョン レベル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
 グラフィックス ハードウェアの機能により [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのレンダリング能力が決まります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] システムには次の 3 つの描画層があります。  
  
-   **描画層 0** グラフィックス ハードウェアの高速化はありません。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]バージョン レベルがバージョン 7.0 未満です。  
  
-   **描画層 1**部分的なグラフィックス ハードウェア高速です。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]バージョン レベルはバージョン 7.0 以上と**より低い**バージョン 9.0 よりもします。  
  
-   **描画層 2** ほとんどのグラフィックス機能でグラフィックス ハードウェア高速が利用されます。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] バージョンのレベルはバージョン 9.0 以上です。  
  
 詳細については[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]階層を表示するを参照してください[グラフィックスの描画層](graphics-rendering-tiers.md)します。  
  
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
