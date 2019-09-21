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
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962873"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>チュートリアル: Win32 アプリケーションでのビジュアル オブジェクトのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、コードに[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]多大な投資をしている場合は、コードを書き換えるのではなく、アプリケーションに機能を追加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]する方が効果的な場合があります。 アプリケーションで同時に[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]されるおよびグラフィックスサブシステムのサポート[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を提供するために、は[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ内のオブジェクトをホストするための機構を提供します。  
  
 このチュートリアルでは、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウでビジュアルオブジェクトをホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]するサンプルアプリケーション ( [Win32 の相互運用のサンプルを使用したヒットテスト](https://go.microsoft.com/fwlink/?LinkID=159995)) を記述する方法について説明します。  

<a name="requirements"></a>   
## <a name="requirements"></a>必要条件  
 このチュートリアルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] プログラミングの基礎知識があることを前提としています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングの基本的な概要について[は、「チュートリアル:初めての WPF デスクトップ](../getting-started/walkthrough-my-first-wpf-desktop-application.md)アプリケーション。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]プログラミングの概要については、「チャールズ petzold 著) による特定の*プログラミングウィンドウ*」を参照してください。  
  
> [!NOTE]
> このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプルコードについては、「 [Win32 相互運用によるヒットテストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159995)」を参照してください。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>ホストの Win32 ウィンドウを作成する  
 ウィンドウ内のオブジェクト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をホストするためのキー <xref:System.Windows.Interop.HwndSource>は、クラスです。 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] このクラスは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ内のオブジェクトをラップし、子ウィンドウ[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]としてに組み込むことができるようにします。  
  
 次の例は、ビジュアルオブジェクトの<xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コンテナーウィンドウとしてオブジェクトを作成するためのコードを示しています。 ウィンドウのウィンドウの[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]スタイル、位置、およびその他のパラメーターを設定するには、 <xref:System.Windows.Interop.HwndSourceParameters>オブジェクトを使用します。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>プロパティの値を WS_EX_TRANSPARENT に設定することはできません。 つまり、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウを透明にすることはできません。 このため、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウの背景色は、親ウィンドウと同じ背景色に設定されます。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>ホストの Win32 ウィンドウにビジュアル オブジェクトを追加する  
 ビジュアルオブジェクトのホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]コンテナーウィンドウを作成したら、ビジュアルオブジェクトを追加できます。 アニメーションなどのビジュアルオブジェクトの変換が、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウの外接する四角形の境界を越えて拡張されないようにする必要があります。  
  
 次の例は、 <xref:System.Windows.Interop.HwndSource>オブジェクトを作成し、そのオブジェクトにビジュアルオブジェクトを追加するためのコードを示しています。  
  
> [!NOTE]
> オブジェクトのプロパティは、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウに追加された最初のビジュアルオブジェクトに設定されます。 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> ルート ビジュアル オブジェクトは、ビジュアル オブジェクト ツリーの最上位ノードを定義します。 ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウに追加された後続のビジュアルオブジェクトは、子オブジェクトとして追加されます。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Win32 メッセージ フィルターを実装する  
 ビジュアルオブジェクト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]のホストウィンドウには、アプリケーションキューからウィンドウに送信されるメッセージを処理するためのウィンドウメッセージフィルタープロシージャが必要です。 ウィンドウプロシージャは、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]システムからメッセージを受信します。 これらは入力メッセージか、またはウィンドウ管理メッセージです。 必要に応じて、メッセージをウィンドウ プロシージャで処理したり、既定の処理用のシステムにメッセージを渡すことができます。  
  
 ビジュアル<xref:System.Windows.Interop.HwndSource>オブジェクトの親として定義したオブジェクトは、指定したウィンドウメッセージフィルタープロシージャを参照する必要があります。 <xref:System.Windows.Interop.HwndSource>オブジェクトを作成するときに、ウィンドウ<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>プロシージャを参照するようにプロパティを設定します。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 次の例に示すは、左右のマウス ボタンのアップ メッセージを処理するためのコードです。 マウスヒット位置の座標値は、 `lParam`パラメーターの値に含まれています。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Win32 メッセージを処理する  
 次の例のコードは、ホスト[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウに含まれるビジュアルオブジェクトの階層に対してヒットテストを実行する方法を示しています。 ポイントがビジュアルオブジェクトのジオメトリ内にあるかどうかを識別するには、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドを使用して、ルートビジュアルオブジェクトとヒットテストの対象となる座標値を指定します。 この場合、ルートビジュアルオブジェクトは、 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>オブジェクトのプロパティの値です。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 ビジュアルオブジェクトに対するヒットテストの詳細については、「[ビジュアル層でのヒットテスト](hit-testing-in-the-visual-layer.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [Win32 相互運用によるヒットテストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159995)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
