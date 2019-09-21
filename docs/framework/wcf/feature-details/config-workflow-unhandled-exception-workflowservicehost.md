---
title: '方法: WorkflowServiceHost を使用してワークフロー サービスの未処理の例外動作を構成する'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957256"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>方法: WorkflowServiceHost を使用してワークフロー サービスの未処理の例外動作を構成する
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。 このトピックでは、この動作を構成ファイルで構成する方法を示します。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior を構成するには  
  
1. 次の例`workflowUnhandledException`に示すように、`behavior` `action`属性を使用して`serviceBehaviors`、ハンドルされない例外が発生したときに実行するアクションを指定して、< > 要素内の < > 要素に < > 要素を追加します。  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > 前の構成サンプルでは、簡略化された構成を使用しています。 詳細については、「簡略化された[構成](../../../../docs/framework/wcf/simplified-configuration.md)」を参照してください。  
  
     この動作は、次の例に示すように、コードで構成できます。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` <`workflowUnhandledException`> 要素の属性は、次のいずれかの値に設定できます。  
  
     **破棄**  
     永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します (つまり、最後の永続性ポイントにロールバックします)。  
  
     **abandonAndSuspend**  
     メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。  
  
     **cancel**  
     インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。  
  
     **terminate**  
     メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。  
  
     の詳細<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>については、「[ワークフローサービスホストの機能拡張](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
