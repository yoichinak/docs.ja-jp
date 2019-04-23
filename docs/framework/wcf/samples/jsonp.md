---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767540"
---
# <a name="jsonp"></a>JSONP
このサンプルでは、WCF REST サービスの JSONP (JSON with Padding) をサポートする方法を示します。 JSONP とは、現在のドキュメントでスクリプト タグを生成してドメイン間スクリプトを呼び出す際に使用される変換です。 結果は、指定したコールバック関数で返されます。 JSONP は、`<script src="http://..." >` などのタグで任意のドメインからのスクリプトを評価でき、このようなタグによって取得されたスクリプトを既に他の関数が定義されている範囲で評価するという考えに基づいています。

## <a name="demonstrates"></a>使用例
 JSONP によるドメイン間スクリプト。

## <a name="discussion"></a>説明
 このサンプルには、ブラウザーで表示された後にスクリプト ブロックを動的に追加する Web ページが含まれています。 このスクリプト ブロックは、`GetCustomer` 操作を 1 つ持つ WCF REST サービスを呼び出します。 WCF REST サービスは、コールバック関数名でラップされた顧客の名前とアドレスを返します。 WCF REST サービスが応答を返すと、顧客データを使用して Web ページ上のコールバック関数が呼び出され、このコールバック関数によって Web ページ上に顧客データが表示されます。 スクリプト タグの挿入とコールバック関数の実行は、ASP.NET AJAX ScriptManager コントロールによって自動的に処理されます。 次のコードに示すように、使用パターンはすべての ASP.NET AJAX プロキシと同じで、JSONP を有効にするための行が 1 つ追加されます。

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Web ページでは、WCF REST サービスを呼び出すことができます。これは、WCF REST サービスが、<xref:System.ServiceModel.Description.WebScriptEndpoint> が `crossDomainScriptAccessEnabled` に設定された `true` を使用しているからです。 Web.config ファイルでこれらの構成が終わったら、 \<system.serviceModel > 要素。

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。 ときに`crossDomainScriptAccessEnabled`に設定されている`true`操作の応答形式が JSON と、WCF インフラストラクチャがコールバック クエリ文字列パラメーターの要求の URI を検査し、コールバック クエリ文字列の値を使用して JSON 応答をラップします。パラメーター。 このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。 ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。

 サンプルを 2 つの ASP.NET web アプリケーションの構成: WCF サービスだけが含まれていて、もう 1 つにはサービスを呼び出す .aspx web ページが含まれています。 ソリューションの実行中、Visual Studio 2012 をホストする別のポート上の 2 つの web サイトが異なるドメイン上のサービスとクライアントの居住環境を作成します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. JSONP サンプルのソリューションを開きます。  
  
2. F5 キーを押して起動`http://localhost:26648/JSONPClientPage.aspx`ブラウザーにします。  
  
3. 通知は、ページの読み込み後に"Name"および"Address"のテキスト入力は、値が格納されます。  これらの値は、ブラウザーはページのレンダリングを完了した後に、WCF サービスへの呼び出しから提供されたものです。
