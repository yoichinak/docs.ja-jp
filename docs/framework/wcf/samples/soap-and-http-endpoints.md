---
title: SOAP エンドポイントおよび HTTP エンドポイント
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144020"
---
# <a name="soap-and-http-endpoints"></a>SOAP エンドポイントおよび HTTP エンドポイント
このサンプルでは、RPC ベースのサービスを実装し、それを SOAP 形式で公開する方法と、WCF Web プログラミング モデルを使用して "プレーンな古い XML" (POX) 形式で公開する方法を示します。 サービスの HTTP バインディングの詳細については、基本 HTTP[サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルを参照してください。 このサンプルでは、さまざまなバインドを使用して SOAP および HTTP で RPC ベースのサービスを公開する方法について詳しく示します。  
  
## <a name="demonstrates"></a>対象  
 WCF を使用して、SOAP および HTTP 経由で RPC サービスを公開します。  
  
## <a name="discussion"></a>ディスカッション  
 このサンプルは、WCF サービスを含む Web アプリケーション プロジェクト (サービス) と、SOAP および HTTP バインディングを使用してサービス操作を呼び出すコンソール アプリケーション (クライアント) の 2 つのコンポーネントで構成されます。  
  
 WCF サービスは、入力として渡`GetData`された`PutData`文字列をエコーする 2 つの操作を公開します。 サービス操作には、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用して注釈が付けられます。 これらの属性は、これらの操作の HTTP 投影を制御します。 また、サービス操作には、<xref:System.ServiceModel.OperationContractAttribute> を使用して注釈が付けられます。この属性では、サービス操作を SOAP バインディングで公開できます。 サービスの `PutData` メソッドは <xref:System.ServiceModel.Web.WebFaultException> をスローします。この例外は、HTTP では HTTP ステータス コードを使用して返送され、SOAP では SOAP エラーとして返送されます。  
  
 Web.config ファイルは、次の 3 つのエンドポイントを使用して WCF サービスを構成します。  
  
- SOAP ベースのクライアントからアクセスするためのサービス メタデータを公開する ~/service.svc/mex エンドポイント  
  
- クライアントが HTTP バインディングを使用してサービスにアクセスできる ~/service.svc/http エンドポイント  
  
- クライアントが HTTP バインディングで SOAP を使用してサービスにアクセスできる ~/service.svc/soap endpoint エンドポイント  
  
 HTTP エンドポイントは、 に`webHttp``helpEnabled`設定されている標準エンドポイント><で`true`構成されます。 その結果、サービスは、HTTP ベースのクライアントがサービスにアクセスするために使用できる、XHTML ベースのヘルプ ページ (~/service.svc/http/help) を公開します。  
  
 クライアント プロジェクトでは、SOAP プロキシ **([サービス参照の追加]** を使用して生成) を使用して<xref:System.Net.WebClient>サービスにアクセスし、 を使用してサービスにアクセスする方法を示します。  
  
 サンプルは、1 つの Web ホスト サービスと 1 つのコンソール アプリケーションで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. SOAP および HTTP エンドポイント サンプルのソリューションを開きます。  
  
2. Ctrl + Shift + B キーを押して、ソリューションをビルドします。  
  
3. まだ開いていない場合は、Ctrl キーを押しながら W キーを押して、S キーを押して**ソリューション エクスプローラー**ウィンドウを開きます。  
  
4. [**ソリューション エクスプローラー** ] ウィンドウで **、Service**プロジェクトを右クリックし、[**デバッグ**] コンテキスト メニュー オプションの上にカーソルを置き、[**新しいインスタンスの開始**] コンテキスト メニューを表示します。 [**新しいインスタンスの開始 ]** をクリックします。 これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5. ソリューション エクスプローラー ウィンドウで、クライアント プロジェクトを右クリックし、コンテキスト メニューの [**デバッグ**] の上にカーソルを置き、**新しいインスタンスの開始**のコンテキスト メニューを表示します。 [**新しいインスタンスの開始 ]** をクリックします。  
  
6. クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7. サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8. クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows 通知領域で、ASP.NET開発サーバーアイコンを右クリックし、コンテキスト メニューから **[停止**] を選択します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
