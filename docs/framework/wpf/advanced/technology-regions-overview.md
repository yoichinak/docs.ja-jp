---
title: 技術領域の概要
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: afea62dfe7ba26375cb23b661c6682bf1b59a19d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621037"
---
# <a name="technology-regions-overview"></a>技術領域の概要
WPF、Win32、DirectX などのアプリケーションで複数のプレゼンテーション テクノロジを使用する場合は、一般的な最上位ウィンドウ内のレンダリング領域を共有する必要があります。 このトピックでは、プレゼンテーション層と、WPF の相互運用アプリケーションの入力に影響を与える問題について説明します。  
  
## <a name="regions"></a>領域  
 最上位レベルのウィンドウ内には、次を各 HWND 相互運用アプリケーションのテクノロジのいずれかを構成する (「空域」とも呼ばれます)、専用の領域を持つを考えることができます。 ウィンドウ内の各ピクセルは、その HWND のリージョンを構成する 1 つの HWND に属しています。 (厳密に言えばが 1 つ以上[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]リージョンの 1 つ以上を使用する必要がある場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]HWND では、この説明のために、1 つしかないを想定できますが、)。 リージョンは、すべてのレイヤーやアプリケーションの有効期間中にそのピクセルの上にレンダリングしようとする他のウィンドウはレンダリング レベルのと同じテクノロジの一部である必要がありますを意味します。 表示しようとしています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]経由でピクセル[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、望ましくない結果に潜在顧客、および相互運用を可能な限りは許可されていません[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]します。  
  
### <a name="region-examples"></a>リージョンの例  
 次の図は、アプリケーションが混在する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]、および[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 それぞれのテクノロジ (ピクセル単位) の独自の独立した、重複しないセットを使用して、リージョンの問題はありません。  
  
 ![Win32、DirectX、および WPF が混在するアプリケーションの例です。](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 このアプリケーションで、マウス ポインターの位置を使用して、これら 3 つのリージョンのいずれかをレンダリングしようとするアニメーションを作成することをとします。 どちらのテクノロジが自体アニメーション担当に関係なくそのテクノロジが、その他の 2 つのリージョンに違反します。 次の図は、Win32 リージョン経由での WPF 円を表示するためにしようとします。  
  
 ![Win32 リージョン経由での WPF 円を表示しようとしました。](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 別の違反は、透過性/アルファ ブレンドのさまざまなテクノロジとの間を使用しようとするかどうかです。  次の図に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ボックスに違反している、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]と[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]リージョン。 ため、ピクセルを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]それら両方が共同で所有する必要があるボックスが半透明[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、することはできません。  このため、これは違反であり、ビルドすることはできません。  
  
 ![Win32、DirectX のリージョンに違反して WPF ボックスを示す図。](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 前の 3 つの例に使用される四角形の領域が、さまざまな図形が可能です。  たとえば、地域の穴をことができます。 次の図は、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]これは、サイズの四角形の穴を持つ領域、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]の地域の結合します。  
  
 ![四角形の穴を持つ Win32 領域を示す図。](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 領域を完全に四角形にすることもできますがない図形や、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (リージョン)。  
  
 ![四角形以外のリージョンを示す図。](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>透明性と最上位レベルの Windows  
 Windows のウィンドウ マネージャーが本当にのみ処理[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]Hwnd。 そのため、すべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND です。 <xref:System.Windows.Window> HWND が HWND の一般的な規則を遵守する必要があります。 その HWND 内[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コード行えるあらゆる全体的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]をサポートします。 デスクトップで、その他の Hwnd とのやり取りが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]規定を遵守する必要があります[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]処理およびルールを表示します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用して四角形以外の windows をサポートしている[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— HRGNs 四角形以外の windows、およびピクセルごとのアルファのレイヤード ウィンドウ。  
  
 定数のアルファ版および色キーを指定することはできません。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] レイヤード ウィンドウの機能は、プラットフォームによって異なります。  
  
 レイヤード ウィンドウと、ウィンドウ全体半透明 (半透明)、ウィンドウのすべてのピクセルに適用するアルファ値を指定しています。  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]サポート ピクセルごとのアルファ版が、これがこのモードですべての子を描画するために必要とするため、実用的なプログラムで使用する非常に困難ですが実際には HWND 自分で、ダイアログ ボックスのドロップダウン リストなど)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HRGNs; をサポートしていますただしが管理なし[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]この機能。 プラットフォームを使用することができますを呼び出すと<xref:System.Windows.Interop.HwndSource>を呼び出して、関連する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]します。 詳細については、次を参照してください。[マネージ コードからネイティブ関数の呼び出し](/cpp/dotnet/calling-native-functions-from-managed-code)します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイヤード ウィンドウには、さまざまなオペレーティング システムにさまざまな機能があります。 これは、ため[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]をレンダリングするレイヤード ウィンドウが主に用に設計された、[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]レンダリングされません[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]レンダリング。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイヤード ウィンドウをサポートするハードウェアの高速化[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]以降。 ハードウェア高速化レイヤー上の windows[!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]サポートは必要[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]機能のバージョンによって異なりますので、[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]そのコンピューター上です。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 透明色キーをサポートしません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ハードウェア アクセラレータによるレンダリングは、特に場合、要求された正確な色を表示するためには保証できません。  
  
- アプリケーションが実行されている場合[!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]、レイヤード ウィンドウの上に[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]サーフェスがちらつく場合に、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]アプリケーションのレンダリングします。  (実際のレンダリング シーケンスは[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)]し、レイヤード ウィンドウを非表示に[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]、描画し、[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)]レイヤード ウィンドウを戻します)。  非[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイヤード ウィンドウにもこの制限があります。  
  
## <a name="see-also"></a>関連項目

- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [チュートリアル: Win32 での WPF クロックのホスト](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [WPF での Win32 コンテンツのホスト](hosting-win32-content-in-wpf.md)
