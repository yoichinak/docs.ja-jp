---
title: '方法: UI であるアドインを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: fa30b7860bd8afdb68b0b54cd8d40f3e1ec86077
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949129"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>方法: UI であるアドインを作成する
この例では、WPF スタンドアロンアプリケーションによってホストされる Windows Presentation Foundation (WPF) であるアドインを作成する方法を示します。  
  
 アドインは、WPF ユーザーコントロールである UI です。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 WPF スタンドアロンアプリケーションは、アドイン UI をメインアプリケーションウィンドウのコンテンツとしてホストします。  
  
 **必須コンポーネント**  
  
 この例では、このシナリオを有効にする .NET Framework アドインモデルの WPF 拡張機能に焦点を当て、次のことを前提としています。  
  
- パイプライン、アドイン、およびホスト開発を含む .NET Framework アドインモデルに関する知識。 これらの概念についてよく知らない場合は、「[アドインと拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。 パイプライン、アドイン、およびホストアプリケーションの実装方法を示すチュートリアルについては、「 [チュートリアル:拡張可能なアプリケーション](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))を作成する。  
  
- .NET Framework アドインモデルに対する WPF 拡張機能に関する知識。 「 [WPF アドインの概要](wpf-add-ins-overview.md)」を参照してください。  
  
## <a name="example"></a>例  
 WPF UI であるアドインを作成するには、各パイプラインセグメント、アドイン、およびホストアプリケーションに特定のコードが必要です。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装

アドインが UI の場合、アドインのコントラクトはを実装<xref:System.AddIn.Contract.INativeHandleContract>する必要があります。 この例`IWPFAddInContract`では、 <xref:System.AddIn.Contract.INativeHandleContract>次のコードに示すように、がを実装しています。  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装

アドインは<xref:System.Windows.FrameworkElement>型のサブクラスとして実装されるため、アドインビューでもサブクラス<xref:System.Windows.FrameworkElement>を指定する必要があります。 次のコードは、 `WPFAddInView`クラスとして実装されているコントラクトのアドインビューを示しています。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
ここでは、アドインビューはから<xref:System.Windows.Controls.UserControl>派生しています。 そのため、アドインの UI もから<xref:System.Windows.Controls.UserControl>派生する必要があります。  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装

コントラクトが<xref:System.AddIn.Contract.INativeHandleContract>の場合、アドイン<xref:System.Windows.FrameworkElement>は (アドインビューのパイプラインセグメントで指定されている) です。 したがって、 <xref:System.Windows.FrameworkElement>分離境界を越える<xref:System.AddIn.Contract.INativeHandleContract>前に、をに変換する必要があります。 この作業は、次のコードに示すように、を呼び<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>出すことによってアドイン側のアダプターによって実行されます。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

アドインが ui を返すアドインモデル (「 [ui を返すアドインを作成](how-to-create-an-add-in-that-returns-a-ui.md)する」を参照) では、アドインアダプターはを<xref:System.Windows.FrameworkElement>呼び出し<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>て、をに変換します。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>このモデルでも呼び出される必要がありますが、呼び出すコードを記述するメソッドを実装する必要があります。 これを行うには<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> 、を呼び出すコードがを<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>必要<xref:System.AddIn.Contract.INativeHandleContract>とする場合<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>に、を呼び出すコードをオーバーライドして実装します。 この場合、呼び出し元はホスト側のアダプターであり、これについては、後で説明します。  
  
> [!NOTE]
> また、このモデルで<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>をオーバーライドして、ホストアプリケーション ui とアドイン ui 間のタブ移動を有効にする必要もあります。 詳細については、「Wpf アドインの[概要](wpf-add-ins-overview.md)」の「wpf アドインの制限事項」を参照してください。  
  
アドイン側アダプターはから<xref:System.AddIn.Contract.INativeHandleContract>派生するインターフェイスを実装するため、を実装<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>する必要もあります。ただし、をオーバーライドし<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>た場合は無視されます。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装

このモデルでは、ホストアプリケーションは通常、ホストビューが<xref:System.Windows.FrameworkElement>サブクラスであることを想定しています。 が分離境界を<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Contract.INativeHandleContract>越え<xref:System.Windows.FrameworkElement>た後、ホスト側アダプターはをに変換する必要があります。 メソッドは、 <xref:System.Windows.FrameworkElement>を取得するためにホストアプリケーションによって呼び出されないため、ホストビューはそれ<xref:System.Windows.FrameworkElement>を含むを "返す" 必要があります。 そのため、ホストビューは、などの他の<xref:System.Windows.FrameworkElement> ui を<xref:System.Windows.Controls.UserControl>含むことができるのサブクラスから派生する必要があります。 次のコードは、 `WPFAddInHostView`クラスとして実装されているコントラクトのホストビューを示しています。  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装

コントラクトが<xref:System.AddIn.Contract.INativeHandleContract>の場合、ホストアプリケーションは (ホストビュー <xref:System.Windows.Controls.UserControl>で指定されているように) を必要とします。 そのため、分離境界を越え<xref:System.Windows.FrameworkElement>た後にをに変換してから、ホストビュー (から<xref:System.Windows.Controls.UserControl>派生) のコンテンツとして設定する必要があります。<xref:System.AddIn.Contract.INativeHandleContract>  
  
この作業は、次のコードに示されているように、ホスト側アダプターによって行われます。  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

ご覧のように、ホスト側アダプターは、アドイン側<xref:System.AddIn.Contract.INativeHandleContract>アダプターの<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>メソッドを呼び出すことによってを取得します (これ<xref:System.AddIn.Contract.INativeHandleContract>はが分離境界を越える点です)。  
  
次に、を呼び出し<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>て、をに変換します。 最後に<xref:System.Windows.FrameworkElement> 、はホストビューのコンテンツとして設定されます。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>アドインの実装

アドイン側アダプターとアドイン ビューが用意できると、次のコードに示されているように、アドイン ビューから派生することでアドインを実装できます。  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

この例では、このモデルの1つの興味深い利点を確認できます。アドインの開発者は、アドインとアドインの UI の両方ではなく、アドインのみを実装する必要があります (UI でもあるため)。  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装

ホスト側アダプターとホストビューを作成すると、ホストアプリケーションは .NET Framework アドインモデルを使用して、パイプラインを開き、アドインのホストビューを取得できます。 これらの手順を次のコードに示します。  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

ホストアプリケーションは、一般的な .NET Framework アドインモデルコードを使用してアドインをアクティブ化します。これにより、ホストビューが暗黙的にホストアプリケーションに返されます。 その後、ホストアプリケーションでは、 <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Grid>からのホストビュー () が表示されます。  
  
 アドインの UI との対話処理のコードは、アドインのアプリケーションドメインで実行されます。 このような対話には、次のようなものがあります。  
  
- イベントの<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click>処理。  
  
- を表示<xref:System.Windows.MessageBox>しています。  
  
 このアクティビティは、ホスト アプリケーションから完全に分離されています。  
  
## <a name="see-also"></a>関連項目

- [アドインおよび拡張機能](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF のアドインの概要](wpf-add-ins-overview.md)
