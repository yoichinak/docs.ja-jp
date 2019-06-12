---
title: アプリケーション管理の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: c36de23a6a49e684330fc0f47fc46bd86c55e767
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834077"
---
# <a name="application-management-overview"></a>アプリケーション管理の概要
すべてのアプリケーションは、アプリケーションの実装と管理に適用される機能を共有することがよくあります。 このトピックでは、機能の概要、<xref:System.Windows.Application>クラスを作成すると、アプリケーションを管理します。  

## <a name="the-application-class"></a>Application クラス  
 WPF では、一般的なアプリケーション スコープの機能がカプセル化された、<xref:System.Windows.Application>クラス。 <xref:System.Windows.Application>クラスには、次の機能が含まれています。  
  
- アプリケーションの有効期間を追跡し、相互作用する。  
  
- コマンド ライン パラメーターを取得し、処理する。  
  
- 未処理の例外を検出し、応答する。  
  
- アプリケーション スコープのプロパティと リソースを共有する。  
  
- スタンドアロン アプリケーションのウィンドウを管理する。  
  
- ナビゲーションを追跡し、管理する。  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>アプリケーションのクラスを使用して一般的なタスクを実行する方法  
 すべての詳細の興味のあるないかどうか、<xref:System.Windows.Application>クラス、次の表に、いくつかの一般的なタスクの一覧<xref:System.Windows.Application>とそれを実現する方法。 関連する API とトピックを表示することによって、詳細情報とサンプル コードを参照できます。  
  
|タスク|方法|  
|----------|--------------|  
|現在のアプリケーションを表すオブジェクトを取得する|<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> プロパティを使用します。|  
|起動画面をアプリケーションに追加する|参照してください[スプラッシュ スクリーンを WPF アプリケーションに追加](how-to-add-a-splash-screen-to-a-wpf-application.md)します。|  
|アプリケーションを起動する|<xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> メソッドを使用します。|  
|アプリケーションを停止する|使用して、<xref:System.Windows.Application.Shutdown%2A>のメソッド、<xref:System.Windows.Application.Current%2A?displayProperty=nameWithType>オブジェクト。|  
|コマンド ラインから引数を取得する|処理、<xref:System.Windows.Application.Startup?displayProperty=nameWithType>イベントと使用、<xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType>プロパティ。 例については、次を参照してください。、<xref:System.Windows.Application.Startup?displayProperty=nameWithType>イベント。|  
|アプリケーションの終了コードを取得し、設定する|設定、<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType>プロパティ、<xref:System.Windows.Application.Exit?displayProperty=nameWithType>イベント ハンドラーまたは呼び出し、<xref:System.Windows.Application.Shutdown%2A>メソッドと整数を渡します。|  
|未処理の例外を検出し、応答する|処理、<xref:System.Windows.Application.DispatcherUnhandledException>イベント。|  
|アプリケーション スコープのリソースを取得し、設定する|<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> プロパティを使用します。|  
|アプリケーション スコープのリソース ディクショナリを使用する|参照してください[アプリケーション スコープのリソース ディクショナリを使用する](how-to-use-an-application-scope-resource-dictionary.md)します。|  
|アプリケーション スコープのプロパティを取得し、設定する|<xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> プロパティを使用します。|  
|アプリケーションの状態を取得し、保存する|参照してください[永続化およびアプリケーション セッション全体でアプリケーション スコープのプロパティを復元](persist-and-restore-application-scope-properties.md)します。|  
|リソース ファイル、コンテンツ ファイル、起点ファイルなど、コード以外のデータ ファイルを管理する。|参照してください[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](wpf-application-resource-content-and-data-files.md)します。|  
|スタンドアロン アプリケーションのウィンドウを管理する|「[WPF ウィンドウの概要](wpf-windows-overview.md)」を参照してください。|  
|ナビゲーションを追跡し、管理する|参照してください[ナビゲーションの概要](navigation-overview.md)します。|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>アプリケーション定義  
 機能を利用する、<xref:System.Windows.Application>クラス、アプリケーション定義を実装する必要があります。 WPF アプリケーションの定義から派生したクラスは、<xref:System.Windows.Application>が特殊な MSBuild 設定で構成されているとします。  

