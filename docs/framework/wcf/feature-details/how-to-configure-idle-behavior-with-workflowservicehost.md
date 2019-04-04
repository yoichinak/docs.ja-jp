---
title: '方法: WorkflowServiceHost でアイドル状態の動作を構成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: dff9145954084d0f299edc1e3f2f6c0d7ea1a80e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727392"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>方法: WorkflowServiceHost でアイドル状態の動作を構成します。
ワークフローは、外部からの働きかけによって再開される必要があるブックマークに遭遇すると、アイドル状態になります。たとえば、 <xref:System.ServiceModel.Activities.Receive> アクティビティを使用して配信されるメッセージをワークフローが待機している場合などです。 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> は、サービス インスタンスがアイドル状態になってから、インスタンスが永続化またはアンロードされるまでの時間を指定できる動作です。 これには、これらの時間の範囲を設定する 2 つのプロパティがあります。 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。アンロードとは、インスタンスをインスタンス ストアに永続化し、メモリから削除することを意味します。 このトピックでは、 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を構成ファイルで構成する方法について説明します。  
  
### <a name="to-configure-workflowidlebehavior"></a>WorkflowIdleBehavior を構成するには  
  
1.  次の例に示すように、<`workflowIdle`> 要素を <`serviceBehaviors`> 要素内の <`behavior`> 要素に追加します。  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。 `timeToPersist` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。 `timeToUnload` の既定値は 1 分です。 `timeToPersist` の既定値は <xref:System.TimeSpan.MaxValue>です。 インスタンスをメモリ内でアイドル状態を保ちながら信頼性を保持する場合、 `timeToPersist` < `timeToUnload`です。 アイドル状態のインスタンスがアンロードされないようにするには、 `timeToUnload` を <xref:System.TimeSpan.MaxValue>に設定します。 詳細については<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>を参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。 詳細については、[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)を参照してください。  
  
### <a name="to-change-idle-behavior-in-code"></a>コードのアイドル動作を変更するには  
  
-   次の例では、プログラムによって永続化とアンロードを行う前に待機する時間を変更します。  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>関連項目
- [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)
- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
