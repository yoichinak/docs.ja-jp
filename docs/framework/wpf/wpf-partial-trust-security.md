---
title: WPF 部分信頼セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 75ebf605e9abb844e7a713b448aefe2ec4cd1a27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218382"
---
# <a name="wpf-partial-trust-security"></a>WPF 部分信頼セキュリティ
<a name="introduction"></a> 一般に、悪意のある破損を防ぐための重要なシステム リソースに直接アクセスする必要がなくなりますインターネット アプリケーションを制限する必要があります。 既定では、[!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)]クライアント側のスクリプト言語は、重要なシステム リソースにアクセスすることができません。 Windows Presentation Foundation (WPF)、ブラウザーからブラウザーでホストされるアプリケーションを起動できるのような一連の制限に準拠している必要があります。 これらの制限を適用する[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]依存両方[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]と[!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)](を参照してください[WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md))。 既定では、ブラウザーでホストされるアプリケーションはインターネット ゾーンを要求[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]インターネット、ローカル イントラネット、またはローカル コンピューターから起動するかどうかに関係なく、権限のセット。 アクセス許可の完全なセットよりも小さいか何かを実行しているアプリケーションは、部分信頼で実行されていると見なされます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] さまざまなサポートを実施し、できるだけ多くの機能使用できることを安全にに沿ってを使用して、部分信頼では、 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]、部分信頼のプログラミングの他のサポートを提供します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [機能の WPF 部分信頼サポート](#WPF_Feature_Partial_Trust_Support)  
  
-   [部分信頼のプログラミング](#Partial_Trust_Programming)  
  
-   [アクセス許可の管理](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>機能の WPF 部分信頼サポート  
 次の表では、インターネット ゾーン アクセス許可のセットの制限内で使用しても安全な高度な機能の Windows Presentation Foundation (WPF) を示します。  
  
 表 1:部分信頼で安全な WPF の機能  
  
|機能分野|機能|  
|------------------|-------------|  
|全般|ブラウザー ウィンドウ<br /><br /> 起点サイト アクセス<br /><br /> IsolatedStorage (512 KB の制限)<br /><br /> UIAutomation プロバイダー<br /><br /> コマンドの実行<br /><br /> 入力方式エディター (IME)<br /><br /> スタイラスのタブレットと手描き入力<br /><br /> マウスのキャプチャと移動イベントを使用してシミュレートされたドラッグ アンド ドロップ<br /><br /> OpenFileDialog<br /><br /> (XamlReader.Load) を使用して XAML 逆シリアル化|  
|Web 統合|ブラウザーのダウンロード ダイアログ ボックス<br /><br /> ユーザーが開始した最上位レベルのナビゲーション<br /><br /> mailto:links<br /><br /> Uniform Resource Identifier パラメーター<br /><br /> HTTPWebRequest<br /><br /> IFRAME でホストされている WPF のコンテンツ<br /><br /> フレームを使用して、同じサイトの HTML ページのホスト<br /><br /> Web ブラウザーを使用して、同じサイトの HTML ページのホスト<br /><br /> Web サービス (ASMX)<br /><br /> (Windows Communication Foundation を使用して) web サービス<br /><br /> [スクリプティング]<br /><br /> ドキュメント オブジェクト モデル|  
|ビジュアル|2D および 3D<br /><br /> アニメーション<br /><br /> メディア (発信元とドメイン間のサイト)<br /><br /> イメージング/オーディオ/ビデオ|  
|読み取り|FlowDocument<br /><br /> XPS ドキュメント<br /><br /> 埋め込み (& a) のシステム フォント<br /><br /> CFF & TrueType フォント|  
|編集|スペル チェック<br /><br /> RichTextBox<br /><br /> プレーン テキストとインクのクリップボードのサポート<br /><br /> ユーザーが開始した貼り付け<br /><br /> 選択したコンテンツのコピー|  
|コントロール|[全般] のコントロール|  
  
 この表は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]高レベルで機能します。 詳細については、[!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)]ドキュメント内の各メンバーに必要なアクセス許可[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]します。 さらに、次の機能には、特別な考慮事項を含め、部分信頼の実行に関する情報の詳細します。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (を参照してください[XAML の概要 (WPF)](./advanced/xaml-overview-wpf.md))。  
  
-   ポップアップ (を参照してください<xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>)。  
  
-   ドラッグ アンド ドロップ (を参照してください[ドラッグ アンド ドロップの概要](./advanced/drag-and-drop-overview.md))。  
  
-   クリップボード (を参照してください<xref:System.Windows.Clipboard?displayProperty=nameWithType>)。  
  
-   イメージング (を参照してください<xref:System.Windows.Controls.Image?displayProperty=nameWithType>)。  
  
-   シリアル化 (を参照してください<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>、 <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>)。  
  
-   ファイル ダイアログ ボックスを開きます (を参照してください<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>)。  
  
 次の表にアウトライン、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]インターネットの制限内で実行しても安全ではない機能をゾーンのアクセス許可セット。  
  
 表 2:部分信頼で安全でないある WPF 機能  
  
