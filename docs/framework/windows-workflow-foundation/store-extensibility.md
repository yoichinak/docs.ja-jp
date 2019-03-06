---
title: ストア拡張
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 0c6f67469db04705a9ac7827ef301ff226ea3bdb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465728"
---
# <a name="store-extensibility"></a>ストア拡張

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用して、永続性データベースのインスタンスをクエリする場合に使用できるカスタムのアプリケーション固有のプロパティを昇格できます。 プロパティを昇格することで、データベース内の特殊なビュー内で値が使用できるようになります。 これらの昇格したプロパティ (ユーザー クエリで使用できるプロパティ) は、単純型 (Int64、Guid、String、DateTime など) またはシリアル化されたバイナリ型 (byte[]) になる場合があります。

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスには <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> メソッドがあり、クエリで使用できるプロパティとしてプロパティを昇格するために使用できます。 次の例は、ストア拡張のエンド ツー エンドの例です。

1. この例のシナリオでは、ドキュメント処理 (DP) アプリケーションにワークフローがあり、それぞれがドキュメント処理にカスタム アクティビティを使用しています。 これらのワークフローは、エンド ユーザーから見える必要がある一連の状態変数を備えています。 これを実現するために、DP アプリケーションには <xref:System.Activities.Persistence.PersistenceParticipant> 型を持つインスタンス拡張機能があり、状態変数を提供するアクティビティによって使用されます。

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. 次に、新しい機能拡張がホストに追加されます。

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     カスタム永続参加要素を追加する方法の詳細については、次を参照してください。、[永続参加要素](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)サンプル。

3. DP アプリケーションでカスタム アクティビティのさまざまな状態フィールドの設定、 **Execute**メソッド。

    ```csharp
    public override void Execute(CodeActivityContext context)
    {
        // ...
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();
        // ...
    }
    ```

4. ワークフロー インスタンスが永続性ポイントに達すると、 **CollectValues**のメソッド、 **DocumentStatusExtension**永続参加要素は、永続性データにこれらのプロパティを保存しますコレクションです。

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");

        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)
        {
            readWriteValues = new Dictionary<XName, object>();
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);

            writeOnlyValues = null;
        }
        // ...
    }
    ```

    > [!NOTE]
    > これらすべてのプロパティに渡される**SqlWorkflowInstanceStore**を介して、永続化フレームワークによって、 **SaveWorkflowCommand.InstanceData**コレクション。

5. DP アプリケーションは、SQL Workflow Instance Store を初期化しを呼び出す、**昇格**メソッドをこのデータを昇格します。

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);

    List<XName> variantProperties = new List<XName>()
    {
        xNS.GetName("UserName"),
        xNS.GetName("ApprovalStatus"),
        xNS.GetName("DocumentId"),
        xNS.GetName("LastModifiedTime")
    };

    store.Promote("DocumentStatus", variantProperties, null);
    ```

    この昇格情報に基づいて**SqlWorkflowInstanceStore**の列のデータのプロパティを配置、 [InstancePromotedProperties](#InstancePromotedProperties)ビュー。

6. 昇格テーブルのデータのサブセットを照会するために、DP アプリケーションによって昇格ビューの上にカスタマイズされたビューが追加されます。

    ```sql
    create view [dbo].[DocumentStatus] with schemabinding
    as
        select  P.[InstanceId] as [InstanceId],
            P.Value1 as [UserName],
            P.Value2 as [ApprovalStatus],
            P.Value3 as [DocumentId],
            P.Value4 as [LastUpdatedTime]
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P
    where P.PromotionName = N'DocumentStatus'
    go
    ```

## <a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] view

|列名|列の型|説明|
|-----------------|-----------------|-----------------|
|InstanceId|GUID|この昇格が属するワークフロー インスタンス。|
|PromotionName|nvarchar(400)|昇格自体の名前。|
|Value1、Value2、Value3、…Value32|sql_variant|昇格したプロパティ自体の値。 ほとんどの SQL プリミティブ データ型はバイナリ ブロブを除外し、長さが 8,000 バイトを超える文字列は sql_variant に合わせて短縮されます。|
|Value33、Value34、Value35、…、Value64|varbinary(max)|varbinary(max) として明示的に宣言される昇格したプロパティの値。|
