---
title: '方法: WorkflowServiceHost を使用して追跡を構成する'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185070"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>方法: WorkflowServiceHost を使用して追跡を構成する
このトピックでは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] でホストされている <xref:System.ServiceModel.Activities.WorkflowServiceHost> ワークフロー サービスの追跡を構成する方法について説明します。 これは、Web.config ファイルにサービスの動作を指定することによって指定します。  
  
### <a name="configure-tracking-in-configuration"></a>構成での追跡の構成  
  
1. 次の<xref:System.Activities.Tracking.EtwTrackingParticipant>例に示`behavior`すように、構成ファイルに <>要素を追加します。  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > 前の構成サンプルでは、簡略化された構成を使用しています。 詳細については、「[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)」を参照してください。  
  
     前の構成サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。 追跡プロファイルは、<>`trackingProfile``tracking`要素内の<>要素内に作成されます。 追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。 追跡プロファイルを作成する方法を次の例に示します。  
  
    ```xml  
    <system.serviceModel>  
        <tracking>
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>
       </tracking>  
    </system.serviceModel>  
    ```  
  
     追跡プロファイルの詳細については、「[追跡](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)プロファイル」を参照してください。  
  
     追跡全般の詳細については、「[ワークフローの追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。  
  
### <a name="configure-tracking-in-code"></a>コードでの追跡の構成  
  
1. 次の例に示すように、コードで <xref:System.Activities.Tracking.EtwTrackingParticipant> を動作を使用して <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> を追加します。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     前のコード サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。 追跡プロファイルは、前のセクション`trackingProfile`で示したように、<>`tracking`要素内の<>要素内に作成されます。  
  
     追跡プロファイルの詳細については、「[追跡](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)プロファイル」を参照してください。  
  
     追跡全般の詳細については、「[ワークフローの追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。 プログラムで追跡を構成する例については、「[ワークフローの追跡の構成](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [WCF サービスの簡略化された構成](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [追跡プロファイル](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
