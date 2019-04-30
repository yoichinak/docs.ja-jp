---
title: SOAP エンドポイントおよび HTTP エンドポイント
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 07f0c5a5a66683cf636595824b2ccaeaf1ab6a63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007815"
---
# <a name="soap-and-http-endpoints"></a>SOAP エンドポイントおよび HTTP エンドポイント
このサンプルでは、RPC ベースのサービスを実装して、SOAP 形式と WCF Web プログラミング モデルを使用して"Plain Old XML"(POX) 形式で公開する方法を示します。 参照してください、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サービス用の HTTP バインドの詳細についてはサンプルです。 このサンプルでは、さまざまなバインドを使用して SOAP および HTTP で RPC ベースのサービスを公開する方法について詳しく示します。  
  
## <a name="demonstrates"></a>使用例  
 SOAP および WCF を使用して HTTP 経由の RPC サービスを公開します。  
  
## <a name="discussion"></a>説明  
 このサンプルは、2 つのコンポーネントで構成されています: WCF サービスと SOAP と HTTP バインディングを使用してサービス操作を呼び出すコンソール アプリケーション (クライアント) を含む Web アプリケーション プロジェクト (サービス)。  
  
 2 つの操作を公開する WCF サービス`GetData`と`PutData`– 入力として渡された文字列をエコーします。 サービス操作には、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用して注釈が付けられます。 これらの属性は、これらの操作の HTTP 投影を制御します。 また、サービス操作には、<xref:System.ServiceModel.OperationContractAttribute> を使用して注釈が付けられます。この属性では、サービス操作を SOAP バインディングで公開できます。 サービスの `PutData` メソッドは <xref:System.ServiceModel.Web.WebFaultException> をスローします。この例外は、HTTP では HTTP ステータス コードを使用して返送され、SOAP では SOAP エラーとして返送されます。  
  
 Web.config ファイルでは、3 つのエンドポイントを持つ WCF サービスを構成します。  
  
- SOAP ベースのクライアントからアクセスするためのサービス メタデータを公開する ~/service.svc/mex エンドポイント  
  
- クライアントが HTTP バインディングを使用してサービスにアクセスできる ~/service.svc/http エンドポイント  
  
- クライアントが HTTP バインディングで SOAP を使用してサービスにアクセスできる ~/service.svc/soap endpoint エンドポイント  
  
 HTTP エンドポイントが構成されている、<`webHttp`> 標準エンドポイントを持つ`helpEnabled`に設定`true`します。 その結果、サービスは、HTTP ベースのクライアントがサービスにアクセスするために使用できる、XHTML ベースのヘルプ ページ (~/service.svc/http/help) を公開します。  
  
 クライアント プロジェクトでは、SOAP プロキシを使用してサービスへのアクセスを示します (を使用して生成**サービス参照の追加**) を使用して、サービスへのアクセスと<xref:System.Net.WebClient>します。  
  
 サンプルは、1 つの Web ホスト サービスと 1 つのコンソール アプリケーションで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. SOAP および HTTP エンドポイント サンプルのソリューションを開きます。  
  
2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3. それがまだ開いていない場合は CTRL + W、S を開くキーを押して、**ソリューション エクスプ ローラー**ウィンドウ。  
  
4. **ソリューション エクスプ ローラー**ウィンドウで、右クリックし、**サービス**プロジェクトし、カーソルを置く、**デバッグ**コンテキスト メニュー オプションように、**新しい開始インスタンス**コンテキスト メニューが表示されます。 クリックして**新しいインスタンスを開始**します。 これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5. ソリューション エクスプ ローラー ウィンドウからクライアント プロジェクトを右クリックし、カーソルを置く、**デバッグ**コンテキスト メニュー オプションように、**新しいインスタンスを開始**コンテキスト メニューが表示されます。 クリックして**新しいインスタンスを開始**します。  
  
6. クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7. サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8. クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows 通知領域には、ASP.NET 開発サーバーのアイコンを右クリックして**停止**コンテキスト メニュー。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
