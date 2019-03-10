---
title: 動的な更新
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: a1d5337bf69cb87d790ce4074cde4c18c989a4d8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724476"
---
# <a name="dynamic-update"></a>動的な更新

動的更新は、ワークフロー アプリケーションの開発者が永続化されたワークフロー インスタンスのワークフロー定義を更新するためのメカニズムを提供します。 これには、バグ修正の実装、新しい要件の実装、または予期しない変更への対応があります。 このトピックでは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で導入された動的更新機能の概要について説明します。

## <a name="dynamic-update"></a>動的な更新

永続化されたワークフロー インスタンスに動的更新を適用するには、必要な変更を反映するよう永続化されたワークフロー インスタンスを変更する方法を説明した指示をランタイム用に含む <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> を作成します。 更新マップが作成されると、対象の永続化されたワークフロー インスタンスに適用されます。 動的更新が適用されると、更新された新しいワークフロー定義を使用して、ワークフロー インスタンスが再開される場合があります。 更新マップを作成して適用する際に必要な手順は 4 つあります。

1. [動的更新用のワークフロー定義を準備します。](dynamic-update.md#Prepare)

2. [必要な変更を反映するようにワークフロー定義を更新します。](dynamic-update.md#Update)

3. [更新マップを作成します。](dynamic-update.md#Create)

4. [目的の永続化されたワークフロー インスタンスに更新マップを適用します。](dynamic-update.md#Apply)

> [!NOTE]
> 更新マップの作成に対応する手順 1. ～ 3. は、更新の適用とは関係なく実行できます。 マップをオフラインで、ワークフロー開発者が、更新プログラムを作成する一般的なシナリオと、管理者が後で更新プログラムを適用します。

このトピックでは、コンパイルされた XAML ワークフローの永続インスタンスに新しいアクティビティを追加するという動的更新プロセスの概要について説明します。

### <a name="Prepare"></a> 動的更新用のワークフロー定義を準備します。

動的更新プロセスでは、最初に、更新に必要なワークフロー定義を準備します。 これを行うには、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> メソッドを呼び出し、変更するワークフロー定義を渡します。 このメソッドは、ワークフロー ツリーを検証して、変更後のワークフロー定義と後で比較できるようにタグ付けを必要とする、パブリック アクティビティやパブリック変数などのすべてのオブジェクトを特定します。 この処理が完了すると、ワークフロー ツリーは複製され、元のワークフロー定義にアタッチされます。 更新マップを作成すると、ワークフロー定義の更新後のバージョンが元のワークフロー定義と比較され、その相違点に基づいて更新マップが生成されます。

動的更新用に XAML ワークフローを準備するために、XAML ワークフローが <xref:System.Activities.ActivityBuilder> に読み込まれた後、<xref:System.Activities.ActivityBuilder> が <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> に渡される場合があります。

> [!NOTE]
> シリアル化されたワークフローの操作の詳細については、<xref:System.Activities.ActivityBuilder>を参照してください[ワークフローのシリアル化と XAML との間のアクティビティ](serializing-workflows-and-activities-to-and-from-xaml.md)します。

次の例では、(複数の子アクティビティを持つ `MortgageWorkflow` で構成される) <xref:System.Activities.Statements.Sequence> の定義が <xref:System.Activities.ActivityBuilder> に読み込まれ、動的更新用に準備されます。 メソッドから制御が戻ると、<xref:System.Activities.ActivityBuilder> には元のワークフロー定義とコピーが格納されます。

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

> [!NOTE]
> このトピックに付属するサンプル コードをダウンロードするには、次を参照してください。[動的更新のサンプル コード](https://go.microsoft.com/fwlink/?LinkId=227905)します。

### <a name="Update"></a> 必要な変更を反映するようにワークフロー定義を更新します。

ワークフロー定義を更新するための準備が完了したら、必要な変更を加えることができます。 アクティビティの追加または削除、パブリック変数の追加、移動、または削除、引数の追加または削除、およびアクティビティ デリゲートのシグネチャの変更を実行できます。 実行中のアクティビティを削除したり、実行中のデリゲートのシグネチャを変更したりすることはできません。 これらの変更は、コードを使用して行うか、再ホストされたワークフロー デザイナーで行うことができます。 次の例では、カスタムの `VerifyAppraisal` アクティビティが、前の例の `MortgageWorkflow` の本体を構成する Sequence に追加されます。

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="Create"></a> 更新マップを作成します。

更新用に準備されたワークフロー定義を変更すると、更新マップを作成できます。 動的更新マップを作成するには、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> メソッドを呼び出します。 これにより、永続化されたワークフロー インスタンスを新しいワークフロー定義で読み込んで再開できるように変更するためにランタイムに必要な情報を含む <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> が返されます。 次の例では、前の例で変更した `MortgageWorkflow` 定義に対して動的マップが作成されます。

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

この更新マップは、永続化されたワークフロー インスタンスを変更するためにすぐに使用できますが、通常は、後で更新が適用されるように保存できます。 更新マップを保存する 1 つの方法として、次の例に示すように、更新マップをファイルにシリアル化します。

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 空制御が戻ると、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> の呼び出し時に追加された、複製されたワークフロー定義とその他の動的更新情報が削除され、更新されたワークフロー インスタンスを後で再開するときに使用できるように変更後のワークフロー定義を保存できるようになります。 次の例では、変更後のワークフロー定義が `MortgageWorkflow_v2.xaml` に保存されます。

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> 目的の永続化されたワークフロー インスタンスに更新マップを適用します。

更新マップは作成後にいつでも適用できます。 これは、<xref:System.Activities.DynamicUpdate.DynamicUpdateMap> によって返された <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> インスタンスを使用してすぐに実行することも、更新マップの保存したコピーを使用して後で実行することもできます。 ワークフロー インスタンスを更新するには、<xref:System.Activities.WorkflowApplicationInstance> を使用して、そのワークフロー インスタンスを <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType> に読み込みます。 次に、更新されたワークフロー定義と必要な <xref:System.Activities.WorkflowApplication> を使用して、<xref:System.Activities.WorkflowIdentity> を作成します。 この <xref:System.Activities.WorkflowIdentity> は、元のワークフローの永続化に使用されたものとは異なる場合があるため、通常は、永続化されたインスタンスが変更されていることを示すために使用されます。 <xref:System.Activities.WorkflowApplication> は、作成されると、<xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> を取得する <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> のオーバーロードを使用して読み込まれ、<xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> の呼び出しを使用してアンロードされます。 これにより、動的更新が適用され、更新されたワークフロー インスタンスが永続化されます。

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a>更新されたワークフロー インスタンスの再開

動的更新が適用されると、ワークフロー インスタンスが再開される場合があります。 更新された新しい定義と <xref:System.Activities.WorkflowIdentity> を使用する必要があります。

> [!NOTE]
> 操作の詳細については<xref:System.Activities.WorkflowApplication>と<xref:System.Activities.WorkflowIdentity>を参照してください[を使用して WorkflowIdentity と Versioning](using-workflowidentity-and-versioning.md)します。

次の例では、前の例の `MortgageWorkflow_v1.1.xaml` ワークフローがコンパイルされ、更新されたワークフロー定義を使用して読み込まれ、再開されます。

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```

> [!NOTE]
> このトピックに付属するサンプル コードをダウンロードするには、次を参照してください。[動的更新のサンプル コード](https://go.microsoft.com/fwlink/?LinkId=227905)します。
