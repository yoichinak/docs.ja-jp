---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: e82312cb17fbd3f76f781ea37f761e946319a0a0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351856"
---
# <a name="findcriteria"></a>\<findCriteria >
探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。 条件は、(探しているサービスの種類を指定して) 検索条件にグループ化することができ、検索 (検索持続期間)、終了条件。  
  
 \<system.ServiceModel >  
\<standardEndpoints>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|duration|ネットワーク上でサービスからの応答を待機する最長時間を指定する Timespan 値。 既定の時間は 20 秒です。|  
|maxResults|ネットワークまたはインターネット上で待機する、サービスから応答の最大数を指定する整数。 `duration` 属性に指定した時間が経過する前に応答の最大数に達した場合、検索操作は終了します。|  
|scopeMatchBy|Probe メッセージのスコープをエンドポイントのスコープと一致させるときに使用する、一致のアルゴリズムを指定する URI。<br /><br /> サポートされているスコープ一致規則は 5 つあります。 スコープ一致規則を指定しなかった場合は、`ScopeMatchByPrefix` が使用されます。 詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<contractTypeNames>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|ワークフロー サービス コントラクト型の名前を格納する構成要素のコレクション。|  
|\<拡張機能 > の\<findCriteria >|拡張を提供する XML 要素オブジェクトのコレクション。|  
|[\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|特定のサービスを特定する検索操作の実行中に使用される絶対 URI を格納するオブジェクトのコレクション。<br /><br /> 特定のサービスが見つかった場合、サービス URI とスコープ URI が一致します。複雑な一致を処理するスコープ規則が使用されることもあります。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。|  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
