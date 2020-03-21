---
title: アプリのデプロイ
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186313"
---
# <a name="deploy-a-wpf-application"></a>WPF アプリケーションを展開する

Windows プレゼンテーション ファンデーション (WPF) アプリケーションをビルドした後、展開する必要があります。 Windows と .NET Framework には、いくつかの展開テクノロジが含まれています。 WPF アプリケーションの展開に使用される配置テクノロジは、アプリケーションの種類によって異なります。 このトピックでは、各展開テクノロジの概要と、各 WPF アプリケーションの種類の展開要件と共に使用する方法について簡単に説明します。

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>配置テクノロジ  
 Windows と .NET Framework には、次のようないくつかの展開テクノロジが含まれています。  
  
- XCopy による配置。  
  
- Windows インストーラーの配置。  
  
- ClickOnce 配置。  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>XCopy による配置  
 XCopy による配置とは、XCopy コマンド ライン プログラムを使用して、ある場所から別の場所へファイルをコピーすることです。 XCopy による配置は、次のような状況に適しています。  
  
- アプリケーションは自己完結型である。 実行するためにクライアントを更新する必要がない。  
  
- アプリケーション ファイルは、ビルド場所 (ローカル ディスク、UNC ファイル共有など) から発行場所 (Web サイト、UNC ファイル共有など) に移動する必要があります。  
  
- アプリケーションはシェル統合 ([スタート] メニューのショートカット、デスクトップ アイコンなど) を必要としない。  
  
 XCopy は、単純な配置シナリオには適していますが、複雑な配置機能が必要なシナリオには十分に対応できません。 特に、配置を堅牢な方法で管理する場合、XCopy を使用すると、スクリプトの作成、実行、および維持というオーバーヘッドが生じます。 さらに、XCopy は、バージョン管理、アンインストール、およびロールバックをサポートしません。  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Windows インストーラー  
 Windows インストーラを使用すると、アプリケーションを自己完結型の実行可能ファイルとしてパッケージ化し、クライアントに簡単に配布して実行できます。 さらに、Windows インストーラは Windows と共にインストールされ、デスクトップ、スタート メニュー、およびコントロール パネルの [プログラム] との統合が可能になります。  
  
 Windows インストーラは、アプリケーションのインストールとアンインストールを簡略化しますが、インストールされているアプリケーションをバージョン管理の観点から最新の状態に保つ機能は提供しません。  
  
 Windows インストーラの詳細については、「 [Windows インストーラの展開](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)」を参照してください。
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>ClickOnce の配置  
 ClickOnce は、Web スタイル以外のアプリケーションに対する Web スタイルのアプリケーションの配置を有効にします。 アプリケーションは、Web サーバーまたはファイル サーバーに公開され、これらのサーバーから配置されます。 ClickOnce は、Windows インストーラでインストールされたアプリケーションが実行するクライアント機能の完全な範囲をサポートしていませんが、次のようなサブセットをサポートしています。  
  
- [スタート] メニューおよび [プログラム] コントロール パネルとの統合。  
  
- バージョン管理、ロールバック、およびアンインストール。  
  
- アプリケーションを常に配置場所から起動するオンライン インストール モード。  
  
- 新しいバージョンがリリースされたときの自動更新。  
  
