---
title: 基本的な HTTP サービス
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 247fedac339ebb22a6ef3b3e84f557451ecaaf1a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337111"
---
# <a name="basic-http-service"></a>基本的な HTTP サービス
このサンプルでは、"POX"(Plain Old XML) サービス-Windows Communication Foundation (WCF) REST プログラミング モデルを使用するとよく呼ばれる、HTTP ベース、RPC ベース サービスを実装する方法を示します。 このサンプルは、2 つのコンポーネントで構成されています。 自己ホスト型 WCF HTTP サービス (Service.cs) と、サービスを作成し、への呼び出しを、コンソール アプリケーション (Program.cs)。  
  
## <a name="sample-details"></a>サンプルの詳細  
 2 つの操作を公開する WCF サービス`EchoWithGet`と`EchoWithPost`、入力として渡された文字列が返されます。  
  
 `EchoWithGet` 操作には、この操作で HTTP <xref:System.ServiceModel.Web.WebGetAttribute> 要求が処理されることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebGetAttribute> では明示的に <xref:System.UriTemplate> を指定しないため、操作には `s` という名前のクエリ文字列パラメーターを使用して渡される入力文字列が必要です。 サービスが要求する URI の形式は、<xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> プロパティを使用してカスタマイズすることができます。  
  
 `EchoWithPost` 操作には、これが `GET` 操作ではなく、副作用があることを示す、<xref:System.ServiceModel.Web.WebInvokeAttribute> という注釈が付いています。 <xref:System.ServiceModel.Web.WebInvokeAttribute> では明示的に `Method` を指定しないため、この操作は、要求本文に文字列が含まれる HTTP `POST` 要求を処理します (XML 形式など)。 HTTP メソッド、要求の URI の形式は、それぞれ <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティ、<xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> プロパティを使用して、カスタマイズすることができます。  
  
 App.config ファイルでは、<xref:System.ServiceModel.Description.WebHttpEndpoint> に設定されている <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> プロパティを持つ既定の `true` を使用して、WCF サービスを構成します。 WCF インフラストラクチャに自動のベース HTML ヘルプ ページを作成するため、`http://localhost:8000/Customers/help`サービスへの HTTP 要求を作成する方法と、サービスの HTTP 応答を使用する方法に関する情報を提供します。  
  
 Program.cs では、WCF チャネル ファクトリを使用して、サービスとプロセスの応答を呼び出す方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 <xref:System.Net.HttpWebRequest> や <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1. 基本的な HTTP サービス サンプルのソリューションを開きます。 Visual Studio 2012 を起動するときに、正常に実行するには、サンプルの管理者として実行する必要があります。 これは、Visual Studio 2012 のアイコンを右クリックして選択**管理者として実行**コンテキスト メニュー。  
  
2. Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションを、デバッグを行わずに実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。 サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
3. 任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
