---
title: <behavior>ワークフロー<serviceBehaviors>の
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152321"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>\<サービスの\<動作>ワークフローの動作>
**動作**要素には、サービスの動作に関する設定のコレクションが含まれています。 各動作は、その**名前**でインデックス付けされます。 サービスは、[\<エンドポイント>](../wcf/endpoint-element.md)要素の**behaviorConfiguration**属性を使用して、この名前を介して各動作にリンクできます。 これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<システム。サービスモデル>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<動作>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<サービス動作>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<動作>**  
  
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
|[\<バッファ受信>](bufferreceive.md)|サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。|  
|[\<ルーティング>](../wcf/routing-of-servicebehavior.md)|<xref:System.Activities.Tracking.EtwTrackingParticipant> を使用して、サービスで ETW 追跡を利用するためのサービス動作。|  
|[\<>を送信します。](sendmessagechannelcache.md)|キャッシュの共有レベルのカスタマイズや、チャネル ファクトリ キャッシュの設定を可能にするほか、Send メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定も可能にするサービス動作。|  
|[\<>](sqlworkflowinstancestore.md)|ワークフロー サービス インスタンスの状態情報の永続化を SQL Server 2005 または SQL Server 2008 データベースでサポートする <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 機能を構成するためのサービス動作。|  
|[\<ワークフローアイドル>](workflowidle.md)|アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。|  
|[\<ワークフローインスタンス管理>](workflowinstancemanagement.md)|ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。|  
|[\<ワークフロー未処理の例外>](workflowunhandledexception.md)|ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービス動作>](servicebehaviors-of-workflow.md)|サービス動作要素のコレクション。|
