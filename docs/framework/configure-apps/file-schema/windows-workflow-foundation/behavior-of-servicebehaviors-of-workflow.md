---
title: <behavior>ワークフロー <serviceBehaviors>の
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946077"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<ワークフローの servicebehaviors > の\<動作 >
**Behavior**要素には、サービスの動作に関する設定のコレクションが含まれています。 各動作は、**名前**によってインデックスが作成されます。 サービスは、 [ \<エンドポイント >](../wcf/endpoint-element.md)要素の**設定**属性を使用して、この名前を使用して各動作にリンクできます。 これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。  
  
\<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  hostLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|動作の構成名を含む一意の文字列。 この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bufferReceive >](bufferreceive.md)|サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。|  
|[\<ルーティング >](../wcf/routing-of-servicebehavior.md)|サービスがを使用して<xref:System.Activities.Tracking.EtwTrackingParticipant>ETW 追跡を利用できるようにするサービス動作。|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|キャッシュ共有レベルのカスタマイズ、チャネルファクトリキャッシュの設定、およびメッセージを送信するアクティビティを使用してサービスエンドポイントにメッセージを送信するワークフローのチャネルキャッシュの設定を可能にするサービス動作。|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|ワークフローサービスインスタンスの状態情報の SQL Server 2005 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>または SQL Server 2008 データベースへの永続化をサポートする機能を構成できるようにするサービス動作。|  
|[\<workflowIdle >](workflowidle.md)|アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。|  
|[\<workflowInstanceManagement >](workflowinstancemanagement.md)|ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。|  
|[\<workflowUnhandledException >](workflowunhandledexception.md)|ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|サービス動作要素のコレクション。|
