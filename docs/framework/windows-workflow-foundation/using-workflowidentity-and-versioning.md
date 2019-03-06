---
title: WorkflowIdentity と Versioning の使用
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: ad1d3385801b451795c6be321094851339a55f81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373427"
---
# <a name="using-workflowidentity-and-versioning"></a>WorkflowIdentity と Versioning の使用
<xref:System.Activities.WorkflowIdentity> を使用すると、ワークフロー アプリケーションの開発者は、名前と <xref:System.Version> をワークフロー定義に関連付け、永続化されたワークフロー インスタンスにこの情報を関連付けることができます。 この ID 情報は、ワークフロー アプリケーションの開発者がワークフロー定義の複数のバージョンの side-by-side 実行などのシナリオを有効にするために使用できます。また、動的更新などの他の機能の基礎となります。 このトピックでは、<xref:System.Activities.WorkflowIdentity> ホスティングでの <xref:System.Activities.WorkflowApplication> の使用の概要について説明します。 ワークフロー サービスでのワークフロー定義のサイド バイ サイドでの実行については、次を参照してください。 [WorkflowServiceHost でサイド バイ サイドのバージョン管理](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)します。 動的更新については、次を参照してください。[動的更新](../../../docs/framework/windows-workflow-foundation/dynamic-update.md)します。  
  
## <a name="in-this-topic"></a>このトピックの内容  
  
