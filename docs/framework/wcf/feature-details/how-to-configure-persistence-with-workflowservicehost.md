---
title: WorkflowServiceHost を使用して永続性を構成する方法
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2974b6bcbb94c5b54d91025aeabe7c2d2e94c7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185053"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>WorkflowServiceHost を使用して永続性を構成する方法
このトピックでは、構成ファイルを使用して、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフローに対して永続化を有効にするように、SQL Workflow Instance Store の機能を構成する方法について説明します。 SQL Workflow Instance Store 機能を使用する前に、ワークフロー インスタンスの永続化に使用する SQL データベースを作成する必要があります。 詳細については、「[方法 : ワークフローおよびワークフロー サービスの SQL 永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)」を参照してください。  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>構成において SQL Workflow Instance Store を構成するには  
  
1. SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、XML 構成で設定を変更するために使用できるサービス動作です。 次の構成例は、構成ファイル内の<>`sqlWorkflowInstanceStore`動作要素を使用して SQL ワークフロー インスタンス ストアを構成する方法を示しています。  
  
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
  
     SQL ワークフロー インスタンス ストアを構成する方法の詳細については、「[方法 : ワークフローおよびワークフロー サービスの SQL 永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)」を参照してください。 <>`sqlWorkflowInstanceStore`動作要素の個々の設定の詳細については[、「SQL ワークフロー インスタンス ストア](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)」を参照してください。 Windows Server AppFabric は自己の永続ストアを提供します。 詳細については、「 [Windows Server アプリ ファブリックの永続性](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))」を参照してください。  
  
    > [!NOTE]
    > 前の構成例では、簡略化された構成を使用しています。 詳細については、[簡略化された構成を](../../../../docs/framework/wcf/simplified-configuration.md)参照してください。  
  
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
  
     SQL ワークフロー インスタンス ストアを構成する方法の詳細については、「[方法 : ワークフローおよびワークフロー サービスの SQL 永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)」を参照してください。 動作要素の個々の設定の詳細については、「 SQL[ワークフロー インスタンス ストア](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)」を参照してください。 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> Windows Server AppFabric は自己の永続ストアを提供します。 詳細については、「 [Windows Server アプリ ファブリックの永続性](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))」を参照してください。  
  
    > [!NOTE]
    > 前の構成例では、簡略化された構成を使用しています。 詳細については、[簡略化された構成を](../../../../docs/framework/wcf/simplified-configuration.md)参照してください。  
  
     プログラムで永続化を構成する方法の例については、「[方法 : ワークフローとワークフロー サービスの永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server AppFabric の永続化](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
