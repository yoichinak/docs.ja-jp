---
title: Security
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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174616"
---
# <a name="security-wpf"></a>セキュリティ (WPF)
<a name="introduction"></a>Windows プレゼンテーション基盤 (WPF) スタンドアロンアプリケーションおよびブラウザホストアプリケーションを開発する場合は、セキュリティ モデルを考慮する必要があります。 WPF スタンドアロン アプリケーションは、Windows インストーラー (.msi)、XCopy、または ClickOnce を使用して展開されたかどうかにかかわらず、無制限のアクセス許可 (CAS**FullTrust**アクセス許可セット) で実行されます。 部分的に信頼されたスタンドアロンの WPF アプリケーションを ClickOnce で展開することはサポートされていません。 ただし、完全信頼ホスト アプリケーションは、.NET Framework<xref:System.AppDomain>アドイン モデルを使用して部分信頼を作成できます。 詳細については、「 [WPF アドインの概要](./app-development/wpf-add-ins-overview.md)」を参照してください。  
  
 WPF ブラウザーでホストされるアプリケーションは、Windows インターネット エクスプローラーまたは Firefox によってホストされ、XAML ブラウザー アプリケーション (XBaps) または緩やかな[!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)]ドキュメントのいずれかである場合があります詳細については、「 WPF XAML XAML ブラウザー[アプリケーションの概要](./app-development/wpf-xaml-browser-applications-overview.md)」を参照してください。  
  
 WPF ブラウザーでホストされるアプリケーションは、既定では、部分信頼セキュリティ サンドボックス内で実行されます。**Internet** これにより、一般的な Web アプリケーションが分離されると予想されるのと同じ方法で、WPF ブラウザーでホストされるアプリケーションをクライアント コンピューターから効果的に分離できます。 XBAP は、デプロイメント URL およびクライアントのセキュリティ構成のセキュリティ ゾーンに基づいて、完全な信頼まで特権を昇格することができます。 詳細については、「 [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)」を参照してください。  
  
 このトピックでは、Windows プレゼンテーション ファンデーション (WPF) スタンドアロン アプリケーションとブラウザー ホスト アプリケーションのセキュリティ モデルについて説明します。  
  
 このトピックには、次のセクションが含まれます。  
  
