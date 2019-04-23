---
title: '方法: WorkflowServiceHost を使用して永続性を構成する'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: b8839f42a9b8b5f4da0a1a8364c7eac5a4c06d4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337163"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>方法: WorkflowServiceHost を使用して永続性を構成する
このトピックでは、構成ファイルを使用して、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフローに対して永続化を有効にするように、SQL Workflow Instance Store の機能を構成する方法について説明します。 SQL Workflow Instance Store 機能を使用する前に、ワークフロー インスタンスの永続化に使用する SQL データベースを作成する必要があります。 詳細については、「[方法 :SQL 永続性ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)します。  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>構成において SQL Workflow Instance Store を構成するには  
  
1. SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、XML 構成で設定を変更するために使用できるサービス動作です。 次の構成例では、構成ファイルで <`sqlWorkflowInstanceStore`> という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     SQL workflow instance store を構成する方法の詳細については、次を参照してください。[方法。SQL 永続性ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)します。 個別の設定の詳細については、<`sqlWorkflowInstanceStore`> 動作要素を参照してください[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)します。 Windows Server AppFabric は自己の永続ストアを提供します。 詳細については、次を参照してください。 [Windows Server App Fabric の永続化](https://go.microsoft.com/fwlink/?LinkId=193121)します。  
  
    > [!NOTE]
    >  前の構成例では、簡略化された構成を使用しています。 詳細については、次を参照してください[簡略化された構成。](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>コードで SQL Workflow Instance Store を構成するには  
  
1. SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、コードで設定を変更できるサービス動作です。 次の例では、コードで <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> という動作要素を使用して SQL Workflow Instance Store を構成する方法を示します。  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     SQL workflow instance store を構成する方法の詳細については、次を参照してください。[方法。SQL 永続性ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)します。 個別の設定の詳細については、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>動作の要素を参照してください[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)します。 Windows Server AppFabric は自己の永続ストアを提供します。 詳細については、次を参照してください。 [Windows Server App Fabric の永続化](https://go.microsoft.com/fwlink/?LinkId=193121)します。  
  
    > [!NOTE]
    >  前の構成例では、簡略化された構成を使用しています。 詳細については、次を参照してください[簡略化された構成。](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     永続化をプログラムで構成する方法の例については、次を参照してください。[方法。ワークフローとワークフロー サービスの永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)します。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Fabric の永続化](https://go.microsoft.com/fwlink/?LinkId=193121)
