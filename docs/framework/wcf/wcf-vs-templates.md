---
title: WCF Visual Studio テンプレート
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 72239f9e0e6d7882e6a29222c0b68f3bfd5d89d5
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2019
ms.locfileid: "56443238"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio テンプレート
Windows Communication Foundation (WCF) の Visual Studio テンプレートは、定義済みのプロジェクトと項目テンプレートを WCF サービスや周辺アプリケーションをすばやく作成する Visual Studio で使用することができます。  
  
## <a name="using-the-wcf-templates"></a>WCF テンプレートの使用  
 WCF Visual Studio テンプレートでは、サービスの開発の基本クラスの構造を提供します。 これには、サービス コントラクト、データ コントラクト、サービス実装、および構成の基本的な定義が含まれます。 これらのテンプレートを使用すると、最小限のコードを使用した単純なサービスや、より高度なサービスのビルド ブロックを作成できます。  
  
### <a name="wcf-service-library-project-template"></a>WCF サービス ライブラリ プロジェクト テンプレート  
 [新しいプロジェクト] ダイアログ ボックスで、WCF サービス ライブラリ プロジェクト テンプレートが使用可能な**Visual C# \WCF**と**Visual Basic\WCF**します。  
  
 使用して新しいプロジェクトを作成する場合、 **WCF サービス**テンプレート、新しいプロジェクトに自動的に次の 3 つのファイルが含まれています。  
  
-   サービス コントラクト ファイル (IService1.cs または IService1.vb)。 サービス コントラクトのファイルは、適用される WCF サービスの属性を持つインターフェイスです。 このファイルには、サービスの定義方法を示す単純なサービスの定義が含まれています。その他に、パラメーター ベースの操作や、単純なデータ コントラクトのサンプルも含まれています。 これは、WCF サービス プロジェクトを作成したら、コード エディターに表示される既定のファイルです。  
  
-   サービス実装ファイル (Service1.cs または Service1.vb)。 サービス実装ファイルは、サービス コントラクト ファイルに定義されているコントラクトを実装します。  
  
-   アプリケーション構成ファイル (App.config)。 構成ファイルでは、セキュリティで保護された HTTP バインディングで WCF サービス モデルの基本的な要素を提供します。 サービスのエンドポイントも含まれており、メタデータの交換も可能です。  
  
> [!NOTE]
>  Visual Studio を使用して実行した場合、プロジェクトの構成ファイルと App.config ファイルを認識するように構成、 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)既定の構成します。 サービス ライブラリを実行可能ファイルでホストする場合は、DLL の構成ファイルは無効になるため、その実行可能ファイルの構成ファイルに構成コードを移動する必要があります。  
  
### <a name="wcf-service-application-template"></a>WCF サービス アプリケーション テンプレート  
 [新しいプロジェクト] ダイアログ ボックスで、WCF サービス アプリケーション テンプレートが使用可能な**Visual C# \WCF**と**Visual Basic\WCF**します。  
  
 使用して新しいプロジェクトを作成する場合、 **WCF Web アプリケーション サービス**テンプレート プロジェクトにはには、次の 4 つのファイルが含まれています。  
  
-   サービス ホスト ファイル (service1.svc)。  
  
-   サービス コントラクト ファイル (IService1.cs または IService1.vb)。  
  
-   サービス実装ファイル (Service1.svc.cs または Service1.svc.vb)。  
  
-   Web 構成ファイル (Web.config)。  
  
 このテンプレートでは、自動的に Web サイトが作成されて (仮想ディレクトリに配置されます)、サービスがホストされます。  
  
### <a name="wcf-web-site-template"></a>WCF Web サイト テンプレート  
 新しいプロジェクト ダイアログ ボックスで、WCF Web サイト テンプレートが使用可能な**Visual C# \Web Site\WCF サービス**と**Visual Basic\Web \ wcf サービス**します。 これによって、WCF サービス アプリケーションのテンプレートと同じファイルが作成されますが、ASP.NET Web サイトであるかのように編成されます。 App_Code フォルダーと App_Data フォルダーが作成されます。  
  
