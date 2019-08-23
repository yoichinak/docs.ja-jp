---
title: <behavior> の <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 8c847368934cc4cd8ccaab017ede00b7b8963897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926402"
---
# <a name="behavior-of-servicebehaviors"></a>\<servicebehaviors の\<動作 > >
`behavior` 要素には、サービスの動作設定のコレクションが含まれます。 各動作には、それぞれの `name` によってインデックスが付けられます。 サービスは、 `behaviorConfiguration` [ \<エンドポイント >](endpoint-element.md)要素の属性を使用して、この名前を使用して各動作にリンクできます。 これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
> [!NOTE]
> SendMessageChannelCache > 要素など、Windows Workflow アクティビティに固有の動作要素[ \<は、servicebehaviors > ページ\<の > の動作](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)に記載されて[ \<](../windows-workflow-foundation/sendmessagechannelcache.md)います。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|動作の構成名を含む一意の文字列。 この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<dataContractSerializer >](datacontractserializer-element.md)|DataContractSerializer 用の構成データが含まれています。|  
|[\<persistenceProvider >](persistenceprovider.md)|使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。|  
|[\<ルーティング >](routing-of-servicebehavior.md)|ルーティング構成の動的な変更を可能にするルーティング サービスへの実行時アクセスを提供します。|  
|[\<serviceAuthenticationManager >](serviceauthenticationmanager.md)|サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。|  
|[\<serviceAuthorization >](serviceauthorization-element.md)|サービス操作へのアクセスを承認する設定を指定します。|  
|[\<serviceCredentials>](servicecredentials.md)|サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。|  
|[\<serviceDebug >](servicedebug.md)|Windows Communication Foundation (WCF) サービスのデバッグ機能とヘルプ情報機能を指定します。|  
|[\<serviceDiscovery >](servicediscovery.md)|サービス エンドポイントの探索可能性を指定します。|  
|[\<serviceMetadata >](servicemetadata.md)|サービス メタデータと関連情報の公開を指定します。|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。|  
|[\<serviceThrottling >](servicethrottling.md)|WCF サービスの制限メカニズムを指定します。|  
|[\<serviceTimeouts>](servicetimeouts.md)|サービスのタイムアウトを指定します。|  
|[\<workflowRuntime>](workflowruntime.md)|ワークフローベースの WCF サービスをホストするための WorkflowRuntime のインスタンスの設定を指定します。|  
|[\<useRequestHeadersForMetadataAddress >](userequestheadersformetadataaddress.md)|メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|サービス動作要素のコレクション。|
