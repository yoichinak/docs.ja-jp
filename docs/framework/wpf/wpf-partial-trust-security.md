---
title: 部分信頼セキュリティ
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
ms.openlocfilehash: 99c7d9cfae2b137053ca77d9e3d7055b4674ce5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174577"
---
# <a name="wpf-partial-trust-security"></a>WPF 部分信頼セキュリティ
<a name="introduction"></a>一般に、インターネット アプリケーションは、悪意のある損害を防ぐために、重要なシステム リソースに直接アクセスできないように制限する必要があります。 既定では、HTML およびクライアント側のスクリプト言語は、重要なシステム リソースにアクセスできません。 Windows プレゼンテーションファンデーション (WPF) ブラウザーでホストされているアプリケーションはブラウザーから起動できるため、同様の制限セットに準拠する必要があります。 これらの制限を適用するために、WPF はコード アクセス セキュリティ (CAS) と ClickOnce の両方に依存しています[(WPF セキュリティ戦略 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)を参照)。 既定では、ブラウザでホストされるアプリケーションは、インターネット、ローカル イントラネット、またはローカル コンピューターから起動されるかどうかにかかわらず、インターネット ゾーン CAS のアクセス許可セットを要求します。 完全なアクセス許可セットより小さいもので実行されるアプリケーションは、部分信頼で実行されていると言います。  
  
 WPF は、部分信頼で可能な限り多くの機能を安全に使用できるように、さまざまなサポートを提供し、CAS と共に部分信頼プログラミングの追加サポートを提供します。  
  
 このトピックには、次のセクションが含まれます。  
  
