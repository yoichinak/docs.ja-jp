---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 1fc85838d7491f94b8da1e0ab458d6d021cd2b32
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989775"
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

 Web ページでは、WCF REST サービスを呼び出すことができます。これは、WCF REST サービスが、<xref:System.ServiceModel.Description.WebScriptEndpoint> が `crossDomainScriptAccessEnabled` に設定された `true` を使用しているからです。 これらの構成はどちらも、system.servicemodel > 要素の\<web.config ファイルで行います。

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

 ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。 が`crossDomainScriptAccessEnabled` に`true`設定され、操作の応答形式が JSON である場合、WCF インフラストラクチャは、コールバッククエリ文字列パラメーターの要求の URI を検査し、コールバッククエリ文字列の値を使用して json 応答をラップします。引き. このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。 ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。

 このサンプルは2つの ASP.NET web アプリケーションで構成されています。1つは WCF サービスだけを含み、もう1つはサービスを呼び出す .aspx web ページを含んでいます。 ソリューションを実行すると、Visual Studio 2012 は異なるポートで2つの web サイトをホストします。これにより、サービスとクライアントが異なるドメイン上に存在する環境が作成されます。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1. JSONP サンプルのソリューションを開きます。  
  
2. F5 キーを押し`http://localhost:26648/JSONPClientPage.aspx`て、ブラウザーでを起動します。  
  
3. ページが読み込まれた後、"名前" と "アドレス" のテキスト入力に値が設定されていることに注意してください。  これらの値は、ブラウザーがページの表示を終了した後に、WCF サービスの呼び出しから指定されました。
