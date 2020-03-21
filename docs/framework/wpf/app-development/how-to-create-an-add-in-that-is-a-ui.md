---
title: '方法 : UI であるアドインを作成する'
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
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141030"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>方法 : UI であるアドインを作成する
この例では、WPF スタンドアロン アプリケーションによってホストされる Windows プレゼンテーション ファンデーション (WPF) であるアドインを作成する方法を示します。  
  
 アドインは、WPF ユーザー コントロールである UI です。 ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。 WPF スタンドアロン アプリケーションは、メイン アプリケーション ウィンドウのコンテンツとしてアドイン UI をホストします。  
  
 **前提条件**  
  
 この例では、このシナリオを有効にする .NET Framework アドイン モデルの WPF 拡張機能を強調表示し、次のことを前提としています。  
  
- パイプライン、アドイン、ホスト開発など、.NET Framework アドイン モデルに関する知識。 これらの概念に詳しくない場合は、「[アドインと機能拡張](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))」を参照してください。 パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルについては、「[チュートリアル : 拡張アプリケーションの作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))」を参照してください。  
  
- .NET Framework アドイン モデルに対する WPF 拡張機能に関する知識。 [WPF アドインの概要 を](wpf-add-ins-overview.md)参照してください。  
  
## <a name="example"></a>例  
 WPF UI であるアドインを作成するには、パイプライン セグメント、アドイン、およびホスト アプリケーションごとに特定のコードが必要です。  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>コントラクト パイプライン セグメントの実装

アドインが UI の場合、アドインのコントラクトは を実装<xref:System.AddIn.Contract.INativeHandleContract>する必要があります。 この例では、`IWPFAddInContract`次の<xref:System.AddIn.Contract.INativeHandleContract>コードに示すように を実装します。  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>アドイン ビュー パイプライン セグメントの実装

アドインは<xref:System.Windows.FrameworkElement>型のサブクラスとして実装されているため、アドイン ビューもサブクラス<xref:System.Windows.FrameworkElement>を使用する必要があります。 次のコードは、クラスとして実装されたコントラクトのアドイン ビューを`WPFAddInView`示しています。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
ここでは、アドイン ビューは<xref:System.Windows.Controls.UserControl>から派生します。 したがって、アドイン UI も<xref:System.Windows.Controls.UserControl>から派生する必要があります。  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>アドイン側アダプター パイプライン セグメントの実装

コントラクトが<xref:System.AddIn.Contract.INativeHandleContract>である間、アドインは<xref:System.Windows.FrameworkElement>(アドイン ビュー パイプライン セグメントで指定された) です。 したがって、分離<xref:System.Windows.FrameworkElement>境界を越える前<xref:System.AddIn.Contract.INativeHandleContract>に に 変換する必要があります。 この作業は、次のコードに示すように、 を呼<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>び出すことによってアドイン側アダプターによって実行されます。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

アドインが UI を返すアドイン モデル (「UI を[返すアドインを作成](how-to-create-an-add-in-that-returns-a-ui.md)する」を参照) では、アドイン アダプタは<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>呼び<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>出して に変換します。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>このモデルでも呼び出す必要がありますが、呼び出すコードを記述するメソッドを実装する必要があります。 これを行うには、呼び<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>出すコードがを必要<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>としている場合に呼び<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>出すコード<xref:System.AddIn.Contract.INativeHandleContract>をオーバーライドして実装します。 この場合、呼び出し元はホスト側のアダプターであり、これについては、後で説明します。  
  
> [!NOTE]
> ホスト アプリケーション UI<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>とアドイン UI 間のタブ移動を有効にするには、このモデルでオーバーライドする必要があります。 詳細については、「WPF アドインの概要」の[「WPF アドインの](wpf-add-ins-overview.md)制限」を参照してください。  
  
アドイン側アダプタは から<xref:System.AddIn.Contract.INativeHandleContract>派生するインターフェイスを実装しているため、 をオーバーライドすると<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A><xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>、このメソッドは無視されますが、 も実装する必要があります。  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>ホスト ビュー パイプライン セグメントの実装

このモデルでは、ホスト アプリケーションは通常、ホスト ビューをサブ<xref:System.Windows.FrameworkElement>クラスと想定します。 ホスト側アダプターは、分離境界<xref:System.AddIn.Contract.INativeHandleContract>を越えた<xref:System.Windows.FrameworkElement>後に<xref:System.AddIn.Contract.INativeHandleContract>を に変換する必要があります。 メソッドは、ホスト アプリケーションからを取得するために呼び出されていないの<xref:System.Windows.FrameworkElement>で、ホスト ビューは、 を<xref:System.Windows.FrameworkElement>格納することによって" 返す必要があります。 したがって、ホスト ビューは、 などの<xref:System.Windows.FrameworkElement><xref:System.Windows.Controls.UserControl>他の UI を含むことができる サブクラスから派生する必要があります。 次のコードは、クラスとして実装されたコントラクトのホスト ビューを`WPFAddInHostView`示しています。  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>ホスト側アダプター パイプライン セグメントの実装

コントラクトが<xref:System.AddIn.Contract.INativeHandleContract>である間、ホスト アプリケーションは<xref:System.Windows.Controls.UserControl>ホスト ビューで指定された を要求します。 したがって、分離境界<xref:System.AddIn.Contract.INativeHandleContract>を越えた<xref:System.Windows.FrameworkElement>後に、ホスト ビューのコンテンツとして設定される前に 、 に変換する必要があります<xref:System.Windows.Controls.UserControl>( から派生します)。  
  
この作業は、次のコードに示されているように、ホスト側アダプターによって行われます。  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

ご覧のとおり、ホスト側アダプターは、アドイン側アダプター<xref:System.AddIn.Contract.INativeHandleContract>の<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>メソッドを呼び出すことによってを取得します (これは分離境界を<xref:System.AddIn.Contract.INativeHandleContract>越えるポイントです)。  
  
ホスト側アダプタは、 を<xref:System.AddIn.Contract.INativeHandleContract>呼び出<xref:System.Windows.FrameworkElement><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>して に変換します。 最後に<xref:System.Windows.FrameworkElement>、ホスト ビューの内容として 設定されます。  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>アドインの実装

アドイン側アダプターとアドイン ビューが用意できると、次のコードに示されているように、アドイン ビューから派生することでアドインを実装できます。  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

この例では、アドイン の開発者はアドイン クラスとアドイン UI の両方ではなく、アドインを実装するだけで済むという、このモデルの興味深い利点を見ることができます。  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>ホスト アプリケーションの実装

ホスト側のアダプターとホスト ビューを作成すると、ホスト アプリケーションは .NET Framework アドイン モデルを使用してパイプラインを開き、アドインのホスト ビューを取得できます。 これらの手順を次のコードに示します。  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

ホスト アプリケーションは、一般的な .NET Framework アドイン モデル コードを使用してアドインをアクティブ化します。 ホスト アプリケーションは、その後、 からホスト<xref:System.Windows.Controls.UserControl>ビュー ( <xref:System.Windows.Controls.Grid>) を表示します。  
  
 アドイン UI との対話を処理するためのコードは、アドインのアプリケーション ドメインで実行されます。 このような対話には、次のようなものがあります。  
  
- イベントの<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>処理。  
  
- を表示<xref:System.Windows.MessageBox>する。  
  
 このアクティビティは、ホスト アプリケーションから完全に分離されています。  
  
## <a name="see-also"></a>関連項目

- [アドインと拡張性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF アドインの概要](wpf-add-ins-overview.md)