- [WPF 機能の部分信頼のサポート](#WPF_Feature_Partial_Trust_Support)  
  
- [部分信頼プログラミング](#Partial_Trust_Programming)  
  
- [権限の管理](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>
## <a name="wpf-feature-partial-trust-support"></a>WPF 機能の部分信頼のサポート  
 次の表は、インターネット ゾーンアクセス許可セットの制限内で安全に使用できる Windows プレゼンテーション ファンデーション (WPF) の高レベル機能を示しています。  
  
 表 1: 部分信頼で安全な WPF 機能  
  
|機能領域|機能|  
|------------------|-------------|  
|全般|ブラウザ ウィンドウ<br /><br /> 原産地アクセスサイト<br /><br /> 分離ストレージ (512 KB の制限)<br /><br /> UI オートメーション プロバイダ<br /><br /> コマンド実行<br /><br /> 入力方式エディター (IME)<br /><br /> タブレット スタイラスとインク<br /><br /> マウス キャプチャと移動イベントを使用したシミュレートされたドラッグ/ドロップ<br /><br /> OpenFileDialog<br /><br /> XAML 逆シリアル化 (XamlReader.Load 経由)|  
|ウェブ統合|ブラウザのダウンロードダイアログ<br /><br /> トップレベルのユーザー起動ナビゲーション<br /><br /> メール先:リンク<br /><br /> 統一リソース識別子のパラメータ<br /><br /> リクエスト<br /><br /> IFRAME でホストされる WPF コンテンツ<br /><br /> フレームを使用した同一サイト HTML ページのホスティング<br /><br /> ウェブブラウザを使用した同じサイトHTMLページのホスティング<br /><br /> ウェブサービス(ASMX)<br /><br /> Web サービス (Windows コミュニケーション ファウンデーションを使用)<br /><br /> スクリプトの作成<br /><br /> ドキュメント オブジェクト モデル|  
|ビジュアル|2D および 3D<br /><br /> アニメーション<br /><br /> メディア(原産地とクロスドメイン)<br /><br /> イメージング/オーディオ/ビデオ|  
|読書|FlowDocument<br /><br /> XPS ドキュメント<br /><br /> 組み込み&システムフォント<br /><br /> CFF & TrueType フォント|  
|編集|スペルチェック<br /><br /> RichTextBox<br /><br /> プレーンテキストとインク クリップボードのサポート<br /><br /> ユーザーが開始した貼り付け<br /><br /> 選択したコンテンツのコピー|  
|コントロール|一般的なコントロール|  
  
 この表は、高度なレベルでの WPF 機能を示しています。 詳細については、Windows SDK では、WPF の各メンバーに必要なアクセス許可が文書化されています。 さらに、以下の機能には、部分信頼の実行に関する詳細な情報が含まれています。  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)](XAML[の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)を参照してください)。  
  
- ポップアップ (を参照<xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>)。  
  
- ドラッグ アンド ドロップ(「[ドラッグ アンド ドロップの概要](./advanced/drag-and-drop-overview.md)」を参照)。  
  
- クリップボード (<xref:System.Windows.Clipboard?displayProperty=nameWithType>を参照)。  
  
- イメージング (を<xref:System.Windows.Controls.Image?displayProperty=nameWithType>参照)。  
  
- シリアル化<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>(<xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>を参照)。  
  
- [ファイルを開く]<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>ダイアログ ボックス (を参照)。  
  
 次の表は、インターネット ゾーンアクセス許可セットの制限内で実行しても安全ではない WPF 機能の概要を示しています。  
  
 表 2: 部分信頼で安全でない WPF 機能  
  
|機能領域|機能|  
|------------------|-------------|  
|全般|ウィンドウ (アプリケーション定義のウィンドウとダイアログ ボックス)<br /><br /> SaveFileDialog<br /><br /> ファイル システム<br /><br /> レジストリへのアクセス<br /><br /> ドラッグ アンド ドロップ<br /><br /> XAML シリアル化 (XamlWriter を介して保存)<br /><br /> UI オートメーション クライアント<br /><br /> ソース ウィンドウ アクセス (HwndHost)<br /><br /> 完全な音声サポート<br /><br /> Windows フォームの相互運用性|  
|ビジュアル|ビットマップ効果<br /><br /> 画像のエンコーディング|  
|編集|リッチ テキスト形式のクリップボード<br /><br /> 完全な XAML サポート|  
  
<a name="Partial_Trust_Programming"></a>
## <a name="partial-trust-programming"></a>部分信頼プログラミング  
 XBAP アプリケーションの場合、既定のアクセス許可セットを超えるコードは、セキュリティ ゾーンによって動作が異なります。 ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。 ユーザーは、インストールを続行するか取り消すかを選択できます。 次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全な信頼を受け取るアプリケーションで行う必要のある操作を示しています。  
  
|セキュリティ ゾーン|動作|完全信頼を受け取るための操作|  
|-------------------|--------------|------------------------|  
|ローカル コンピューター|完全な信頼を自動的に受け取る|対処は必要ありません。|  
|イントラネットおよび信頼済みサイト|完全な信頼のプロンプトを表示する|プロンプトにソースが表示されるように、証明書を使用して XBAP に署名します。|  
|インターネット|"信頼されていません" というメッセージが表示され、失敗する|証明書を使用して XBAP に署名します。|  
  
> [!NOTE]
> 前の表で説明した動作は、ClickOnce 信頼された配置モデルに従っていない完全信頼 XARP に対するものです。  
  
 一般に、許可されたアクセス許可を超える可能性があるコードは、スタンドアロン アプリケーションとブラウザー ホスト アプリケーションの両方で共有される共通のコードです。 CAS と WPF には、このシナリオを管理するためのいくつかの手法が用意されています。  
  
<a name="Detecting_Permissions_using_CAS"></a>
### <a name="detecting-permissions-using-cas"></a>CAS を使用したアクセス許可の検出  
 状況によっては、ライブラリ アセンブリ内の共有コードをスタンドアロン アプリケーションと XBaap の両方で使用できます。 このような場合、アプリケーションに付与されたアクセス許可セットで許可されている以上のアクセス許可が必要な機能がコードで実行される場合があります。 アプリケーションは、Microsoft .NET Framework セキュリティを使用して、特定のアクセス許可を持っているかどうかを検出できます。 具体的には、目的のアクセス許可のインスタンスでメソッドを<xref:System.Security.CodeAccessPermission.Demand%2A>呼び出すことによって、特定のアクセス許可があるかどうかをテストできます。 次の例では、ローカル ディスクにファイルを保存できるかどうかを照会するコードを示します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 アプリケーションに目的のアクセス許可がない場合、 を<xref:System.Security.CodeAccessPermission.Demand%2A>呼び出すと、セキュリティ例外がスローされます。 それ以外の場合は、アクセス許可が付与されています。 `IsPermissionGranted`この動作をカプセル化し`true`、`false`必要に応じて返します。  
  
<a name="Graceful_Degradation_of_Functionality"></a>
### <a name="graceful-degradation-of-functionality"></a>機能のグレースフルな低下  
 コードに必要な操作を行うためのアクセス許可があるかどうかを検出できることは、異なるゾーンから実行できるコードにとって興味深いことです。 ゾーンを検出することは一つのことですが、可能であれば、ユーザーに代替手段を提供する方がはるかに優れています。 たとえば、完全信頼アプリケーションでは、通常、ユーザーは任意の場所にファイルを作成できますが、部分信頼アプリケーションでは分離ストレージ内にしかファイルを作成できません。 ファイルを作成するコードが、完全信頼 (スタンドアロン) アプリケーションと部分信頼 (ブラウザでホストされる) アプリケーションの両方で共有されるアセンブリ内に存在し、両方のアプリケーションがユーザーにファイルを作成できるようにする場合、共有コードは、ファイルが適切な場所にファイルを作成する前に、部分的または完全な信頼で実行されます。 次のコードは、両方を示しています。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 多くの場合、部分的な信頼の代替を見つけることができるはずです。  
  
 イントラネットなどの制御された環境では、カスタム マネージ フレームワークをクライアント ベース全体にインストールしてグローバル アセンブリ キャッシュ (GAC) にインストールできます。 これらのライブラリは、完全な信頼を必要とするコードを実行し、使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>して部分信頼のみが許可されているアプリケーションから参照できます (詳細については、「[セキュリティ](security-wpf.md)と WPF[セキュリティ戦略 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)」を参照してください)。  
  
<a name="Browser_Host_Detection"></a>
### <a name="browser-host-detection"></a>ブラウザのホスト検出  
 アクセス許可ごとにチェックする必要がある場合は、CAS を使用してアクセス許可を確認する方法が適しています。 ただし、この手法は通常の処理の一部として例外をキャッチする方法に依存しますが、これは一般的には推奨されず、パフォーマンス上の問題が生じます。 代わりに、XAML ブラウザー アプリケーション (XBAP) がインターネット ゾーンサンドボックス内でのみ実行される<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>場合は、XAML ブラウザー アプリケーション (XBAP) に true を返すプロパティを使用できます。  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A>アプリケーションがブラウザーで実行されているかどうかは区別されるだけで、アプリケーションが実行されているアクセス許可のセットは区別されません。  
  
<a name="Managing_Permissions"></a>
## <a name="managing-permissions"></a>権限の管理  
 既定では、XBaap は部分信頼 (既定のインターネット ゾーンアクセス許可セット) で実行されます。 ただし、アプリケーションの要件によっては、アクセス許可のセットをデフォルトから変更することができます。 たとえば、XBap をローカル イントラネットから起動すると、次の表に示すアクセス許可セットの増加を利用できます。  
  
 表 3: ローカル イントラネットとインターネットのアクセス許可  
  
|権限|属性|ローカルイントラネット|インターネット|  
|----------------|---------------|-------------------|--------------|  
|DNS|DNS サーバーへのアクセス|はい|いいえ|  
|環境変数|Read|はい|いいえ|  
|ファイル ダイアログ|[ファイル]|はい|はい|  
|ファイル ダイアログ|制限なし|はい|いいえ|  
|分離ストレージ|ユーザー別のアセンブリ分離|はい|いいえ|  
|分離ストレージ|不明な分離|はい|はい|  
|分離ストレージ|無制限のユーザー クォータ|はい|いいえ|  
|メディア|安全なオーディオ、ビデオ、および画像|はい|はい|  
|印刷|既定の印刷|はい|いいえ|  
|印刷|安全な印刷|はい|はい|  
|リフレクション|出力|はい|いいえ|  
|Security|マネージ コードの実行|はい|はい|  
|Security|アサート付与されたアクセス許可|はい|いいえ|  
|ユーザー インターフェイス|制限なし|はい|いいえ|  
|ユーザー インターフェイス|安全なトップレベル ウィンドウ|はい|はい|  
|ユーザー インターフェイス|独自のクリップボード|はい|はい|  
|Web ブラウザー|HTML への安全なフレーム ナビゲーション|はい|はい|  
  
> [!NOTE]
> 切り取りと貼り付けは、ユーザーが開始したときにのみ部分的な信頼で許可されます。  
  
 アクセス許可を増やす必要がある場合は、プロジェクトの設定と ClickOnce アプリケーション マニフェストを変更する必要があります。 詳細については、「[WPF XAML ブラウザー アプリケーションの概要](./app-development/wpf-xaml-browser-applications-overview.md)」をご覧ください。 次のドキュメントも役立つ場合があります。  
  
- [Mage.exe (マニフェスト生成および編集ツール)](../tools/mage-exe-manifest-generation-and-editing-tool.md)  
  
- [MageUI.exe (マニフェスト生成と編集ツール、グラフィカルクライアント)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
  
- [クリックワンス アプリケーションのセキュリティ保護](/visualstudio/deployment/securing-clickonce-applications):  
  
 XBAP が完全な信頼を必要とする場合は、同じツールを使用して要求されたアクセス許可を増やすことができます。 XBAP は、ローカル コンピュータ、イントラネット、またはブラウザの信頼済みサイトまたは許可されたサイトに記載されている URL にインストールされ、起動された場合にのみ完全な信頼を受けます。 アプリケーションがイントラネットまたは信頼済みサイトからインストールされている場合、ユーザーには昇格されたアクセス許可を通知する標準の ClickOnce プロンプトが表示されます。 ユーザーは、インストールを続行するか取り消すかを選択できます。  
  
 または、任意のセキュリティ ゾーンから完全に信頼された配置を行う場合は、ClickOnce 信頼された配置モデルを使用できます。 詳細については、「[信頼されたアプリケーションの展開の概要](/visualstudio/deployment/trusted-application-deployment-overview)および[セキュリティ](security-wpf.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [セキュリティ](security-wpf.md)
- [WPF のセキュリティ方針 - プラットフォーム セキュリティ](wpf-security-strategy-platform-security.md)
- [WPF のセキュリティ方針 - セキュリティ エンジニアリング](wpf-security-strategy-security-engineering.md)
