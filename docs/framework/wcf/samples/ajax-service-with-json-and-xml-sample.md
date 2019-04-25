---
title: JSON および XML 形式の AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: a93e7bdf8cda88a1e86b59e5c3d37f049bdfcf28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304793"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON および XML 形式の AJAX サービスのサンプル
このサンプルでは、Windows Communication Foundation (WCF) を使用して、JavaScript Object Notation (JSON) または XML データを返す Asynchronous JavaScript and XML (AJAX) サービスを作成する方法を示します。 AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。 このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプル。  
  
 他の AJAX サンプルとは異なり、このサンプルでは ASP.NET AJAX および <xref:System.Web.UI.ScriptManager> コントロールを使用しません。 いくつか追加の構成では、WCF AJAX サービスは、JavaScript を使用して HTML ページからアクセスでき、このシナリオを次に示します。 WCF を使用して ASP.NET AJAX での例は、次を参照してください。 [AJAX のサンプル](ajax.md)します。
  
 このサンプルでは、JSON と XML 間で操作の応答のタイプを切り替える方法を示します。 この機能は、サービスが ASP.NET AJAX または HTML/JavaScript クライアント ページでアクセスできるように構成されているかどうかにかかわらず使用できます。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。
  
ASP.NET AJAX 以外のクライアントを使用するには、.svc ファイルで <xref:System.ServiceModel.Activation.WebServiceHostFactory> (<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ではありません) を使用します。 <xref:System.ServiceModel.Activation.WebServiceHostFactory> によって、<xref:System.ServiceModel.Description.WebHttpEndpoint> 標準エンドポイントがサービスに追加されます。 エンドポイントは; .svc ファイルに相対する空のアドレスで構成されます。つまり、サービスのアドレスは`http://localhost/ServiceModelSamples/service.svc`操作名以外にない追加のサフィックス。  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。 追加の変更が不要な場合は、このセクションを削除できます。  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 既定のデータ形式<xref:System.ServiceModel.Description.WebHttpEndpoint>の既定のデータ形式は XML で、<xref:System.ServiceModel.Description.WebScriptEndpoint>は JSON です。 詳細については、次を参照してください。 [ASP.NET を使用せずに作成する WCF AJAX サービス](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)します。  
  
 次のサンプルのサービスには、2 つの操作で標準の WCF サービスです。 どちらの操作でも <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> または <xref:System.ServiceModel.Web.WebGetAttribute> 属性に <xref:System.ServiceModel.Web.WebInvokeAttribute> の本文スタイルが必要です。この本文スタイルは、`webHttp` 動作に固有で、JSON/XML データ形式の切り替えに影響しません。  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 操作の応答の形式は XML では、既定として指定の設定、 [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)動作します。 ただし、応答形式を明示的に指定することをお勧めします。  
  
 その他の操作では `WebInvokeAttribute` 属性を使用し、応答に XML ではなく JSON を明示的に指定します。  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 どちらの場合も、操作が返す複合型のことに注意してください。 `MathResult`、標準の WCF データ コントラクト型であります。  
  
 クライアント Web ページ XmlAjaxClientPage.htm には、ユーザーがクリックしたときに、前の 2 つの操作のいずれかを呼び出す JavaScript コードが含まれています、 **calculation (return JSON) を実行**または**calculation (return XML) の実行**ページ上のボタン。 サービスを呼び出すコードによって JSON 本文が作成され、HTTP POST を使用して送信されます。 要求を手動で作成、JavaScript とは異なり、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルとその他のサンプル ASP.NET AJAX を使用します。  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 サービスが応答すると、応答はこれ以上の処理を行わずにページ上のテキスト ボックスに表示されます。 これは、使用される XML および JSON データ形式を直接確認できるように、デモンストレーションの目的で実装されています。  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. 」の説明に従って、ソリューション XmlAjaxService.sln をビルド[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
3. 移動します`http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm`(開かないで XmlAjaxClientPage.htm プロジェクト ディレクトリからブラウザーで)。  
  
## <a name="see-also"></a>関連項目

- [HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
