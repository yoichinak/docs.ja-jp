---
title: '方法 : UI を返すアドインを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174590"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>方法 : UI を返すアドインを作成する
この例では、Windows プレゼンテーション ファンデーション (WPF) をホスト WPF スタンドアロン アプリケーションに返すアドインを作成する方法を示します。  
  
 アドインは、WPF ユーザー コントロールである UI を返します。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 WPF スタンドアロン アプリケーションはアドインをホストし、ユーザー コントロール (アドインによって返される) をメイン アプリケーション ウィンドウのコンテンツとして表示します。  
  
 **前提条件**  
  
 この例では、このシナリオを有効にする .NET Framework アドイン モデルの WPF 拡張機能を強調表示し、次のことを前提としています。  
  
- パイプライン、アドイン、ホスト開発など、.NET Framework アドイン モデルに関する知識。 これらの概念に詳しくない場合は、「[アドインと機能拡張](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。 パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルについては、「[チュートリアル : 拡張アプリケーションの作成](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))」を参照してください。  
  
- .NET Framework アドイン モデルに対する WPF 拡張機能に関する知識は次[のとおりです。](wpf-add-ins-overview.md)  
  
## <a name="example"></a>例  
 WPF UI を返すアドインを作成するには、パイプライン セグメント、アドイン、およびホスト アプリケーションごとに特定のコードが必要です。  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装  
 メソッドは、UI を返すコントラクトによって定義され、その戻り値は型<xref:System.AddIn.Contract.INativeHandleContract>である必要があります。 これは、次のコード`GetAddInUI`でコントラクトの`IWPFAddInContract`メソッドによって示されています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装  
 アドインは、 のサブクラスとして提供される UI<xref:System.Windows.FrameworkElement>を実装しているため、関連付`IWPFAddInView.GetAddInUI`けるアドイン ビューのメソッドは type の値を返す<xref:System.Windows.FrameworkElement>必要があります。 次のコードは、コントラクトのアドイン ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装  
 コントラクト メソッドは<xref:System.AddIn.Contract.INativeHandleContract>を返しますが、アドインは<xref:System.Windows.FrameworkElement>(アドイン ビューで指定された) を返します。 したがって、分離境界<xref:System.Windows.FrameworkElement>を越える前に<xref:System.AddIn.Contract.INativeHandleContract>に 変換する必要があります。 この作業は、次のコードに示すように、 を呼<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>び出すことによってアドイン側アダプターによって実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装  
 ホスト アプリケーションには<xref:System.Windows.FrameworkElement>、 を表示するため、関連付けるホスト ビューのメソッド`IWPFAddInHostView.GetAddInUI`は type の<xref:System.Windows.FrameworkElement>値を返す必要があります。 次のコードは、コントラクトのホスト ビューがインターフェイスとして実装されることを示しています。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装  
 コントラクト メソッドは<xref:System.AddIn.Contract.INativeHandleContract>を返しますが、ホスト<xref:System.Windows.FrameworkElement>アプリケーションはホスト ビューで指定された を要求します。 したがって、分離境界<xref:System.AddIn.Contract.INativeHandleContract>を越えた後に<xref:System.Windows.FrameworkElement>に変換する必要があります。 この処理は、次のコードに示すように、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>を呼び出すことによってホスト側アダプターによって実行されます。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>アドインの実装  
 アドイン側`WPFAddIn1.AddIn`のアダプタとアドイン ビューが作成された場合、アドイン ( ) は`IWPFAddInView.GetAddInUI`<xref:System.Windows.FrameworkElement>オブジェクトを返すメソッドを実装する必要があります<xref:System.Windows.Controls.UserControl>(この例では a)。 <xref:System.Windows.Controls.UserControl>の`AddInUI`実装は、次のコードで示します。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 `IWPFAddInView.GetAddInUI`アドインによる の実装では、次のコードに示すように、 の`AddInUI`新しいインスタンスを返すだけです。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装  
 ホスト側のアダプターとホスト ビューを作成すると、ホスト アプリケーションは 、.NET Framework アドイン モデルを使用してパイプラインを開き、アドインのホスト ビューを取得し`IWPFAddInHostView.GetAddInUI`、メソッドを呼び出すことができます。 これらの手順を次のコードに示します。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>関連項目

- [アドインと拡張性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF アドインの概要](wpf-add-ins-overview.md)
