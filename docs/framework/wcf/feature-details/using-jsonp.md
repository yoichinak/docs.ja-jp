---
title: "JSONP の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3cd0d20f619444b2a00fccafdf63557b5e09e21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-jsonp"></a>JSONP の使用

JSONP (JSON with Padding) は、Web ブラウザーでクロスサイト スクリプトの利用を可能にするためのメカニズムです。 JSONP は、現在読み込まれているドキュメントを取得したサイトとは異なるサイトから、スクリプトを読み込むための Web ブラウザーの機能を軸に設計されています。 このメカニズムは、次の例に示すように、JSON ペイロードにユーザー定義のコールバック関数の名前を埋め込むことで機能します。

```javascript
callback({"a" = \\"b\\"});
```

上記の例では、JSON ペイロード `{"a" = \\"b\\"}` が、関数呼び出し `callback` にラップされています。 コールバック関数は、現在の Web ページで定義済みである必要があります。 JSONP 応答のコンテンツの種類は`application/javascript`します。

JSONP は自動的には有効化されません。 有効にするには、次の例のように、HTTP の標準エンドポイントのいずれか (`javascriptCallbackEnabled` または `true`) で、<xref:System.ServiceModel.Description.WebHttpEndpoint> 属性を <xref:System.ServiceModel.Description.WebScriptEndpoint> に設定する必要があります。

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

コールバック関数名は、次の URL に示すように、callback というクエリ変数で指定できます。

`http://baseaddress/Service/RestService?callback=functionName`

このサービスを呼び出すと、次のような応答が送信されます。

```javascript
functionName({"root":"Something"});
```  

コールバック関数名は、次の例のように、サービス クラスに <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> を適用して指定することもできます。

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

上に示したサービスでは、要求は次のような形式になります。

`http://baseaddress/Service/RestService?$callback=anotherFunction`

このサービスを呼び出すと、次のような応答が返されます。

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>HTTP 状態コード

HTTP 状態コードが 200 以外の JSONP 応答には、次の例のように、HTTP 状態コードの数値表現が 2 つ目のパラメーターとして付加されます。

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>検証

JSONP が有効な場合、以下の検証が行われます。

- `javascriptCallback` が有効になっており、要求にコールバック クエリ文字列のパラメーターが含まれ、応答形式が JSON に設定されている場合は、WCF インフラストラクチャから例外がスローされます。

- 要求にコールバック クエリ文字列のパラメーターが含まれているが、操作が HTTP GET ではない場合は、コールバック パラメーターが無視されます。

- コールバック名が `null` または空の文字列の場合は、応答の形式が JSONP に設定されません。

## <a name="see-also"></a>関連項目

[WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
