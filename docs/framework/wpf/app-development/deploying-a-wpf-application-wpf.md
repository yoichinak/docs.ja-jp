---
title: WPF アプリケーションの配置 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: daa69997f70c22a97482fd7e63d42506e7051732
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291299"
---
# <a name="deploying-a-wpf-application-wpf"></a>WPF アプリケーションの配置 (WPF)
Windows Presentation Foundation (WPF) アプリケーションを構築した後は、アプリケーションを配置する必要があります。 Windows と .NET Framework には、いくつかの展開テクノロジが含まれています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置に使用される配置テクノロジは、アプリケーションの種類によって決まります。 このトピックでは、それぞれの配置テクノロジの概要と使用法を、それぞれの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの種類の配置要件に関連して説明します。  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>配置テクノロジ  
 Windows と .NET Framework には、次のようないくつかの展開テクノロジが含まれています。  
  
- XCopy による配置。  
  
- [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] による配置。  
  
- ClickOnce 配置  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy による配置  
 XCopy による配置とは、XCopy コマンド ライン プログラムを使用して、ある場所から別の場所へファイルをコピーすることです。 XCopy による配置は、次のような状況に適しています。  
  
- アプリケーションは自己完結型である。 実行するためにクライアントを更新する必要がない。  
  
- アプリケーションファイルを別の場所に移動する必要があります。たとえば、ビルドの場所 (ローカルディスク、UNC ファイル共有など) から発行場所 (Web サイト、UNC ファイル共有など) に移動します。  
  
- アプリケーションはシェル統合 ([スタート] メニューのショートカット、デスクトップ アイコンなど) を必要としない。  
  
 XCopy は、単純な配置シナリオには適していますが、複雑な配置機能が必要なシナリオには十分に対応できません。 特に、配置を堅牢な方法で管理する場合、XCopy を使用すると、スクリプトの作成、実行、および維持というオーバーヘッドが生じます。 さらに、XCopy は、バージョン管理、アンインストール、およびロールバックをサポートしません。  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows インストーラー  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用すると、アプリケーションを自己完結型の実行可能ファイルとしてパッケージ化でき、容易にクライアントに配布して、実行できます。 さらに、[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] は Windows と共にインストールされ、デスクトップ、[スタート] メニュー、および [プログラム] コントロールパネルとの統合を可能にします。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] は、アプリケーションのインストールとアンインストールを単純化しますが、インストールされたアプリケーションをバージョン管理の観点から最新に保つ機能を提供しません。  
  
 Windows インストーラーの詳細については、「 [Windows インストーラーの展開](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)」を参照してください。
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce 配置  
 ClickOnce を使用すると、Web 以外のアプリケーションに対して Web スタイルのアプリケーションを配置できます。 アプリケーションは、Web サーバーまたはファイル サーバーに公開され、これらのサーバーから配置されます。 ClickOnce では、横-0 にインストールされ @no__t たアプリケーションが実行するすべてのクライアント機能がサポートされているわけではありませんが、次のようなサブセットをサポートしています。  
  
- [スタート] メニューおよび [プログラム] コントロール パネルとの統合。  
  
- バージョン管理、ロールバック、およびアンインストール。  
  
- アプリケーションを常に配置場所から起動するオンライン インストール モード。  
  
- 新しいバージョンがリリースされたときの自動更新。  
  
