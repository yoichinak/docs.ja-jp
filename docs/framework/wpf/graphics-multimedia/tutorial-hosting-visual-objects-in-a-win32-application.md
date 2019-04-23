---
title: 'チュートリアル: Win32 アプリケーションでのビジュアル オブジェクトのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: b260f96246f0d9e5447b74a05e1396bfef176197
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111463"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>チュートリアル: Win32 アプリケーションでのビジュアル オブジェクトのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]、コードがありますを追加すると効率的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]機能をアプリケーションにコードを書き直すではなく。 サポートを提供する[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、同時に使用されるグラフィックス サブシステム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内のオブジェクトをホストするためのメカニズムを提供、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。  
  
 このチュートリアルは、サンプル アプリケーションを記述する方法を説明します[Win32 の相互運用性サンプルによるヒット テストの](https://go.microsoft.com/fwlink/?LinkID=159995)、そのホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]visual オブジェクト、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。  

<a name="requirements"></a>   
## <a name="requirements"></a>必要条件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの基礎知識があることを前提としています。 基本的な事柄[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングを参照してください[チュートリアル。初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。 概要については[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングを参照してください、数多くの書籍の件名、特に*プログラミング Windows* Charles Petzold 著。  
  
> [!NOTE]
>  このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプル コードで、次を参照してください。 [Win32 の相互運用性サンプルによるヒット テストの](https://go.microsoft.com/fwlink/?LinkID=159995)します。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>ホストの Win32 ウィンドウを作成する  
 ホストする鍵[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内のオブジェクトを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、<xref:System.Windows.Interop.HwndSource>クラス。 このクラスは、ラップ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内のオブジェクトを[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]に組み込むことができるように、ウィンドウ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]子ウィンドウとして。  
  
 次の例では、コードを作成するため、<xref:System.Windows.Interop.HwndSource>オブジェクトとして、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ビジュアル オブジェクトのコンテナーのウィンドウ。 ウィンドウ スタイル、位置、およびその他のパラメーターを設定する、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウで、使用、<xref:System.Windows.Interop.HwndSourceParameters>オブジェクト。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  値、<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>プロパティを WS_EX_TRANSPARENT に設定することはできません。 つまり、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウを透明にすることはできません。 このため、ホストの背景色[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウがその親ウィンドウと同じ背景色に設定します。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>ホストの Win32 ウィンドウにビジュアル オブジェクトを追加する  
 ホストを作成すると[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コンテナー ウィンドウ、ビジュアル オブジェクトのビジュアル オブジェクトを追加しています。 アニメーションなど、ビジュアル オブジェクトの変換が、ホストの境界を超えて拡張しないことを確認する[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウの外接する四角形。  
  
 次の例では、コードを作成するため、<xref:System.Windows.Interop.HwndSource>オブジェクトおよびにビジュアル オブジェクトを追加します。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>オブジェクトがホストに追加する最初のビジュアル オブジェクトに設定されている[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。 ルート ビジュアル オブジェクトは、ビジュアル オブジェクト ツリーの最上位ノードを定義します。 ホストに追加された後続のビジュアル オブジェクト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウは、子オブジェクトとして追加されます。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 メッセージ フィルターを実装する  
 ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ビジュアル オブジェクトのウィンドウには、アプリケーション キューから、ウィンドウに送信されたメッセージを処理するウィンドウ メッセージ フィルター プロシージャが必要です。 ウィンドウ プロシージャからメッセージを受信する、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]システム。 これらは入力メッセージか、またはウィンドウ管理メッセージです。 必要に応じて、メッセージをウィンドウ プロシージャで処理したり、既定の処理用のシステムにメッセージを渡すことができます。  
  
 <xref:System.Windows.Interop.HwndSource>ビジュアル オブジェクトの親が提供するウィンドウ メッセージ フィルター プロシージャを参照する必要がありますを定義するオブジェクト。 作成するときに、<xref:System.Windows.Interop.HwndSource>オブジェクト、設定、<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>ウィンドウ プロシージャを参照するプロパティ。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 次の例に示すは、左右のマウス ボタンのアップ メッセージを処理するためのコードです。 マウスの座標値ヒット位置の値に含まれている、`lParam`パラメーター。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 メッセージを処理する  
 次の例のコードは、ホストに含まれているビジュアル オブジェクトの階層に対してヒット テストを実行する方法を示します[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ。 使用して、ビジュアル オブジェクトのジオメトリ内にポイントがあるかどうかを識別することができます、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>ルート ビジュアル オブジェクトとに対してヒット テスト、座標の値を指定します。 ルート ビジュアル オブジェクトの値は、ここで、<xref:System.Windows.Interop.HwndSource.RootVisual%2A>のプロパティ、<xref:System.Windows.Interop.HwndSource>オブジェクト。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 ビジュアル オブジェクトに対するヒット テストの詳細については、次を参照してください。[ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [Win32 の相互運用サンプルによるヒット テスト](https://go.microsoft.com/fwlink/?LinkID=159995)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
