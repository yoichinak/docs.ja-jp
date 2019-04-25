---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 995ff9979096757225c9241e977f86f755955945
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158771"
---
# <a name="servicethrottling"></a>\<serviceThrottling>
WCF (Windows Communication Foundation) サービスの調整機構を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceThrottling>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|maxConcurrentCalls|<xref:System.ServiceModel.ServiceHost> で同時に処理できるメッセージ数を制限する正の整数。 制限を超えた呼び出しはキューに置かれます。 この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。 既定値は 16 x プロセッサ数です。|  
|maxConcurrentInstances|<xref:System.ServiceModel.InstanceContext> で同時に実行できる <xref:System.ServiceModel.ServiceHost> オブジェクト数を制限する正の整数。 追加インスタンスの作成要求は、キューに置かれ、制限下のスロットが利用できるようになったときに完了されます。 既定値は maxConcurrentSessions と MaxConcurrentCalls の合計です。|  
|maxConcurrentSessions|<xref:System.ServiceModel.ServiceHost> オブジェクトが受け入れることのできるセッション数を制限する正の整数。<br /><br /> サービスは制限を超える接続を受け入れますが、制限内のチャネルだけがアクティブです (メッセージがチャネルから読み取られます)。 この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。 既定値は 100 x プロセッサ数です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 調整コントロールは、同時呼び出し、同時インスタンス、または同時セッションの数を制限して、リソースの過剰消費を防ぎます。  
  
 属性の値に到達するたびにトレースが出力されます。 最初のトレースは警告として出力されます。  
  
## <a name="example"></a>例  
 次の構成例では、サービスで同時呼び出しの最大数を 2 に、同時インスタンスの最大数を 10 に制限することを指定しています。 この例の実行の詳細な例を参照してください。[スロットル](../../../../../docs/framework/wcf/samples/throttling.md)します。  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
