---
title: '方法: 複数のバージョンをワークフロー サイド バイ サイドのホストします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 6cb552752c1693ce8008eb57e0703882b7281830
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705988"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a>方法: 複数のバージョンをワークフロー サイド バイ サイドのホストします。
`WorkflowIdentity` を使用すると、ワークフロー アプリケーションの開発者は、名前とバージョンをワークフロー定義に関連付け、永続化されたワークフロー インスタンスにこの情報を関連付けることができます。 この ID 情報は、ワークフロー アプリケーションの開発者がワークフロー定義の複数のバージョンの side-by-side 実行などのシナリオを有効にするために使用できます。また、動的更新などの他の機能の基礎となります。 チュートリアルのこの手順では、`WorkflowIdentity` を使用してワークフローの複数のバージョンを同時にホストする方法について説明します。

> [!NOTE]
>  完成版をダウンロードまたはチュートリアルのビデオ チュートリアルを表示を参照してください。 [Windows Workflow Foundation (WF45) - チュートリアル入門](https://go.microsoft.com/fwlink/?LinkID=248976)します。  
  
## <a name="in-this-topic"></a>このトピックの内容  
 チュートリアルのこの手順では、追加情報を提供するようにワークフローの `WriteLine` アクティビティが変更され、新しい `WriteLine` アクティビティが追加されます。 元のワークフロー アセンブリのコピーが格納され、ホスト アプリケーションは、元のワークフローと更新されたワークフローの両方を同時に実行できるように更新されます。  
  
-   [NumberGuessWorkflowActivities プロジェクトのコピーを作成するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [ステート マシン ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [フローチャート ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [シーケンシャル ワークフローを更新するには](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [ワークフローの以前のバージョンを含める WorkflowVersionMap を更新します。](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [ビルドして、アプリケーションの実行](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  このトピックの手順を実行する前に、アプリケーションを実行し、各種類のワークフローをいくつか開始して、ワークフローごとに 1 つまたは 2 つの推定値を作成します。 これらの永続化されたワークフローがこの手順と次の手順で使用される[方法。実行中のワークフロー インスタンスの定義を更新](how-to-update-the-definition-of-a-running-workflow-instance.md)します。

> [!NOTE]
>  チュートリアル入門の各手順は、その前の手順に応じて異なります。 前の手順を完了しなかった場合は、」からチュートリアルの完成版をダウンロードできます[Windows Workflow Foundation (WF45) - チュートリアル入門](https://go.microsoft.com/fwlink/?LinkID=248976)します。  
  
### <a name="BKMK_BackupCopy"></a> NumberGuessWorkflowActivities プロジェクトのコピーを作成するには  
  
1.  開く、 **WF45GettingStartedTutorial**が開いていない場合、Visual Studio 2012 でのソリューションです。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  閉じる、 **WF45GettingStartedTutorial**ソリューション。  
  
4.  エクスプローラーを開き、チュートリアルのソリューション ファイルおよびプロジェクト フォルダーが格納されているフォルダーに移動します。  
  
5.  という名前の新しいフォルダーを作成する**PreviousVersions**と同じフォルダーに**NumberGuessWorkflowHost**と**NumberGuessWorkflowActivities**します。 このフォルダーは、チュートリアルの以降の手順で使用されるワークフローの異なるバージョンを含むアセンブリを格納するために使用されます。  
  
6.  移動し、 **NumberGuessWorkflowActivities\bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって)。 コピー **NumberGuessWorkflowActivities.dll**貼り付けます、 **PreviousVersions**フォルダー。  
  
7.  名前を変更**NumberGuessWorkflowActivities.dll**で、 **PreviousVersions**フォルダー **NumberGuessWorkflowActivities_v1.dll**します。  
  
    > [!NOTE]
    >  このトピックの手順では、ワークフローの複数のバージョンを格納するためのアセンブリを管理する 1 つの方法を示します。 アセンブリに厳密な名前を付けてグローバル アセンブリ キャッシュに登録するなど、他の方法も使用できます。

8.  という名前の新しいフォルダーを作成する**NumberGuessWorkflowActivities_du**と同じフォルダーに**NumberGuessWorkflowHost**、 **NumberGuessWorkflowActivities**、し、新しく追加**PreviousVersions**フォルダーでは、すべてのファイルとサブフォルダーをコピーし、 **NumberGuessWorkflowActivities**を新しいフォルダー **NumberGuessWorkflowActivities_du**フォルダー。 アクティビティの最初のバージョンのプロジェクトのこのバックアップ コピーが使用される[方法。実行中のワークフロー インスタンスの定義を更新](how-to-update-the-definition-of-a-running-workflow-instance.md)します。

9. 開き直す、 **WF45GettingStartedTutorial** Visual Studio 2012 でのソリューションです。

### <a name="BKMK_UpdateWorkflows"></a> ワークフローを更新するには
 ここでは、ワークフロー定義が更新されます。 ユーザーの推定値についてフィードバックを返す 2 つの `WriteLine` アクティビティが更新され、新しい `WriteLine` アクティビティが追加されます。新しいアクティビティは、数値が推定されるとゲームに関する追加情報を提供します。

#### <a name="BKMK_UpdateStateMachine"></a> ステート マシン ワークフローを更新するには

1.  **ソリューション エクスプ ローラー**下で、 **NumberGuessWorkflowActivities**プロジェクトで、ダブルクリックして**StateMachineNumberGuessWorkflow.xaml**します。

2.  ダブルクリックして、 **Guess Incorrect**ステート マシンを移行します。

3.  
  `Text` アクティビティで、左端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4.  
  `Text` アクティビティで、右端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5.  全体に戻る をクリックして状態マシン ビューは、ワークフロー デザイナーに**StateMachine**階層リンクで、ワークフロー デザイナーの上部に表示します。

6.  ダブルクリックして、 **Guess Correct**ステート マシンを移行します。

7.  ドラッグ、 **WriteLine**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**上にドロップし、**ここにアクティビティを Drop Action**のラベル、遷移します。

8.  
  `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a> フローチャート ワークフローを更新するには

1.  **ソリューション エクスプ ローラー**下で、 **NumberGuessWorkflowActivities**プロジェクトで、ダブルクリックして**FlowchartNumberGuessWorkflow.xaml**します。

2.  左端の `Text` アクティビティの `WriteLine` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  右端の `Text` アクティビティの `WriteLine` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  ドラッグ、 **WriteLine**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**のドロップ ポイント上にドロップし、`True`の最上位にあるアクション`FlowDecision`. 
  `WriteLine` アクティビティがフローチャートに追加され、`True` の `FlowDecision` アクションにリンクされます。

5.  
  `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a> シーケンシャル ワークフローを更新するには

1.  **ソリューション エクスプ ローラー**下で、 **NumberGuessWorkflowActivities**プロジェクトで、ダブルクリックして**SequentialNumberGuessWorkflow.xaml**します。

2.  
  `Text` アクティビティで、左端の `WriteLine` の `If` を更新します。

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3.  
  `Text` アクティビティで、右端の `WriteLine` アクティビティの `If` を更新します。

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4.  ドラッグ、 **WriteLine**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**後ろにドロップし、 **DoWhile**アクティビティように、 **WriteLine**ルート内の最後の活動は、`Sequence`アクティビティ。

5.  
  `Text` プロパティ ボックスに、次の式を入力します。

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a> ワークフローの以前のバージョンを含める WorkflowVersionMap を更新します。

1.  ダブルクリック**WorkflowVersionMap.cs** (または**WorkflowVersionMap.vb**) の下、 **NumberGuessWorkflowHost**プロジェクトを開きます。

2.  次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3.  既存の 3 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。 これらの新しい `v1` ワークフロー ID は、更新が行われる前に開始されたワークフローに対して正しいワークフロー定義を指定するために使用されます。

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

4.  `WorkflowVersionMap` コンストラクターで、3 つの現在のワークフロー ID の `Version` プロパティを `2.0.0.0` に更新します。

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

5.  コンストラクターで、現在のバージョンをディクショナリに追加するコードの直後に、次のコードを追加します。

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

6.  次に、ワークフロー定義の最初のバージョンを含むアセンブリを読み込み、対応するワークフロー定義を作成してそのディクショナリに追加します。

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

1.  Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドし、Ctrl キーを押しながら F5 キーを押して起動します。

2.  クリックして新しいワークフローを開始**新しいゲーム**します。 ワークフローのバージョンは、ステータス ウィンドウの下に表示され、関連付けられた `WorkflowIdentity` から更新後のバージョンを反映します。 完了時にワークフローの追跡ファイルを確認できるように `InstanceId` を書き留めておき、ゲームが完了するまで推定値を入力します。 
  `WriteLine` アクティビティに対する更新に基づき、ステータス ウィンドウに示される情報に、ユーザーの推定値がどのように表示されるかを確認します。

 **1 から 10 までの数値を入力してください。**  
**5 が多すぎます。**  
**1 から 10 までの数値を入力してください。**  
**3 が多すぎます。**  
**1 から 10 までの数値を入力してください。**  
**1 は低いままです。**  
**1 から 10 までの数値を入力してください。**  
**これで、4 つの交替で数を推測します。**  

    > [!NOTE]
    >  
  `WriteLine` アクティビティから更新されたテキストは表示されますが、このトピックで追加された最後の `WriteLine` アクティビティの出力は表示されません。 これは、ステータス ウィンドウが `PersistableIdle` ハンドラーによって更新されるためです。 ワークフローは完了し、最後のアクティビティの後にアイドル状態にならないため、`PersistableIdle` ハンドラーは呼び出されません。 ただし、`Completed` ハンドラーによって同様のメッセージがステータス ウィンドウに表示されます。 必要に応じて、コードを `Completed` ハンドラーに追加し、`StringWriter` からテキストを抽出してステータス ウィンドウに表示できます。

3.  Windows エクスプ ローラーを開きに移動、 **numberguessworkflowhost \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって) と、対応するメモ帳を使用して追跡ファイルを開く完了したワークフロー。 メモして行っていない場合、`InstanceId`を使用して正しい追跡ファイルを識別する、**に変更された日付**Windows エクスプ ローラーの情報。

 **1 から 10 までの数値を入力してください**
**5 が多すぎます**。
 **1 から 10 までの数値を入力してください**
**3 が多すぎます**。
 **1 から 10 までの数値を入力してください**
**1 が小さすぎます**。
 **1 から 10 までの数値を入力してください**
**2 が正しい。察しのように 4 になります。**      更新された `WriteLine` の出力は、このトピックで追加した `WriteLine` の出力を含む追跡ファイル内に含まれています。

4.  数値推測アプリケーションに戻り、更新が行われる前に開始したワークフローのうち 1 つを選択します。 現在選択されているワークフローのバージョンを特定するには、ステータス ウィンドウの下に表示されるバージョン情報を確認します。 いくつかの推定値を入力し、ステータスの更新が前のバージョンからの `WriteLine` アクティビティの出力と一致しており、ユーザーの推定値が含まれていないことを確認してください。 これらのワークフローでは、`WriteLine` の更新を含まない以前のワークフロー定義を使用しているためです。

     次の手順で[方法。実行しているワークフロー インスタンスの定義を更新](how-to-update-the-definition-of-a-running-workflow-instance.md)、実行`v1`ワークフロー インスタンスが更新されるは、新しい機能が含まれているため、`v2`インスタンス。
