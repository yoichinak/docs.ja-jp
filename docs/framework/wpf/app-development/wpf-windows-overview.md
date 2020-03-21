---
title: ウィンドウの概要
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
ms.openlocfilehash: b06afb56f43a874815cf9f679f1f7fefbdfd4565
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145541"
---
# <a name="wpf-windows-overview"></a>WPF ウィンドウの概要
ユーザーは、ウィンドウを介して Windows プレゼンテーションファンデーション (WPF) スタンドアロン アプリケーションと対話します。 ウィンドウの主な目的は、データを視覚化してユーザーがデータと対話できるコンテンツをホストすることです。 スタンドアロン WPF アプリケーションは、クラスを使用して<xref:System.Windows.Window>独自のウィンドウを提供します。 このトピックでは<xref:System.Windows.Window>、スタンドアロン アプリケーションでのウィンドウの作成と管理の基本について説明する前に説明します。  
  
> [!NOTE]
> XAML ブラウザー アプリケーション (XBaps) や緩い[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページを含む、ブラウザーでホストされる WPF アプリケーションは、独自のウィンドウを提供しません。 代わりに、Windows インターネット エクスプローラによって提供されるウィンドウでホストされます。 [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)を参照してください。  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>ウィンドウ クラス  
 次の図は、ウィンドウの構成要素を示しています。  
  
 ![ウィンドウ要素を示すスクリーンショット。](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 ウィンドウは、非クライアント領域とクライアント領域の 2 つに分かれます。  
  
 ウィンドウ*の非クライアント領域*は WPF によって実装され、次のようなほとんどのウィンドウに共通のウィンドウの部分が含まれています。  
  
- 境界線。  
  
- タイトル バー。  
  
- アイコン。  
  
- 最小化ボタン、最大化ボタン、および元に戻すボタン。  
  
- 閉じるボタン。  
  
- ウィンドウを最小化、最大化、元のサイズに戻す、移動、サイズ変更、および閉じるためのメニュー項目を含むシステム メニュー。  
  
 ウィンドウの*クライアント領域*は、ウィンドウの非クライアント領域内の領域であり、メニュー バー、ツール バー、コントロールなどのアプリケーション固有のコンテンツを追加するために開発者によって使用されます。  
  
 WPF では、ウィンドウは、次の操作<xref:System.Windows.Window>を行うために使用するクラスによってカプセル化されます。  
  
- ウィンドウを表示する。  
  
- ウィンドウのサイズ、位置、および外観を構成する。  
  
- アプリケーション固有のコンテンツをホストする。  
  
- ウィンドウの有効期間を管理する。  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>ウィンドウの実装  
 一般的なウィンドウの実装は、外観と動作の両方で構成され、*外観*は、ユーザーに対するウィンドウの外観を定義し、*ユーザー*がウィンドウを操作する方法を定義します。 WPF では、コードまたは[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップを使用して、ウィンドウの外観と動作を実装できます。  
  
 ただし、一般的に、ウィンドウの外観はマークアップを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]実装され、次の例に示すように、その動作は分離コードを使用して実装されます。  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 マークアップ ファイル[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と分離コード ファイルを連携して動作させるには、次の項目が必要です。  
  
- マークアップでは、要素`Window`に属性を`x:Class`含める必要があります。 アプリケーションがビルドされると、マークアップ ファイルに`x:Class`のが存在すると、Microsoft ビルド エンジン (MSBuild) は、属性<xref:System.Windows.Window>で指定された派生した名前を持つ`x:Class``partial`クラスを作成します。 そのためには、スキーマ ( )[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`の XML 名前空間宣言を追加する必要があります。 生成された`partial`クラスは、イベント`InitializeComponent`を登録し、マークアップで実装されるプロパティを設定するために呼び出されるメソッドを実装します。  
  
- 分離コードでは、クラスは、マークアップの属性`partial`で指定されている名前と同じ名前の`x:Class`クラスである必要があり、派生<xref:System.Windows.Window>元である必要があります。 これにより、アプリケーションのビルド時にマークアップ ファイル用に`partial`生成されるクラスに分離コード ファイルを関連付けられます[(WPF アプリケーションのビルドを](building-a-wpf-application-wpf.md)参照)。  
  
- 分離コードでは、クラスは<xref:System.Windows.Window>メソッドを呼び出すコンストラクターを`InitializeComponent`実装する必要があります。 `InitializeComponent`は、イベントを登録し、マークアップで定義`partial`されているプロパティを設定するために、マークアップ ファイルの生成されたクラスによって実装されます。  
  
> [!NOTE]
> Visual Studio を<xref:System.Windows.Window>使用して新しいプロジェクトを追加すると、<xref:System.Windows.Window>マークアップと分離コードの両方を使用して が実装され、ここで説明するようにマークアップ ファイルと分離コード ファイル間の関連付けを作成するために必要な構成が含まれます。  
  
 この構成を適切に行えば、マークアップで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のウィンドウの外観を定義し、その動作を分離コードに実装することに集中できます。 次の例は、マークアップで実装されたボタンと、コード[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ビハインドで実装されたボタンの<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラーを持つウィンドウを示しています。  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>MSBuild 用のウィンドウ定義の構成  
 ウィンドウの実装方法によって、MSBuild の構成方法が決まります。 マークアップと分離コードの両方[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して定義されるウィンドウの場合:  
  
- XAML マークアップ ファイルは MSBuild`Page`項目として構成されます。  
  
- 分離コード ファイルは MSBuild`Compile`項目として構成されます。  
  
 これは、次の MSBuild プロジェクト ファイルに示されています。  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 WPF アプリケーションのビルドについては、「 WPF アプリケーション[のビルド](building-a-wpf-application-wpf.md)」を参照してください。  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>ウィンドウの有効期間  
 クラスと同様に、ウィンドウにも有効期間があります。有効期間は、ウィンドウが開いて最初にインスタンス化されたときに開始し、アクティブ化と非アクティブ化を経て、最後に閉じられるまで継続します。  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>ウィンドウを開く  
 ウィンドウを開くには、次の例に示すように最初にインスタンスを作成します。  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 この例では、`MarkupAndCodeBehindWindow`アプリケーションの起動時に インスタンス化され、イベントが発生したときに発生<xref:System.Windows.Application.Startup>します。  
  
 ウィンドウがインスタンス化されると、そのウィンドウへの参照がオブジェクトによって管理されるウィンドウのリストに自動的に<xref:System.Windows.Application>追加されます (「」を<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>参照)。 さらに、インスタンス化される最初のウィンドウは、既定ではメイン アプリケーション ウィンドウ<xref:System.Windows.Application>として設定されます ( を<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>参照してください )。  
  
 このウィンドウは、メソッドを呼び<xref:System.Windows.Window.Show%2A>出して最終的に開きます。結果を次の図に示します。  
  
 ![ウィンドウを呼び出して開いたウィンドウ。](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 呼び出し<xref:System.Windows.Window.Show%2A>によって開かれるウィンドウはモードレス ウィンドウであり、これは、ユーザーが同じアプリケーション内の他のウィンドウをアクティブにできるモードで動作することを意味します。  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>は、ダイアログ ボックスなどのウィンドウをモーダルに開くために呼び出されます。 詳細については、[ダイアログ ボックスの概要](dialog-boxes-overview.md)を参照してください。  
  
 呼<xref:System.Windows.Window.Show%2A>び出されると、ウィンドウは、ユーザー入力を受信できるインフラストラクチャを確立するために示される前に、初期化作業を実行します。 ウィンドウが初期化されると、<xref:System.Windows.Window.SourceInitialized>イベントが発生し、ウィンドウが表示されます。  
  
 ショートカットとして、<xref:System.Windows.Application.StartupUri%2A>アプリケーションの起動時に自動的に開く最初のウィンドウを指定するように設定できます。  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 アプリケーションが起動すると、 の<xref:System.Windows.Application.StartupUri%2A>値で指定されたウィンドウがモードレスで開かれます。内部的には、ウィンドウはメソッドを<xref:System.Windows.Window.Show%2A>呼び出すことによって開かれます。  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>ウィンドウの所有権  
 <xref:System.Windows.Window.Show%2A>メソッドを使用して開いたウィンドウは、そのウィンドウを作成したウィンドウと暗黙的に関係を持っていません。ユーザーはどちらかのウィンドウを別のウィンドウとは独立して操作できるため、どちらかのウィンドウで次の操作を実行できます。  
  
- もう一方のウィンドウを覆います (一<xref:System.Windows.Window.Topmost%2A>方のウィンドウ`true`のプロパティが に設定されている場合を除く)。  
  
- もう一方のウィンドウに影響を与えずに、最小化/最大化し、元のサイズに戻す。  
  
 一部のウィンドウには、そのウィンドウを開いたウィンドウとの関係が必要です。 たとえば、統合開発環境 (IDE) アプリケーションは、プロパティ ウィンドウと、それらを作成するウィンドウをカバーする一般的な動作を持つツール ウィンドウを開く可能性があります。 また、そのようなウィンドウは、必ず作成元のウィンドウと一緒に閉じ、最小化/最大化し、元のサイズに戻す必要があります。 このような関係は、あるウィンドウを別のウィンドウ*にすることで*確立でき、*所有するウィンドウ*の<xref:System.Windows.Window.Owner%2A>プロパティを*所有者ウィンドウ*への参照で設定することで実現されます。 次の例を参照してください。  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 所有権が確立されると、次のようになります。  
  
- 所有するウィンドウは、プロパティの値を調べることによって、その所有者<xref:System.Windows.Window.Owner%2A>ウィンドウを参照できます。  
  
- 所有者ウィンドウは、プロパティの値を調べることによって、所有するすべてのウィンドウを<xref:System.Windows.Window.OwnedWindows%2A>検出できます。  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>ウィンドウのアクティブ化の防止  
 インターネットメッセンジャー形式アプリケーションの会話ウィンドウや電子メールアプリケーションの通知ウィンドウなど、ウィンドウが表示されたときにアクティブにされてはいけないシナリオがあります。  
  
 アプリケーションに、表示されたときにアクティブにする必要のあるウィンドウがある場合は、その<xref:System.Windows.Window.ShowActivated%2A>プロパティを設定してから`false`、メソッドを<xref:System.Windows.Window.Show%2A>初めて呼び出すことができます。 結果は次のようになります。  
  
- ウィンドウはアクティブになりません。  
  
- ウィンドウの<xref:System.Windows.Window.Activated>イベントは発生しません。  
  
- 現在アクティブなウィンドウは、アクティブのままです。  
  
 ただし、ユーザーがクライアント領域または非クライアント領域をクリックすると、ウィンドウは直ちにアクティブになります。 この場合、次のようになります。  
  
- ウィンドウはアクティブになります。  
  
- ウィンドウの<xref:System.Windows.Window.Activated>イベントが発生します。  
  
- 直前にアクティブだったウィンドウは非アクティブになります。  
  
- ウィンドウと<xref:System.Windows.Window.Activated>イベントは<xref:System.Windows.Window.Deactivated>、ユーザーの操作に応じて、期待どおりに発生します。  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>ウィンドウのアクティブ化  
 ウィンドウが最初に開かれると、そのウィンドウはアクティブウィンドウになります (に設定<xref:System.Windows.Window.ShowActivated%2A>されている場合`false`を除く)。 *アクティブ ウィンドウ*は、キー ストロークやマウス クリックなど、現在ユーザー入力をキャプチャしているウィンドウです。 ウィンドウがアクティブになると、イベントが発生します<xref:System.Windows.Window.Activated>。  
  
> [!NOTE]
> ウィンドウが最初に開かれたときに、 <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.Window.ContentRendered>イベントが発生した後にのみ<xref:System.Windows.Window.Activated>、 イベントと イベントが発生します。 この問題を念頭に置いて、ウィンドウが上が<xref:System.Windows.Window.ContentRendered>ったときにウィンドウを開いたと見なすことができます。  
  
 ウィンドウがアクティブになった後で、ユーザーは同じアプリケーションの別のウィンドウをアクティブ化したり、別のアプリケーションをアクティブ化したりできます。 この場合、現在アクティブなウィンドウは非アクティブになり、イベントが発生<xref:System.Windows.Window.Deactivated>します。 同様に、ユーザーが現在非アクティブになっているウィンドウを選択すると、ウィンドウが再びアクティブになり<xref:System.Windows.Window.Activated>、発生します。  
  
 一<xref:System.Windows.Window.Activated>般的な処理の理由<xref:System.Windows.Window.Deactivated>の 1 つは、ウィンドウがアクティブなときにのみ実行できる機能を有効または無効にすることです。 たとえば、ゲームやビデオ プレーヤーなど、ユーザーの一定の入力や介入が必要な対話型コンテンツが表示されるウィンドウがあります。 次の例は、この動作を処理<xref:System.Windows.Window.Activated>して<xref:System.Windows.Window.Deactivated>実装する方法を示す、簡略化されたビデオ プレーヤーです。  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 ウィンドウが非アクティブでも、バックグラウンドでコードを実行できる種類のアプリケーションもあります。 たとえば、メール クライアントは、ユーザーが他のアプリケーションを使用している間もメール サーバーへのポーリングを続けています。 このようなアプリケーションは、メイン ウィンドウが非アクティブのときにも、別の動作や追加の動作を頻繁に実行します。 メール プログラムでは、新しいメール アイテムを受信トレイに追加し、通知アイコンをシステム トレイに追加することがあります。 通知アイコンは、メール ウィンドウがアクティブでない場合にのみ表示する必要<xref:System.Windows.Window.IsActive%2A>があります。  
  
 バックグラウンド タスクが完了した場合、ウィンドウはメソッドを呼び出<xref:System.Windows.Window.Activate%2A>すことによって、より緊急にユーザーに通知する必要があります。 呼び出されたときに<xref:System.Windows.Window.Activate%2A>ユーザーがアクティブ化された別のアプリケーションと対話している場合、ウィンドウのタスク バー ボタンが点滅します。 ユーザーが現在のアプリケーションと対話している場合、呼び<xref:System.Windows.Window.Activate%2A>出しによってウィンドウがフォアグラウンドに移動します。  
  
> [!NOTE]
> および イベントを使用して、アプリケーション<xref:System.Windows.Application.Activated?displayProperty=nameWithType>スコープ<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>のアクティブ化を処理できます。  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>ウィンドウを閉じる  
 ウィンドウの有効期間は、表示されたときに開始し、ユーザーが閉じたときに終了します。 ウィンドウを閉じるには、非クライアント領域の要素を使用します。これには、次のものが含まれます。  
  
- **[システム**] メニューの [**閉じる**] 項目  
  
- Alt キーを押しながら F4 キーを押す。  
  
- **閉じる**ボタンを押します。  
  
 クライアント領域にさらに機構を追加してウィンドウを閉じることもできます。その一般的な例を、次に示します。  
  
- [**ファイル]** メニューの **[終了]** 項目で、通常はメイン のアプリケーション ウィンドウ用です。  
  
- [**ファイル]** メニューの [**閉じる**] 項目で、通常はセカンダリ アプリケーション ウィンドウで表示されます。  
  
- 通常モーダル ダイアログ ボックスの **[キャンセル]** ボタン。  
  
- 通常、モードレス ダイアログ ボックスで閉**じる**ボタン。  
  
 これらのカスタム メカニズムのいずれかに応答してウィンドウを閉じるには、<xref:System.Windows.Window.Close%2A>メソッドを呼び出す必要があります。 次の例では、[**ファイル]** メニューの **[終了]** をクリックしてウィンドウを閉じる機能を実装しています。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 ウィンドウが閉じると、<xref:System.Windows.Window.Closing>と<xref:System.Windows.Window.Closed>の 2 つのイベントが発生します。  
  
 <xref:System.Windows.Window.Closing>ウィンドウが閉じる前に発生し、ウィンドウの閉じを防ぐことができるメカニズムを提供します。 ウィンドウが閉じるのを防ぐのは、一般的に、ウィンドウ コンテンツに変更したデータが含まれている場合です。 この状況では、イベント<xref:System.Windows.Window.Closing>を処理して、データがダーティかどうかを判断し、データを保存せずにウィンドウを閉じ続けるか、またはウィンドウの閉じをキャンセルするかをユーザーに確認できます。 次の例は、処理の重要な側面<xref:System.Windows.Window.Closing>を示しています。  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 イベント<xref:System.Windows.Window.Closing>ハンドラには、<xref:System.ComponentModel.CancelEventArgs>ウィンドウを閉じないように`Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>設定`true`したプロパティを実装する が渡されます。  
  
 処理<xref:System.Windows.Window.Closing>されない場合、または処理済みでキャンセルされなかった場合は、ウィンドウが閉じます。 実際にウィンドウが閉じる直前に<xref:System.Windows.Window.Closed>、上げられます。 この時点で、ウィンドウが閉じるのを防ぐことはできません。  
  
> [!NOTE]
> メイン アプリケーション ウィンドウが閉じる (<xref:System.Windows.Application.MainWindow%2A>参照) または最後のウィンドウが閉じたときに、アプリケーションを自動的にシャットダウンするようにアプリケーションを構成できます。 詳細については、<xref:System.Windows.Application.ShutdownMode%2A> を参照してください。  
  
 非クライアント領域とクライアント領域で提供されるメカニズムを使用してウィンドウを明示的に閉じることができますが、アプリケーションまたは Windows の他の部分での動作の結果として、次のようなウィンドウを暗黙的に閉じることができます。  
  
- ユーザーがログオフするか、Windows をシャットダウンします。  
  
- ウィンドウの所有者が閉じます (を<xref:System.Windows.Window.Owner%2A>参照)。  
  
- メイン アプリケーション ウィンドウは閉<xref:System.Windows.Application.ShutdownMode%2A>じ<xref:System.Windows.ShutdownMode.OnMainWindowClose>られます。  
  
- <xref:System.Windows.Application.Shutdown%2A> が呼び出されます  
  
> [!NOTE]
> ウィンドウを閉じると、再度開くことはできません。  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>ウィンドウの有効期間イベント  
 次の図は、ウィンドウの有効期間における主要なイベントのシーケンスを示しています。  
  
 ![ウィンドウの有効期間内のイベントを示す図。](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 次の図は、アクティブ化なしで表示されるウィンドウの有効期間 (ウィンドウが表示される前に<xref:System.Windows.Window.ShowActivated%2A>`false`設定されている) の有効期間におけるプリンシパル イベントのシーケンスを示しています。  
  
 ![アクティブ化せずにウィンドウの有効期間内のイベントを示す図。](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>ウィンドウの位置  
 ウィンドウが開いているとき、ウィンドウはデスクトップに対して相対的な x ディメンションと y ディメンションの位置にあります。 この位置は、それぞれと<xref:System.Windows.Window.Left%2A><xref:System.Windows.Window.Top%2A>プロパティを検査することによって決定できます。 これらのプロパティを設定して、ウィンドウの位置を変更できます。  
  
 プロパティを次<xref:System.Windows.Window><xref:System.Windows.Window.WindowStartupLocation%2A><xref:System.Windows.WindowStartupLocation>のいずれかの列挙値で設定することで、最初に表示される a の初期位置を指定することもできます。  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (規定値)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 スタートアップの<xref:System.Windows.WindowStartupLocation.Manual>場所が に指定され、<xref:System.Windows.Window.Left%2A>プロパティ<xref:System.Windows.Window.Top%2A>が設定されていない場合は、<xref:System.Windows.Window>で表示する場所を Windows に要求します。  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>最上位ウィンドウと Z オーダー  
 ウィンドウには、x 位置と y 位置に加えて、他のウィンドウを基準にして垂直位置を決定する z ディメンションの位置もあります。 これはウィンドウの z オーダーともいい、標準 z オーダーと最上位 z オーダーの 2 種類があります。 通常の*Z オーダー*でのウィンドウの位置は、現在アクティブかどうかによって決まります。 既定では、ウィンドウは標準 z オーダーにあります。 *一番上*の z オーダーのウィンドウの位置も、現在アクティブかどうかによって決まります。 また、最上位 z オーダーにあるウィンドウは、常に、標準 z オーダーにあるウィンドウの上に位置します。 ウィンドウは、プロパティを に設定することで、最上位の z<xref:System.Windows.Window.Topmost%2A>オーダー`true`に配置されます。  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 各 z オーダー内では、現在アクティブなウィンドウは、同じ z オーダーにある他のすべてのウィンドウの上に表示されます。  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>ウィンドウ サイズ  
 ウィンドウには、デスクトップの場所があるほかに、さまざまな幅と高さのプロパティや<xref:System.Windows.Window.SizeToContent%2A>.  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>、、<xref:System.Windows.FrameworkElement.Width%2A>および<xref:System.Windows.FrameworkElement.MaxWidth%2A>は、ウィンドウの有効期間中に持つことができる幅の範囲を管理するために使用され、次の例に示すように構成されます。  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 ウィンドウの高さは<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Height%2A>、および<xref:System.Windows.FrameworkElement.MaxHeight%2A>によって管理され、次の例のように構成されます。  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 さまざまな幅の値と高さの値はそれぞれ範囲を指定しているため、サイズを変更できるウィンドウの幅と高さは、それぞれの寸法に指定された範囲内のいずれかの値を取ります。 現在の幅と高さを検出するには、<xref:System.Windows.FrameworkElement.ActualWidth%2A>それぞれ<xref:System.Windows.FrameworkElement.ActualHeight%2A>と を検査します。  
  
 ウィンドウの幅と高さをウィンドウのコンテンツのサイズに合わせて設定する場合は、次の値を<xref:System.Windows.Window.SizeToContent%2A>持つプロパティを使用できます。  
  
- <xref:System.Windows.SizeToContent.Manual>. 効果 (既定値)。  
  
- <xref:System.Windows.SizeToContent.Width>. コンテンツの幅に合わせると、コンテンツの幅と設定<xref:System.Windows.FrameworkElement.MinWidth%2A>の<xref:System.Windows.FrameworkElement.MaxWidth%2A>両方と同じ効果が得られます。  
  
- <xref:System.Windows.SizeToContent.Height>. コンテンツの高さに合わせて、コンテンツの高さの両方<xref:System.Windows.FrameworkElement.MinHeight%2A>を設定<xref:System.Windows.FrameworkElement.MaxHeight%2A>するのと同じ効果があります。  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. コンテンツの<xref:System.Windows.FrameworkElement.MinHeight%2A>幅と高さの両方を設定し、コンテンツの高さに設定<xref:System.Windows.FrameworkElement.MaxHeight%2A>し、コンテンツの幅と両方<xref:System.Windows.FrameworkElement.MinWidth%2A>を設定するの<xref:System.Windows.FrameworkElement.MaxWidth%2A>と同じ効果を持つコンテンツの幅と高さに合わせます。  
  
 次の例では、ウィンドウを最初に表示するときに、そのコンテンツに合わせて垂直方向と水平方向の両方のサイズを自動的に変更するウィンドウを示しています。  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 次の例は、コンテンツに合<xref:System.Windows.Window.SizeToContent%2A>わせてウィンドウのサイズを変更する方法を指定するコードでプロパティを設定する方法を示しています。
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>サイズ変更プロパティの優先順位  
 基本的に、ウィンドウのさまざまなサイズのプロパティを組み合わせて、サイズを変更できるウィンドウの幅と高さの範囲を定義します。 有効な範囲を維持するために、<xref:System.Windows.Window>次の優先順位を使用してサイズ プロパティの値を評価します。  
  
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
  
 優先順位は、<xref:System.Windows.Window.WindowState%2A>最大化時のウィンドウのサイズを決定することもできます。  
  
<a name="WindowState"></a>
## <a name="window-state"></a>ウィンドウの状態  
 サイズを変更できるウィンドウには、有効期間中、通常、最小化、最大化の 3 つの状態があります。 *通常*の状態のウィンドウは、ウィンドウの既定の状態です。 この状態のウィンドウは、サイズ変更グリップ、またはサイズ変更可能な場合は境界線を使用して、ユーザーが移動したりサイズ変更したりできます。  
  
 *最小化された*状態のウィンドウは、タスク バー ボタンに設定されている<xref:System.Windows.Window.ShowInTaskbar%2A>場合は折`true`りたたまれます。それ以外の場合は、可能な限り小さいサイズに縮小され、デスクトップの左下隅に移動します。 最小化されたウィンドウはいずれの種類も、境界線またはサイズ変更グリップを使用してサイズ変更できません。ただし、タスク バーに表示されていない最小化されたウィンドウはデスクトップの任意の場所にドラッグできます。  
  
 *最大化された*状態のウィンドウは、<xref:System.Windows.FrameworkElement.MaxWidth%2A><xref:System.Windows.FrameworkElement.MaxHeight%2A><xref:System.Windows.Window.SizeToContent%2A>最大サイズまで拡張されます。 最小化されたウィンドウと同様、最大化されたウィンドウは、サイズ変更グリップを使用したり、境界線をドラッグしたりすることによってサイズ変更できません。  
  
> [!NOTE]
> ウィンドウの<xref:System.Windows.Window.Top%2A>プロパティ 、、、<xref:System.Windows.Window.Left%2A>および<xref:System.Windows.FrameworkElement.Height%2A><xref:System.Windows.FrameworkElement.Width%2A>プロパティの値は、ウィンドウが現在最大化または最小化されている場合でも、常に通常の状態の値を表します。  
  
 ウィンドウの状態は、次<xref:System.Windows.Window.WindowState%2A><xref:System.Windows.WindowState>のいずれかの列挙値を持つことができるプロパティを設定することによって構成できます。  
  
- <xref:System.Windows.WindowState.Normal> (規定値)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 開くときに最大化されて表示されるウィンドウを作成する方法を、次の例に示します。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 一般に、ウィンドウの<xref:System.Windows.Window.WindowState%2A>初期状態を設定するように設定する必要があります。 サイズ変更可能なウィンドウが表示されると、ユーザーはウィンドウのタイトル バーにある最小化ボタン、最大化ボタン、および元に戻すボタンを使用して、ウィンドウの状態を変更できます。  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>ウィンドウの外観  
 ウィンドウのクライアント領域の外観を変更するために、ボタン、ラベル、テキスト ボックスなど、ウィンドウ固有のコンテンツを追加します。 非クライアント領域を構成するには、<xref:System.Windows.Window>ウィンドウのアイコンを設定したり<xref:System.Windows.Window.Icon%2A><xref:System.Windows.Window.Title%2A>、タイトルを設定したりするためのプロパティを複数提供します。  
  
 また、ウィンドウのサイズ変更モード、ウィンドウ スタイル、デスクトップのタスク バーにボタンとして表示するかどうかを構成して、非クライアント領域の境界線の外観と動作も変更できます。  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>サイズ変更モード  
 <xref:System.Windows.Window.WindowStyle%2A>プロパティに応じて、ユーザーがウィンドウのサイズを変更する方法 (およびかどうかを) 制御できます。 ウィンドウ スタイルの選択は、ユーザーがマウスで境界線をドラッグしてウィンドウのサイズを変更できるかどうか、**クライアント**以外の領域に最小化、**最大化**、**およびサイズ変更**の各ボタンを表示するかどうか、および表示される場合は有効にするかどうかに影響します。  
  
 ウィンドウのサイズを変更する方法は、次<xref:System.Windows.Window.ResizeMode%2A><xref:System.Windows.ResizeMode>のいずれかの列挙値を指定できるプロパティを設定することで構成できます。  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (規定値)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 と同様<xref:System.Windows.Window.WindowStyle%2A>に、ウィンドウのサイズ変更モードは、その有効期間中に変更される可能性が低い、つまり、マークアップから[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設定する可能性が高いことを意味します。  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 ウィンドウが最大化、最小化、または復元されているかどうかを、プロパティを調べることによって検出できることに<xref:System.Windows.Window.WindowState%2A>注意してください。  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>ウィンドウ スタイル  
 ウィンドウの非クライアント領域から公開される境界線は、多くのアプリケーションに適しています。 ただし、ウィンドウの種類によって、異なる種類の境界線が必要な状況や、境界線がまったく必要ない状況があります。  
  
 ウィンドウが取得する境界線の種類を制御するには、列挙体<xref:System.Windows.Window.WindowStyle%2A>の次のいずれかの値を使用して、その<xref:System.Windows.WindowStyle>プロパティを設定します。  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (規定値)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 これらのウィンドウ スタイルの効果を次の図に示します。  
  
 ![ウィンドウの境界線スタイルの図。](./media/wpf-windows-overview/window-border-styles.png)  
  
 マークアップまたはコード<xref:System.Windows.Window.WindowStyle%2A>を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用して設定できます。ウィンドウの有効期間中に変更される可能性は低いため、マークアップを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]構成する可能性が高くなります。  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>四角形以外のウィンドウ スタイル  
 また、境界線<xref:System.Windows.Window.WindowStyle%2A>スタイルが十分でない場合もあります。 たとえば、Microsoft Windows メディア プレーヤーが使用するような、四角形以外の境界線を持つアプリケーションを作成する場合があります。  
  
 たとえば、次の図に示す吹き出しウィンドウを考えてみましょう。  
  
 ![「ドラッグミー」と言う吹き出しウィンドウ。](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 この種類のウィンドウは、プロパティを<xref:System.Windows.Window.WindowStyle%2A>に<xref:System.Windows.WindowStyle.None>設定し、透過性を備えた特別<xref:System.Windows.Window>なサポートを使用して作成できます。  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 値をこの組み合わせで使用し、ウィンドウが完全に透明にレンダリングされるように設定します。 この状態では、ウィンドウの非クライアント領域の表示要素 (閉じるメニュー、最小化ボタン、最大化ボタン、元に戻すボタンなど) は使用できません。 したがって、独自の表示要素を用意する必要があります。  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>タスク バーのプレゼンス  

ウィンドウの既定の外観には、次の図に示すようなタスク バー ボタンが含まれています。

 ![タスク バー ボタンを持つウィンドウを示すスクリーンショット。](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 ウィンドウの種類によっては、メッセージ ボックスやダイアログ ボックスなど、タスク バー ボタンが表示されない場合があります (「[ダイアログ ボックスの概要](dialog-boxes-overview.md)」を参照)。 ウィンドウのタスク バー ボタンを表示するかどうかを制御するには、プロパティを<xref:System.Windows.Window.ShowInTaskbar%2A>設定します`true`(既定)。  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>セキュリティに関する考慮事項  
 <xref:System.Windows.Window>には`UnmanagedCode`、セキュリティアクセス許可をインスタンス化する必要があります。 ローカル コンピューターにインストールされ、ローカル コンピューターから起動されるアプリケーションの場合は、アプリケーションに付与されるアクセス許可セットの範囲内になります。  
  
 ただし、これは、ClickOnce を使用してインターネットまたはローカル イントラネット ゾーンから起動されるアプリケーションに付与されるアクセス許可のセットの範囲外です。 したがって、ユーザーは ClickOnce セキュリティ警告を受け取り、アプリケーションのアクセス許可セットを完全信頼に昇格する必要があります。  
  
 また、XBaAp は既定でウィンドウやダイアログ ボックスを表示できません。 スタンドアロン アプリケーションのセキュリティに関する考慮事項については、「 [WPF セキュリティ戦略 - プラットフォーム セキュリティ](../wpf-security-strategy-platform-security.md)」を参照してください。  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>その他の種類のウィンドウ  
 <xref:System.Windows.Navigation.NavigationWindow>は、ナビゲート可能なコンテンツをホストするように設計されたウィンドウです。 詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。  
  
 ダイアログ ボックスは、ユーザーから情報を収集して機能を完了するためによく使用されるウィンドウです。 たとえば、ユーザーがファイルを開く場合、通常はアプリケーションによって **[ファイルを開く**] ダイアログ ボックスが表示され、ユーザーからファイル名を取得します。 詳細については、「[ダイアログ ボックスの概要](dialog-boxes-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [ダイアログ ボックスの概要](dialog-boxes-overview.md)
- [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)
