---
title: WPF ウィンドウの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: 5acebf0f88f3147bf274818f11697b480146701a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296122"
---
# <a name="wpf-windows-overview"></a>WPF ウィンドウの概要
ユーザーは、windows で Windows Presentation Foundation (WPF) スタンドアロン アプリケーションと対話します。 ウィンドウの主な目的は、データを視覚化してユーザーがデータと対話できるコンテンツをホストすることです。 スタンドアロン[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションを使用して独自のウィンドウの提供、<xref:System.Windows.Window>クラス。 このトピックでは<xref:System.Windows.Window>を作成して、スタンドアロン アプリケーションで windows の管理の基礎を紹介します。  
  
> [!NOTE]
>  ブラウザーによってホストされる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]など、アプリケーション[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]や loose[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページは、独自のウィンドウを指定しません。 代わりに、によって提供されるウィンドウにホストされている[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]します。 参照してください[WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)します。  

<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a>ウィンドウ クラス  
 次の図は、ウィンドウの構成要素を示しています。  
  
 ![ウィンドウ要素を示すスクリーン ショット。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 ウィンドウは、非クライアント領域とクライアント領域の 2 つに分かれます。  
  
 *非クライアント領域*によって実装されるウィンドウの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]次を含む、ほとんどの windows に共通のウィンドウの部分が含まれています。  
  
-   境界線。  
  
-   タイトル バー。  
  
-   アイコン。  
  
-   最小化ボタン、最大化ボタン、および元に戻すボタン。  
  
-   閉じるボタン。  
  
-   ウィンドウを最小化、最大化、元のサイズに戻す、移動、サイズ変更、および閉じるためのメニュー項目を含むシステム メニュー。  
  
 *クライアント領域*ウィンドウがウィンドウの非クライアント領域内の領域と、メニュー バー、ツールバー、およびコントロールなどのアプリケーション固有のコンテンツを追加する開発者によって使用されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、ウィンドウがカプセル化、<xref:System.Windows.Window>次の操作に使用するクラスです。  
  
-   ウィンドウを表示する。  
  
-   ウィンドウのサイズ、位置、および外観を構成する。  
  
-   アプリケーション固有のコンテンツをホストする。  
  
-   ウィンドウの有効期間を管理する。  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a>ウィンドウの実装  
 一般的なウィンドウの実装は、外観と動作を構成、*外観*ユーザーに、ウィンドウの外観を定義および*動作*ユーザーが操作ウィンドウの機能方法を定義しますられています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外観を実装して、コーディングするかを使用してウィンドウの動作、または[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 一般に、ただし、ウィンドウの外観を使用して実装[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ、およびその動作の実装コード ビハインドを使用して次の例に示すようにします。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 有効にする、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ ファイルと分離コード ファイルを連携では、次が必要です。  
  
-   マークアップでは、`Window`要素を含める必要があります、`x:Class`属性。 ときに、アプリケーションがビルドが存在する`x:Class`ファイルにより、マークアップで[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]を作成する、`partial`クラスから派生した<xref:System.Windows.Window>によって指定された名前を持つ、`x:Class`属性。 追加する必要があります、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間宣言、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]スキーマ ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 生成された`partial`クラスが実装する、`InitializeComponent`メソッドが呼び出され、イベントを登録し、マークアップで実装されているプロパティを設定します。  
  
-   分離コード クラスがある必要があります、`partial`によって指定される同じ名前のクラス、`x:Class`のマークアップ、およびその属性がから派生する必要があります<xref:System.Windows.Window>します。 これにより、分離コード ファイルに関連付けられる、`partial`アプリケーションのビルド時にマークアップ ファイル用に生成されたクラス (を参照してください[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md))。  
  
-   分離コードで、<xref:System.Windows.Window>クラスを呼び出すコンス トラクターを実装する必要があります、`InitializeComponent`メソッド。 `InitializeComponent` 実装ファイルの生成されたマークアップによって`partial`イベントを登録し、マークアップで定義されているプロパティを設定するクラス。  
  
> [!NOTE]
>  新しいを追加すると<xref:System.Windows.Window>を使用して、プロジェクトに[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、<xref:System.Windows.Window>マークアップと分離コードの両方を使用して実装され、としてマークアップと分離コード ファイル間の関連付けを作成するために必要な構成が含まれていますここで説明します。  
  
 この構成で、ウィンドウの外観を定義に集中できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップと分離コードでその動作を実装します。 次の例では、実装で、ボタンを使用してウィンドウを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ、およびボタンのイベント ハンドラー<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント、分離コードで実装します。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a>MSBuild 用のウィンドウ定義の構成  
 ウィンドウを実装する方法の構成方法を決定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]します。 両方を使用して定義されているウィンドウの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップと分離コード。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップ ファイルとして構成されている[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目。  
  
-   分離コード ファイルとして構成されている[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile`項目。  
  
 これは、次に示すように、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]プロジェクト ファイル。  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 ビルドについて[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションを参照してください[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)します。  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a>ウィンドウの有効期間  
 クラスと同様に、ウィンドウにも有効期間があります。有効期間は、ウィンドウが開いて最初にインスタンス化されたときに開始し、アクティブ化と非アクティブ化を経て、最後に閉じられるまで継続します。  

<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a>ウィンドウを開く  
 ウィンドウを開くには、次の例に示すように最初にインスタンスを作成します。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 この例で、 `MarkupAndCodeBehindWindow` 、アプリケーションの起動時に発生するときにインスタンス化されるときに、<xref:System.Windows.Application.Startup>イベントが発生します。  
  
 参照が自動的に追加で管理されている windows の一覧に、ウィンドウがインスタンス化されるとき、<xref:System.Windows.Application>オブジェクト (を参照してください<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>)。 さらに、インスタンス化する最初のウィンドウは、既定では、設定<xref:System.Windows.Application>メイン アプリケーション ウィンドウとして (を参照してください<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>)。  
  
 呼び出すことによって、ウィンドウが開かれた最後に、<xref:System.Windows.Window.Show%2A>メソッドは、結果は次の図に示します。  
  
 ![Window.Show の呼び出しによって開いたウィンドウ](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 呼び出すことによって開かれたウィンドウ<xref:System.Windows.Window.Show%2A>はモードレス ウィンドウは、アプリケーションは、同じアプリケーションの他のウィンドウをアクティブ化できるモードで動作することを意味します。  
  
> [!NOTE]
>  <xref:System.Windows.Window.ShowDialog%2A> ダイアログ ボックスなどの windows をモーダルとして開くには呼び出されます。 参照してください[ダイアログ ボックスの概要](dialog-boxes-overview.md)詳細についてはします。  
  
 ときに<xref:System.Windows.Window.Show%2A>が呼び出されると、ウィンドウの初期化作業をする前に実行をユーザー入力を受け取ることのできるインフラストラクチャを確立するために表示されます。 ウィンドウが初期化されるときに、<xref:System.Windows.Window.SourceInitialized>イベントが発生し、ウィンドウが表示されます。  
  
 簡単な方法として<xref:System.Windows.Application.StartupUri%2A>アプリケーションの起動時に自動的に開かれている最初のウィンドウの指定に設定することができます。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 アプリケーションの起動時の値で指定されたウィンドウ<xref:System.Windows.Application.StartupUri%2A>が開かれるウィンドウを呼び出すことによって開くモードレスでは内部的には、その<xref:System.Windows.Window.Show%2A>メソッド。  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a>ウィンドウの所有権  
 使用して開かれるウィンドウ、<xref:System.Windows.Window.Show%2A>メソッドには、暗黙的なリレーションシップを作成したウィンドウではありません。 ユーザーのいずれかのウィンドウが、次を実行できますが、いずれかのウィンドウとは無関係に、その他の対話。  
  
-   一方 (、windows のいずれかの場合を除いて、その<xref:System.Windows.Window.Topmost%2A>プロパティに設定`true`)。  
  
-   もう一方のウィンドウに影響を与えずに、最小化/最大化し、元のサイズに戻す。  
  
 一部のウィンドウには、そのウィンドウを開いたウィンドウとの関係が必要です。 たとえば、[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)]アプリケーションは、プロパティ ウィンドウやツール ウィンドウが一般的な動作では、作成ウィンドウを開く場合があります。 また、そのようなウィンドウは、必ず作成元のウィンドウと一緒に閉じ、最小化/最大化し、元のサイズに戻す必要があります。 このようなリレーションシップは 1 つのウィンドウを確立することができます*独自*別、設定に達すると、<xref:System.Windows.Window.Owner%2A>のプロパティ、*所有されているウィンドウ*への参照、*所有者ウィンドウ*します。 これを次の例に示します。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 所有権が確立されると、次のようになります。  
  
-   所有されているウィンドウの値を調べることによって、オーナー ウィンドウを参照できる、<xref:System.Windows.Window.Owner%2A>プロパティ。  
  
-   オーナー ウィンドウの値を調べることによって、所有するすべての windows を検出できるその<xref:System.Windows.Window.OwnedWindows%2A>プロパティ。  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a>ウィンドウのアクティブ化の防止  
 Windows アクティブにしないインターネット メッセンジャー スタイルのアプリケーションの対話ウィンドウや、電子メール アプリケーションの通知ウィンドウなど、表示するときにシナリオがあります。  
  
 設定することがウィンドウに表示するときにアクティブにすることはできませんが、アプリケーションの場合は、その<xref:System.Windows.Window.ShowActivated%2A>プロパティを`false`呼び出す前に、<xref:System.Windows.Window.Show%2A>初めてメソッド。 結果は次のようになります。  
  
-   ウィンドウはアクティブになりません。  
  
-   ウィンドウの<xref:System.Windows.Window.Activated>イベントは発生しません。  
  
-   現在アクティブなウィンドウは、アクティブのままです。  
  
 ただし、ユーザーがクライアント領域または非クライアント領域をクリックすると、ウィンドウは直ちにアクティブになります。 この場合、次のようになります。  
  
-   ウィンドウはアクティブになります。  
  
-   ウィンドウの<xref:System.Windows.Window.Activated>イベントが発生します。  
  
-   直前にアクティブだったウィンドウは非アクティブになります。  
  
-   ウィンドウの<xref:System.Windows.Window.Deactivated>と<xref:System.Windows.Window.Activated>ユーザー アクションに対する応答として、その後イベントが発生します。  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a>ウィンドウのアクティブ化  
 アクティブなウィンドウがウィンドウを最初に開いたとき (表示される場合を除き、<xref:System.Windows.Window.ShowActivated%2A>設定`false`)。 *アクティブなウィンドウ*は現在キー ストロークやマウス クリックなどのユーザー入力をキャプチャしているウィンドウです。 ウィンドウがアクティブになったときに発生、<xref:System.Windows.Window.Activated>イベント。  
  
> [!NOTE]
>  最初に、ウィンドウを開いたとき、<xref:System.Windows.FrameworkElement.Loaded>と<xref:System.Windows.Window.ContentRendered>イベントが発生した後のみ、<xref:System.Windows.Window.Activated>イベントが発生します。 これを踏まえて、ウィンドウを見なすことができる効果的にとき開く<xref:System.Windows.Window.ContentRendered>が発生します。  
  
 ウィンドウがアクティブになった後で、ユーザーは同じアプリケーションの別のウィンドウをアクティブ化したり、別のアプリケーションをアクティブ化したりできます。 そのような場合は、現在アクティブなウィンドウが非アクティブ化させ、<xref:System.Windows.Window.Deactivated>イベント。 同様に、ユーザーは、現在非アクティブ化されたウィンドウを選択するときに、ウィンドウが再びアクティブと<xref:System.Windows.Window.Activated>が発生します。  
  
 処理するために一般的な理由の 1 つ<xref:System.Windows.Window.Activated>と<xref:System.Windows.Window.Deactivated>を有効にし、ウィンドウがアクティブなときにのみ実行できる機能を無効にします。 たとえば、ゲームやビデオ プレーヤーなど、ユーザーの一定の入力や介入が必要な対話型コンテンツが表示されるウィンドウがあります。 次の例は、処理する方法を示す簡単なビデオ プレーヤー<xref:System.Windows.Window.Activated>と<xref:System.Windows.Window.Deactivated>この動作を実装します。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 ウィンドウが非アクティブでも、バックグラウンドでコードを実行できる種類のアプリケーションもあります。 たとえば、メール クライアントは、ユーザーが他のアプリケーションを使用している間もメール サーバーへのポーリングを続けています。 このようなアプリケーションは、メイン ウィンドウが非アクティブのときにも、別の動作や追加の動作を頻繁に実行します。 メール プログラムでは、新しいメール アイテムを受信トレイに追加し、通知アイコンをシステム トレイに追加することがあります。 通知アイコンは、メール ウィンドウがアクティブで、調べることで確認できる場合にのみ表示必要があります、<xref:System.Windows.Window.IsActive%2A>プロパティ。  
  
 バック グラウンド タスクが完了したら場合、ウィンドウをすることが呼び出すことによってユーザーに通知する緊急<xref:System.Windows.Window.Activate%2A>メソッド。 別のアプリケーションが、ときにアクティブ化される場合は、ユーザーが対話<xref:System.Windows.Window.Activate%2A>が呼び出されると、ウィンドウのタスク バー ボタンが点滅します。 呼び出して、ユーザーは、現在のアプリケーションと対話して場合、<xref:System.Windows.Window.Activate%2A>フォア グラウンドにウィンドウが表示されます。  
  
> [!NOTE]
>  アプリケーション スコープのアクティブ化を使用して処理することができます、<xref:System.Windows.Application.Activated?displayProperty=nameWithType>と<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>イベント。  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a>ウィンドウを閉じる  
 ウィンドウの有効期間は、表示されたときに開始し、ユーザーが閉じたときに終了します。 ウィンドウを閉じるには、非クライアント領域の要素を使用します。これには、次のものが含まれます。  
  
-   **閉じる**の項目、**システム**メニュー。  
  
-   Alt キーを押しながら F4 キーを押す。  
  
-   キーを押して、**閉じる**ボタンをクリックします。  
  
 クライアント領域にさらに機構を追加してウィンドウを閉じることもできます。その一般的な例を、次に示します。  
  
-   **終了**内の項目、**ファイル**メイン アプリケーション ウィンドウの通常のメニュー。  
  
-   A**閉じる**内の項目、**ファイル**一般に、セカンダリ アプリケーション ウィンドウのメニュー。  
  
-   A**キャンセル**一般にモーダル ダイアログ ボックス、ボタンをクリックします。  
  
-   A**閉じる**一般にモードレス ダイアログ ボックス、ボタンをクリックします。  
  
 これらのカスタム機構のいずれかに対応したウィンドウを閉じるを呼び出す必要があります、<xref:System.Windows.Window.Close%2A>メソッド。 次の例を選択してウィンドウを閉じる機能を実装する、**終了**上、**ファイル**メニュー。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 ウィンドウを閉じるときに、2 つのイベントを発生させます。:<xref:System.Windows.Window.Closing>と<xref:System.Windows.Window.Closed>します。  
  
 <xref:System.Windows.Window.Closing> ウィンドウが閉じ、およびどのウィンドウによってクロージャを回避できるメカニズムを提供する前に発生します。 ウィンドウが閉じるのを防ぐのは、一般的に、ウィンドウ コンテンツに変更したデータが含まれている場合です。 このような状況で、<xref:System.Windows.Window.Closing>イベントを処理する場合は、ユーザーに、ウィンドウを閉じると、データを保存せずに続行するか、またはウィンドウを閉じるをキャンセルするかどうかを確認するため、およびデータがダーティかどうかを決定します。 次の例は、処理の重要な側面を示しています。<xref:System.Windows.Window.Closing>します。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>イベント ハンドラーに渡される、 <xref:System.ComponentModel.CancelEventArgs>、実装、 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>プロパティを設定した`true`が閉じないようにするのにします。  
  
 場合<xref:System.Windows.Window.Closing>が処理されないとウィンドウが閉じるか、処理しますが、取り消されないことができます。 ウィンドウが実際に閉じられる直前に<xref:System.Windows.Window.Closed>が発生します。 この時点で、ウィンドウが閉じるのを防ぐことはできません。  
  
> [!NOTE]
>  アプリケーションを構成して、アプリケーションのメイン ウィンドウが閉じるときに自動的をシャット ダウン (を参照してください<xref:System.Windows.Application.MainWindow%2A>) または最後のウィンドウを閉じます。 詳細については、「<xref:System.Windows.Application.ShutdownMode%2A>」を参照してください。  
  
 ウィンドウは、非クライアントおよびクライアント領域で提供される機構によって明示的に閉じることが、中にウィンドウを終了することも暗黙的に、アプリケーションの他の部分での動作の結果として、または[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]次を含みます。  
  
-   ユーザーはログオフまたはシャット ダウン Windows。  
  
-   ウィンドウのオーナーが閉じた場合 (を参照してください<xref:System.Windows.Window.Owner%2A>)。  
  
-   アプリケーションのメイン ウィンドウが閉じられると<xref:System.Windows.Application.ShutdownMode%2A>は<xref:System.Windows.ShutdownMode.OnMainWindowClose>します。  
  
-   <xref:System.Windows.Application.Shutdown%2A> が呼ばれたとき。  
  
> [!NOTE]
>  ウィンドウを閉じると、再度開くことはできません。  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a>ウィンドウの有効期間イベント  
 次の図は、ウィンドウの有効期間に主要なイベントのシーケンスを示しています。  
  
 ![ウィンドウの有効期間中にイベントを示す図。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 次の図は、ライセンス認証を行わずに表示されるウィンドウの有効期間の主要なイベントのシーケンスを示します (<xref:System.Windows.Window.ShowActivated%2A>に設定されている`false`ウィンドウが表示される前に)。  
  
 ![ライセンス認証なしのウィンドウの有効期間でイベントを示す図。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a>ウィンドウの位置  
 ウィンドウが開いているとき、ウィンドウはデスクトップに対して相対的な x ディメンションと y ディメンションの位置にあります。 この場所を調べることで確認できる、<xref:System.Windows.Window.Left%2A>と<xref:System.Windows.Window.Top%2A>プロパティ、それぞれします。 これらのプロパティを設定して、ウィンドウの位置を変更できます。  
  
 最初の場所を指定することもできます、<xref:System.Windows.Window>ときに最初に表示される設定によって、<xref:System.Windows.Window.WindowStartupLocation%2A>プロパティは、次のいずれかで<xref:System.Windows.WindowStartupLocation>列挙値。  
  
-   <xref:System.Windows.WindowStartupLocation.CenterOwner> (既定値)  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 として、初期表示位置が指定されている場合<xref:System.Windows.WindowStartupLocation.Manual>、および<xref:System.Windows.Window.Left%2A>と<xref:System.Windows.Window.Top%2A>プロパティが設定されていない、<xref:System.Windows.Window>に表示される場所の Windows を求められます。  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a>最上位ウィンドウと Z オーダー  
 ウィンドウには、x 位置と y 位置に加えて、他のウィンドウを基準にして垂直位置を決定する z ディメンションの位置もあります。 これはウィンドウの z オーダーともいい、標準 z オーダーと最上位 z オーダーの 2 種類があります。 内のウィンドウの場所、*標準 z オーダー*が現在アクティブかどうかによって決まります。 既定では、ウィンドウは標準 z オーダーにあります。 内のウィンドウの場所、*最上位 z オーダー*が現在アクティブかどうかによっても決定されます。 また、最上位 z オーダーにあるウィンドウは、常に、標準 z オーダーにあるウィンドウの上に位置します。 ウィンドウにある最上位 z オーダーを設定してその<xref:System.Windows.Window.Topmost%2A>プロパティを`true`します。  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 各 z オーダー内では、現在アクティブなウィンドウは、同じ z オーダーにある他のすべてのウィンドウの上に表示されます。  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a>ウィンドウ サイズ  
 デスクトップか所だけでなく、ウィンドウにはさまざまな幅と高さのプロパティを含む、いくつかのプロパティによって決定されるサイズと<xref:System.Windows.Window.SizeToContent%2A>します。  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.MaxWidth%2A>、ウィンドウの有効期間を持つことができ、、次の例に示すように構成される幅の範囲の管理に使用されます。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 ウィンドウの高さは、によって管理される<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Height%2A>、および<xref:System.Windows.FrameworkElement.MaxHeight%2A>の次の例に示すように構成します。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 さまざまな幅の値と高さの値はそれぞれ範囲を指定しているため、サイズを変更できるウィンドウの幅と高さは、それぞれの寸法に指定された範囲内のいずれかの値を取ります。 現在の幅と高さを検出、<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>、それぞれします。  
  
 ウィンドウのサイズに合わせたサイズのコンテンツ、ウィンドウの高さと幅が希望される場合は、使用することができます、<xref:System.Windows.Window.SizeToContent%2A>プロパティで、次の値があります。  
  
-   <xref:System.Windows.SizeToContent.Manual>. 効果 (既定値)。  
  
-   <xref:System.Windows.SizeToContent.Width>. 両方の設定と同じ効果がありますが、コンテンツの幅に合わせる<xref:System.Windows.FrameworkElement.MinWidth%2A>と<xref:System.Windows.FrameworkElement.MaxWidth%2A>コンテンツの幅にします。  
  
-   <xref:System.Windows.SizeToContent.Height>. コンテンツの高さは、両方の設定と同じ効果に合わせる<xref:System.Windows.FrameworkElement.MinHeight%2A>と<xref:System.Windows.FrameworkElement.MaxHeight%2A>コンテンツの高さにします。  
  
-   <xref:System.Windows.SizeToContent.WidthAndHeight>. コンテンツの幅と高さで、両方の設定と同じ効果<xref:System.Windows.FrameworkElement.MinHeight%2A>と<xref:System.Windows.FrameworkElement.MaxHeight%2A>、コンテンツと設定の両方の高さに<xref:System.Windows.FrameworkElement.MinWidth%2A>と<xref:System.Windows.FrameworkElement.MaxWidth%2A>コンテンツの幅にします。  
  
 次の例では、ウィンドウを最初に表示するときに、そのコンテンツに合わせて垂直方向と水平方向の両方のサイズを自動的に変更するウィンドウを示しています。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Window.SizeToContent%2A>コード ウィンドウのコンテンツに合わせてサイズ変更する方法を指定するプロパティ。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a>サイズ変更プロパティの優先順位  
 基本的に、ウィンドウのさまざまなサイズのプロパティを組み合わせて、サイズを変更できるウィンドウの幅と高さの範囲を定義します。 有効な範囲を維持すること<xref:System.Windows.Window>優先順位の次の注文を使用して、サイズ プロパティの値を評価します。  
  
 **高さのプロパティ:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **幅のプロパティ:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 最大化されたで管理されているときに、優先順位の順序はウィンドウのサイズを決定もことができます、<xref:System.Windows.Window.WindowState%2A>プロパティ。  
  
<a name="WindowState"></a>   
## <a name="window-state"></a>ウィンドウの状態  
 サイズを変更できるウィンドウには、有効期間中、通常、最小化、最大化の 3 つの状態があります。 使用してウィンドウを*通常*状態は、ウィンドウの既定の状態。 この状態のウィンドウは、サイズ変更グリップ、またはサイズ変更可能な場合は境界線を使用して、ユーザーが移動したりサイズ変更したりできます。  
  
 使用してウィンドウを*を最小限に抑える*場合、タスク バー ボタンに状態が折りたたまれます<xref:System.Windows.Window.ShowInTaskbar%2A>に設定されている`true`、それ以外の折りたたまれて、最小の可能なサイズ、デスクトップの左下隅に自動的に再配置します。 最小化されたウィンドウはいずれの種類も、境界線またはサイズ変更グリップを使用してサイズ変更できません。ただし、タスク バーに表示されていない最小化されたウィンドウはデスクトップの任意の場所にドラッグできます。  
  
 使用してウィンドウを*を最大化*状態が同じ大きさなることができます、最大サイズに拡大その<xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>と<xref:System.Windows.Window.SizeToContent%2A>プロパティが指定します。 最小化されたウィンドウと同様、最大化されたウィンドウは、サイズ変更グリップを使用したり、境界線をドラッグしたりすることによってサイズ変更できません。  
  
> [!NOTE]
>  値、 <xref:System.Windows.Window.Top%2A>、 <xref:System.Windows.Window.Left%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.Height%2A>ウィンドウのプロパティは、ウィンドウが現在最大化または最小限に抑える場合でも常に通常の状態の値を表します。  
  
 ウィンドウの状態を設定して構成できますその<xref:System.Windows.Window.WindowState%2A>プロパティで、次のいずれかの<xref:System.Windows.WindowState>列挙値。  
  
-   <xref:System.Windows.WindowState.Normal> (既定値)  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 開くときに最大化されて表示されるウィンドウを作成する方法を、次の例に示します。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 一般に、設定する必要があります<xref:System.Windows.Window.WindowState%2A>ウィンドウの初期状態を構成します。 サイズ変更可能なウィンドウが表示されると、ユーザーはウィンドウのタイトル バーにある最小化ボタン、最大化ボタン、および元に戻すボタンを使用して、ウィンドウの状態を変更できます。  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a>ウィンドウの外観  
 ウィンドウのクライアント領域の外観を変更するために、ボタン、ラベル、テキスト ボックスなど、ウィンドウ固有のコンテンツを追加します。 非クライアント領域を構成する<xref:System.Windows.Window>を含むいくつかのプロパティを提供します<xref:System.Windows.Window.Icon%2A>ウィンドウのアイコンを設定して<xref:System.Windows.Window.Title%2A>タイトルを設定します。  
  
 また、ウィンドウのサイズ変更モード、ウィンドウ スタイル、デスクトップのタスク バーにボタンとして表示するかどうかを構成して、非クライアント領域の境界線の外観と動作も変更できます。  

<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a>サイズ変更モード  
 に応じて、<xref:System.Windows.Window.WindowStyle%2A>プロパティを制御できますか (および場合) ユーザーがウィンドウのサイズを変更します。 ウィンドウ スタイルの選択に影響をユーザーには、マウスで境界線をドラッグするかどうか、ウィンドウがサイズ変更するかどうか、**最小化**、**最大化**、および**サイズを変更する**ボタン非クライアント領域に表示し、有効にするかどうか、表示される場合。  
  
 設定してウィンドウのサイズ変更する方法を構成することができます、<xref:System.Windows.Window.ResizeMode%2A>プロパティで、次のいずれかの<xref:System.Windows.ResizeMode>列挙値。  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <xref:System.Windows.ResizeMode.CanResize> (既定値)  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 同様<xref:System.Windows.Window.WindowStyle%2A>、ウィンドウのサイズ変更モードを設定することがほとんどの場合から、その有効期間中に変更する可能性がない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 ウィンドウが最大化されているかどうかを検出するので注意が最小化、および検査することによって、<xref:System.Windows.Window.WindowState%2A>プロパティ。  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a>ウィンドウ スタイル  
 ウィンドウの非クライアント領域から公開される境界線は、多くのアプリケーションに適しています。 ただし、ウィンドウの種類によって、異なる種類の境界線が必要な状況や、境界線がまったく必要ない状況があります。  
  
 ウィンドウの境界線の種類を制御するには、取得、設定したその<xref:System.Windows.Window.WindowStyle%2A>プロパティの値は次のいずれかで、<xref:System.Windows.WindowStyle>列挙体。  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <xref:System.Windows.WindowStyle.SingleBorderWindow> (既定値)  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 これらのウィンドウ スタイルの効果は、次の図に示します。  
  
 ![ウィンドウの境界線のスタイルの図。](./media/wpf-windows-overview/window-border-styles.png)  
  
 設定できる<xref:System.Windows.Window.WindowStyle%2A>いずれかを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップまたはコード ウィンドウの有効期間中に変更する可能性がないため、ほとんどの場合を構成を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>四角形以外のウィンドウ スタイル  
 境界線スタイルを設定、状況もあります<xref:System.Windows.Window.WindowStyle%2A>により満たされない場合。 たとえばなどが四角形以外の枠線でアプリケーションを作成することがあります[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]を使用します。  
  
 たとえば、次の図に示す吹き出しウィンドウがあるとします。  
  
 ![ドラッグ me. ことを示す音声バブル ウィンドウ](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 この種類のウィンドウを設定して作成できます、<xref:System.Windows.Window.WindowStyle%2A>プロパティを<xref:System.Windows.WindowStyle.None>、および特殊なを使用してサポートを<xref:System.Windows.Window>の透明度が。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 値をこの組み合わせで使用し、ウィンドウが完全に透明にレンダリングされるように設定します。 この状態では、ウィンドウの非クライアント領域の表示要素 (閉じるメニュー、最小化ボタン、最大化ボタン、元に戻すボタンなど) は使用できません。 したがって、独自の表示要素を用意する必要があります。  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a>タスク バーのプレゼンス  

ウィンドウの既定の外観には、次の図に示すように、タスク バーのボタンが含まれています。

 ![タスク バー ボタンを持つウィンドウを示すスクリーン ショット。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 ウィンドウの種類によってはメッセージ ボックスやダイアログ ボックスなどのタスク バー ボタンがない (を参照してください[ダイアログ ボックスの概要](dialog-boxes-overview.md))。 ウィンドウのタスク バー ボタンを設定して表示するかを制御することができます、<xref:System.Windows.Window.ShowInTaskbar%2A>プロパティ (`true`既定)。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a>セキュリティの考慮事項  
 <xref:System.Windows.Window> 必要があります`UnmanagedCode`インスタンス化するためのセキュリティ アクセス許可。 ローカル コンピューターにインストールされ、ローカル コンピューターから起動されるアプリケーションの場合は、アプリケーションに付与されるアクセス許可セットの範囲内になります。  
  
 ただし、これは、外からインターネットまたはローカル イントラネット ゾーンを使用して、起動されるアプリケーションに付与された権限のセット[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]します。 その結果、ユーザーが表示されます、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]セキュリティの警告と、アプリケーションの完全な信頼に設定するアクセス許可を昇格する必要があります。  
  
 さらに、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]既定でウィンドウまたはダイアログ ボックスを表示することはできません。 スタンドアロン アプリケーションのセキュリティに関する考慮事項については、次を参照してください。 [WPF のセキュリティ方針 - プラットフォーム セキュリティ](../wpf-security-strategy-platform-security.md)します。  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a>その他の種類のウィンドウ  
 <xref:System.Windows.Navigation.NavigationWindow> ナビゲート可能なコンテンツをホストするように設計されたウィンドウ。 詳細については、次を参照してください。[ナビゲーションの概要](navigation-overview.md))。  
  
 ダイアログ ボックスは、ユーザーから情報を収集して機能を完了するためによく使用されるウィンドウです。 ユーザーが、ファイルが場合など、**ファイルを開く** ダイアログ ボックスは通常、ユーザーからファイル名を取得するアプリケーションで表示されます。 詳細については、「[ダイアログ ボックスの概要](dialog-boxes-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [ダイアログ ボックスの概要](dialog-boxes-overview.md)
- [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)