-   [WorkflowIdentity の使用](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [WorkflowIdentity を使用したサイド バイ サイドで実行](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [ワークフローのバージョン管理をサポートするために .NET Framework 4 永続性データベースのアップグレード](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [データベース スキーマをアップグレードするには](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> WorkflowIdentity の使用  
 
  <xref:System.Activities.WorkflowIdentity> を使用するには、インスタンスを作成および構成し、<xref:System.Activities.WorkflowApplication> インスタンスに関連付けます。 <xref:System.Activities.WorkflowIdentity> インスタンスには 3 種類の識別情報が格納されます。 <xref:System.Activities.WorkflowIdentity.Name%2A> と <xref:System.Activities.WorkflowIdentity.Version%2A> は必須で、名前と <xref:System.Version> を表します。また、<xref:System.Activities.WorkflowIdentity.Package%2A> は省略可能で、アセンブリ名やその他の必要な情報などの情報を格納する追加文字列の指定に使用できます。 <xref:System.Activities.WorkflowIdentity> は、その 3 つのプロパティのいずれかが他の <xref:System.Activities.WorkflowIdentity> と異なる場合に一意です。  
  
> [!IMPORTANT]
>  <xref:System.Activities.WorkflowIdentity> には、個人を特定できる情報 (PII) を含めないでください。 インスタンスの作成に使用される <xref:System.Activities.WorkflowIdentity> に関する情報は、ランタイムによるアクティビティ ライフ サイクルのさまざまなポイントで構成されているすべての追跡サービスに出力されます。 WF の追跡には PII (機密ユーザー データ) を非表示にするメカニズムがありません。 そのため、<xref:System.Activities.WorkflowIdentity> インスタンスには PII データを含めないでください。PII データは、ランタイムによって追跡レコードに出力され、追跡レコードを表示するためのアクセス権を持つユーザーに表示できます。  
  
 次の例では、<xref:System.Activities.WorkflowIdentity> を作成し、`MortgageWorkflow` のワークフロー定義を使用して作成したワークフローのインスタンスに関連付けます。  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 ワークフローを再読み込みして再開すると、永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowIdentity> と一致するように構成されている <xref:System.Activities.WorkflowIdentity> を使用する必要があります。  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 ワークフロー インスタンスの再読み込み時に使用される <xref:System.Activities.WorkflowIdentity> が永続化された <xref:System.Activities.WorkflowIdentity> と一致しない場合は、<xref:System.Activities.VersionMismatchException> がスローされます。 次の例では、前の例で永続化された `MortgageWorkflow` インスタンスで読み込み操作が行われます。 この読み込み操作は、永続化されたインスタンスと一致しない、住宅ローン ワークフローの新しいバージョン用に構成された <xref:System.Activities.WorkflowIdentity> を使用して行われます。  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 前のコードが実行されると、次の <xref:System.Activities.VersionMismatchException> がスローされます。  
  
 **WorkflowIdentity ('MortgageWorkflow v1;バージョン 1.0.0.0' =) の読み込まれたインスタンスと一致しません、WorkflowIdentity ('MortgageWorkflow v2;バージョン 2.0.0.0' =) の指定されたワークフロー定義。インスタンスは、別の定義を使用して読み込むことができるや、動的更新を使用して更新します。**  
### <a name="SxS"></a> WorkflowIdentity を使用したサイド バイ サイドで実行  
 <xref:System.Activities.WorkflowIdentity> を使用すると、ワークフローの複数のバージョンの side-by-side 実行を簡略化できます。 たとえば、実行時間の長いワークフローのビジネス要件を変更します。 ワークフローの多くのインスタンスは、更新されたバージョンを配置すると実行できます。 ホスト アプリケーションは、新しいインスタンスの開始時に更新されたワークフロー定義を使用するよう構成できます。また、インスタンスの再開時に適切なワークフロー定義を指定するのはホスト アプリケーションの役割です。 <xref:System.Activities.WorkflowIdentity> を使用すると、ワークフロー インスタンスの再開時に、一致するワークフロー定義を特定して指定できます。  
  
 永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowIdentity> を取得するには、<xref:System.Activities.WorkflowApplication.GetInstance%2A> メソッドを使用します。 <xref:System.Activities.WorkflowApplication.GetInstance%2A> メソッドは、永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowApplication.Id%2A>、および永続化されたインスタンスを格納する <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を取得して、<xref:System.Activities.WorkflowApplicationInstance> を返します。 <xref:System.Activities.WorkflowApplicationInstance> には、永続化されたワークフロー インスタンスに関する情報 (関連付けられた <xref:System.Activities.WorkflowIdentity> など) が格納されます。 この関連付けられた <xref:System.Activities.WorkflowIdentity> は、ワークフロー インスタンスを読み込んで再開するときに、適切なワークフロー定義を指定するためにホストで使用できます。  
  
> [!NOTE]
>  null の <xref:System.Activities.WorkflowIdentity> は有効で、ホストで使用すると、関連付けられた <xref:System.Activities.WorkflowIdentity> がない、永続化されたインスタンスを適切なワークフロー定義にマップできます。 このシナリオは、ワークフロー アプリケーションがワークフローのバージョン管理で最初に記述されなかった場合、またはアプリケーションが [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] からアップグレードされた場合に発生する可能性があります。 詳細については、次を参照してください。[をアップグレードする .NET Framework 4 永続性データベース ワークフローのバージョン管理をサポートする](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)します。  
  
 次の例では、`Dictionary<WorkflowIdentity, Activity>`関連付けるために使用<xref:System.Activities.WorkflowIdentity>を使用して、一致するワークフロー定義とワークフロー インスタンスを開始、`MortgageWorkflow`に関連付けられているワークフロー定義、 `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 次の例では、前の例の永続化されたワークフロー インスタンスに関する情報を <xref:System.Activities.WorkflowApplication.GetInstance%2A> を呼び出すことによって取得し、永続化された <xref:System.Activities.WorkflowIdentity> の情報を使用して一致するワークフロー定義を取得します。 この情報を使用して <xref:System.Activities.WorkflowApplication> を構成すると、ワークフローが読み込まれます。 <xref:System.Activities.WorkflowApplication.Load%2A> を受け取る <xref:System.Activities.WorkflowApplicationInstance> オーバーロードが使用されるため、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> で構成された <xref:System.Activities.WorkflowApplicationInstance> が <xref:System.Activities.WorkflowApplication> によって使用され、その結果、その <xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティを構成する必要はありません。  
  
> [!NOTE]
>  
  <xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティを設定する場合は、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> によって使用されるのと同じ <xref:System.Activities.WorkflowApplicationInstance> インスタンスで設定する必要があります。そうしないと、<xref:System.ArgumentException> がスローされ、"`The instance is configured with a different InstanceStore than this WorkflowApplication.`" というメッセージが表示されます。  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
## <a name="UpdatingWF4PersistenceDatabases"></a> ワークフローのバージョン管理をサポートするために .NET Framework 4 永続性データベースのアップグレード  
 SqlWorkflowInstanceStoreSchemaUpgrade.sql データベース スクリプトは、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] データベース スクリプトを使用して作成された永続性データベースを更新するために用意されています。 このスクリプトは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で導入された新しいバージョン管理機能をサポートするようにデータベースを更新します。 データベースで永続化されたすべてのワークフロー インスタンスは、既定のバージョン番号が付与されるため、side-by-side 実行および動的更新に参加できるようになります。  
  
 
  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ワークフロー アプリケーションが、提供されたスクリプトを使用してアップグレードされていない永続性データベースで新しいバージョン管理機能を使用する永続化操作を実行すると、<xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> がスローされ、次のようなメッセージが表示されます。  
  
 **SqlWorkflowInstanceStore が '4.0.0.0' のデータベースのバージョンです。このバージョンのデータベースに対して InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' を実行することはできません。データベースを '4.5.0.0' にアップグレードしてください。**  
### <a name="ToUpgrade"></a> データベース スキーマをアップグレードするには  
  
1.  SQL Server Management Studio を開き、たとえば、永続性データベース サーバーに接続 **. \SQLEXPRESS**します。  
  
2.  選択**オープン**、**ファイル**から、**ファイル**メニュー。 次のフォルダーに移動します: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`。  
  
3.  選択**SqlWorkflowInstanceStoreSchemaUpgrade.sql**  をクリック**オープン**します。  
  
4.  永続性データベースの名前を選択、**利用可能なデータベース**ドロップダウンします。  
  
5.  選択**Execute**から、**クエリ**メニュー。  
  
 クエリが完了すると、データベース スキーマがアップグレードされるため、必要に応じて、永続化されたワークフロー インスタンスに割り当てられた既定のワークフロー ID を確認できます。 永続性データベースを展開し、**データベース**のノード、**オブジェクト エクスプ ローラー**の順に展開し、**ビュー**ノード。 右クリックして**System.Activities.DurableInstancing.Instances**選択**上位 1000 行**します。 列の末尾までスクロールし、ビューに追加された 6 つの追加列があることに注意してください。**IdentityName**、 **IdentityPackage**、**ビルド**、**メジャー**、**マイナー**、および**リビジョン**. 値は、永続化されたワークフローになります**NULL**これらのフィールドの null のワークフロー id を表します。
