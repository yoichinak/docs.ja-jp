---
title: ASP.NET キャッシュ統合
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 989f10defa3cde2885d9002b2189751dfe2b920a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587666"
---
# <a name="aspnet-caching-integration"></a>ASP.NET キャッシュ統合
このサンプルでは、WCF WEB HTTP プログラミング モデルで ASP.NET 出力キャッシュを利用する方法を示します。 ここでは、ASP.NET 出力キャッシュ統合機能について集中的に説明します。  
  
## <a name="demonstrates"></a>使用例  
 ASP.NET 出力キャッシュとの統合  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>説明  
 サンプルでは、 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET を使用する Windows Communication Foundation (WCF) サービスでのキャッシュを出力します。 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用される属性で、特定の操作からの応答に適用する構成ファイル内のキャッシュ プロファイルの名前を指定します。  
  
 サービスのサンプル プロジェクトの Service.cs ファイルの両方、`GetCustomer`と`GetCustomers`とマークされた操作は、 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>、"CacheFor60Seconds"キャッシュ プロファイル名を提供します。 キャッシュ プロファイル"CacheFor60Seconds"は提供サービス プロジェクトの Web.config ファイルで、<`caching`> 要素の <`system.web`>。 このキャッシュ プロファイルでの値、`duration`属性には「60」があるため、このプロファイルに関連付けられた応答は、ASP.NET 出力キャッシュに 60 秒間キャッシュされます。 また、このキャッシュ プロファイルの`varmByParam`属性の値が異なるため要求を"format"に設定されて、`format`クエリ文字列パラメーターの応答は別々 にキャッシュします。 最後に、キャッシュ プロファイルの`varyByHeader`Accept ヘッダー値が異なる要求の応答は別々 にキャッシュがあるために、属性が"Accept"に設定します。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 WCF のチャネル ファクトリのような他の .NET Framework クラスを使用してサービスにアクセスすることも、<xref:System.Net.WebClient>します。 SDK 内の他のサンプル (など、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプル) WCF サービスとの通信にこれらのクラスを使用する方法を説明します。  
  
## <a name="to-run-the-sample"></a>サンプルを実行するには  
 このサンプルは、3 つのプロジェクトで構成されます。  
  
- **[サービス]**:Web アプリケーション プロジェクトを ASP.NET でホストされる WCF HTTP サービスが含まれています。  
  
- **クライアント**:サービスを呼び出すコンソール アプリケーション プロジェクト。  
  
- **一般的な**:クライアントとサービスによって使用される Customer 型を含む共有ライブラリ。  
  
 クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. ASP.NET キャッシュ統合サンプルのソリューションを開きます。  
  
2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3. 場合、**ソリューション エクスプ ローラー**ウィンドウが開いていない、CTRL + W キーを押しながら S キーを押します。  
  
4. **ソリューション エクスプ ローラー**ウィンドウで、右クリックして、**サービス**順に選択して**新しいインスタンスを開始**します。 これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5. **ソリューション エクスプ ローラー**ウィンドウで、右クリックして、**クライアント**順に選択して**新しいインスタンスを開始**します。  
  
6. クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7. サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8. クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows 通知領域に、ASP.NET 開発サーバーのアイコンを右クリックし、選択**停止**します。
