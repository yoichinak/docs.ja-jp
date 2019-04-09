---
title: SystemWebRouting 統合サンプル
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 244a7b7b73217086864b16945bc1521a3383aeac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147811"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 統合サンプル
このサンプルでは、<xref:System.Web.Routing> 名前空間のクラスとのホスト層の統合を示します。 <xref:System.Web.Routing> 名前空間のクラスを使用すると、物理リソースに直接対応しない URL をアプリケーションで使用できます。 Web のルーティングを使用すると、開発者は実際の WCF サービスにバックアップし、マップされている HTTP 仮想アドレスの作成ができます。 これは、物理ファイルやリソースを配置せずに WCF サービスをホストする必要がある場合、または .html や .aspx などのファイルがない URL を使用してサービスにアクセスする必要がある場合に役立ちます。 このサンプルでは、<xref:System.Web.Routing.RouteTable> クラスを使用して、global.asax で定義された実行中のサービスにマップされる仮想 URI を作成する方法を示します。 

> [!NOTE]
>  <xref:System.Web.Routing> 名前空間のクラスは、HTTP でホストされるサービスに対してのみ機能します。  
  
この例では、WCF を使用して、2 つの RSS フィードを作成します。、`movies`フィードと`channels`フィード。 サービスをアクティブ化する Url は、拡張機能が含まれていないに登録されている、`Application_Start`のメソッド、`Global`から派生したクラス、<xref:System.Web.HttpApplication>クラス。  
  
> [!NOTE]
>  このサンプルでは、インターネット インフォメーション サービス (IIS) 7.0 のみは機能し、後で、IIS 6.0 とメソッドを使用して、さまざまな拡張機能のない Url をサポートするため。  

#### <a name="to-download-this-sample"></a>このサンプルをダウンロードするには
  
このサンプルは、コンピューターに既にインストールされてことがあります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  Visual Studio を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  ソリューションを実行して Web 開発サーバーを起動するには、F5 キーを押します。  
  
     サンプルのディレクトリの一覧が表示されます。 ファイル拡張子が .svc のファイルがないことに注意してください。  
  
3.  アドレス バーに追加`movies`、URL にのでその it 読み取り`http://localhost:[port]/movies`ENTER キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
4.  アドレス バーに追加`channels`、URL にこれが読み取り`http://localhost:[port]/channels`ENTER キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
5.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
     開発サーバーが終了しない場合、通知領域アイコンを右クリックし **停止**します。  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>このサンプルを使用するには (IIS でホストする場合)  
  
1.  Visual Studio を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。  
  
3.  インターネット インフォメーション サービス (IIS) マネージャーで Web アプリケーションを作成します。  
  
    1.  IIS マネージャーで、右クリックして、**既定の Web サイト**選択**アプリケーションを追加**します。  
  
    2.  **エイリアス**、入力`WebRoutingIntegration`します。  
  
    3.  **物理パス**プロジェクト内の Service フォルダーを選択します。  
  
    4.  **[OK]** を押します。  
  
4.  Web アプリケーションを右クリックしてアプリケーションを起動**アプリケーションの管理**し**参照**します。  
  
5.  アドレス バーに追加`movies`、URL にこれが読み取り`http://localhost:[port]/movies`ENTER キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
6.  アドレス バーに追加`channels`、URL にこれが読み取り`http://localhost:[port]/channels`ENTER キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
7.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
 このサンプルは、HTTP でホストされたサービスの要求をルーティングするために、<xref:System.Web.Routing> 名前空間のクラスを使用してホスト層を構成できることを示しています。  
  
> [!NOTE]
>  既定のアプリケーション プール バージョンを更新する必要があります[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]バージョン 2 に設定されている場合。  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホストおよび永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)
