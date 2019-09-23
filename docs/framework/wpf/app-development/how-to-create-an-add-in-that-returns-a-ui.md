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
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182663"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>方法: UI を返すアドインを作成する
この例では、Windows Presentation Foundation (WPF) をホスト WPF スタンドアロンアプリケーションに返すアドインを作成する方法を示します。  
  
 このアドインは、WPF ユーザーコントロールの UI を返します。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 WPF スタンドアロンアプリケーションは、アドインをホストし、アドインによって返されたユーザーコントロールをメインアプリケーションウィンドウの内容として表示します。  
  
 **必須コンポーネント**  
  
 この例では、このシナリオを有効にする .NET Framework アドインモデルの WPF 拡張機能に焦点を当て、次のことを前提としています。  
  
- パイプライン、アドイン、およびホスト開発を含む .NET Framework アドインモデルに関する知識。 これらの概念についてよく知らない場合は、「[アドインと拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。 パイプライン、アドイン、およびホストアプリケーションの実装方法を示すチュートリアルについては、「 [チュートリアル:拡張可能なアプリケーション](../../add-ins/walkthrough-create-extensible-app.md)を作成する。  
  
- .NET Framework アドインモデルに対する WPF 拡張機能について説明します。これについては、次を参照してください。[WPF アドインの概要](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>例  
 WPF UI を返すアドインを作成するには、各パイプラインセグメント、アドイン、およびホストアプリケーションに特定のコードが必要です。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装  
 メソッドは、UI を返すためにコントラクトによって定義される必要があり、戻り値<xref:System.AddIn.Contract.INativeHandleContract>は型である必要があります。 これは、次の`GetAddInUI`コードの`IWPFAddInContract`コントラクトのメソッドによって示されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装  
 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]アドインは、の<xref:System.Windows.FrameworkElement>サブクラスとして提供するを実装しているため、に関連付けら`IWPFAddInView.GetAddInUI`れているアドインビューのメソッドは<xref:System.Windows.FrameworkElement>型の値を返す必要があります。 次のコードは、コントラクトのアドイン ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装  
 コントラクトメソッドはを返し<xref:System.AddIn.Contract.INativeHandleContract>ますが、アドインは<xref:System.Windows.FrameworkElement> (アドインビューで指定されているように) を返します。 そのため、 <xref:System.Windows.FrameworkElement>分離境界を越える<xref:System.AddIn.Contract.INativeHandleContract>前に、をに変換する必要があります。 この作業は、次のコードに示すように、を呼び<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>出すことによってアドイン側のアダプターによって実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装  
 ホストアプリケーションはを表示<xref:System.Windows.FrameworkElement>するため、に関連付けら`IWPFAddInHostView.GetAddInUI`れているホストビューのメソッドは、型<xref:System.Windows.FrameworkElement>の値を返す必要があります。 次のコードは、コントラクトのホスト ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装  
 コントラクトメソッドはを返し<xref:System.AddIn.Contract.INativeHandleContract>ますが、ホストアプリケーションは ( <xref:System.Windows.FrameworkElement>ホストビューで指定されているように) を必要とします。 そのため、分離境界を越えると<xref:System.Windows.FrameworkElement> 、はに変換される必要があります。<xref:System.AddIn.Contract.INativeHandleContract> この作業は、次のコードに示すように、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>を呼び出すことによってホスト側アダプターによって実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>アドインの実装  
 アドイン側のアダプターとアドインビューを作成した場合、`WPFAddIn1.AddIn`アドイン () は、 <xref:System.Windows.FrameworkElement>オブジェクト (この例では`IWPFAddInView.GetAddInUI` <xref:System.Windows.Controls.UserControl> ) を返すメソッドを実装する必要があります。 の実装<xref:System.Windows.Controls.UserControl> `AddInUI`は、次のコードによって示されます。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 アドイン`IWPFAddInView.GetAddInUI`によるの実装では、次のコードに示すように、単`AddInUI`にの新しいインスタンスを返す必要があります。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 ホスト側アダプターとホストビューを作成すると、ホストアプリケーションは .NET Framework アドインモデルを使用してパイプラインを開き、アドインのホストビューを取得して、 `IWPFAddInHostView.GetAddInUI`メソッドを呼び出すことができます。 これらの手順を次のコードに示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>関連項目

- [アドインおよび拡張機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF のアドインの概要](wpf-add-ins-overview.md)