- ファイル拡張子の登録。  
  
 ClickOnce の詳細については、「 [clickonce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF アプリケーションの配置  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置オプションは、アプリケーションの種類によって決まります。 配置の観点から見ると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には次の 3 種類のアプリケーションがあります。  
  
- スタンドアロン アプリケーション。  
  
- マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーション。  
  
- [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>スタンドアロン アプリケーションの配置  
 スタンドアロンアプリケーションは、ClickOnce または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用してデプロイされます。 いずれの場合も、スタンドアロン アプリケーションを実行するには、アプリケーションが完全に信頼されている必要があります。 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用して配置されたスタンドアロン アプリケーションには、完全な信頼が自動的に付与されます。 ClickOnce を使用して配置されるスタンドアロンアプリケーションには、完全な信頼が自動的に付与されるわけではありません。 代わりに、ClickOnce によって、スタンドアロンアプリケーションをインストールする前にユーザーが受け入れる必要があるセキュリティ警告ダイアログが表示されます。 受け入れた場合、スタンドアロン アプリケーションがインストールされ、完全な信頼が付与されます。 受け入れなかった場合、スタンドアロン アプリケーションはインストールされません。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>マークアップのみの XAML アプリケーションの配置  
 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは通常、HTML ページなどの Web サーバーに発行され、Internet Explorer を使用して表示できます。 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、部分信頼セキュリティ サンドボックス内で実行され、インターネット ゾーン アクセス許可セットによって定義された制約が適用されます。 これにより、HTML ベースの Web アプリケーションに対する同等のセキュリティサンドボックスが提供されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションのセキュリティの詳細については、「[セキュリティ](../security-wpf.md)」を参照してください。  
  
 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、XCopy または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用してローカル ファイル システムにインストールできます。 これらのページは、Internet Explorer またはエクスプローラーを使用して表示できます。  
  
 XAML の詳細については、「[XAML の概要 (WPF)](../advanced/xaml-overview-wpf.md)」を参照してください。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML ブラウザー アプリケーションの配置  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、次の 3 つのファイルを配置する必要があるコンパイル済みのアプリケーションです。  
  
- *ApplicationName*:実行可能アセンブリアプリケーションファイル。  
  
- *ApplicationName*:配置マニフェスト。  
  
- *ApplicationName*.manifest:アプリケーション マニフェスト。  
  
> [!NOTE]
> 配置マニフェストおよびアプリケーション マニフェストの詳細については、「[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください。  
  
 これらのファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] がビルドされるときに生成されます。 詳細については、「[方法 :新しい WPF ブラウザーアプリケーションプロジェクト @ no__t-0 を作成します。 マークアップのみの @no__t 0 ページと同様に、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は通常、Web サーバーに発行され、Internet Explorer を使用して表示されます。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、任意の配置技術を使用してクライアントに配置できます。 ただし、次の機能が用意されているため、ClickOnce を使用することをお勧めします。  
  
1. 新しいバージョンが公開されたときの自動更新。  
  
2. 完全な信頼で実行する [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の特権の昇格。  
  
 既定では、ClickOnce は、.deploy 拡張子を持つアプリケーション ファイルを公開します。 これは問題になる可能性がありますが、無効にできます。 詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)」を参照してください。  
  
 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] の配置の詳細については、「[WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)」を参照してください。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework のインストール  
 @No__t 0 アプリケーションを実行するには、Microsoft .NET Framework がクライアントにインストールされている必要があります。 @No__t ブラウザーでホストされているアプリケーションを表示すると、.NET Framework と共にクライアントがインストールされているかどうかが自動的に検出されます。 .NET Framework がインストールされていない場合、Internet Explorer はユーザーにインストールを促すメッセージを表示します。  
  
 .NET Framework がインストールされているかどうかを検出するために、Internet Explorer には、次の拡張子を持つコンテンツファイルのフォールバック Multipurpose Internet Mail Extensions (MIME) ハンドラーとして登録されたブートストラップアプリケーションが含まれています。 .xaml、.xps、xbap、、および. アプリケーション。 これらのファイルの種類に移動したときに、.NET Framework がクライアントにインストールされていない場合、ブートストラップアプリケーションは、インストールするためのアクセス許可を要求します。 アクセス許可が指定されていない場合は、.NET Framework もアプリケーションもインストールされません。  
  
 アクセス許可が付与されている場合、Internet Explorer は Microsoft バックグラウンドインテリジェント転送サービス (BITS) を使用して .NET Framework をダウンロードしてインストールします。 .NET Framework が正常にインストールされると、最初に要求されたファイルが新しいブラウザーウィンドウで開かれます。  
  
 詳細については、「[.NET Framework およびアプリケーションの配置](../../deployment/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)
- [Security](../security-wpf.md)
