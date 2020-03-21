---
title: 'チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187424"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただし、Win32 コードに多大な投資を行う場合は、コードを書[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]き直すよりも、アプリケーションに機能を追加した方が効果的な場合があります。 アプリケーションで同時に使用される Win32 および[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]グラフィックス サブシステムをサポートするために[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、Win32 ウィンドウでオブジェクトをホストするメカニズムを提供します。  
  
 このチュートリアルでは、Win32 ウィンドウでビジュアル オブジェクトをホスト[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]するサンプル アプリケーション[、Win32 相互運用サンプルを使用したヒット テスト](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)を記述する方法について説明します。  

<a name="requirements"></a>
## <a name="requirements"></a>必要条件  
 このチュートリアルでは、Win32 プログラミング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と Win32 プログラミングの両方に関する基本的な知識があることを前提としています。 プログラミングの基本的な概要については、「[チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Win32 プログラミングの概要については、この問題に関する多数の書籍、特にチャールズ ペトゾルドの*プログラミング Windows*を参照してください。  
  
> [!NOTE]
> このチュートリアルには、関連するサンプルからのコード例が多数含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 完全なサンプル コードについては、「 [Win32 相互運用のサンプルを使用したヒット テスト](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)」を参照してください。  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>ホストの Win32 ウィンドウを作成する  
 Win32[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウでオブジェクトをホストするキーは<xref:System.Windows.Interop.HwndSource>、クラスです。 このクラスは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、Win32 ウィンドウにオブジェクトをラップし、子ウィンドウとしてオブジェクトを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]組み込むことができます。  
  
 次の例は、ビジュアル オブジェクトの<xref:System.Windows.Interop.HwndSource>Win32 コンテナー ウィンドウとしてオブジェクトを作成するコードを示しています。 Win32 ウィンドウのウィンドウ スタイル、位置、およびその他のパラメーターを設定するには、<xref:System.Windows.Interop.HwndSourceParameters>オブジェクトを使用します。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> プロパティの値を<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>WS_EX_TRANSPARENTに設定することはできません。 これは、ホストの Win32 ウィンドウを透明にできないことを意味します。 このため、ホストの Win32 ウィンドウの背景色は、その親ウィンドウと同じ背景色に設定されます。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>ホストの Win32 ウィンドウにビジュアル オブジェクトを追加する  
 ビジュアル オブジェクトのホスト Win32 コンテナー ウィンドウを作成したら、ビジュアル オブジェクトを追加できます。 アニメーションなどのビジュアル オブジェクトの変換が、ホスト Win32 ウィンドウの外接する四角形の境界を超えないようにします。  
  
 オブジェクトを作成し、オブジェクトにビジュアル<xref:System.Windows.Interop.HwndSource>オブジェクトを追加するコードを次の例に示します。  
  
> [!NOTE]
> オブジェクト<xref:System.Windows.Interop.HwndSource.RootVisual%2A>の<xref:System.Windows.Interop.HwndSource>プロパティは、ホスト Win32 ウィンドウに追加された最初のビジュアル オブジェクトに設定されます。 ルート ビジュアル オブジェクトは、ビジュアル オブジェクト ツリーの最上位ノードを定義します。 ホスト Win32 ウィンドウに追加された以降のビジュアル オブジェクトは、子オブジェクトとして追加されます。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Win32 メッセージ フィルターを実装する  
 ビジュアル オブジェクトのホスト Win32 ウィンドウには、アプリケーション キューからウィンドウに送信されるメッセージを処理するためのウィンドウ メッセージ フィルター プロシージャが必要です。 ウィンドウ プロシージャは Win32 システムからメッセージを受信します。 これらは入力メッセージか、またはウィンドウ管理メッセージです。 必要に応じて、メッセージをウィンドウ プロシージャで処理したり、既定の処理用のシステムにメッセージを渡すことができます。  
  
 ビジュアル<xref:System.Windows.Interop.HwndSource>オブジェクトの親として定義したオブジェクトは、指定したウィンドウ メッセージ フィルター プロシージャを参照する必要があります。 オブジェクトを<xref:System.Windows.Interop.HwndSource>作成するときに、ウィンドウ プロシージャ<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>を参照するようにプロパティを設定します。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 次の例に示すは、左右のマウス ボタンのアップ メッセージを処理するためのコードです。 マウスのヒット位置の座標値は、パラメーターの値に`lParam`含まれます。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Win32 メッセージを処理する  
 次の例のコードは、ホストの Win32 ウィンドウに含まれるビジュアル オブジェクトの階層に対してヒット テストを実行する方法を示しています。 ルート ビジュアル オブジェクトとヒット テストの対象となる座標値を<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>指定する方法を使用して、ポイントがビジュアル オブジェクトのジオメトリ内にあるかどうかを識別できます。 この場合、ルートビジュアルオブジェクトはオブジェクトのプロパティの<xref:System.Windows.Interop.HwndSource.RootVisual%2A>値です。 <xref:System.Windows.Interop.HwndSource>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 ビジュアル オブジェクトに対するヒット テストの詳細については、「[ビジュアル レイヤーでのヒット テスト](hit-testing-in-the-visual-layer.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndSource>
- [Win32 相互運用によるヒット テストのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
