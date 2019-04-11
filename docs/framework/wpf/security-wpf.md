---
title: セキュリティ (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: 968913a52a1d86746498aed7c97b63594d346a31
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313568"
---
# <a name="security-wpf"></a>セキュリティ (WPF)
<a name="introduction"></a> Windows Presentation Foundation (WPF) スタンドアロン アプリケーションとブラウザーによってホストされるアプリケーションを開発する場合は、セキュリティ モデルを検討する必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 無制限のアクセス許可を持つスタンドアロン アプリケーションの実行 ( [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] **FullTrust**アクセス許可セット) Windows インストーラー (.msi)、XCopy を使用してデプロイするかどうか、または[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]します。 部分的に信頼されたスタンドアロンの WPF アプリケーションを ClickOnce で展開することはサポートされていません。 ただし、完全に信頼されたホスト アプリケーションは部分的に信頼を作成できます<xref:System.AppDomain>.NET Framework アドイン モデルを使用します。 詳細については、次を参照してください。 [WPF アドインの概要](./app-development/wpf-add-ins-overview.md)します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ブラウザーでホストされるアプリケーションがによってホストされる[!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)]Firefox、またはいずれかを指定できます[!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]または loose[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)]詳細については、ドキュメントを参照してください[WPF XAML ブラウザー アプリケーションの概要](./app-development/wpf-xaml-browser-applications-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ブラウザーでホストされるアプリケーションが既定では、既定値に制限されていますが、部分信頼セキュリティ サンド ボックス内で実行[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]**インターネット**ゾーン アクセス許可セット。 これを効果的に分離[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]分離する一般的な Web アプリケーションが予想と同様に、クライアント コンピューターからブラウザーでホストされるアプリケーション。 XBAP は、デプロイメント URL およびクライアントのセキュリティ構成のセキュリティ ゾーンに基づいて、完全な信頼まで特権を昇格することができます。 詳細については、次を参照してください。 [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)します。  
  
 このトピックでは、Windows Presentation Foundation (WPF) スタンドアロン アプリケーションとブラウザーによってホストされるアプリケーションのセキュリティ モデルについて説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [安全なナビゲーション](#SafeTopLevelNavigation)  
  
-   [Web ブラウザーのセキュリティ設定](#InternetExplorerSecuritySettings)  
  
-   [WebBrowser コントロールと機能コントロール](#webbrowser_control_and_feature_controls)  
  
-   [部分信頼クライアント アプリケーションに対する APTCA の無効化](#APTCA)  
  
-   [Loose XAML ファイルに対するサンドボックスの動作](#LooseContentSandboxing)  
  
-   [セキュリティを向上する WPF アプリケーションを開発するためのリソース](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>安全なナビゲーション  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]ナビゲーションの 2 つの種類を区別します。 アプリケーションとブラウザー。  
  
 *アプリケーション ナビゲーション*は、ブラウザーによってホストされるアプリケーション内のコンテンツ項目間のナビゲーションです。 *ブラウザー ナビゲーション*は、ブラウザー自体のコンテンツとロケーション URL を変更するナビゲーションです。 アプリケーション ナビゲーション (通常は XAML) とブラウザー ナビゲーション (通常は HTML) 間のリレーションシップは、次の図に示します。
  
 ![アプリケーションのナビゲーションとブラウザー ナビゲーション間のリレーションシップ。](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 安全と見なされるコンテンツの種類、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]に移動するが主に続くアプリケーションまたはブラウザーのナビゲーションを使用するかどうか。  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>アプリケーション ナビゲーションのセキュリティ  
 アプリケーション ナビゲーションがパックには安全と見なさ[!INCLUDE[TLA2#tla_uri](../../../includes/tla2sharptla-uri-md.md)]、4 種類のコンテンツをサポートします。  
  
|コンテンツ タイプ|説明|URI の例|  
|------------------|-----------------|-----------------|  
|リソース|ビルドの種類のプロジェクトに追加されるファイル**リソース**します。|`pack://application:,,,/MyResourceFile.xaml`|  
|Content|ビルドの種類のプロジェクトに追加されるファイル**コンテンツ**します。|`pack://application:,,,/MyContentFile.xaml`|  
|起点サイト|ビルドの種類のプロジェクトに追加されるファイル**None**します。|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|アプリケーション コード|コンパイルされたコード分離を含む XAML リソース。<br /><br /> - または -<br /><br /> ビルドの種類のプロジェクトに追加される XAML ファイル**ページ**します。|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
>  アプリケーション データ ファイルとパックの詳細については[!INCLUDE[TLA2#tla_uri#plural](../../../includes/tla2sharptla-urisharpplural-md.md)]を参照してください[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](./app-development/wpf-application-resource-content-and-data-files.md)します。  
  
 これらのコンテンツ タイプのファイルは、ユーザーまたはプログラムを使用して移動できます。  
  
-   **ユーザー ナビゲーション**。 ユーザーが移動する をクリックして、<xref:System.Windows.Documents.Hyperlink>要素。  
  
-   **プログラム ナビゲーション**。 設定して、ユーザーに関連するせず、アプリケーションに移動した、<xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>プロパティ。  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>ブラウザー ナビゲーションのセキュリティ  
 ブラウザー ナビゲーションは、次の条件の下でのみ安全と見なされます。  
  
-   **ユーザー ナビゲーション**。 ユーザーが移動する をクリックして、<xref:System.Windows.Documents.Hyperlink>メイン内にある要素<xref:System.Windows.Navigation.NavigationWindow>ではなく、入れ子になった<xref:System.Windows.Controls.Frame>。  
  
-   **ゾーン**。 移動先のコンテンツが、インターネットまたはローカル イントラネット上に存在する。  
  
-   **プロトコル**。 使用されているプロトコルが**http**、 **https**、**ファイル**、または**mailto**します。  
  
 場合、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]これらの条件に準拠していない方法でコンテンツに移動しようとしています、<xref:System.Security.SecurityException>がスローされます。  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Web ブラウザーのセキュリティ設定  
 コンピューターのセキュリティ設定によって、Web ブラウザーに付与されるアクセス権が決まります。 Web ブラウザーでは、任意のアプリケーションまたはを使用するコンポーネントが含まれています、 [WinINet](https://go.microsoft.com/fwlink/?LinkId=179379)または[UrlMon](https://go.microsoft.com/fwlink/?LinkId=179383) Api、Internet Explorer や PresentationHost.exe など。  
  
 [!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)] またはを実行する許可されている機能を構成できますメカニズムを提供します[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]次を含みます。  
  
-   .NET framework に依存するコンポーネント  
  
-   ActiveX コントロールおよびプラグイン  
  
-   ダウンロード  
  
-   [スクリプティング]  
  
-   ユーザー認証  
  
 この方法でセキュリティで保護することができる機能のコレクションがのゾーンごとに構成されている、**インターネット**、**イントラネット**、**信頼済みサイト**、および**制限付きサイト**ゾーン。 次の手順では、セキュリティ設定の構成方法について説明します。  
  
1. **[コントロール パネル]** を開きます。  
  
2. クリックして**ネットワークとインターネット** をクリックし、**インターネット オプション**します。  
  
     [インターネット オプション] ダイアログ ボックスが表示されます。  
  
3. **セキュリティ** タブで、セキュリティ設定を構成するゾーンを選択します。  
  
4. をクリックして、**レベルのカスタマイズ**ボタンをクリックします。  
  
     **セキュリティ設定** ダイアログ ボックスが表示され、選択したゾーンのセキュリティ設定を構成することができます。  
  
     ![セキュリティの設定 ダイアログ ボックスのスクリーン ショット。](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
>  [インターネット オプション] ダイアログ ボックスは、Internet Explorer から開くこともできます。 クリックして**ツール** をクリックし、**インターネット オプション**します。  
  
 以降で[!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)]、具体的には .NET Framework の次のセキュリティ設定が含まれています。  
  
-   **Loose XAML**。 コントロールかどうか[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]できますに移動し、疎[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイル。 ([有効]、[無効]、および [ダイアログを表示する] オプション)。  
  
-   **XAML ブラウザー アプリケーション**。 コントロールかどうか[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]に移動し、実行できる[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。 ([有効]、[無効]、および [ダイアログを表示する] オプション)。  
  
 既定では、これらの設定はすべて有効になっているため、**インターネット**、**ローカル イントラネット**、および**信頼済みサイト**ゾーン、および無効にするに、**制限付きサイト**ゾーン。  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>セキュリティ関連の WPF レジストリの設定  
 [インターネット オプション] から使用できるセキュリティ設定以外に、セキュリティ上重要なさまざまな WPF 機能を選択的にブロックするために次のレジストリ値を使用できます。 値は次のキーで定義されます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 設定可能な値を次の表に示します。  
  
|値名|値型|値のデータ|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|LooseXamlDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|WebBrowserDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|MediaAudioDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|MediaImageDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|MediaVideoDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
|ScriptInteropDisallow|REG_DWORD|許可しない場合は 1、許可する場合は 0。|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>WebBrowser コントロールと機能コントロール  
 WPF<xref:System.Windows.Controls.WebBrowser>コントロールは、Web コンテンツをホストするために使用できます。 WPF<xref:System.Windows.Controls.WebBrowser>コントロールが基になる WebBrowser ActiveX コントロールをラップします。 WPF では、いくつかのサポートを提供、WPF を使用すると、アプリケーションを保護するため<xref:System.Windows.Controls.WebBrowser>コントロールをホストするには、Web コンテンツが信頼されていません。 使用してアプリケーションによって直接ただし、一部のセキュリティ機能を適用する必要があります、<xref:System.Windows.Controls.WebBrowser>コントロール。 WebBrowser ActiveX コントロールの詳細については、次を参照してください。 [WebBrowser コントロールの概要とチュートリアル](https://go.microsoft.com/fwlink/?LinkId=179388)します。  
  
> [!NOTE]
>  このセクションにも当てはまります、<xref:System.Windows.Controls.Frame>を使用するための制御、 <xref:System.Windows.Controls.WebBrowser> HTML コンテンツに移動します。  
  
 場合、WPF<xref:System.Windows.Controls.WebBrowser>信頼されていない Web コンテンツをホストするコントロールを使用すると、アプリケーションは部分的に信頼を使用する必要があります<xref:System.AppDomain>悪意のある HTML スクリプト コードからアプリケーション コードを分離します。 これを使用して、アプリケーションがホストされているスクリプトと対話する場合に特に、<xref:System.Windows.Controls.WebBrowser.InvokeScript%2A>メソッドと<xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>プロパティ。 詳細については、次を参照してください。 [WPF アドインの概要](./app-development/wpf-add-ins-overview.md)します。  
  
 アプリケーションは、WPF を使用する場合<xref:System.Windows.Controls.WebBrowser>コントロール、セキュリティを強化し、攻撃を軽減する別の方法は、Internet Explorer 機能コントロールを有効にします。 機能コントロールは、Internet Explorer と WebBrowser ActiveX コントロールをホストしているアプリケーションの機能を構成するには、管理者および開発者を許可する Internet Explorer に追加される、WPF<xref:System.Windows.Controls.WebBrowser>ラップを制御します。 機能コントロールを使用して構成できる、 [CoInternetSetFeatureEnabled](https://go.microsoft.com/fwlink/?LinkId=179394)関数またはレジストリの値を変更します。 機能コントロールの詳細については、次を参照してください。[機能コントロールの概要](https://go.microsoft.com/fwlink/?LinkId=179390)と[インターネット機能コントロール](https://go.microsoft.com/fwlink/?LinkId=179392)します。  
  
 WPF を使用するスタンドアロン WPF アプリケーションを開発しているかどうか<xref:System.Windows.Controls.WebBrowser>コントロール、WPF は、次の機能、アプリケーションのコントロールを自動的に有効にします。  
  
|機能コントロール|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 これらの機能コントロールは無条件で有効になるため、完全信頼アプリケーションに悪影響が及ぶ場合があります。 この場合、特定のアプリケーションとそのアプリケーションがホストしているコンテンツにセキュリティ上のリスクがなければ、対応する機能コントロールを無効にできます。  
  
 機能コントロールは、WebBrowser ActiveX オブジェクトをインスタンス化するプロセスで適用されます。 そのため、信頼されていないコンテンツに移動できるスタンドアロン アプリケーションを作成する場合は、その他の機能コントロールを有効にすることを検討すべきです。  
  
> [!NOTE]
>  この推奨事項は、MSHTML および SHDOCVW ホスト セキュリティの一般的な推奨事項に基づいています。 詳細については、次を参照してください[The MSHTML Host Security FAQ:。パート I of II](https://go.microsoft.com/fwlink/?LinkId=179396)と[MSHTML ホスト セキュリティ FAQ:パート II of II](https://go.microsoft.com/fwlink/?LinkId=179415)します。  
  
 実行可能ファイルでは、レジストリ値を 1 に設定して以下の機能コントロールを有効にすることを検討してください。  
  
|機能コントロール|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 実行可能ファイルでは、レジストリ値を 0 に設定して以下の機能コントロールを無効にすることを検討してください。  
  
|機能コントロール|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 部分的に信頼を実行する場合[!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)]を含む、WPF<xref:System.Windows.Controls.WebBrowser>制御[!INCLUDE[TLA#tla_iegeneric](../../../includes/tlasharptla-iegeneric-md.md)]WPF、Internet Explorer プロセスのアドレス空間で WebBrowser ActiveX コントロールをホストします。 WebBrowser ActiveX コントロールがでホストされているため、[!INCLUDE[TLA2#tla_iegeneric](../../../includes/tla2sharptla-iegeneric-md.md)]プロセスでは、WebBrowser ActiveX コントロールのすべての Internet Explorer の機能コントロールも有効にします。  
  
 Internet Explorer で実行されている XBAP にも、標準のスタンドアロン アプリケーションよりも高いレベルのセキュリティが適用されます。 この追加のセキュリティは Internet Explorer、およびそのため、WebBrowser ActiveX コントロールで実行されるため保護モードは既定で[!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]と[!INCLUDE[win7](../../../includes/win7-md.md)]します。 保護モードの詳細については、次を参照してください。[を理解すると、保護モードの Internet Explorer での作業](https://go.microsoft.com/fwlink/?LinkId=179393)します。  
  
> [!NOTE]
>  WPF を含む XBAP を実行しようとするかどうかは<xref:System.Windows.Controls.WebBrowser>firefox の場合、インターネット ゾーン内のコントロール、<xref:System.Security.SecurityException>がスローされます。 これは、WPF セキュリティ ポリシーが原因です。  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>部分信頼クライアント アプリケーションに対する APTCA の無効化  
 マネージ アセンブリがインストールされている場合、[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]ユーザーがそれらをインストールする明示的なアクセス許可を提供する必要がありますので、完全に信頼されたなります。 完全に信頼されているため、これらを使用できるのは完全信頼マネージド クライアント アプリケーションのみです。 部分的に信頼されたアプリケーションが使用するためでマークする必要があります、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA)。 この属性は、部分信頼で実行しても安全であるとテストで確認されたアセンブリだけに設定します。  
  
 ただし、APTCA アセンブリにインストールされた後、セキュリティ上の欠陥が発生することは、[!INCLUDE[TLA2#tla_gac](../../../includes/tla2sharptla-gac-md.md)]します。 セキュリティ上の欠陥が検出されたら、アセンブリの発行者は、既存のインストールでの問題を解決し、問題発見後に発生する可能性があるインストールに備えるため、セキュリティ更新プログラムを作成できます。 更新プログラムの 1 つのオプションとして、アセンブリのアンインストールが考えられますが、その場合はこのアセンブリを使用する他の完全信頼クライアント アプリケーションを破損するおそれがあります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 部分的な信頼、APTCA アセンブリを無効にできますメカニズムを提供します[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]APTCA アセンブリをアンインストールせずにします。  
  
 APTCA アセンブリを無効にするには、特殊なレジストリ キーを作成する必要があります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 次のコードは一例を示しています。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 このキーにより、APTCA アセンブリのエントリが設定されます。 また、アセンブリを有効または無効にする値をこのキーに作成する必要があります。 値の詳細を次に示します。  
  
-   値の名前:**APTCA_FLAG**します。  
  
-   値の種類:**REG_DWORD**します。  
  
-   値のデータ:**1** ; を無効にするには**0**有効にします。  
  
 部分信頼クライアント アプリケーションに対してアセンブリを無効にする必要がある場合は、レジストリ キーおよび値を作成する更新プログラムを作成します。  
  
> [!NOTE]
>  .NET Framework のコア アセンブリには、マネージ アプリケーションを実行するために必要であるために、この方法で無効にしては受けません。 APTCA アセンブリの無効化のサポートは、主にサードパーティ アプリケーションを対象にしたものです。  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Loose XAML ファイルに対するサンドボックスの動作  
 Loose[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイルは、分離コード、イベント ハンドラー、またはアプリケーション固有のアセンブリに依存しないマークアップのみの XAML ファイルです。 ときに失わ[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ブラウザーから直接ファイルに移動、既定のインターネット ゾーン アクセス許可セットに基づいてセキュリティ サンド ボックスに読み込まれます。  
  
 ただし、セキュリティ動作は異なる場合は、疎[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]からいずれかのファイルに移動、<xref:System.Windows.Navigation.NavigationWindow>または<xref:System.Windows.Controls.Frame>スタンドアロン アプリケーションでします。  
  
 どちらの場合も、loose[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]にナビゲートするファイルは、ホスト アプリケーションのアクセス許可を継承します。 ただし、この動作できない可能性があります、緩やかな場合は特に、セキュリティの観点から望ましく[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイルは、信頼されていないか、不明なエンティティが作成されました。 この種類のコンテンツと呼ばれる*外部コンテンツ*、両方と<xref:System.Windows.Controls.Frame>と<xref:System.Windows.Navigation.NavigationWindow>に移動したときに分離することができます。 設定して隔離、 **SandboxExternalContent**プロパティを true に次の例で示すように<xref:System.Windows.Controls.Frame>と<xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 このように設定すると、外部コンテンツは、アプリケーションをホストするプロセスとは異なるプロセスに読み込まれます。 このプロセスは既定のインターネット ゾーン アクセス許可セットに限定されており、ホスト アプリケーションとクライアント コンピューターから外部コンテンツを効果的に分離します。  
  
> [!NOTE]
>  でもへのナビゲーション[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]からいずれかのファイル、<xref:System.Windows.Navigation.NavigationWindow>または<xref:System.Windows.Controls.Frame>スタンドアロンのアプリケーションが実装されている、PresentationHost プロセスに関連するインフラストラクチャをホストする WPF のブラウザーに基づくセキュリティ レベルとはInternet Explorer で直接、コンテンツが読み込まれるときによりも若干小さい[!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)]と[!INCLUDE[win7](../../../includes/win7-md.md)](これもよい presentationhost)。 これは、Web ブラウザーを使用しているスタンドアロン WPF アプリケーションに、Internet Explorer の保護モード セキュリティ機能が追加されていないためです。  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>セキュリティを向上する WPF アプリケーションを開発するためのリソース  
 次にその他のリソースの開発に役立つ[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]セキュリティを向上するアプリケーション。  
  
|区分|リソース|  
|----------|--------------|  
|マネージド コード|[パターンとプラクティス アプリケーション セキュリティ ガイダンス インデックス](https://go.microsoft.com/fwlink/?LinkId=117426)|  
|[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]|[コード アクセス セキュリティ](../misc/code-access-security.md)|  
|[!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)]|[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)|  
|[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]|[WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>関連項目

- [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [WPF のセキュリティ方針 - セキュリティ エンジニアリング](wpf-security-strategy-security-engineering.md)
- [パターンとプラクティス アプリケーション セキュリティ ガイダンス インデックス](https://go.microsoft.com/fwlink/?LinkId=117426)
- [コード アクセス セキュリティ](../misc/code-access-security.md)
- [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML の概要 (WPF)](./advanced/xaml-overview-wpf.md)
