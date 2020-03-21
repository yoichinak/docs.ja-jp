---
title: ASP.NET を使用せずに WCF AJAX サービスを作成する方法
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185235"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET を使用せずに WCF AJAX サービスを作成する方法
Windows 通信基盤 (WCF) AJAX サービスは ASP.NET、任意の JavaScript 対応 Web ページからアクセスできます。 このトピックでは、このような WCF サービスを作成する方法について説明します。  
  
 Wcf を ASP.NET AJAX で使用する方法については、「 [ASP.NET AJAX の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)」を参照してください。  
  
 WCF AJAX サービスの作成には、次の 3 つの部分があります。  
  
- ブラウザーからアクセスできる AJAX エンドポイントの作成  
  
- AJAX 互換サービス コントラクトの作成  
  
- WCF AJAX サービスへのアクセス  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX エンドポイントの作成  
 WCF サービスで AJAX サポートを有効にする最も基本的な<xref:System.ServiceModel.Activation.WebServiceHostFactory>方法は、次の例のように、サービスに関連付けられた .svc ファイルで を使用することです。  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 構成を使用して AJAX エンドポイントを追加することもできます。 次のコード スニペットに示すように、サービス エンドポイントで <xref:System.ServiceModel.WebHttpBinding> を使用し、<xref:System.ServiceModel.Description.WebHttpBehavior> を使用してこのエンドポイントを構成します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 動作例については[、「JSON と XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)を使用した AJAX サービス」を参照してください。  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>AJAX 互換サービス コントラクトの作成  
 既定では、AJAX エンドポイントを介して公開されるサービス コントラクトは、XML 形式でデータを返します。 また、次の例に示すように、既定では、エンドポイント アドレスの後に操作名を追加した URL に対する HTTP POST 要求によって、サービス操作にアクセスできます。  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 この操作には、HTTP POST を`http://serviceaddress/endpointaddress/GetCities`使用して XML メッセージを返すことができます。  
  
 Web プログラミング モデルを活用することで、これらの基本的な部分をカスタマイズできます。 たとえば、<xref:System.ServiceModel.Web.WebGetAttribute> 属性または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、操作が応答する HTTP 動詞を制御したり、これらの属性の `UriTemplate` プロパティを使用して、カスタム URI を指定したりできます。 詳細については[、「WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)」を参照してください。  
  
 AJAX サービスでは、JSON データ形式がよく使用されます。 XML ではなく JSON を返す操作を作成するには、<xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (または <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) プロパティを <xref:System.ServiceModel.Web.WebMessageFormat.Json> に設定します。 「[スタンドアロン JSON シリアル化」](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)トピックでは、組み込みの .NET 型とデータ コントラクト型が JSON にマップされる方法について説明します。  
  
 JSON の要求と応答は、通常 1 つの項目のみで構成されます。 前述の `GetCities` 操作の場合、要求は次のようなステートメントになります。  
  
```json
"na"  
```  
  
 この要求に対する応答は、次のようなステートメントになります。  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 操作で追加のパラメーターを受け取る場合は、両方のパラメーターを 1 つの JSON オブジェクトにラップするために、要求スタイルをラップする必要があります。 このスタイルの JSON メッセージの一例を次に示します。  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 次のコントラクトがこのメッセージを受け入れます。  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX サービスへのアクセス  
 WCF AJAX エンドポイントは、常に JSON 要求と XML 要求の両方を受け入れます。  
  
 コンテンツタイプが "application/json" の HTTP POST 要求は JSON として扱われ、XML を示すコンテンツタイプ (例えば「text/xml」) を持つ要求は XML として扱われます。  
  
 HTTP GET 要求では、URL 自体にすべての要求パラメーターが含まれています。  
  
 エンドポイントに対して HTTP 要求を作成する方法は、ユーザーが自由に決定できます。 また、要求の本文を構成する JSON の作成についても、ユーザーが完全に制御できます。 JavaScript からの要求の作成例については[、JSON と XML を使用した AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)を参照してください。