### <a name="implementing-an-application-definition"></a>アプリケーション定義の実装  
 一般的な WPF アプリケーションの定義は、マークアップと分離コードの両方を使用して実装されます。 これにより、マークアップを使用して、アプリケーションのプロパティやリソースを宣言によって設定したり、イベントを登録したりでき、分離コードでイベントを処理し、アプリケーション固有の動作を実装することができます。  
  
 次の例では、マークアップと分離コードの両方を使用してアプリケーション定義を実装する方法を示します。  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 マークアップ ファイルと分離コード ファイルを連携させるには、次のようにする必要があります。  
  
- マークアップでは、`Application`要素を含める必要があります、`x:Class`属性。 ときに、アプリケーションがビルドが存在する`x:Class`を作成するために MSBuild を原因と、マークアップ ファイルを`partial`クラスから派生した<xref:System.Windows.Application>によって指定された名前を持つ、`x:Class`属性。 XAML スキーマの XML 名前空間宣言を追加する必要があります (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`)。
  
- 分離コード クラスがある必要があります、`partial`によって指定される同じ名前のクラス、`x:Class`マークアップ属性およびから派生する必要があります<xref:System.Windows.Application>します。 これにより、分離コード ファイルに関連付けられる、`partial`アプリケーションのビルド時にマークアップ ファイル用に生成されたクラス (を参照してください[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md))。  
  
> [!NOTE]
>  新しい WPF アプリケーション プロジェクトまたは Visual Studio を使用して WPF ブラウザー アプリケーション プロジェクトを作成するときに、アプリケーション定義は既定で含まれているし、マークアップと分離コードの両方を使用して定義されます。  
  
 このコードは、アプリケーション定義を実装するために最低限必要です。 ただし、追加の MSBuild の構成を構築してアプリケーションを実行する前にアプリケーション定義にする必要があります。  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>MSBuild 用のアプリケーション定義の構成  
 スタンドアロン アプリケーションと XAML ブラウザー アプリケーション (Xbap) に実行する前に、一定レベルのインフラストラクチャの実装が必要です。 このインフラストラクチャの最も重要な部分は、エントリ ポイントです。 ユーザーがアプリケーションを起動するとき、オペレーティング システムはエントリ ポイントを呼び出します。これは、アプリケーションを起動するための、よく知られている機能です。  
  
 従来、開発者は、テクノロジに応じて、このコードの一部または全部を自分で記述する必要がありました。 ただし、WPF このコードを生成する MSBuild として、アプリケーション定義のマークアップ ファイルが構成されている`ApplicationDefinition`項目を次の MSBuild プロジェクト ファイルに示すようにします。  
  
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
  
 MSBuild とマークされている分離コード ファイルには、コードが含まれている、ため`Compile`項目、通常は。  
  
 アプリケーション定義のマークアップと分離コード ファイルにこれらの MSBuild 構成のアプリケーションでは、次のようなコードを生成する MSBuild が発生します。  
  
 [!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
 [!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]  
  
 結果のコードは、アプリケーション定義に追加のインフラストラクチャのコードは、エントリ ポイント メソッドが含まれる`Main`します。 <xref:System.STAThreadAttribute>属性に適用されます、`Main`メソッドの WPF アプリケーションのメイン UI スレッドが STA スレッドでは WPF アプリケーションに必要であることを示します。 呼び出されると、`Main`の新しいインスタンスを作成します。`App`呼び出す前に、`InitializeComponent`マークアップでイベントが登録され、プロパティを設定するメソッドを実装します。 `InitializeComponent`が生成される、明示的に呼び出す必要はありません`InitializeComponent`と同じように、アプリケーション定義から<xref:System.Windows.Controls.Page>と<xref:System.Windows.Window>実装します。 最後に、<xref:System.Windows.Application.Run%2A>メソッドが呼び出され、アプリケーションを起動します。  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>現在のアプリケーションの取得  
 の機能、<xref:System.Windows.Application>クラスは、アプリケーション全体で共有されているのインスタンスは 1 つだけ指定できます、<xref:System.Windows.Application>あたりクラス<xref:System.AppDomain>します。 これを強制する、<xref:System.Windows.Application>クラスがシングルトン クラスとして実装されます (を参照してください[Implementing Singleton in c#](https://go.microsoft.com/fwlink/?LinkId=100567))、自体の 1 つのインスタンスを作成し、提供する共有アクセスを使って、 `static` <xref:System.Windows.Application.Current%2A>プロパティ。  
  
 次のコードへの参照を取得する方法を示しています、 <xref:System.Windows.Application> 、現在のオブジェクト<xref:System.AppDomain>します。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> インスタンスへの参照を返します、<xref:System.Windows.Application>クラス。 参照の場合、<xref:System.Windows.Application>派生クラスの値をキャストする必要があります、<xref:System.Windows.Application.Current%2A>プロパティは、次の例に示すようにします。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 値を検査する<xref:System.Windows.Application.Current%2A>の有効期間のどの時点でも、<xref:System.Windows.Application>オブジェクト。 ただし、注意が必要です。 後に、<xref:System.Windows.Application>クラスがインスタンス化は、この期間の状態、<xref:System.Windows.Application>オブジェクトに整合性がありません。 この期間中、<xref:System.Windows.Application>アプリケーション インフラストラクチャを確立、プロパティの設定、およびイベントの登録など、コードを実行するために必要なさまざまな初期化タスクを実行するがします。 使用しようとする場合、 <xref:System.Windows.Application> 、コードがあります。 この期間中、オブジェクトの予期しない結果をさまざまな依存している場合に特に<xref:System.Windows.Application>プロパティを設定します。  
  
 ときに<xref:System.Windows.Application>が初期化操作が完了するとその有効期間が実際に開始します。  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>アプリケーションの有効期間  
 WPF アプリケーションの有効期間がによって発生するいくつかのイベントによってマークされている<xref:System.Windows.Application>アプリケーションが開始したことを知らせるがアクティブ化され、非アクティブ化し、シャット ダウンされています。  

<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>スプラッシュ スクリーン  
 以降、.NET Framework 3.5 SP1 では、スタートアップ ウィンドウで、使用するイメージを指定できますまたは*スプラッシュ スクリーン*します。 <xref:System.Windows.SplashScreen>クラスでは、簡単に、アプリケーションの読み込み中に、スタートアップ ウィンドウを表示します。 <xref:System.Windows.SplashScreen>ウィンドウが作成され、表示する前に<xref:System.Windows.Application.Run%2A>が呼び出されます。 詳細については、次を参照してください。[アプリケーションの起動時間](../advanced/application-startup-time.md)と[スプラッシュ スクリーンを WPF アプリケーションに追加](how-to-add-a-splash-screen-to-a-wpf-application.md)します。  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>アプリケーションの起動  
 後<xref:System.Windows.Application.Run%2A>が呼び出されますと、アプリケーションが初期化される、アプリケーションを実行する準備ができます。 ときにこの時点で表されますが、<xref:System.Windows.Application.Startup>イベントが発生します。  
  
[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]
  
 この時点で、アプリケーションの有効期間は最も一般的なすは UI を表示します。  
  
<a name="Showing_a_User_Interface"></a>
### <a name="showing-a-user-interface"></a>ユーザー インターフェイスの表示  
 ほとんどのスタンドアロンの Windows アプリケーションを開く、<xref:System.Windows.Window>開始時期を実行します。 <xref:System.Windows.Application.Startup>次のコードに示すように、イベント ハンドラーが 1 つの場所がこれを行うことができます。  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  最初の<xref:System.Windows.Window>スタンドアロンのインスタンス化される、既定で、アプリケーションでアプリケーションのメイン ウィンドウになります。 これは、<xref:System.Windows.Window>によってオブジェクトが参照される、<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>プロパティ。 値、<xref:System.Windows.Application.MainWindow%2A>場合最初よりも、別のウィンドウにプロパティをプログラムで変更することができますをインスタンス化<xref:System.Windows.Window>メイン ウィンドウにする必要があります。  
  
 移動が多くの場合、XBAP を最初に起動するとき、<xref:System.Windows.Controls.Page>します。 これを次のコードに示します。  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 処理する場合<xref:System.Windows.Application.Startup>のみ開く、<xref:System.Windows.Window>かに移動して、<xref:System.Windows.Controls.Page>を設定することができます、`StartupUri`マークアップ属性の代わりにします。  
  
 次の例は、使用する方法を示します、<xref:System.Windows.Application.StartupUri%2A>開くためのスタンドアロン アプリケーションから、<xref:System.Windows.Window>します。  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 次の例は、使用する方法を示します<xref:System.Windows.Application.StartupUri%2A>XBAP に移動しますから、<xref:System.Windows.Controls.Page>します。  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 このマークアップは、ウィンドウを開くことについて、前のコードと同じ効果があります。  
  
> [!NOTE]
>  ナビゲーションの詳細については、次を参照してください。[ナビゲーションの概要](navigation-overview.md)します。  
  
 処理する必要がある、<xref:System.Windows.Application.Startup>を開くイベント、<xref:System.Windows.Window>既定以外のコンス トラクターを使用してインスタンス化する必要があるまたはそのプロパティを設定または表示するには、前に、そのイベントをサブスクライブする必要があるコマンドライン引数を処理する必要がある場合ですアプリケーションを起動したときに指定されました。  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>コマンド ライン引数の処理  
 、Windows では、コマンド プロンプトまたはデスクトップのいずれかからスタンドアロン アプリケーションを起動できます。 どちらの場合も、コマンド ライン引数をアプリケーションに渡すことができます。 次の例は、1 つのコマンド ライン引数 "/StartMinimized" を指定して起動されるアプリケーションを示しています。  
  
 `wpfapplication.exe /StartMinimized`  
  
 WPF、アプリケーションの初期化中に、オペレーティング システムからコマンドライン引数を取得およびコマンドを渡し、<xref:System.Windows.Application.Startup>イベント ハンドラーを使用して、<xref:System.Windows.StartupEventArgs.Args%2A>のプロパティ、<xref:System.Windows.StartupEventArgs>パラメーター。 次のようなコードを使用して、コマンド ライン引数を取得し、格納することができます。  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 コード ハンドル<xref:System.Windows.Application.Startup>を確認するかどうか、 **/StartMinimized**コマンドライン引数が指定されました。 メイン ウィンドウに開いた場合は、を<xref:System.Windows.WindowState>の<xref:System.Windows.WindowState.Minimized>します。 ため、<xref:System.Windows.Window.WindowState%2A>プロパティ プログラムでは、メイン<xref:System.Windows.Window>コードで明示的に開く必要があります。  
  
 Xbap は取得できず、ClickOnce 配置を使用して起動するためにコマンドライン引数を処理 (を参照してください[WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md))。 ただし、起動に使用される URL のクエリ文字列パラメーターを取得して処理することはできます。  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>アプリケーションのアクティブ化と非アクティブ化  
 Windows では、アプリケーションを切り替えることができます。 最も一般的な方法は、Alt キーを押しながら Tab キーを押す方法です。 表示されている場合、アプリケーションに切り替えるだけできます<xref:System.Windows.Window>項目を選択できます。 現在選択されている<xref:System.Windows.Window>は、*アクティブなウィンドウ*(とも呼ばれます、*フォア グラウンド ウィンドウ*) であり、<xref:System.Windows.Window>ユーザー入力を受け取る。 アクティブなウィンドウにアプリケーションが、*アクティブなアプリケーション*(または*フォア グラウンド アプリケーション*)。 アプリケーションは、次の状況でアクティブ アプリケーションになります。  
  
- 起動しを示しています、<xref:System.Windows.Window>します。  
  
- 選択して、ユーザーが別のアプリケーションから切り替えた、<xref:System.Windows.Window>アプリケーションにします。  
  
 処理することにより、アプリケーションがアクティブになったときに検出することができます、<xref:System.Windows.Application.Activated?displayProperty=nameWithType>イベント。  
  
 同様に、アプリケーションは、次の状況で非アクティブになります。  
  
- ユーザーが現在のアプリケーションから別のアプリケーションに切り替えた。  
  
- アプリケーションがシャットダウンされた。  
  
 処理することにより、アプリケーションが非アクティブになったときに検出することができます、<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>イベント。  
  
 次のコードを処理する方法を示しています、<xref:System.Windows.Application.Activated>と<xref:System.Windows.Application.Deactivated>アプリケーションがアクティブかどうかを確認するイベントです。  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A<xref:System.Windows.Window>アクティブおよび非アクティブ化できるはもします。 詳細については、「<xref:System.Windows.Window.Activated?displayProperty=nameWithType>」および「<xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>」を参照してください。  
  
> [!NOTE]
>  どちらも<xref:System.Windows.Application.Activated?displayProperty=nameWithType>も<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>Xbap が発生します。  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>アプリケーションのシャットダウン  
 アプリケーションの有効期間は、シャット ダウンされると終了します。シャットダウンは、次の理由で発生します。  
  
- ユーザーが閉じたすべて<xref:System.Windows.Window>します。  
  
- ユーザーがメインを閉じた<xref:System.Windows.Window>します。  
  
- ユーザーは、ログオフまたはシャット ダウンによって、Windows セッションを終了します。  
  
- アプリケーション固有の条件が満たされた。  
  
 アプリケーションのシャット ダウンの管理に役立つ<xref:System.Windows.Application>を提供します、<xref:System.Windows.Application.Shutdown%2A>メソッド、<xref:System.Windows.Application.ShutdownMode%2A>プロパティ、および<xref:System.Windows.Application.SessionEnding>と<xref:System.Windows.Application.Exit>イベント。  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> 持つアプリケーションから呼び出すことができますのみ<xref:System.Security.Permissions.UIPermission>します。 スタンドアロン WPF アプリケーションには、常に、このアクセス許可があります。 ただし、インターネット ゾーン部分信頼セキュリティ サンド ボックスで実行されている Xbap は必要ありません。  
  
#### <a name="shutdown-mode"></a>シャットダウン モード  
 ほとんどのアプリケーションは、すべてのウィンドウが閉じられるか、メイン ウィンドウが閉じられたときにシャットダウンします。 ただし、場合によっては、他のアプリケーションに固有の条件によって、アプリケーションがシャット ダウンするタイミングに影響します。 アプリケーションがシャットを設定して、条件を指定する<xref:System.Windows.Application.ShutdownMode%2A>、次のいずれかで<xref:System.Windows.ShutdownMode>列挙値。  
  
- <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 既定値<xref:System.Windows.Application.ShutdownMode%2A>は<xref:System.Windows.ShutdownMode.OnLastWindowClose>アプリケーションに自動的にシャット ダウン、ユーザーがアプリケーションの最後のウィンドウを閉じたときのことを意味します。 ただし場合は、アプリケーションはメイン ウィンドウが閉じられたときに、シャット ダウンする必要があります、WPF が自動的を設定した場合<xref:System.Windows.Application.ShutdownMode%2A>に<xref:System.Windows.ShutdownMode.OnMainWindowClose>します。 これを次の例に示します。  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 設定するときに、アプリケーション固有のシャット ダウン条件がある場合は、<xref:System.Windows.Application.ShutdownMode%2A>に<xref:System.Windows.ShutdownMode.OnExplicitShutdown>します。 明示的に呼び出すことによって、アプリケーションをシャット ダウンする必要がここで、<xref:System.Windows.Application.Shutdown%2A>メソッドです。 それ以外の場合、アプリケーションが引き続きすべてのウィンドウを閉じた場合でも実行します。 なお<xref:System.Windows.Application.Shutdown%2A>暗黙的にすると呼び出されます、<xref:System.Windows.Application.ShutdownMode%2A>か<xref:System.Windows.ShutdownMode.OnLastWindowClose>または<xref:System.Windows.ShutdownMode.OnMainWindowClose>します。  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> XBAP から設定できますが、無視されます。ブラウザーまたは XBAP をホストするブラウザーが閉じられたときから移動、ときに、常に、XBAP はシャット ダウンです。 詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。  
  
#### <a name="session-ending"></a>セッションの終了  
 によって記述されるシャット ダウン条件、<xref:System.Windows.Application.ShutdownMode%2A>プロパティは、アプリケーションに固有です。 ただし、場合によっては、アプリケーションは、外部条件の結果としてシャットダウンすることもあります。 最も一般的な外部条件は、ユーザーは、次の操作を Windows セッションを終了したときに発生します。  
  
- ログオフ  
  
- シャット ダウン  
  
- 再起動  
  
- 休止  
  
 Windows セッションが終了を検出するには、処理、<xref:System.Windows.Application.SessionEnding>イベントは、次の例に示すようにします。  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 この例で、コードの検査、 <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> Windows セッションが終了する方法を決定するプロパティ。 この値を使用して、ユーザーに確認メッセージを表示します。 ユーザーがセッションの終了をしない場合、コードが設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>に`true`Windows セッションを終了に防ぐためにします。  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> Xbap は発生しません。

#### <a name="exit"></a>終了  
 アプリケーションがシャット ダウンするときには、アプリケーション状態の保存など、いくつかの最終処理を実行しなければならない場合があります。 このような場合は、処理することができます、<xref:System.Windows.Application.Exit>イベントとして、`App_Exit`イベント ハンドラーは、次の例です。 内のイベント ハンドラーとして定義されて、 *App.xaml*ファイル。 その実装で強調表示されて、 *App.xaml.cs*と*Application.xaml.vb*ファイル。
  
[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]  
  
 [!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
 [!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]  
  
 完全な例では、次を参照してください。[を永続化およびアプリケーション セッション全体でアプリケーション スコープのプロパティを復元](persist-and-restore-application-scope-properties.md)します。  
  
 <xref:System.Windows.Application.Exit> スタンドアロン アプリケーションと Xbap の両方で処理できます。 Xbap の<xref:System.Windows.Application.Exit>は、次の状況で発生します。  
  
- XBAP はから移動します。  
  
- [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]XBAP をホストするタブが閉じられたときに、します。  
  
- ブラウザーが閉じられた。  
  
#### <a name="exit-code"></a>終了コード  
 ほとんどのアプリケーションは、ユーザー要求に応じてオペレーティング システムから起動されます。 ただし、アプリケーションは、特定のタスクを実行するために、別のアプリケーションに起動されることもあります。 起動されたアプリケーションがシャット ダウンするとき、起動元のアプリケーションは、起動されたアプリケーションのシャット ダウン条件を知ならなければならないことがあります。 このような状況では、Windows は、アプリケーションをシャット ダウン時にアプリケーション終了コードを返すをできます。 既定では、WPF アプリケーションには、終了コード値 0 が返されます。  
  
> [!NOTE]
>  アプリケーションの終了コードが表示される Visual Studio からデバッグするときに、**出力**ウィンドウで、次のようなメッセージ、アプリケーションのシャット ダウン、時。  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  開く、**出力**をクリックしてウィンドウ**出力**上、**ビュー**メニュー。  
  
 終了コードを変更するを呼び出すことができます、<xref:System.Windows.Application.Shutdown%28System.Int32%29>整数の引数の終了コードを受け取る、オーバー ロードします。  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 終了コードの値を検出して処理することにより、変更、<xref:System.Windows.Application.Exit>イベント。 <xref:System.Windows.Application.Exit>イベント ハンドラーに渡される、<xref:System.Windows.ExitEventArgs>の終了コードへのアクセスを提供する、<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A>プロパティ。 詳細については、「 <xref:System.Windows.Application.Exit> 」を参照してください。  
  
> [!NOTE]
>  終了コードは、スタンドアロン アプリケーションと Xbap の両方で設定できます。 ただし、Xbap の終了コード値が無視されます。  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>未処理の例外  
 ときには、アプリケーションは、予期しない例外がスローされたときなど、異常な条件下でシャットダウンすることがあります。 この場合、アプリケーションには、例外を検出して処理するためのコードがありません。 この種類の例外は、未処理の例外と呼ばれます。アプリケーションが閉じられる前に、次の図に示されているような通知が表示されます。  
  
 ![ハンドルされない例外通知を示すスクリーン ショット。](./media/application-management-overview/unhandled-exception-notification.png)  
  
 ユーザー エクスペリエンスの観点から、アプリケーションは、次のいずれか、またはすべてを行うことによって、この既定の動作を回避することをお勧めします。  
  
- わかりやすい情報を表示する。  
  
- アプリケーションの続行を試みる。  
  
- 記録なは、Windows イベント ログの開発者にとって使いやすい例外情報。  
  
 これはどのような未処理の例外を検出できることに依存このサポートを実装する、<xref:System.Windows.Application.DispatcherUnhandledException>のイベントが発生します。  
  
[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException>イベント ハンドラーに渡される、<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs>例外自体を含め、未処理の例外に関するコンテキスト情報を含むパラメーター (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>)。 この情報を使用して、例外の処理方法を決定できます。  
  
 処理するときに<xref:System.Windows.Application.DispatcherUnhandledException>を設定する必要があります、<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType>プロパティを`true`、それ以外の WPF は引き続き例外を処理できないし、前に説明した既定の動作に戻ります。 ハンドルされない例外が発生した場合、どちらか、<xref:System.Windows.Application.DispatcherUnhandledException>イベントが処理されない、またはイベントを処理し、<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A>に設定されている`false`アプリケーションがすぐにシャット ダウンします。 さらに、他の<xref:System.Windows.Application>イベントが発生します。 そのため、処理する必要があります<xref:System.Windows.Application.DispatcherUnhandledException>場合は、アプリケーションがあるコードをアプリケーションがシャット ダウンする前に実行する必要があります。  
  
 アプリケーションは、未処理の例外の結果としてシャットダウンすることがありますが、通常は、次のセクションで説明されているように、ユーザーの要求に応じてシャットダウンします。  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>アプリケーションの有効期間イベント  
 Xbap のスタンドアロン アプリケーションとまったく同じ有効期間はありません。 次の図は、スタンドアロン アプリケーションの有効期間中の主なイベントと発生順を示しています。  
  
 ![スタンドアロン アプリケーション - アプリケーション オブジェクト イベント](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 同様に、次の図は、XBAP の有効期間における主なイベントを示していて、発生するシーケンスを示しています。  
  
 ![XBAP - アプリケーション オブジェクト イベント](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Application>
- [WPF ウィンドウの概要](wpf-windows-overview.md)
- [ナビゲーションの概要](navigation-overview.md)
- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](wpf-application-resource-content-and-data-files.md)
- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
- [アプリケーション モデル:操作方法に関するトピック](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [アプリケーションの開発](index.md)
