---
title: 伝達
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: faa0e6ecb53963587e3fc253cd8beae1dc2c4bf5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154038"
---
# <a name="propagation"></a>伝達
このトピックでは、Windows Communication Foundation (WCF) トレース モデルでのアクティビティ伝達について説明します。  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>伝達を使用したエンドポイント間でのアクティビティの関連付け  
 伝達を使用することで、複数のアプリケーション エンドポイントについて、同じ処理単位 (要求など) のエラー トレースを直接関連付けることができます。 さまざまなエンドポイントで発生した同じ処理単位のエラーは、アプリケーション ドメインが異なる場合でも同じアクティビティとしてグループ化されます。 これは、メッセージ ヘッダーで特定のアクティビティ ID を伝達することによって実現されます。 したがって、サーバーの内部エラーによってクライアントがタイムアウトした場合、これらのエラーは直接関係しているので、どちらも同じアクティビティに表示されます。  
  
 これを行うには、前述の例に示すように `ActivityTracing` 設定を使用します。 さらに、すべてのエンドポイントで `propagateActivity` トレース ソースの `System.ServiceModel` 属性を設定します。  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 アクティビティの伝達は、TLS のアクティビティ ID が含まれていますが、送信メッセージにヘッダーを追加する WCF の原因となる構成可能な機能です。 サーバー側の以降のトレースでこの ID を含めることにより、クライアントとサーバーのアクティビティを相互に関連付けることができます。  
  
## <a name="propagation-definition"></a>伝達の定義  
 次のすべての条件に該当する場合に、アクティビティ M の gAId がアクティビティ N に伝達されます。  
  
-   M に起因して N が作成された。  
  
-   M の gAId を N が認識している。  
  
-   N の gAId と M の gAId が同じである。  
  
 次の XML スキーマに示すように、gAId は ActivityId メッセージ ヘッダーによって伝達されます。  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 メッセージ ヘッダーの例を次に示します。  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>伝達とアクティビティ境界  
 エンドポイント間でアクティビティ ID が伝達されると、メッセージの受信側は、その (伝達された) アクティビティ ID を使用して Start トレースと Stop トレースを出力します。 したがって、各トレース ソースごとに、該当の gAId を持つ Start/Stop トレースが存在することになります。 複数のエンドポイントが同じプロセス内に存在し、同じトレース ソース名を使用している場合、同じ lAId (同じ gAId、同じトレース ソース、同じプロセス) を持つ複数の Start と Stop が作成されます。  
  
## <a name="synchronization"></a>同期  
 異なるコンピューター上で実行されるエンドポイント間でイベントを同期するには、メッセージ内で伝達される ActivityId ヘッダーに CorrelationId を追加します。 ツールはこの ID を使用することにより、クロックにずれのあるコンピューター間でもイベントを同期できます。 具体的に言うと、サービス トレース ビューアー ツールは、エンドポイント間のメッセージ フローを示す際に、この ID を使用します。  
  
## <a name="see-also"></a>関連項目

- [トレースの構成](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [エンドツーエンドのトレースのシナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