|機能分野|機能|  
|------------------|-------------|  
|全般|ウィンドウ (定義されている Windows のアプリケーションとダイアログ ボックス)<br /><br /> SaveFileDialog<br /><br /> ファイル システム<br /><br /> レジストリへのアクセス<br /><br /> ドラッグ アンド ドロップ<br /><br /> (XamlWriter.Save) を使用して XAML シリアル化<br /><br /> UIAutomation クライアント<br /><br /> ソース ウィンドウへのアクセス (HwndHost)<br /><br /> 完全な音声サポート<br /><br /> Windows フォームの相互運用性|  
|ビジュアル|ビットマップ効果<br /><br /> イメージのエンコード|  
|編集|リッチ テキスト形式のクリップボード<br /><br /> 完全な XAML のサポート|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>部分信頼のプログラミング  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]アプリケーション、コードを既定の権限セットを超えるには、セキュリティ ゾーンに応じて異なる動作です。 ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。 ユーザーは、インストールを続行するか取り消すかを選択できます。 次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全な信頼を受け取るアプリケーションで行う必要のある操作を示しています。  
  
|セキュリティ ゾーン|動作|完全信頼を受け取るための操作|  
|-------------------|--------------|------------------------|  
|ローカル コンピューター|完全な信頼を自動的に受け取る|アクションは必要ありません。|  
|イントラネットおよび信頼済みサイト|完全な信頼のプロンプトを表示する|プロンプトにソースが表示されるように、証明書を使用して XBAP に署名します。|  
|インターネット|"信頼されていません" というメッセージが表示され、失敗する|証明書を使用して XBAP に署名します。|  
  
> [!NOTE]
>  前の表で説明されている動作では、完全な信頼の Xbap の ClickOnce 信頼済み配置モデルに従っていません。  
  
 一般に、許可されたアクセス許可を超える可能性があるコードは、スタンドアロンとブラウザー ホスト アプリケーションの両方の間で共有される共通のコードを使用する可能性があります。 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]このシナリオを管理するためのいくつかの手法を提供します。  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>CA を使用してアクセス許可の検出  
 一部の状況では両方のスタンドアロン アプリケーションで使用されるライブラリのアセンブリで共有コードを[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。 このような場合は、コードは、アプリケーションの受賞メンバーのアクセス許可セットで以上のアクセス許可が必要になる機能を実行可能性があります。 アプリケーションには、Microsoft .NET Framework のセキュリティを使用して特定のアクセス許可があるかどうかを検出できます。 具体的には、呼び出すことによって、特定のアクセス許可があるかどうかをテストする、<xref:System.Security.CodeAccessPermission.Demand%2A>メソッドを必要なアクセス許可のインスタンス。 これは、コードでローカル ディスクにファイルを保存する機能があるかどうかをクエリするが次の例に示します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 アプリケーションが、必要なアクセス許可への呼び出しを持たないかどうか<xref:System.Security.CodeAccessPermission.Demand%2A>セキュリティ例外がスローされます。 それ以外の場合、アクセス許可が与えられています。 `IsPermissionGranted` この動作をカプセル化し、返します`true`または`false`に応じて。  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>正常な機能が低下  
 コードが実行する必要がありますが、権限を持つかどうかを検出できることは、異なるゾーンから実行できるコードにとって重要です。 ゾーンは、1 つを検出するときにまで可能であれば、ユーザーの代替手段を提供することをお勧めします。 たとえば、完全信頼アプリケーションでは、通常、部分信頼アプリケーションは、分離ストレージでファイルを作成のみが、必要な任意の場所のファイルを作成するユーザーができます。 ファイルを作成するコードは完全な信頼 (スタンドアロン) アプリケーションと部分的な信頼 (ブラウザーによってホストされる) のアプリケーションの両方で共有されているアセンブリに存在する両方のアプリケーションに必要なユーザー ファイルを作成できるようにする場合は、共有コードがかどうかを検出する必要があります。適切な場所にファイルを作成する前に、部分的または完全な信頼で実行されています。 次のコードでは、両方を示します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 多くの場合、部分信頼の代替を検索できる必要があります。  
  
 イントラネットなど、制御された環境でカスタム マネージ フレームワークをインストールして、クライアントにベース、[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]します。 これらのライブラリの完全な信頼を必要とするコードを実行できるを使用して部分信頼はのみ許可されているアプリケーションから参照<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(詳細については、次を参照してください[セキュリティ](security-wpf.md)と[WPF のセキュリティ。方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md))。  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>ブラウザーでホストの検出  
 使用して[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]アクセス許可を確認するには適切な手法をごとのアクセス許可ごとに確認する必要がある場合は。 ただし、この手法に依存例外をキャッチ標準の一部として処理する一般的には推奨されず、パフォーマンスの問題を持つことができます。 代わりに場合、[!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)]インターネット ゾーンのサンド ボックス内にのみ実行される、使用できます、<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>プロパティに対して true を返す[!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]します。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> のみを実行しているアプリケーションのアクセス許可のどの設定されていないブラウザーでアプリケーションが実行されているかどうかを区別します。  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>アクセス許可の管理  
 既定では、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]部分信頼 (既定のインターネット ゾーン アクセス許可セット) で実行します。 ただし、アプリケーションの要件に応じて既定の権限のセットを変更することです。 たとえば場合、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]が起動される、ローカルのイントラネットからの次の表に示すように、増加のアクセス許可セット、活用をかかること。  
  
 表 3:ローカル イントラネットとインターネットのアクセス許可  
  
