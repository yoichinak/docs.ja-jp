---
title: アプリケーション管理の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: d8e26ff197e22ffa18b4acdd020b80879023c0f7
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364094"
---
# <a name="application-management-overview"></a>アプリケーション管理の概要
すべてのアプリケーションは、アプリケーションの実装と管理に適用される機能を共有することがよくあります。 このトピックでは、アプリケーションを作成および管理<xref:System.Windows.Application>するためのクラスの機能の概要について説明します。  

## <a name="the-application-class"></a>Application クラス  
 WPF では、一般的なアプリケーションスコープの機能はクラス<xref:System.Windows.Application>にカプセル化されています。 クラス<xref:System.Windows.Application>には、次の機能が含まれています。  
  
- アプリケーションの有効期間を追跡し、相互作用する。  
  
- コマンド ライン パラメーターを取得し、処理する。  
  
- 未処理の例外を検出し、応答する。  
  
- アプリケーション スコープのプロパティと リソースを共有する。  
  
- スタンドアロン アプリケーションのウィンドウを管理する。  
  
- ナビゲーションを追跡し、管理する。  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>アプリケーションのクラスを使用して一般的なタスクを実行する方法  
 <xref:System.Windows.Application>クラスの詳細に関心がない場合は、次の表に、の<xref:System.Windows.Application>一般的なタスクとその実行方法を示します。 関連する API とトピックを表示することによって、詳細情報とサンプル コードを参照できます。  
  
|タスク|方法|  
|----------|--------------|  
|現在のアプリケーションを表すオブジェクトを取得する|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> プロパティを使用します。|  
|起動画面をアプリケーションに追加する|「[スプラッシュスクリーンを WPF アプリケーションに追加する」を](how-to-add-a-splash-screen-to-a-wpf-application.md)参照してください。|  
|アプリケーションを起動する|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> メソッドを使用します。|  
|アプリケーションを停止する|オブジェクトのメソッドを使用します。 <xref:System.Windows.Application.Shutdown%2A> <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>|  
|コマンド ラインから引数を取得する|イベントを処理し、 <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>プロパティを使用します。 <xref:System.Windows.Application.Startup?displayProperty=nameWithType> 例については、 <xref:System.Windows.Application.Startup?displayProperty=nameWithType>イベントを参照してください。|  
|アプリケーションの終了コードを取得し、設定する|イベントハンドラー <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType>のプロパティ<xref:System.Windows.Application.Shutdown%2A>を設定するか、メソッドを呼び出して整数を渡します。 <xref:System.Windows.Application.Exit?displayProperty=nameWithType>|  
|未処理の例外を検出し、応答する|イベントを<xref:System.Windows.Application.DispatcherUnhandledException>処理します。|  
|アプリケーション スコープのリソースを取得し、設定する|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> プロパティを使用します。|  
|アプリケーション スコープのリソース ディクショナリを使用する|「[アプリケーションスコープのリソースディクショナリを使用する](how-to-use-an-application-scope-resource-dictionary.md)」を参照してください。|  
|アプリケーション スコープのプロパティを取得し、設定する|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> プロパティを使用します。|  
|アプリケーションの状態を取得し、保存する|「アプリケーション[セッション全体でアプリケーションスコープのプロパティを永続化および復元](persist-and-restore-application-scope-properties.md)する」を参照してください。|  
|リソース ファイル、コンテンツ ファイル、起点ファイルなど、コード以外のデータ ファイルを管理する。|「 [WPF アプリケーションのリソースファイル、コンテンツファイル、およびデータファイル](wpf-application-resource-content-and-data-files.md)」を参照してください。|  
|スタンドアロン アプリケーションのウィンドウを管理する|「[WPF ウィンドウの概要](wpf-windows-overview.md)」を参照してください。|  
|ナビゲーションを追跡し、管理する|「[ナビゲーションの概要](navigation-overview.md)」を参照してください。|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>アプリケーション定義  
 <xref:System.Windows.Application>クラスの機能を利用するには、アプリケーション定義を実装する必要があります。 WPF アプリケーション定義は、から<xref:System.Windows.Application>派生するクラスで、特別な MSBuild 設定を使用して構成されます。  

### <a name="implementing-an-application-definition"></a>アプリケーション定義の実装  
 一般的な WPF アプリケーション定義は、マークアップと分離コードの両方を使用して実装されます。 これにより、マークアップを使用して、アプリケーションのプロパティやリソースを宣言によって設定したり、イベントを登録したりでき、分離コードでイベントを処理し、アプリケーション固有の動作を実装することができます。  
  
 次の例では、マークアップと分離コードの両方を使用してアプリケーション定義を実装する方法を示します。  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 マークアップ ファイルと分離コード ファイルを連携させるには、次のようにする必要があります。  
  