- [安全なナビゲーション](#SafeTopLevelNavigation)  
  
- [Web ブラウザーのセキュリティ設定](#InternetExplorerSecuritySettings)  
  
- [WebBrowser コントロールと機能コントロール](#webbrowser_control_and_feature_controls)  
  
- [部分信頼クライアント アプリケーションに対する APTCA の無効化](#APTCA)  
  
- [Loose XAML ファイルに対するサンドボックスの動作](#LooseContentSandboxing)  
  
- [セキュリティを向上する WPF アプリケーションを開発するためのリソース](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>安全なナビゲーション  
 XBaps の場合、WPF はアプリケーションとブラウザーの 2 種類のナビゲーションを区別します。  
  
 *アプリケーション ナビゲーション*は、ブラウザーによってホストされるアプリケーション内のコンテンツ項目間のナビゲーションです。 *ブラウザー ナビゲーション*は、ブラウザー自体のコンテンツとロケーション URL を変更するナビゲーションです。 アプリケーション ナビゲーション (通常は XAML) とブラウザー ナビゲーション (通常は HTML) の関係を次の図に示します。
  
 ![アプリケーション ナビゲーションとブラウザー ナビゲーションの関係。](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 XBAP が移動しても安全と見なされるコンテンツの種類は、主にアプリケーション ナビゲーションとブラウザー ナビゲーションのどちらを使用するかによって決まります。  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>アプリケーション ナビゲーションのセキュリティ  
 アプリケーションナビゲーションは、4 種類のコンテンツをサポートするパック URI で識別できる場合は安全であると見なされます。  
  
|コンテンツの種類|説明|URI の例|  
|------------------|-----------------|-----------------|  
|リソース|ビルドの種類が**Resource**のプロジェクトに追加されるファイル。|`pack://application:,,,/MyResourceFile.xaml`|  
|コンテンツ|ビルドの種類が **[コンテンツ]** のプロジェクトに追加されるファイル。|`pack://application:,,,/MyContentFile.xaml`|  
|起点サイト|ビルドの種類が**None**のプロジェクトに追加されるファイル。|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|アプリケーション コード|コンパイルされたコード分離を含む XAML リソース。<br /><br /> または<br /><br /> ビルドの種類が**Page**のプロジェクトに追加される XAML ファイル。|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> アプリケーション データ ファイルとパック URI の詳細については、「 [WPF アプリケーション リソース、コンテンツ、およびデータ ファイル](./app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。  
  
 これらのコンテンツ タイプのファイルは、ユーザーまたはプログラムを使用して移動できます。  
  
- **ユーザー ナビゲーション**。 ユーザーは<xref:System.Windows.Documents.Hyperlink>、要素をクリックして移動します。  
  
- **プログラム ナビゲーション**。 アプリケーションは、たとえば、プロパティを設定することによって、ユーザーを関与させることなく移動<xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>します。  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>ブラウザー ナビゲーションのセキュリティ  
 ブラウザー ナビゲーションは、次の条件の下でのみ安全と見なされます。  
  
- **ユーザー ナビゲーション**。 ユーザーは、 の入れ<xref:System.Windows.Documents.Hyperlink>子になっていませんメイン<xref:System.Windows.Navigation.NavigationWindow>内の要素をクリックして<xref:System.Windows.Controls.Frame>移動します。  
  
- **ゾーン**。 移動先のコンテンツが、インターネットまたはローカル イントラネット上に存在する。  
  
- **プロトコル**。 使用されているプロトコルは、 **http**、 **https**、**ファイル**、または**mailto**です。  
  
 XBAP がこれらの条件に準拠しない方法でコンテンツに移動しようとすると、a<xref:System.Security.SecurityException>がスローされます。  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Web ブラウザーのセキュリティ設定  
 コンピューターのセキュリティ設定によって、Web ブラウザーに付与されるアクセス権が決まります。 Web 閲覧ソフトウェアには、インターネット エクスプローラやプレゼンテーションホスト.exe など[、WinINet](/windows/win32/wininet/portal) API または[UrlMon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) API を使用するアプリケーションまたはコンポーネントが含まれます。  
  
 インターネット エクスプローラには、次のような、または Internet Explorer から実行できる機能を構成するためのメカニズムが用意されています。  
  
- .NET フレームワーク依存コンポーネント  
  
- ActiveX コントロールおよびプラグイン  
  
- ダウンロード  
  
- スクリプトの作成  
  
- ユーザー認証  
  
 この方法でセキュリティで保護できる機能のコレクションは、**ゾーンごとに、インターネット**、**イントラネット**、**信頼済みサイト**、および**制限付きサイト**ゾーンに対して構成されます。 次の手順では、セキュリティ設定の構成方法について説明します。  
  
1. **[コントロール パネル]** を開きます。  
  
2. [**ネットワークとインターネット**] をクリックし、[**インターネット オプション**] をクリックします。  
  
     [インターネット オプション] ダイアログ ボックスが表示されます。  
  
3. [**セキュリティ**] タブで、セキュリティ設定を構成するゾーンを選択します。  
  
4. [**レベルのカスタマイズ**] ボタンをクリックします。  
  
     [**セキュリティの設定]** ダイアログ ボックスが表示され、選択したゾーンのセキュリティ設定を構成できます。  
  
     ![[セキュリティの設定] ダイアログ ボックスを示すスクリーンショット。](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> [インターネット オプション] ダイアログ ボックスは、Internet Explorer から開くこともできます。 [**ツール**] をクリックし、[**インターネット オプション**] をクリックします。  
  
 Windows インターネット エクスプローラ 7 以降、.NET Framework 専用の次のセキュリティ設定が含まれています。  
  
- **Loose XAML**。 ファイルに移動したり、ファイルを削除[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]したりできるかどうかを制御します。 ([有効]、[無効]、および [ダイアログを表示する] オプション)。  
  
- **XAML ブラウザー アプリケーション**。 XBaap に移動して実行できるかどうかを制御します。 ([有効]、[無効]、および [ダイアログを表示する] オプション)。  
  
 既定では、これらの設定はすべて**インターネット**ゾーン、ローカル**イントラネット**ゾーン、**信頼済みサイト**ゾーンで有効になり、**制限付きサイト**ゾーンでは無効になっています。  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>セキュリティ関連の WPF レジストリの設定  
 [インターネット オプション] から使用できるセキュリティ設定以外に、セキュリティ上重要なさまざまな WPF 機能を選択的にブロックするために次のレジストリ値を使用できます。 値は次のキーで定義されます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 設定可能な値を次の表に示します。  
  
|値の名前|値の型|値のデータ|  
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
 WPF<xref:System.Windows.Controls.WebBrowser>コントロールを使用して、Web コンテンツをホストできます。 WPF<xref:System.Windows.Controls.WebBrowser>コントロールは、基になる WebBrowser ActiveX コントロールをラップします。 WPFWPF コントロールを使用して信頼されていない Web コンテンツを<xref:System.Windows.Controls.WebBrowser>ホストする場合、WPF ではアプリケーションのセキュリティ保護がサポートされています。 ただし、一部のセキュリティ機能は、コントロールを使用するアプリケーション<xref:System.Windows.Controls.WebBrowser>によって直接適用する必要があります。 WebBrowser ActiveX コントロールの詳細については、「 [WebBrowser コントロールの概要とチュートリアル](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85))」を参照してください。  
  
> [!NOTE]
> このセクションは、HTML<xref:System.Windows.Controls.Frame>コンテンツに移動<xref:System.Windows.Controls.WebBrowser>するために を使用するので、コントロールにも適用されます。  
  
 WPF<xref:System.Windows.Controls.WebBrowser>コントロールを使用して信頼されていない Web コンテンツをホストする場合、アプリケーションは、悪意<xref:System.AppDomain>のある HTML スクリプト コードからアプリケーション コードを分離するために、部分信頼を使用する必要があります。 これは、アプリケーションが<xref:System.Windows.Controls.WebBrowser.InvokeScript%2A>メソッドとプロパティを使用してホストされたスクリプトと対話する場合に特に<xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>当てはまります。 詳細については、「 [WPF アドインの概要](./app-development/wpf-add-ins-overview.md)」を参照してください。  
  
 アプリケーションで WPF<xref:System.Windows.Controls.WebBrowser>コントロールを使用する場合、セキュリティを強化し、攻撃を軽減する別の方法は、Internet Explorer 機能のコントロールを有効にすることです。 機能コントロールは、管理者や開発者が、WebBrowser <xref:System.Windows.Controls.WebBrowser> ActiveX コントロールをホストするアプリケーションを構成する機能を構成することを可能にする、Internet Explorer への追加機能です。 機能コントロールは、機能を使用して構成できます、 [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85))関数またはレジストリ内の値を変更します。 機能コントロールの詳細については、「 機能コントロールと[インターネット機能コントロール](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85))[の概要](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85))」を参照してください。  
  
 WPF コントロールを使用するスタンドアロン WPF アプリケーションを開発している<xref:System.Windows.Controls.WebBrowser>場合、WPF はアプリケーションに対して次の機能コントロールを自動的に有効にします。  
  
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
  
 機能コントロールは、WebBrowser ActiveX オブジェクトをインスタンス化するプロセスによって適用されます。 そのため、信頼されていないコンテンツに移動できるスタンドアロン アプリケーションを作成する場合は、その他の機能コントロールを有効にすることを検討すべきです。  
  
> [!NOTE]
> この推奨事項は、MSHTML および SHDOCVW ホスト セキュリティの一般的な推奨事項に基づいています。 詳細については、「 [MSHTML ホスト セキュリティに関するよく寄せられる質問 : II のパート I」](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/)および[「MSHTML ホスト セキュリティに関するよく寄せられる質問: パート II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/)」を参照してください。  
  
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
  
 Windows インターネット エクスプ ローラーで WPF<xref:System.Windows.Controls.WebBrowser>コントロールを含む部分的に信頼された XAML ブラウザー アプリケーション (XBAP) を実行する場合、WPF は、インターネット エクスプ ローラー プロセスのアドレス空間で WebBrowser ActiveX コントロールをホストします。 WebBrowser ActiveX コントロールは、インターネット エクスプローラ プロセスでホストされているため、WebBrowser ActiveX コントロールに対しては、インターネット エクスプローラのすべての機能コントロールも有効になっています。  
  
 Internet Explorer で実行されている XBAP にも、標準のスタンドアロン アプリケーションよりも高いレベルのセキュリティが適用されます。 このセキュリティが強化されているのは、Windows Vista および Windows 7 では、インターネット エクスプローラ (つまり、WebBrowser ActiveX コントロール) が既定で保護モードで動作するためです。 保護モードの詳細については、「 [Internet Explorer の保護モードとは」](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/)を参照してください。  
  
> [!NOTE]
> Firefox で WPF<xref:System.Windows.Controls.WebBrowser>コントロールを含む XBAP を実行しようとすると、インターネット ゾーンで<xref:System.Security.SecurityException>a がスローされます。 これは、WPF セキュリティ ポリシーが原因です。  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>部分信頼クライアント アプリケーションに対する APTCA の無効化  
 マネージ アセンブリがグローバル アセンブリ キャッシュ (GAC) にインストールされると、ユーザーがアセンブリをインストールするための明示的なアクセス許可を与える必要があるため、完全に信頼されます。 完全に信頼されているため、これらを使用できるのは完全信頼マネージド クライアント アプリケーションのみです。 部分的に信頼されたアプリケーションで使用できるようにするには<xref:System.Security.AllowPartiallyTrustedCallersAttribute>、(APTCA)でマークする必要があります。 この属性は、部分信頼で実行しても安全であるとテストで確認されたアセンブリだけに設定します。  
  
 ただし、GaC にインストールした後、APTCA アセンブリにセキュリティ上の欠陥が発生する可能性があります。 セキュリティ上の欠陥が検出されたら、アセンブリの発行者は、既存のインストールでの問題を解決し、問題発見後に発生する可能性があるインストールに備えるため、セキュリティ更新プログラムを作成できます。 更新プログラムの 1 つのオプションとして、アセンブリのアンインストールが考えられますが、その場合はこのアセンブリを使用する他の完全信頼クライアント アプリケーションを破損するおそれがあります。  
  
 WPF は、APTCA アセンブリをアンインストールせずに部分的に信頼された XBAP に対して APTCA アセンブリを無効にできるメカニズムを提供します。  
  
 APTCA アセンブリを無効にするには、特殊なレジストリ キーを作成する必要があります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 次のコードは一例を示しています。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 このキーにより、APTCA アセンブリのエントリが設定されます。 また、アセンブリを有効または無効にする値をこのキーに作成する必要があります。 値の詳細を次に示します。  
  
- 値名: **APTCA_FLAG。**  
  
- 値の種類: **REG_DWORD。**  
  
- 値のデータ: **1**を無効にします。**0**を指定すると有効になります。  
  
 部分信頼クライアント アプリケーションに対してアセンブリを無効にする必要がある場合は、レジストリ キーおよび値を作成する更新プログラムを作成します。  
  
> [!NOTE]
> コア .NET Framework アセンブリは、マネージ アプリケーションの実行に必要なため、この方法で無効にしても影響を受けません。 APTCA アセンブリの無効化のサポートは、主にサードパーティ アプリケーションを対象にしたものです。  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Loose XAML ファイルに対するサンドボックスの動作  
 ルー[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ズ ファイルは、分離コード、イベント ハンドラー、またはアプリケーション固有のアセンブリに依存しないマークアップのみの XAML ファイルです。 ルース[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイルがブラウザから直接に移動されると、既定のインターネット ゾーンアクセス許可セットに基づいてセキュリティ サンドボックスに読み込まれます。  
  
 ただし、緩い[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイルがスタンドアロン アプリケーションまたは<xref:System.Windows.Navigation.NavigationWindow><xref:System.Windows.Controls.Frame>スタンドアロン アプリケーション内の のに移動する場合は、セキュリティの動作が異なります。  
  
 どちらの場合も、ナビゲーション先[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]の緩いファイルは、そのホスト アプリケーションのアクセス許可を継承します。 ただし、この動作は、特に、信頼されていないエンティティまたは不明なエンティティによって[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]、緩いファイルが作成された場合、セキュリティの観点から望ましくないことがあります。 このタイプのコンテンツは*外部コンテンツ*と呼ばれ、<xref:System.Windows.Controls.Frame><xref:System.Windows.Navigation.NavigationWindow>両方とも移動時に分離するように構成できます。 分離は、次の例<xref:System.Windows.Controls.Frame>と で示すように、**サンドボックス外部コンテンツ**プロパティを true<xref:System.Windows.Navigation.NavigationWindow>に設定することで実現されます。  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 このように設定すると、外部コンテンツは、アプリケーションをホストするプロセスとは異なるプロセスに読み込まれます。 このプロセスは既定のインターネット ゾーン アクセス許可セットに限定されており、ホスト アプリケーションとクライアント コンピューターから外部コンテンツを効果的に分離します。  
  
> [!NOTE]
> スタンドアロン アプリケーションまたは[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]<xref:System.Windows.Navigation.NavigationWindow>スタンドアロン アプリケーション<xref:System.Windows.Controls.Frame>内の緩いファイルへのナビゲーションは、プレゼンテーション ホスト インフラストラクチャに基づいて実装されていても、プレゼンテーション ホスト プロセスを伴う WPF ブラウザーのホストインフラストラクチャに基づいて、コンテンツが Windows Vista および Windows 7 の Internet Explorer に直接読み込まれる場合よりもセキュリティ レベルが若干小さくなります (これはプレゼンテーション ホストを通じて行われます)。 これは、Web ブラウザーを使用しているスタンドアロン WPF アプリケーションに、Internet Explorer の保護モード セキュリティ機能が追加されていないためです。  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>セキュリティを向上する WPF アプリケーションを開発するためのリソース  
 セキュリティを促進する WPF アプリケーションの開発に役立つ追加リソースを次に示します。  
  
|領域|リソース|  
|----------|--------------|  
|マネージド コード|[patterns & practices アプリケーション セキュリティ ガイダンス インデックス](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[コード アクセス セキュリティ](../misc/code-access-security.md)|  
|ClickOnce|[クリックワンスのセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>関連項目

- [WPF 部分信頼セキュリティ](wpf-partial-trust-security.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [WPF のセキュリティ方針 - セキュリティ エンジニアリング](wpf-security-strategy-security-engineering.md)
- [patterns & practices アプリケーション セキュリティ ガイダンス インデックス](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [コード アクセス セキュリティ](../misc/code-access-security.md)
- [クリックワンスのセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)
- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
