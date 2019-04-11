---
title: WebContentTypeMapper のサンプル
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 381fc4a3084b1a2620384a04de85b9085e02ae16
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344677"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper のサンプル
このサンプルでは、Windows Communication Foundation (WCF) メッセージの本文の形式を新しいコンテンツ タイプをマップする方法を示します。  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>要素は、JSON、XML、または同じエンドポイントで生のバイナリ メッセージを受信する WCF は、Web メッセージ エンコーダーをプラグインします。 このエンコーダは、要求の HTTP コンテンツ タイプを調べて、メッセージ本文の書式を決定します。 このサンプルでは、コンテンツ タイプと本文書式との間の割り当てを制御するための <xref:System.ServiceModel.Channels.WebContentTypeMapper> クラスを示します。  
  
 WCF では、コンテンツの種類の既定のマッピングのセットを提供します。 たとえば、`application/json` は JSON に割り当てられ、`text/xml` は XML に割り当てられています。 JSON または XML に割り当てられていないコンテンツ タイプは、生のバイナリ形式に割り当てられます。  
  
 場合によっては (プッシュ スタイルの API など)、クライアントによって返されるコンテンツ タイプがサービス開発者によって制御されないことがあります。 たとえば、クライアントは `text/javascript` としてではなく `application/json` として JSON を返す場合があります。 この場合、サービス開発者は、特定のコンテンツ タイプを正しく処理できるように、次のサンプル コードに示すような <xref:System.ServiceModel.Channels.WebContentTypeMapper> の派生型を指定する必要があります。  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 この派生型は、<xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> メソッドをオーバーライドする必要があります。 このメソッドは、`contentType` 引数を評価して、<xref:System.ServiceModel.Channels.WebContentFormat.Json>、<xref:System.ServiceModel.Channels.WebContentFormat.Xml>、<xref:System.ServiceModel.Channels.WebContentFormat.Raw>、または <xref:System.ServiceModel.Channels.WebContentFormat.Default> のいずれかの値を返す必要があります。 <xref:System.ServiceModel.Channels.WebContentFormat.Default> の戻り値は、Web メッセージ エンコーダの既定の割り当てによって決まります。 前のサンプル コードでは、`text/javascript` コンテンツ タイプが JSON に割り当てられ、その他すべての割り当ては変わりません。  
  
 `JsonContentTypeMapper` クラスを使用するには、Web.config 内で次のコードを使用します。  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper の使用要件を検証するには、Web.config ファイルから contentTypeMapper 属性を削除します。 `text/javascript` を使用して JSON コンテンツを送信しようとすると、クライアント ページの読み込みに失敗します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. 」の説明に従って、ソリューション WebContentTypeMapperSample.sln をビルド[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)します。  
  
3. 移動します`http://localhost/ServiceModelSamples/JCTMClientPage.htm`(はプロジェクト ディレクトリ内からブラウザーで JCTMClientPage.htm を開くしない操作を行います)。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
