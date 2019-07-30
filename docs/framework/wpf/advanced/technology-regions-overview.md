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
ms.openlocfilehash: e2c93f4471db2d72851a5d5bd8806b59a3e5ee28
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629862"
---
# <a name="technology-regions-overview"></a>技術領域の概要
WPF、Win32、DirectX などのアプリケーションで複数のプレゼンテーションテクノロジが使用されている場合は、一般的なトップレベルウィンドウ内でレンダリング領域を共有する必要があります。 このトピックでは、WPF 相互運用アプリケーションのプレゼンテーションと入力に影響する可能性がある問題について説明します。  
  
## <a name="regions"></a>領域  
 最上位レベルのウィンドウでは、相互運用アプリケーションのいずれかのテクノロジを構成する各 HWND が独自のリージョン ("空域" とも呼ばれます) を持つことを概念にすることができます。 ウィンドウ内の各ピクセルは、その HWND の領域を構成する1つの HWND に属します。 (厳密に言えば、複数の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND がある場合は複数の領域がありますが、この説明では、1つだけを想定できます)。 この領域は、アプリケーションの有効期間中にそのピクセルの上にレンダリングを試みるすべてのレイヤーまたはその他のウィンドウが、同じレンダリングレベルのテクノロジに含まれる必要があることを意味します。 このような[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]場合、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]望ましくない結果に対してピクセルをレンダリングしようとすると、相互運用 api を使用して可能な限り許可されなくなります。  
  
### <a name="region-examples"></a>領域の例  
 次の図は、、DirectX、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]および[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をミキシングするアプリケーションを示しています。 各テクノロジでは、重複しない個別のピクセルセットが使用され、リージョンに関する問題はありません。  
  
 ![Win32、DirectX、WPF を混在させるアプリケーションの例。](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 このアプリケーションがマウスポインターの位置を使用して、これら3つの領域のいずれかにレンダリングしようとするアニメーションを作成するとします。 どのテクノロジがアニメーション自体を担当するかにかかわらず、そのテクノロジは他の2つの領域に違反します。 次の図は、Win32 領域に WPF の円を表示しようとした場合を示しています。  
  
 ![Win32 領域の上に WPF の円を表示しようとしました。](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 異なるテクノロジ間で透明度/アルファブレンドを使用しようとすると、別の違反があります。  次の図では、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ボックスがおよび[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] DirectX 領域に違反しています。 この[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ボックス内のピクセルは半透明であるため、DirectX と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の両方によって共同で所有されている必要がありますが、これは不可能です。  これは別の違反であるため、ビルドできません。  
  
 ![Win32 および DirectX 領域に違反している WPF ボックスを示す図。](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 前の3つの例では、四角形の領域を使用していましたが、さまざまな形状が考えられます。  たとえば、領域には穴を付けることができます。 次の図は、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]四角形の穴がある領域を示しています[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。これは、と DirectX 領域の組み合わせのサイズです。  
  
 ![四角形の穴を持つ Win32 領域を示す図。](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 また、領域は完全に四角形ではなく、または[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (region) によって describable された形でもかまいません。  
  
 ![四角形以外の領域を示す図。](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>透明度とトップレベルウィンドウ  
 Windows のウィンドウマネージャーは、実際に[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]は hwnd のみを処理します。 したがって、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はすべて<xref:System.Windows.Window> HWND です。 Hwnd <xref:System.Windows.Window>は、すべての hwnd の一般的な規則に従う必要があります。 その HWND 内で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、コードは api 全体[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をサポートします。 ただし、デスクトップ上の他の hwnd との[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]対話につい[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ては、は処理と表示の規則を遵守する必要があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、api を使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]して四角形以外のウィンドウをサポートしています。非四角形ウィンドウの場合は hrgns、ピクセル単位のアルファの場合はレイヤードウィンドウです。  
  
 定数アルファおよびカラーキーはサポートされていません。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]レイヤードウィンドウの機能は、プラットフォームによって異なります。  
  
 レイヤードウィンドウでは、ウィンドウ内のすべてのピクセルに適用するアルファ値を指定することで、ウィンドウ全体を半透明 (半透明) にすることができます。  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]実際にはピクセル単位のアルファはサポートされていますが、このモードでは、ダイアログやドロップダウンを含む子 HWND を自分で描画する必要があるため、実際のプログラムでは使用するのが非常に困難です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]HRGNs をサポートします。ただし、この機能にはマネージ Api はありません。 プラットフォーム呼び出しおよびを使用し<xref:System.Windows.Interop.HwndSource>て、関連[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]する api を呼び出すことができます。 詳細については、「[マネージコードからのネイティブ関数の呼び出し](/cpp/dotnet/calling-native-functions-from-managed-code)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]階層化されたウィンドウの機能は、オペレーティングシステムによって異なります。 これは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]が directx を使用してレンダリングするためです。また[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 、レイヤーウィンドウは、主に directx レンダリングではなくレンダリング用に設計されています。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以降では、ハードウェアアクセラレータ[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]によるレイヤードウィンドウをサポートしています。 ハードウェアアクセラレータに[!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]よるレイヤードウィンドウは、microsoft directx のサポートを必要とします。そのため、機能は、そのコンピューター上の microsoft directx のバージョンによって異なります。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は透明色キーをサポートして[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]いません。これは、特にレンダリングがハードウェアアクセラレータを使用する場合に、要求した色が正確にレンダリングされることを保証できないためです。  
  
- アプリケーションがで[!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]実行されている場合、directx アプリケーションがレンダリングされると、directx サーフェイス上のレイヤードウィンドウがちらつきます。  (実際のレンダリングシーケンスでは[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 、レイヤードウィンドウが非表示になり、DirectX が[!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)]描画された後、レイヤーウィンドウが戻ります)。  階層化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されていないウィンドウにもこの制限があります。  
  
## <a name="see-also"></a>関連項目

- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [チュートリアル: Win32 での WPF クロックのホスト](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [WPF での Win32 コンテンツのホスト](hosting-win32-content-in-wpf.md)