- ファイル拡張子の登録。  
  
 ClickOnce の詳細については、「 [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>WPF アプリケーションの配置  
 WPF アプリケーションの配置オプションは、アプリケーションの種類によって異なります。 展開の観点から見ると、WPF には次の 3 つの重要なアプリケーションの種類があります。  
  
- スタンドアロン アプリケーション。  
  
- マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーション。  
  
- XAML ブラウザー アプリケーション (XBaPs)  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>スタンドアロン アプリケーションの配置  
 スタンドアロン アプリケーションは、ClickOnce または Windows インストーラーを使用して展開されます。 いずれの場合も、スタンドアロン アプリケーションを実行するには、アプリケーションが完全に信頼されている必要があります。 完全な信頼は、Windows インストーラを使用して展開されるスタンドアロン アプリケーションに自動的に付与されます。 ClickOnce を使用して配置されたスタンドアロン アプリケーションには、自動的に完全な信頼が付与されません。 代わりに、スタンドアロン アプリケーションをインストールする前にユーザーが受け入れる必要があるセキュリティ警告ダイアログが表示されます。 受け入れた場合、スタンドアロン アプリケーションがインストールされ、完全な信頼が付与されます。 受け入れなかった場合、スタンドアロン アプリケーションはインストールされません。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>マークアップのみの XAML アプリケーションの配置  
 マークアップのみの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページは、通常 HTML ページなどの Web サーバーに発行され、Internet Explorer を使用して表示できます。 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、部分信頼セキュリティ サンドボックス内で実行され、インターネット ゾーン アクセス許可セットによって定義された制約が適用されます。 これにより、HTML ベースの Web アプリケーションと同等のセキュリティサンドボックスが提供されます。  
  
 WPF アプリケーションのセキュリティの詳細については、「[セキュリティ](../security-wpf.md)」を参照してください。  
  
 マークアップのみの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページは、XCopy または Windows インストーラを使用してローカル ファイル システムにインストールできます。 これらのページは、インターネット エクスプローラまたはエクスプローラを使用して表示できます。  
  
 XAML の詳細については、「[XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)」を参照してください。  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>XAML ブラウザー アプリケーションの配置  
 XBaps は、次の 3 つのファイルをデプロイする必要があるコンパイル済みアプリケーションです。  
  
- *ApplicationName*.exe: 実行可能アセンブリのアプリケーション ファイル。  
  
- *ApplicationName*.xbap: 配置マニフェスト。  
  
- *ApplicationName*.exe.manifest: アプリケーション マニフェスト。  
  
> [!NOTE]
> 配置マニフェストおよびアプリケーション マニフェストの詳細については、「[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください。  
  
 これらのファイルは、XBAP が構築されるときに生成されます。 詳細については、「[方法: 新しい WPF ブラウザー アプリケーション プロジェクトを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))」を参照してください。 マークアップのみの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページと同様に、XBaap は通常 Web サーバーに公開され、Internet Explorer を使用して表示されます。  
  
 XBaPs は、任意の展開手法を使用してクライアントに展開できます。 ただし、次の機能を提供するため、ClickOnce をお勧めします。  
  
1. 新しいバージョンが公開されたときの自動更新。  
  
2. 完全信頼で実行されている XBAP の昇格特権。  
  
 既定では、ClickOnce は、.deploy 拡張子を持つアプリケーション ファイルを公開します。 これは問題になる可能性がありますが、無効にできます。 詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)」を参照してください。  
  
 XAML ブラウザー アプリケーション (XAPS) の展開の詳細については、「 [WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)」を参照してください。  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>.NET Framework のインストール  
 WPF アプリケーションを実行するには、クライアントに Microsoft .NET Framework をインストールする必要があります。 WPF ブラウザー でホストされているアプリケーションを表示すると、クライアントが .NET Framework と共にインストールされているかどうかが自動的に検出されます。 .NET Framework がインストールされていない場合は、インストールを求めるメッセージが表示されます。  
  
 .NET Framework がインストールされているかどうかを検出するために、Internet Explorer には、次の拡張子を持つコンテンツ ファイルのフォールバック多目的インターネット メール拡張機能 (MIME) ハンドラーとして登録されているブートストラップ アプリケーションが含まれています。、および .アプリケーション。 これらのファイルの種類に移動し、.NET Framework がクライアントにインストールされていない場合、ブートストラップ アプリケーションはインストールのアクセス許可を要求します。 アクセス許可が与えられる場合は、.NET Framework もアプリケーションもインストールされません。  
  
 アクセス許可が与えられている場合、Internet Explorer は、Microsoft バックグラウンド インテリジェント転送サービス (BITS) を使用して .NET Framework をダウンロードしてインストールします。 .NET Framework のインストールが成功すると、最初に要求されたファイルが新しいブラウザー ウィンドウで開かれます。  
  
 詳細については、「[.NET Framework およびアプリケーションの配置](../../deployment/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)
- [セキュリティ](../security-wpf.md)
