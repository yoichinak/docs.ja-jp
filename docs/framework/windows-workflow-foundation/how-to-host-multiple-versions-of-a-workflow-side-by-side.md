---
title: '方法: ワークフローの複数のバージョンを同時にホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989643"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>方法: ワークフローの複数のバージョンを同時にホストする

`WorkflowIdentity` を使用すると、ワークフロー アプリケーションの開発者は、名前とバージョンをワークフロー定義に関連付け、永続化されたワークフロー インスタンスにこの情報を関連付けることができます。 この ID 情報は、ワークフロー アプリケーションの開発者がワークフロー定義の複数のバージョンの side-by-side 実行などのシナリオを有効にするために使用できます。また、動的更新などの他の機能の基礎となります。 チュートリアルのこの手順では、`WorkflowIdentity` を使用してワークフローの複数のバージョンを同時にホストする方法について説明します。

> [!NOTE]
> チュートリアルの完成したバージョンをダウンロードしたり、ビデオチュートリアルを表示したりするには、「 [Windows Workflow Foundation (WF45)-はじめにチュートリアル](https://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。

## <a name="in-this-topic"></a>このトピックの内容

チュートリアルのこの手順では、追加情報を提供するようにワークフローの `WriteLine` アクティビティが変更され、新しい `WriteLine` アクティビティが追加されます。 元のワークフロー アセンブリのコピーが格納され、ホスト アプリケーションは、元のワークフローと更新されたワークフローの両方を同時に実行できるように更新されます。

- [NumberGuessWorkflowActivities プロジェクトのコピーを作成するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [StateMachine ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [フローチャートワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [シーケンシャルワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [以前のワークフローバージョンを含むように WorkflowVersionMap を更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [アプリケーションをビルドして実行するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> このトピックの手順を実行する前に、アプリケーションを実行し、各種類のワークフローをいくつか開始して、ワークフローごとに 1 つまたは 2 つの推定値を作成します。 これらの永続化されたワークフローは、 [この手順と次の手順で使用します。実行中のワークフローインスタンス](how-to-update-the-definition-of-a-running-workflow-instance.md)の定義を更新します。

> [!NOTE]
> チュートリアル入門の各手順は、その前の手順に応じて異なります。 前の手順を完了していない場合は、 [Windows Workflow Foundation (WF45)-はじめにチュートリアル](https://go.microsoft.com/fwlink/?LinkID=248976)からチュートリアルの完成したバージョンをダウンロードできます。

### <a name="BKMK_BackupCopy"></a>NumberGuessWorkflowActivities プロジェクトのコピーを作成するには

1. **WF45GettingStartedTutorial**ソリューションが開いていない場合は、Visual Studio 2012 で開きます。

2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。

3. **WF45GettingStartedTutorial**ソリューションを閉じます。

4. エクスプローラーを開き、チュートリアルのソリューション ファイルおよびプロジェクト フォルダーが格納されているフォルダーに移動します。

5. **NumberGuessWorkflowHost**および**NumberGuessWorkflowActivities**と同じフォルダーに、**以前のバージョン**という名前の新しいフォルダーを作成します。 このフォルダーは、チュートリアルの以降の手順で使用されるワークフローの異なるバージョンを含むアセンブリを格納するために使用されます。

6. **NumberGuessWorkflowActivities\bin\debug**フォルダー (または、プロジェクトの設定によっては**bin\release** ) に移動します。 **NumberGuessWorkflowActivities**をコピーし、 **[以前のバージョン]** フォルダーに貼り付けます。

7. **以前のバージョン**のフォルダーの**NumberGuessWorkflowActivities**の名前を**NumberGuessWorkflowActivities_v1**に変更します。

    > [!NOTE]
    > このトピックの手順では、ワークフローの複数のバージョンを格納するためのアセンブリを管理する 1 つの方法を示します。 アセンブリに厳密な名前を付けてグローバル アセンブリ キャッシュに登録するなど、他の方法も使用できます。

8. **NumberGuessWorkflowActivities_du**という名前の新しいフォルダーを**NumberGuessWorkflowHost**、 **NumberGuessWorkflowActivities**、および新しく追加した以前の**バージョン**のフォルダーと同じフォルダーに作成し、すべてのファイルをコピーします。**NumberGuessWorkflowActivities**フォルダーのサブフォルダーを新しい**NumberGuessWorkflowActivities_du**フォルダーに追加します。 アクティビティの初期バージョンに対応するプロジェクトのこのバックアップコピーは、次の[方法で使用されます。実行中のワークフローインスタンス](how-to-update-the-definition-of-a-running-workflow-instance.md)の定義を更新します。

9. Visual Studio 2012 で**WF45GettingStartedTutorial**ソリューションを再度開きます。

### <a name="BKMK_UpdateWorkflows"></a>ワークフローを更新するには

ここでは、ワークフロー定義が更新されます。 ユーザーの推定値についてフィードバックを返す 2 つの `WriteLine` アクティビティが更新され、新しい `WriteLine` アクティビティが追加されます。新しいアクティビティは、数値が推定されるとゲームに関する追加情報を提供します。

#### <a name="BKMK_UpdateStateMachine"></a>StateMachine ワークフローを更新するには

1. **ソリューションエクスプローラー**の**NumberGuessWorkflowActivities**プロジェクトで、 **statemachinenumberguessworkflow.xaml**をダブルクリックします。

2. ステートマシンで、[推測された**不適切**な切り替え] をダブルクリックします。

3. `Text` アクティビティで、左端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. `Text` アクティビティで、右端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. ワークフローデザイナーの上部にある階層リンク表示で **[StateMachine]** をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。

6. ステートマシンの **推定** の 正しい切り替え をダブルクリックします。

7. **ツールボックス**の **[プリミティブ]** セクションから**WriteLine**アクティビティをドラッグし、遷移の **[ここにアクションアクティビティをドロップ]** します ラベルの上にドロップします。

8. `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a>フローチャートワークフローを更新するには

1. **ソリューションエクスプローラー**の**NumberGuessWorkflowActivities**プロジェクトで、 **flowchartnumberguessworkflow.xaml**をダブルクリックします。

2. 左端の `Text` アクティビティの `WriteLine` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. 右端の `Text` アクティビティの `WriteLine` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. **ツールボックス** `True`の **[プリミティブ]** セクションから**WriteLine**アクティビティをドラッグし、最上位`FlowDecision`のアクションのドロップポイントにドロップします。 `WriteLine` アクティビティがフローチャートに追加され、`True` の `FlowDecision` アクションにリンクされます。

5. `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a>シーケンシャルワークフローを更新するには

1. **ソリューションエクスプローラー**の**NumberGuessWorkflowActivities**プロジェクトで、 **sequentialnumberguessworkflow.xaml**をダブルクリックします。

2. `Text` アクティビティで、左端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. `Text` アクティビティで、右端の `WriteLine` アクティビティの `If` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. **ツールボックス**の **[プリミティブ]** セクションから**writeline**アクティビティをドラッグし、 **dowhile**アクティビティの後にドロップして、 **writeline**がルート`Sequence`アクティビティの最後のアクティビティになるようにします。

5. `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a>以前のワークフローバージョンを含むように WorkflowVersionMap を更新するには

1. **NumberGuessWorkflowHost**プロジェクトの下にある**WorkflowVersionMap.cs** (または**workflowversionmap .vb**) をダブルクリックして開きます。

2. 次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. 既存の 3 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。 これらの新しい `v1` ワークフロー ID は、更新が行われる前に開始されたワークフローに対して正しいワークフロー定義を指定するために使用されます。

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. `WorkflowVersionMap` コンストラクターで、3 つの現在のワークフロー ID の `Version` プロパティを `2.0.0.0` に更新します。

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    ワークフローの現在のバージョンをディクショナリに追加するコードでは、プロジェクトで参照されている現在のバージョンを使用しているため、ワークフロー定義を初期化するコードを更新する必要はありません。

5. コンストラクターで、現在のバージョンをディクショナリに追加するコードの直後に、次のコードを追加します。

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    これらのワークフロー ID は、対応するワークフロー定義の最初のバージョンに関連付けられます。

6. 次に、ワークフロー定義の最初のバージョンを含むアセンブリを読み込み、対応するワークフロー定義を作成してそのディクショナリに追加します。

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    次の例では、更新された `WorkflowVersionMap` クラス全体を示します。

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

### <a name="BKMK_BuildAndRun"></a> アプリケーションをビルドして実行するには

1. Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドし、Ctrl キーを押しながら F5 キーを押して起動します。

2. **[新しいゲーム]** をクリックして、新しいワークフローを開始します。 ワークフローのバージョンは、ステータス ウィンドウの下に表示され、関連付けられた `WorkflowIdentity` から更新後のバージョンを反映します。 完了時にワークフローの追跡ファイルを確認できるように `InstanceId` を書き留めておき、ゲームが完了するまで推定値を入力します。 `WriteLine` アクティビティに対する更新に基づき、ステータス ウィンドウに示される情報に、ユーザーの推定値がどのように表示されるかを確認します。

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > `WriteLine` アクティビティから更新されたテキストは表示されますが、このトピックで追加された最後の `WriteLine` アクティビティの出力は表示されません。 これは、ステータス ウィンドウが `PersistableIdle` ハンドラーによって更新されるためです。 ワークフローは完了し、最後のアクティビティの後にアイドル状態にならないため、`PersistableIdle` ハンドラーは呼び出されません。 ただし、`Completed` ハンドラーによって同様のメッセージがステータス ウィンドウに表示されます。 必要に応じて、コードを `Completed` ハンドラーに追加し、`StringWriter` からテキストを抽出してステータス ウィンドウに表示できます。

3. エクスプローラーを開き、 **NumberGuessWorkflowHost\bin\debug**フォルダー (プロジェクトの設定によっては**bin\release** ) に移動し、完了したワークフローに対応するメモ帳を使用して追跡ファイルを開きます。 `InstanceId`をメモしていない場合は、Windows エクスプローラーの **[更新日時]** 情報を使用して、正しい追跡ファイルを特定できます。

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    更新された `WriteLine` の出力は、このトピックで追加した `WriteLine` の出力を含む追跡ファイル内に含まれています。

4. 数値推測アプリケーションに戻り、更新が行われる前に開始したワークフローのうち 1 つを選択します。 現在選択されているワークフローのバージョンを特定するには、ステータス ウィンドウの下に表示されるバージョン情報を確認します。 いくつかの推定値を入力し、ステータスの更新が前のバージョンからの `WriteLine` アクティビティの出力と一致しており、ユーザーの推定値が含まれていないことを確認してください。 これらのワークフローでは、`WriteLine` の更新を含まない以前のワークフロー定義を使用しているためです。

    次の手順では[、次の操作を行います。実行中のワークフローインスタンス](how-to-update-the-definition-of-a-running-workflow-instance.md)の定義を更新します。実行中`v1`のワークフローインスタンスが更新され、 `v2`インスタンスとして新しい機能が含まれるようになります。