|アクセス許可|属性|LocalIntranet|インターネット|  
|----------------|---------------|-------------------|--------------|  
|DNS|DNS サーバーのアクセス|[はい]|いいえ|  
|環境変数|読み取り|[はい]|いいえ|  
|ファイル ダイアログ|開く|[はい]|[はい]|  
|ファイル ダイアログ|無制限|[はい]|いいえ|  
|分離ストレージ|ユーザーによるアセンブリの分離|[はい]|いいえ|  
|分離ストレージ|不明な分離|[はい]|[はい]|  
|分離ストレージ|無制限のユーザー クォータ|[はい]|いいえ|  
|メディア|安全なオーディオ、ビデオ、およびイメージ|[はい]|[はい]|  
|印刷|既定の印刷|[はい]|いいえ|  
|印刷|安全な印刷|[はい]|[はい]|  
|リフレクション|出力|[はい]|いいえ|  
|セキュリティ|マネージ コードの実行|[はい]|[はい]|  
|セキュリティ|付与されたアクセス許可をアサートします。|[はい]|いいえ|  
|ユーザー インターフェイス|無制限|[はい]|いいえ|  
|ユーザー インターフェイス|安全な最上位レベルの windows|[はい]|[はい]|  
|ユーザー インターフェイス|独自のクリップボード|[はい]|[はい]|  
|Web ブラウザー|HTML への安全なフレームのナビゲーション|[はい]|[はい]|  
  
> [!NOTE]
>  切り取りと貼り付けが部分信頼で場合にだけ許可ユーザーが開始しました。  
  
 アクセス許可を増やす必要がある場合は、プロジェクトの設定と、ClickOnce アプリケーション マニフェストを変更する必要があります。 詳細については、「[WPF XAML ブラウザー アプリケーションの概要](./app-development/wpf-xaml-browser-applications-overview.md)」をご覧ください。 次のドキュメントも便利な場合があります。  
  
-   [Mage.exe (マニフェスト生成および編集ツール)](../tools/mage-exe-manifest-generation-and-editing-tool.md)します。  
  
-   [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)します。  
  
-   [ClickOnce アプリケーションのセキュリティ](/visualstudio/deployment/securing-clickonce-applications)します。  
  
 場合、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]完全な信頼が必要です。 要求されたアクセス許可を増やすと同じツールを使用することができます。 ただし、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]上にインストールされ、イントラネット、ローカル コンピューターとは、ブラウザーの信頼済みまたは許可されたサイトに記載されている URL から起動された場合のみ、完全な信頼が受信されます。 アプリケーションは、イントラネットまたは信頼済みサイトからインストールする場合、ユーザーには管理者特権でのアクセス許可のことを通知する標準の ClickOnce プロンプトが表示されます。 ユーザーは、インストールを続行するか取り消すかを選択できます。  
  
 また、任意のセキュリティ ゾーンから完全な信頼の展開用 ClickOnce 信頼済み配置モデルを使用できます。 詳細については、次を参照してください。 [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview)と[セキュリティ](security-wpf.md)します。  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](security-wpf.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [WPF のセキュリティ方針 - セキュリティ エンジニアリング](wpf-security-strategy-security-engineering.md)
