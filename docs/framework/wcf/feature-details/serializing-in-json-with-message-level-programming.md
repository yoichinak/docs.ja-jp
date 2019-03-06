---
title: メッセージ レベルのプログラミングによる JSON 形式でのシリアル化
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: bd7ec1d2e8a4becf182ec9493d8f486b55182cd5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379706"
---
# <a name="serializing-in-json-with-message-level-programming"></a>メッセージ レベルのプログラミングによる JSON 形式でのシリアル化
WCF は、JSON 形式でのデータのシリアル化をサポートします。 このトピックでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用して型をシリアル化することを WCF に命令する方法について説明します。  
  
## <a name="typed-message-programming"></a>型指定されたメッセージのプログラミング  
 
  <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> がサービス操作に適用されるときに使用されます。 どちらの属性でも、`RequestFormat` と `ResponseFormat` を指定できます。 要求と応答の JSON を使用します。 これらの両方を設定`WebMessageFormat.Json`します。  JSON を使用するために使用する必要があります、 <xref:System.ServiceModel.WebHttpBinding>、自動的に構成される<xref:System.ServiceModel.Description.WebHttpBehavior>します。 WCF のシリアル化の詳細については、次を参照してください。[シリアル化および逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)します。 JSON と WCF の詳細については、次を参照してください。[サービス_ステーション - An の概要を RESTful サービスと WCF](https://msdn.microsoft.com/magazine/dd315413.aspx)します。  
  
> [!IMPORTANT]
>  JSON を使用するには、SOAP 通信をサポートしていない <xref:System.ServiceModel.WebHttpBinding> と <xref:System.ServiceModel.Description.WebHttpBehavior> を使用する必要があります。 サービスと通信する、<xref:System.ServiceModel.WebHttpBinding>サービス メタデータの公開はサポートされないので、Visual Studio のサービス参照の追加機能または svcutil コマンド ライン ツールを使用して、クライアント側プロキシを生成することはできません。 使用するサービスのプログラムでを呼び出す方法の詳細<xref:System.ServiceModel.WebHttpBinding>を参照してください[WCF で REST サービスを使用する方法](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx)します。  
  
## <a name="untyped-message-programming"></a>型指定されていないメッセージのプログラミング  
 型指定されていないメッセージ オブジェクトを直接操作する場合は、型指定されていないメッセージのプロパティを明示的に設定して JSON としてシリアル化する必要があります。 これを行う方法を次のコード スニペットに示します。  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>関連項目
- [AJAX の統合と JSON のサポート](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [スタンドアロン JSON のシリアル化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [JSON シリアル化](../../../../docs/framework/wcf/samples/json-serialization.md)
