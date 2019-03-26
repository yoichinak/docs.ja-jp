---
title: '方法: SQL 永続性ワークフローとワークフロー サービスを有効にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 84a9220e39c0d79dc53bee576735d1062c1c037c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710279"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>方法: SQL 永続性ワークフローとワークフロー サービスを有効にします。

このトピックでは、ワークフローとワークフロー サービスの永続性をプログラムと構成ファイルの両方から使用して有効にできるように、SQL Workflow Instance Store の機能を構成する方法について説明します。

Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。 詳細については、次を参照してください[App Fabric 永続化の構成。](https://go.microsoft.com/fwlink/?LinkId=201204)

SQL Workflow Instance Store 機能を使用する前に、この機能においてワークフロー インスタンスの永続化に使用するデータベースを作成します。 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] セットアップ プログラムによって、SQL Workflow Instance Store 機能に関連する SQL スクリプト ファイルが %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN フォルダーにコピーされます。 これらのスクリプト ファイルは、SQL Workflow Instance Store がワークフロー インスタンスの永続化に使用する SQL Server 2005 または SQL Server 2008 のデータベースに対して実行します。 最初に SqlWorkflowInstanceStoreSchema.sql ファイルを実行してから、SqlWorkflowInstanceStoreLogic.sql ファイルを実行します。

> [!NOTE]
> 永続性データベースをクリーンアップして新しいデータベースにするには、%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN にあるスクリプトを次の順序で実行します。
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> 永続性データベースを作成しない場合、ホストがワークフローを永続化しようとしたときに、SQL Workflow Instance Store 機能によって次のような例外がスローされます。
>
> System.Data.SqlClient.SqlException:ストアド プロシージャ 'system.activities.durableinstancing.createlockowner'' が見つかりませんでした。

以下のセクションでは、SQL Workflow Instance Store を使用してワークフローとワークフロー サービスの永続性を有効にする方法について説明します。 SQL Workflow Instance Store のプロパティの詳細については、[SQL Workflow Instance Store のプロパティ](properties-of-sql-workflow-instance-store.md)を参照してください。

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>WorkflowApplication を使用する自己ホスト型ワークフローの永続化の有効化

<xref:System.Activities.WorkflowApplication> オブジェクト モデルを使用して、プログラムから <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する自己ホスト型ワークフローの永続化を有効にすることができます。 これを行う手順を次に示します。

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>自己ホスト型ワークフローの永続化を有効にするには

1. System.Activities.DurableInstancing.dll への参照を追加します。

2. ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. 次のコード例に示すように、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構築して <xref:System.Activities.WorkflowApplication.InstanceStore%2A> の <xref:System.Activities.WorkflowApplication> に割り当てます。

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > 使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。

4. <xref:System.Activities.WorkflowApplication.Persist%2A> オブジェクトの <xref:System.Activities.WorkflowApplication> メソッドを呼び出してワークフローを永続化するか、<xref:System.Activities.WorkflowApplication.Unload%2A> メソッドを呼び出してワークフローを永続化およびアンロードします。 また、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> オブジェクトによって発生した <xref:System.Activities.WorkflowApplication> イベントを処理して、<xref:System.Activities.PersistableIdleAction.Persist> の適切なメンバー (<xref:System.Activities.PersistableIdleAction.Unload> または <xref:System.Activities.PersistableIdleAction>) を返すこともできます。

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> 参照してください、[方法。作成および実行 a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md)の手順、[チュートリアル入門](getting-started-tutorial.md)ステップ バイ ステップの指示します。

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost を使用する自己ホスト型ワークフロー サービスの永続化の有効化

<xref:System.ServiceModel.WorkflowServiceHost> クラスまたは <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、プログラムから <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> を使用する自己ホスト型ワークフロー サービスの永続化を有効にすることができます。

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>SqlWorkflowInstanceStoreBehavior クラスの使用

<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、自己ホスト型ワークフロー サービスの永続化を有効にする手順を次に示します。

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>SqlWorkflowInstanceStoreBehavior を使用して永続化を有効にするには

1. System.ServiceModel.dll への参照を追加します。

2. ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. `WorkflowServiceHost` のインスタンスを作成し、ワークフロー サービスのエンドポイントを追加します。

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. `SqlWorkflowInstanceStoreBehavior` オブジェクトを作成して、動作オブジェクトのプロパティを設定します。

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. ワークフロー サービス ホストを開きます。

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>DurableInstancingOptions プロパティの使用

`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。 同じ内容をプログラムから実行するには、次のコード例に示すように、<xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> クラスを使用せずに `WorkflowServiceHost` の `SqlWorkflowInstanceStoreBehavior` プロパティを設定します。

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>WorkflowServiceHost を使用する WAS でホストされるワークフロー サービスの構成ファイルを使用した永続化の有効化

構成ファイルを使用することで、自己ホスト型または Windows プロセス アクティブ化サービス (WAS) でホストされるワークフロー サービスの永続化を有効にできます。 WAS でホストされるワークフロー サービスは、自己ホスト型ワークフローのように WorkflowServiceHost を使用します。

`SqlWorkflowInstanceStoreBehavior`、簡単に変更できるようにするサービス動作、 [SQL Workflow Instance Store](sql-workflow-instance-store.md) XML 構成のプロパティ。 WAS でホストされるワークフロー サービスの場合は、Web.config ファイルを使用します。 次の構成例では、構成ファイルで `sqlWorkflowInstanceStore` という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05">

        <sqlWorkflowInstanceStore/>
    </behavior>
</serviceBehaviors>
```

`connectionString` または `connectionStringName` プロパティの値が設定されていない場合、SQL Workflow Instance Store は既定の名前付き接続文字列 `DefaultSqlWorkflowInstanceStoreConnectionString` を使用します。

`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。 同じ内容をプログラムから実行するには、サービスの動作要素を使用せずに `SqlWorkflowInstanceStore` を `WorkflowServiceHost` と一緒に使用します。

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> ユーザー名やパスワードなどの機密情報は、Web.config ファイルに保存しないことをお勧めします。 Web.config ファイルに機密情報を保存する場合は、ファイル システムのアクセス制御リスト (ACL) を使用して、Web.config ファイルへのアクセスをセキュリティで保護する必要があります。 さらに、保護することできますも構成ファイル内の構成値で説明したよう[暗号化構成を使用して保護された構成情報](https://go.microsoft.com/fwlink/?LinkId=178419)します。

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL Workflow Instance Store 機能に関連する Machine.config の要素


  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] のインストールでは、SQL Workflow Instance Store 機能に関連する次の要素が Machine.config ファイルに追加されます。

- 使用できるように、Machine.config ファイルに次の動作拡張機能要素を追加、 \<sqlWorkflowInstanceStore > サービスの永続化を構成する構成ファイル内のサービス動作要素。

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        <system.serviceModel>
    <configuration>
    ```
