---
title: '方法: UI を返すアドインを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115753"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>方法: UI を返すアドインを作成する
この例では、スタンドアロンの WPF アプリケーションのホストに Windows Presentation Foundation (WPF) を返すアドインを作成する方法を示します。  
  
 アドインには、WPF ユーザー コントロールの UI を返します。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 スタンドアロンの WPF アプリケーションでは、アドインをホストし、アプリケーションのメイン ウィンドウの内容として (アドインによって返される) ユーザー コントロールを表示します。  
  
 **必須コンポーネント**  
  
 この例では、このシナリオを有効にする、.NET Framework アドイン モデルを WPF 拡張を強調表示し、前提条件は次。  
  
-   .NET Framework アドイン モデルのパイプライン、アドイン、およびホストの開発を含むナレッジです。 これらの概念に慣れていない場合は、次を参照してください。[アドインおよび拡張](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))します。 パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルについては、次を参照してください。[チュートリアル。拡張可能なアプリケーションを作成する](../../add-ins/walkthrough-create-extensible-app.md)します。  
  
-   WPF の拡張機能を .NET Framework アドイン モデルはこちらのサポート技術情報:[WPF アドインの概要](wpf-add-ins-overview.md)します。  
  
## <a name="example"></a>例  
 WPF UI を返すアドインを作成するには、各パイプライン セグメント、アドイン、およびホスト アプリケーションの特定のコードが必要です。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装  
 メソッドは、UI を返すためのコントラクトを定義する必要があり、その戻り値型でなければなりません<xref:System.AddIn.Contract.INativeHandleContract>します。 これを示します、`GetAddInUI`のメソッド、`IWPFAddInContract`次のコード コントラクトします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装  
 アドインを実装しているため、[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]のサブクラスとして提供<xref:System.Windows.FrameworkElement>、メソッドは、アドイン ビューに関連付けられた`IWPFAddInView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>します。 次のコードは、コントラクトのアドイン ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装  
 コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、アドインを返しますが、 <xref:System.Windows.FrameworkElement> (アドイン ビューによって、指定した)。 その結果、<xref:System.Windows.FrameworkElement>に変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>分離境界を越える前にします。 呼び出して追加アドイン側アダプターによってこの作業が実行される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装  
 ホスト アプリケーションが表示されるため、 <xref:System.Windows.FrameworkElement>、メソッドは、ホスト ビューに関連付けられた`IWPFAddInHostView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>します。 次のコードは、コントラクトのホスト ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装  
 コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、ホスト アプリケーションが必要ですが、 <xref:System.Windows.FrameworkElement> (ホスト ビューによって、指定した)。 その結果、<xref:System.AddIn.Contract.INativeHandleContract>に変換する必要があります、<xref:System.Windows.FrameworkElement>分離境界を越えた後。 呼び出して、ホスト側アダプターによってこの作業が実行される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>、次のコードに示すようにします。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>アドインの実装  
 追加アドイン側アダプターとアドイン ビューが作成されると、アドイン (`WPFAddIn1.AddIn`) を実装する必要があります、`IWPFAddInView.GetAddInUI`を返すメソッドを<xref:System.Windows.FrameworkElement>オブジェクト (、<xref:System.Windows.Controls.UserControl>この例では)。 実装、 <xref:System.Windows.Controls.UserControl>、 `AddInUI`、次のコードで示されています。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 実装、 `IWPFAddInView.GetAddInUI` 、アドインによって単純にする必要がありますの新しいインスタンスを返す`AddInUI`を次のコードに示すように、します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 ホスト側アダプターとホスト ビューの作成、ホスト アプリケーションは、パイプラインを開き、アドイン、および呼び出しのホスト ビューを取得する .NET Framework アドイン モデルを使用できます、`IWPFAddInHostView.GetAddInUI`メソッド。 これらの手順を次のコードに示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>関連項目

- [アドインおよび拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF のアドインの概要](wpf-add-ins-overview.md)