- マークアップでは`Application` 、要素に属性`x:Class`を含める必要があります。 アプリケーションがビルドされると、マークアップ`x:Class`ファイルにが存在することにより、 `partial` MSBuild はから<xref:System.Windows.Application>派生したクラスを作成し、 `x:Class`属性で指定された名前を持ちます。 そのためには、XAML スキーマ (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) の XML 名前空間宣言を追加する必要があります。
  
- 分離コードでは、クラスは、マークアップ`partial`で`x:Class`属性によって指定された名前と同じ名前を持つクラスで<xref:System.Windows.Application>ある必要があり、から派生する必要があります。 これにより、分離コードファイルは、アプリケーションのビルド`partial`時にマークアップファイル用に生成されたクラスに関連付けることができます (「 [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください)。  
  
> [!NOTE]
>  Visual Studio を使用して新しい WPF アプリケーションプロジェクトまたは WPF ブラウザーアプリケーションプロジェクトを作成すると、アプリケーション定義が既定で含まれ、マークアップと分離コードの両方を使用して定義されます。  
  
 このコードは、アプリケーション定義を実装するために最低限必要です。 ただし、アプリケーションをビルドして実行する前に、追加の MSBuild 構成をアプリケーション定義に対して行う必要があります。  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>MSBuild 用のアプリケーション定義の構成  
 スタンドアロンアプリケーションと XAML ブラウザーアプリケーション (Xbap) を実行するには、特定のレベルのインフラストラクチャを実装する必要があります。 このインフラストラクチャの最も重要な部分は、エントリ ポイントです。 ユーザーがアプリケーションを起動するとき、オペレーティング システムはエントリ ポイントを呼び出します。これは、アプリケーションを起動するための、よく知られている機能です。  
  
 従来、開発者は、テクノロジに応じて、このコードの一部または全部を自分で記述する必要がありました。 ただし、次の msbuild プロジェクトファイルに示すように、WPF は、アプリケーション定義のマークアップファイル`ApplicationDefinition`が msbuild 項目として構成されている場合に、このコードを生成します。  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 分離コードファイルはコードを含んでいるため、通常のように`Compile` MSBuild 項目としてマークされます。  
  
 これらの MSBuild 構成をアプリケーション定義のマークアップファイルと分離コードファイルに適用すると、MSBuild によって次のようなコードが生成されます。  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 生成されたコードは、アプリケーション定義に、エントリポイントメソッド`Main`を含む追加のインフラストラクチャコードを追加します。 この属性は、wpf アプリケーション`Main`のメイン UI スレッドが、wpf アプリケーションに必要な STA スレッドであることを示すために、メソッドに適用されます。 <xref:System.STAThreadAttribute> 呼び出されると`Main` 、 `InitializeComponent`メソッドを呼び出して`App`イベントを登録し、マークアップで実装されるプロパティを設定する前に、の新しいインスタンスを作成します。 が`InitializeComponent`生成されるため、および<xref:System.Windows.Window>の実装の<xref:System.Windows.Controls.Page>場合と`InitializeComponent`同様に、アプリケーション定義からを明示的に呼び出す必要はありません。 最後に、 <xref:System.Windows.Application.Run%2A>メソッドが呼び出され、アプリケーションが起動されます。  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>現在のアプリケーションの取得  
 <xref:System.Windows.Application>クラスの機能はアプリケーション全体で共有されるため、 <xref:System.Windows.Application>クラス<xref:System.AppDomain>のインスタンスは1つだけにすることができます。 これ<xref:System.Windows.Application>を強制するために、クラスはシングルトンクラスとして実装されます (「[シングルトンC#の実装](https://go.microsoft.com/fwlink/?LinkId=100567)」を参照してください)。これは、 `static`単独のインスタンスを1つ作成し、 <xref:System.Windows.Application.Current%2A>プロパティを使用して共有アクセスを提供します。  
  
 次のコードは、現在<xref:System.Windows.Application> <xref:System.AppDomain>ののオブジェクトへの参照を取得する方法を示しています。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A><xref:System.Windows.Application>クラスのインスタンスへの参照を返します。 <xref:System.Windows.Application>派生クラスへの参照が必要な場合は、次の例に示す<xref:System.Windows.Application.Current%2A>ように、プロパティの値をキャストする必要があります。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 の<xref:System.Windows.Application.Current%2A>値は、 <xref:System.Windows.Application>オブジェクトの有効期間の任意の時点で調べることができます。 ただし、注意が必要です。 クラスがインスタンス化された後、 <xref:System.Windows.Application>オブジェクトの状態に一貫性がない期間があります。 <xref:System.Windows.Application> この期間中、 <xref:System.Windows.Application>は、アプリケーションインフラストラクチャの確立、プロパティの設定、イベントの登録など、コードの実行に必要なさまざまな初期化タスクを実行します。 この期間中に<xref:System.Windows.Application>オブジェクトを使用しようとすると、設定されているさまざまな<xref:System.Windows.Application>プロパティに依存している場合は特に、予期しない結果が発生する可能性があります。  
  
 が<xref:System.Windows.Application>初期化作業を完了すると、その有効期間は実際に開始されます。  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>アプリケーションの有効期間  
 WPF アプリケーションの有効期間は、によって発生するいくつかの<xref:System.Windows.Application>イベントによってマークされます。これにより、アプリケーションが起動したとき、アクティブ化されているかどうか、およびシャットダウンされたことがわかります。  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>スプラッシュ スクリーン  
 .NET Framework 3.5 SP1 以降では、スタートアップウィンドウまたは*スプラッシュスクリーン*で使用するイメージを指定できます。 クラス<xref:System.Windows.SplashScreen>を使用すると、アプリケーションの読み込み中にスタートアップウィンドウを簡単に表示できます。 が<xref:System.Windows.SplashScreen>呼び出される前に<xref:System.Windows.Application.Run%2A> 、ウィンドウが作成されて表示されます。 詳細については、「[アプリケーションの起動時間](../advanced/application-startup-time.md)」と「[スプラッシュスクリーンを WPF アプリケーションに追加する](how-to-add-a-splash-screen-to-a-wpf-application.md)」を参照してください。  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>アプリケーションの起動  
 <xref:System.Windows.Application.Run%2A>が呼び出され、アプリケーションが初期化されると、アプリケーションを実行する準備が整います。 この瞬間は、イベントが<xref:System.Windows.Application.Startup>発生したときに示されます。  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 アプリケーションの有効期間のこの時点で、最も一般的なのは UI を表示することです。  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>ユーザー インターフェイスの表示  
 ほとんどのスタンドアロン Windows アプリケーション<xref:System.Windows.Window>は、実行の開始時にを開きます。 <xref:System.Windows.Application.Startup>イベントハンドラーは、次のコードに示すように、この操作を実行できる1つの場所です。  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  既定で<xref:System.Windows.Window>は、スタンドアロンアプリケーションで最初にインスタンス化されるがメインアプリケーションウィンドウになります。 この<xref:System.Windows.Window>オブジェクトは、 <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>プロパティによって参照されます。 最初にインスタンス化<xref:System.Windows.Application.MainWindow%2A> <xref:System.Windows.Window>されたウィンドウとは異なるウィンドウがメインウィンドウに表示される場合は、プロパティの値をプログラムで変更できます。  
  
 XBAP が最初に起動すると、最も多くの<xref:System.Windows.Controls.Page>場合、に移動します。 これを次のコードに示します。  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 を<xref:System.Windows.Application.Startup> <xref:System.Windows.Controls.Page>開くか、に移動するだけを処理する場合は、代わりにマーク`StartupUri`アップで属性を設定できます。 <xref:System.Windows.Window>  
  
 次の例は、スタンドアロンアプリケーション<xref:System.Windows.Application.StartupUri%2A>からを使用してを<xref:System.Windows.Window>開く方法を示しています。  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 次の例は、XBAP から<xref:System.Windows.Application.StartupUri%2A>を使用して<xref:System.Windows.Controls.Page>に移動する方法を示しています。  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 このマークアップは、ウィンドウを開くことについて、前のコードと同じ効果があります。  
  
> [!NOTE]
>  ナビゲーションの詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。  
  
 パラメーター化され<xref:System.Windows.Application.Startup>ていないコンストラクターを使用してインスタンス化する必要がある場合、またはイベントを表示する前にそのイベントをサブスクライブする必要がある場合、またはコマンドライン引数を処理する必要がある場合は、イベントを処理してを<xref:System.Windows.Window>開く必要があります。アプリケーションの起動時に指定された。  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>コマンド ライン引数の処理  
 Windows では、スタンドアロンアプリケーションはコマンドプロンプトまたはデスクトップから起動できます。 どちらの場合も、コマンド ライン引数をアプリケーションに渡すことができます。 次の例は、1 つのコマンド ライン引数 "/StartMinimized" を指定して起動されるアプリケーションを示しています。  
  
 `wpfapplication.exe /StartMinimized`  
  
 アプリケーションの初期化中に、WPF はオペレーティングシステムからコマンドライン引数を取得し、 <xref:System.Windows.Application.Startup> <xref:System.Windows.StartupEventArgs>パラメーターの<xref:System.Windows.StartupEventArgs.Args%2A>プロパティを使用してイベントハンドラーに渡します。 次のようなコードを使用して、コマンド ライン引数を取得し、格納することができます。  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 このコードは<xref:System.Windows.Application.Startup> **、コマンドライン**引数が指定されているかどうかを確認するためにを処理します。指定<xref:System.Windows.WindowState>さ<xref:System.Windows.WindowState.Minimized>れている場合は、のを使用してメインウィンドウを開きます。 プロパティは<xref:System.Windows.Window.WindowState%2A>プログラムによって設定する必要があるため<xref:System.Windows.Window> 、コードで main を明示的に開く必要があることに注意してください。  
  
 Xbap は ClickOnce 配置を使用して起動されるため、コマンドライン引数を取得して処理することはできません (「 [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください)。 ただし、起動に使用される URL のクエリ文字列パラメーターを取得して処理することはできます。  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>アプリケーションのアクティブ化と非アクティブ化  
 Windows では、ユーザーがアプリケーションを切り替えることができます。 最も一般的な方法は、Alt キーを押しながら Tab キーを押す方法です。 アプリケーションをに切り替えることができるのは、ユーザーが<xref:System.Windows.Window>選択できる可視性がある場合のみです。 現在選択さ<xref:System.Windows.Window>れているは*アクティブウィンドウ*( <xref:System.Windows.Window> *前面ウィンドウ*とも呼ばれます) で、はユーザー入力を受け取るです。 アクティブなウィンドウを含むアプリケーションは、*アクティブなアプリケーション*(または*フォアグラウンドアプリケーション*) です。 アプリケーションは、次の状況でアクティブ アプリケーションになります。  
  
- これが起動され、 <xref:System.Windows.Window>が表示されます。  
  
- ユーザーは、アプリケーションでを<xref:System.Windows.Window>選択することによって、別のアプリケーションから切り替えることができます。  
  
 イベントを<xref:System.Windows.Application.Activated?displayProperty=nameWithType>処理することによって、アプリケーションがアクティブになったことを検出できます。  
  
 同様に、アプリケーションは、次の状況で非アクティブになります。  
  
- ユーザーが現在のアプリケーションから別のアプリケーションに切り替えた。  
  
- アプリケーションがシャットダウンされた。  
  
 <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>イベントを処理することによって、アプリケーションが非アクティブになったことを検出できます。  
  
 次のコードは、アプリケーションがアクティブ<xref:System.Windows.Application.Activated>か<xref:System.Windows.Application.Deactivated>どうかを判断するために、イベントおよびイベントを処理する方法を示しています。  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 は<xref:System.Windows.Window> 、アクティブ化および非アクティブ化することもできます。 詳細については、「<xref:System.Windows.Window.Activated?displayProperty=nameWithType>」および「<xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
>  Xbap に対しても<xref:System.Windows.Application.Activated?displayProperty=nameWithType> が発生しません。<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>アプリケーションのシャットダウン  
 アプリケーションの有効期間は、シャット ダウンされると終了します。シャットダウンは、次の理由で発生します。  
  
- ユーザーは、すべて<xref:System.Windows.Window>のを閉じます。  
  
- ユーザーがメイン<xref:System.Windows.Window>を閉じます。  
  
- ユーザーは、ログオフまたはシャットダウンによって Windows セッションを終了します。  
  
- アプリケーション固有の条件が満たされた。  
  
 アプリケーションのシャットダウンを管理するため<xref:System.Windows.Application>に、 <xref:System.Windows.Application.Shutdown%2A>には、 <xref:System.Windows.Application.ShutdownMode%2A>メソッド、プロパティ、 <xref:System.Windows.Application.SessionEnding>および<xref:System.Windows.Application.Exit>イベントとイベントが用意されています。  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A>は、を持つ<xref:System.Security.Permissions.UIPermission>アプリケーションからのみ呼び出すことができます。 スタンドアロン WPF アプリケーションは、常にこのアクセス許可を持っています。 ただし、インターネットゾーンの部分信頼セキュリティサンドボックスで実行されている Xbap では実行されません。  
  
#### <a name="shutdown-mode"></a>シャットダウン モード  
 ほとんどのアプリケーションは、すべてのウィンドウが閉じられるか、メイン ウィンドウが閉じられたときにシャットダウンします。 ただし、場合によっては、他のアプリケーションに固有の条件によって、アプリケーションがシャット ダウンするタイミングに影響します。 <xref:System.Windows.Application.ShutdownMode%2A> 次<xref:System.Windows.ShutdownMode>のいずれかの列挙値を使用してを設定することにより、アプリケーションがシャットダウンする条件を指定できます。  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 の<xref:System.Windows.Application.ShutdownMode%2A>既定値はです<xref:System.Windows.ShutdownMode.OnLastWindowClose>。これは、アプリケーションの最後のウィンドウがユーザーによって閉じられたときに、アプリケーションが自動的にシャットダウンすることを意味します。 ただし、メインウィンドウが閉じられたときにアプリケーションをシャットダウンする必要がある場合は、をに<xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnMainWindowClose>設定すると、WPF によって自動的に起動されます。 これを次の例に示します。  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 アプリケーション固有のシャットダウン条件がある場合は、を<xref:System.Windows.Application.ShutdownMode%2A>に<xref:System.Windows.ShutdownMode.OnExplicitShutdown>設定します。 この場合、 <xref:System.Windows.Application.Shutdown%2A>メソッドを明示的に呼び出すことによってアプリケーションをシャットダウンする必要があります。それ以外の場合は、すべてのウィンドウが閉じられている場合でも、アプリケーションの実行は継続されます。 が<xref:System.Windows.ShutdownMode.OnLastWindowClose>また<xref:System.Windows.Application.Shutdown%2A> <xref:System.Windows.Application.ShutdownMode%2A> は<xref:System.Windows.ShutdownMode.OnMainWindowClose>の場合、は暗黙的に呼び出されることに注意してください。  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A>は XBAP から設定できますが、無視されます。XBAP は、ブラウザーから移動したとき、または XBAP をホストしているブラウザーを閉じたときに常にシャットダウンされます。 詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。  
  
#### <a name="session-ending"></a>セッションの終了  
 <xref:System.Windows.Application.ShutdownMode%2A>プロパティによって示されるシャットダウン条件は、アプリケーションに固有のものです。 ただし、場合によっては、アプリケーションは、外部条件の結果としてシャットダウンすることもあります。 最も一般的な外部条件は、ユーザーが次の操作によって Windows セッションを終了したときに発生します。  
  
- ログオフ  
  
- シャット ダウン  
  
- 再起動  
  
- 休止  
  
 Windows セッションが終了したことを検出するには<xref:System.Windows.Application.SessionEnding> 、次の例に示すように、イベントを処理します。  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 この例では、コードが<xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A>プロパティを調べて、Windows セッションがどのように終了しているかを確認します。 この値を使用して、ユーザーに確認メッセージを表示します。 ユーザーがセッションを終了したくない場合、コードはをに<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true`設定して、Windows セッションが終了しないようにします。  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding>Xbap に対しては発生しません。

#### <a name="exit"></a>終了  
 アプリケーションがシャット ダウンするときには、アプリケーション状態の保存など、いくつかの最終処理を実行しなければならない場合があります。 このような状況では、イベント<xref:System.Windows.Application.Exit>ハンドラーが次の`App_Exit`例に示すように、イベントを処理できます。 これは、 *app.xaml*ファイルのイベントハンドラーとして定義されます。 その実装は、 *App.xaml.cs*ファイルと*app.xaml*ファイルで強調表示されています。
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 完全な例については、「アプリケーション[セッション全体でアプリケーションスコープのプロパティを永続化および復元](persist-and-restore-application-scope-properties.md)する」を参照してください。  
  
 <xref:System.Windows.Application.Exit>は、スタンドアロンアプリケーションと Xbap の両方で処理できます。 Xbap の場合<xref:System.Windows.Application.Exit> 、は次のような状況で発生します。  
  
- XBAP は移動されません。  
  
- で[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]は、XBAP をホストしているタブが閉じられています。  
  
- ブラウザーが閉じられた。  
  
#### <a name="exit-code"></a>終了コード  
 ほとんどのアプリケーションは、ユーザー要求に応じてオペレーティング システムから起動されます。 ただし、アプリケーションは、特定のタスクを実行するために、別のアプリケーションに起動されることもあります。 起動されたアプリケーションがシャット ダウンするとき、起動元のアプリケーションは、起動されたアプリケーションのシャット ダウン条件を知ならなければならないことがあります。 このような状況では、アプリケーションがシャットダウン時にアプリケーションの終了コードを返すことができます。 既定では、WPF アプリケーションは終了コード値0を返します。  
  
> [!NOTE]
>  Visual Studio からデバッグする場合、アプリケーションの終了コードは、次のようなメッセージで、アプリケーションのシャットダウン時に**出力**ウィンドウに表示されます。  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  **[表示]** メニューの **[出力]** をクリックして、 **[出力]** ウィンドウを開きます。  
  
 終了コードを変更するには、終了コード<xref:System.Windows.Application.Shutdown%28System.Int32%29>として整数引数を受け取るオーバーロードを呼び出すことができます。  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 終了コードの値を検出し、 <xref:System.Windows.Application.Exit>イベントを処理することによって変更できます。 イベントハンドラーには、 <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A>プロパティ<xref:System.Windows.ExitEventArgs>を使用して終了コードへのアクセスを提供するが渡されます。 <xref:System.Windows.Application.Exit> 詳細については、「 <xref:System.Windows.Application.Exit> 」を参照してください。  
  
> [!NOTE]
>  終了コードは、スタンドアロンアプリケーションと Xbap の両方で設定できます。 ただし、Xbap の場合、終了コードの値は無視されます。  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>未処理の例外  
 ときには、アプリケーションは、予期しない例外がスローされたときなど、異常な条件下でシャットダウンすることがあります。 この場合、アプリケーションには、例外を検出して処理するためのコードがありません。 この種類の例外は、未処理の例外と呼ばれます。アプリケーションが閉じられる前に、次の図に示されているような通知が表示されます。  
  
 ![未処理の例外通知を示すスクリーンショット。](./media/application-management-overview/unhandled-exception-notification.png)  
  
 ユーザー エクスペリエンスの観点から、アプリケーションは、次のいずれか、またはすべてを行うことによって、この既定の動作を回避することをお勧めします。  
  
- わかりやすい情報を表示する。  
  
- アプリケーションの続行を試みる。  
  
- 開発者にとってわかりやすい例外情報を Windows イベントログに記録します。  
  
 このサポートを実装すると、ハンドルされない例外 (イベントが発生<xref:System.Windows.Application.DispatcherUnhandledException>したもの) を検出できるかどうかによって異なります。  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 イベントハンドラーには、例外<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs>自体 (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>) を含む、未処理の例外に関するコンテキスト情報を含むパラメーターが渡されます。 <xref:System.Windows.Application.DispatcherUnhandledException> この情報を使用して、例外の処理方法を決定できます。  
  
 を処理<xref:System.Windows.Application.DispatcherUnhandledException>するときは、 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType>プロパティをに`true`設定する必要があります。そうしないと、WPF は例外を未処理のままと見なし、前に説明した既定の動作に戻します。 未処理の例外が発生し<xref:System.Windows.Application.DispatcherUnhandledException> 、イベントが処理されない場合、またはイベントが<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A>処理され、 `false`がに設定されている場合、アプリケーションは直ちにシャットダウンします。 さらに、他<xref:System.Windows.Application>のイベントは発生しません。 そのため、アプリケーションがシャットダウン<xref:System.Windows.Application.DispatcherUnhandledException>する前に実行する必要があるコードがアプリケーションにあるかどうかを処理する必要があります。  
  
 アプリケーションは、未処理の例外の結果としてシャットダウンすることがありますが、通常は、次のセクションで説明されているように、ユーザーの要求に応じてシャットダウンします。  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>アプリケーションの有効期間イベント  
 スタンドアロンアプリケーションと Xbap の有効期間はまったく同じではありません。 次の図は、スタンドアロン アプリケーションの有効期間中の主なイベントと発生順を示しています。  
  
 ![スタンドアロン アプリケーション - アプリケーション オブジェクト イベント](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 同様に、次の図は、XBAP の有効期間中の主なイベントと、それらが発生する順序を示しています。  
  
 ![XBAP - アプリケーション オブジェクト イベント](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Application>
- [WPF ウィンドウの概要](wpf-windows-overview.md)
- [ナビゲーションの概要](navigation-overview.md)
- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](wpf-application-resource-content-and-data-files.md)
- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
- [アプリケーションモデル:操作方法に関するトピック](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [アプリケーションの開発](index.md)
