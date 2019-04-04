---
title: '方法: ワークフローを構成する未処理の例外動作 WorkflowServiceHost を使用'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 9a13bb9390e891295491722898bd780bc1cac587
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636158"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>方法: ワークフローを構成する未処理の例外動作 WorkflowServiceHost を使用
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。 このトピックでは、この動作を構成ファイルで構成する方法を示します。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior を構成するには  
  
1.  追加、<`workflowUnhandledException`> 内の要素を <`behavior`> 内の要素を <`serviceBehaviors`> 要素を使用して、`action`次の例に示すように、ハンドルされない例外が発生したときに実行するアクションを指定する属性。  
  
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
    >  前の構成サンプルでは、簡略化された構成を使用しています。 詳細については、[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)を参照してください。  
  
     この動作は、次の例に示すように、コードで構成できます。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action`の属性、<`workflowUnhandledException`> 要素は、次の値のいずれかに設定することができます。  
  
     **abandon**  
     永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します (つまり、最後の永続性ポイントにロールバックします)。  
  
     **abandonAndSuspend**  
     メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。  
  
     **キャンセル**  
     インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。  
  
     **terminate**  
     メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。  
  
     詳細については<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>を参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)します。  
  
## <a name="see-also"></a>関連項目
- [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