### <a name="wcf-service-item-template"></a>WCF サービス項目テンプレート  
 WCF サービス項目テンプレートは、WCF サービスを既存の Visual Studio プロジェクトに追加する簡単な方法を提供するカスタム テンプレートです。  
  
 このテンプレートを使用するには、**ソリューション エクスプ ローラー**ウィンドウで、プロジェクトの名前を右クリックし、 をポイント**追加**、 をクリックし、**新しい項目の**を起動する、**新規追加項目** ダイアログ ボックス。  
  
 サービス インターフェイス ファイルとサービス実装ファイルがルート プロジェクト フォルダーに配置されます。  
  
 このテンプレートでは、新しいサービスの構成セクションが既存の構成ファイルと互換性がある場合にそれらがマージされます。  
  
 既存のプロジェクトが Web プロジェクトの場合は、サービス ホスト ファイル (service1.svc) も作成されます。  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF サービス プロジェクト/項目テンプレート  
 これらのテンプレートは、WCF サービスをワークフロー サービスをホストする作成し、これは、web サービスのようにアクセスできるワークフローです。 この他に、XAML プログラミング モデルや命令型プログラミング モデルのテンプレートも用意されています。 これらのテンプレートを使用すると、シーケンシャル ワークフローやステート マシン ワークフローを作成できます。 これらのワークフローの種類の詳細については、次を参照してください。[方法。ワークフロー作成](../windows-workflow-foundation/how-to-create-a-workflow.md)です。 ワークフロー プロジェクトの作成の詳細については、[従来のワークフロー プロジェクトを作成する](/visualstudio/workflow-designer/creating-legacy-workflow-projects)を参照してください。  
  
 XOML 型のワークフローが使用される代わりにコード ベースのときに、visual Studio デザイナーの応答性が向上します。 XOML ワークフローは、既定で作成されるワークフロー型です。  
  
### <a name="wcf-syndication-service-library-template"></a>WCF 配信サービス ライブラリ テンプレート  
 このテンプレートでは、WCF サービスとして RSS または ATOM 形式のフィードを公開することができます。 詳細については、[WCF 配信](../../../docs/framework/wcf/feature-details/wcf-syndication.md)を参照してください。  
  
#### <a name="changing-the-address-of-the-feed"></a>フィードのアドレスの変更  
 配信テンプレートは、実行中に Internet Explorer を使用します。 プロジェクトを右クリックすると**ソリューション エクスプ ローラー** Visual Studio で、次のように選択します**プロパティ**を選択してから、**デバッグ**とタブには、の既定のアドレスを表示できます、。テンプレート。 Internet Explorer は、このアドレスにあるフィードを開きます。  
  
 内のアドレスを変更する必要がありますもフィードのアドレスを変更する場合、**デバッグ**タブ。これを変更しないと、Internet Explorer が既定のアドレスにあるフィードを開こうとして、エラーになります。  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>AJAX 対応 WCF サービス項目テンプレート  
 このテンプレートは、WCF サービスとしての AJAX コントロールを公開します。 AJAX コントロールの詳細については、、 [AJAX コントロールに関するドキュメント](https://go.microsoft.com/fwlink/?LinkId=96717)を参照してください。  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Silverlight 対応 WCF サービス項目テンプレート  
 このテンプレートは、Silverlight クライアントまたはフロントエンドにデータを提供する Web サービスを作成します。 テンプレートは、サービス コードと、Silverlight クライアントとの通信をサポートする構成を含む WCF サービスを作成する Web サイトまたは Web アプリケーション プロジェクトに追加できます。 使用することができますし、**サービス参照の追加**をクライアントにサービスのクライアント プロキシを追加して、Silverlight クライアントと Silverlight 対応 WCF サービスの間でデータを交換します。  
  
 このテンプレートにアクセスするでの Web サイトまたは Web アプリケーション プロジェクトを右クリックし**ソリューション エクスプ ローラー**、 をクリックして**新しい項目の追加**、 をクリック**Silverlight 対応 WCF サービス**します。  
  
> [!NOTE]
>  Silverlight 対応 WCF サービスは、セキュリティ設定を一切有効にせずに `basicHttpBinding` エンドポイントを公開します。 したがって、サービスに接続しているすべてのクライアントが、このサービスに関する情報を取得できることになります。 また、サービスとクライアント間で交換されるメッセージの署名と暗号化も行われません。 エンドポイントを正しくセキュリティで保護するには、ASP.NET 認証や HTTPS などのメカニズムを使用する必要があります。  
  
## <a name="see-also"></a>関連項目
- [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
