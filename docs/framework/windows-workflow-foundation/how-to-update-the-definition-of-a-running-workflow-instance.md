---
title: '方法: 実行中のワークフロー インスタンスの定義を更新します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: d3ff9d217d085e3afe5171cce9d80f8dbc32ff36
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722907"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>方法: 実行中のワークフロー インスタンスの定義を更新します。

動的更新は、ワークフロー アプリケーションの開発者が永続化されたワークフロー インスタンスのワークフロー定義を更新するためのメカニズムを提供します。 必要な変更には、バグ修正の実装、新しい要件の実装、または予期しない変更への対応があります。 このチュートリアルでは、この手順は、の永続化されたインスタンスを変更する動的更新を使用する方法を示します、`v1`で導入された新しい機能と一致する数値推測ワークフロー[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。

> [!NOTE]
> 完成版をダウンロードまたはチュートリアルのビデオ チュートリアルを表示を参照してください。 [Windows Workflow Foundation (WF45) - チュートリアル入門](https://go.microsoft.com/fwlink/?LinkID=248976)します。

## <a name="in-this-topic"></a>このトピックの内容

- [CreateUpdateMaps プロジェクトを作成するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [StateMachineNumberGuessWorkflow を更新するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [FlowchartNumberGuessWorkflow を更新するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [SequentialNumberGuessWorkflow を更新するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [ビルドおよび CreateUpdateMaps アプリケーションを実行するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [更新されたワークフロー アセンブリをビルドするには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [新しいバージョンで WorkflowVersionMap を更新するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [動的更新を適用するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [更新されたワークフローでアプリケーションを実行するには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [以前のバージョンのワークフローを開始できるようにするには](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="BKMK_CreateProject"></a> CreateUpdateMaps プロジェクトを作成するには

1. 右クリックして**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**します。

2. **インストール済み**ノードの  **Visual c#**、 **Windows** (または**Visual Basic**、 **Windows**)。

    > [!NOTE]
    > Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。

     .NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。 選択**コンソール アプリケーション**から、 **Windows**一覧。 型**CreateUpdateMaps**に、**名前**ボックスし、をクリックして**OK**します。

3. 右クリックして**CreateUpdateMaps**で**ソリューション エクスプ ローラー**選択**参照の追加**します。

4. 選択**Framework**から、**アセンブリ**内のノード、**参照の追加**一覧。 型**System.Activities**に、**アセンブリの検索**ボックスをアセンブリをフィルター処理し、目的の参照を簡単に選択します。

5. 横にあるチェック ボックスをオン**System.Activities**から、**検索結果**一覧。

6. 型**シリアル化**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Runtime.Serialization**から、**検索結果**一覧。

7. 型**System.Xaml**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Xaml**から、**検索結果**一覧。

8. をクリックして**OK**を閉じます**参照マネージャー**参照を追加します。

9. 次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. `Program` クラス (または `Module1`) に次の 2 つの文字列メンバーを追加します。

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. `StartUpdate` クラス (または `Program`) に次の `Module1` メソッドを追加します。 このメソッドにより、指定した xaml ワークフロー定義が `ActivityBuilder` に読み込まれた後、`DynamicUpdate.PrepareForUpdate` が呼び出されます。 `PrepareForUpdate` は `ActivityBuilder` 内にワークフロー定義のコピーを作成します。 ワークフロー定義が変更されると、更新マップを作成するように変更されたワークフロー定義と共に、このコピーは使用されます。

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. 次に、`CreateUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。 これにより、DynamicUpdateServices.CreateUpdateMap が呼び出されて動的更新マップが作成され、指定した名前を使用してその更新マップが保存されます。 この更新マップには、`ActivityBuilder` に格納されている元のワークフロー定義を使用して開始された、永続化されたワークフロー インスタンスが、更新されたワークフロー定義を使用して完了するよう更新するために、ワークフロー ランタイムで必要な情報が含まれています。

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. `SaveUpdatedDefinition` クラス (または `Program`) に次の `Module1` メソッドを追加します。 このメソッドは、更新マップが作成されると、更新されたワークフロー定義を保存します。

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="BKMK_StateMachine"></a> StateMachineNumberGuessWorkflow を更新するには

1. 
  `CreateStateMachineUpdateMap` クラス (または `Program`) に `Module1` を追加します。

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. 
  `StartUpdate` を呼び出し、ワークフローのルート `StateMachine` アクティビティへの参照を取得します。

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. 2 つの式を次に、更新`WriteLine`に加えられた更新と一致するようにユーザーの推定値が大きすぎるか小さすぎるかどうかを表示するアクティビティ[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. 終了メッセージを表示する新しい `WriteLine` アクティビティを追加します。

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. ワークフローを更新したら、`CreateUpdateMaps` と `SaveUpdatedDefinition` を呼び出します。 `CreateUpdateMaps` は `DynamicUpdateMap` を作成して保存し、`SaveUpdatedDefinition` は更新されたワークフロー定義を保存します。

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    完成した `CreateStateMachineUpdateMap` メソッドは次のようになります。

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_Flowchart"></a> FlowchartNumberGuessWorkflow を更新するには

1. 
  `CreateFlowchartUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。 このメソッドは `CreateStateMachineUpdateMap` に似ています。 最初に `StartUpdate` を呼び出し、フローチャート ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_Sequential"></a> SequentialNumberGuessWorkflow を更新するには

1. 
  `CreateSequentialUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。 このメソッドは、他の 2 つのメソッドに似ています。 最初に `StartUpdate` を呼び出し、シーケンシャル ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="BKMK_CreateUpdateMaps"></a> ビルドおよび CreateUpdateMaps アプリケーションを実行するには

1. 
  `Main` メソッドを更新し、次の 3 つのメソッド呼び出しを追加します。 これらのメソッドは次のセクションで追加されます。 各メソッドは、対応する数値推測ワークフローを更新し、更新内容を示す `DynamicUpdateMap` を作成します。

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. 右クリックして**CreateUpdateMaps**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**します。

3. Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `CreateUpdateMaps` アプリケーションを実行します。

    > [!NOTE]
    > `CreateUpdateMaps`アプリケーション確認する場合は、実行中にステータス情報は表示されませんが、 **NumberGuessWorkflowActivities_du**フォルダーと**PreviousVersions**フォルダーが表示されます更新されたワークフロー定義ファイルは、更新マップ。

    更新マップが作成され、ワークフロー定義が更新されたら、次に、更新された定義を含む更新されたワークフロー アセンブリをビルドします。

### <a name="BKMK_BuildAssembly"></a> 更新されたワークフロー アセンブリをビルドするには

1. Visual Studio 2012 の 2 番目のインスタンスを開きます。

2. 選択**オープン**、**プロジェクト/ソリューション**から、**ファイル**メニュー。

3. 移動し、 **NumberGuessWorkflowActivities_du**で作成したフォルダー[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)を選択します**NumberGuessWorkflowActivities.csproj** (または**vbproj**)、をクリック**オープン**します。

4. **ソリューション エクスプ ローラー**を右クリックして**SequentialNumberGuessWorkflow.xaml**選択**プロジェクトから除外**します。 同じ操作を行う**FlowchartNumberGuessWorkflow.xaml**と**StateMachineNumberGuessWorkflow.xaml**します。 この手順により、以前のバージョンのワークフロー定義がプロジェクトから削除されます。

5. 選択**既存項目の追加**から、**プロジェクト**メニュー。

6. 移動し、 **NumberGuessWorkflowActivities_du**で作成したフォルダー[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。

7. 選択**XAML ファイル (\*.xaml;\*します。xoml)** から、**ファイルの種類**ドロップダウン リスト。

8. 選択**SequentialNumberGuessWorkflow_du.xaml**、 **FlowchartNumberGuessWorkflow_du.xaml**、および**StateMachineNumberGuessWorkflow_du.xaml** をクリックします。**追加**します。

    > [!NOTE]
    > 複数の項目を同時に選択するには、Ctrl を押しながら各項目をクリックします。

    この手順により、更新されたワークフロー定義がプロジェクトに追加されます。

9. Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。

10. 選択**ソリューションを閉じる**から、**ファイル**メニュー。 ソリューション ファイル、プロジェクトが必要ではありませんので、クリックして**いいえ**ソリューション ファイルを保存せずに Visual Studio を閉じます。 選択**終了**から、**ファイル**] メニューの [Visual Studio を終了します。

11. Windows エクスプ ローラーを開きに移動し、 **numberguessworkflowactivities_du \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって)。

12. 名前を変更**NumberGuessWorkflowActivities.dll**に**NumberGuessWorkflowActivities_v15.dll**、コピー、 **PreviousVersions** で作成したフォルダー[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。

### <a name="BKMK_UpdateWorkflowVersionMap"></a> 新しいバージョンで WorkflowVersionMap を更新するには

1. Visual Studio 2012 の最初のインスタンスに切り替えます。

2. ダブルクリック**WorkflowVersionMap.cs** (または**WorkflowVersionMap.vb**) の下、 **NumberGuessWorkflowHost**プロジェクトを開きます。

3. 既存の 6 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。 このチュートリアルでは、`1.5.0.0` は動的更新 ID の `WorkflowIdentity.Version` として使用されます。 これらの新しい `v15` ワークフロー ID は、動的に更新される永続化されたワークフロー インスタンスに適切なワークフロー定義を指定するために使用されます。

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
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

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. コンストラクターの末尾に、次のコードを追加します。 このコードでは、動的更新ワークフロー ID を初期化し、対応するワークフロー定義を読み込み、これらをワークフロー バージョン ディクショナリに追加します。

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     完成した `WorkflowVersionMap` クラスは次のようになります。

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

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

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

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

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

5. Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。

### <a name="BKMK_ApplyUpdate"></a> 動的更新を適用するには

1. 右クリックして**WF45GettingStartedTutorial**で**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**します。

2. **インストール済み**ノードの  **Visual c#**、 **Windows** (または**Visual Basic**、 **Windows**)。

    > [!NOTE]
    > Visual Studio で第一言語として設定されているプログラミング言語に応じて、 **[インストール済み]** ノードの **[他の言語]** ノードの下に、 **[Visual C#]** ノードまたは **[Visual Basic]** ノードが表示されます。

    .NET Framework バージョンのドロップダウン リストで **[.NET Framework 4.5]** が選択されていることを確認します。 選択**コンソール アプリケーション**から、 **Windows**一覧。 型**ApplyDynamicUpdate**に、**名前**ボックスし、をクリックして**OK**します。

3. 右クリックして**ApplyDynamicUpdate**で**ソリューション エクスプ ローラー**選択**参照の追加**します。

4. クリックして**ソリューション**横にチェック ボックスをオンおよび**NumberGuessWorkflowHost**します。 この参照は、`ApplyDynamicUpdate` で `NumberGuessWorkflowHost.WorkflowVersionMap` クラスを使用できるようにするために必要です。

5. 選択**Framework**から、**アセンブリ**内のノード、**参照の追加**一覧。 型**System.Activities**に、**アセンブリの検索**ボックス。 これにより、アセンブリがフィルター処理され、目的の参照が選択しやすくなります。

6. 横にあるチェック ボックスをオン**System.Activities**から、**検索結果**一覧。

7. 型**シリアル化**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Runtime.Serialization**から、**検索結果**一覧。

8. 型**DurableInstancing**に、**アセンブリの検索**ボックスし、チェック ボックスの横にある**System.Activities.DurableInstancing**と**System.Runtime.DurableInstancing**から、**検索結果**一覧。

9. をクリックして**OK**を閉じます**参照マネージャー**参照を追加します。

10. 右クリックして**ApplyDynamicUpdate**ソリューション エクスプ ローラーで選択**追加**、**クラス**します。 型`DynamicUpdateInfo`に、**名前**ボックスし、をクリックして**追加**します。

11. 
  `DynamicUpdateInfo` クラスに次の 2 つのメンバーを追加します。 完成した `DynamicUpdateInfo` クラスは次のようになります。 このクラスには、ワークフロー インスタンスの更新時に使用された更新マップと新しいワークフロー ID に関する情報が格納されています。

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. 次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. ダブルクリック**Program.cs** (または**Module1.vb**) ソリューション エクスプ ローラーでします。

14. 次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. `Program` クラス (または `Module1`) に次の接続文字列メンバーを追加します。

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > 使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。

16. `GetIDs` クラス (または `Program`) に次の `Module1` メソッドを追加します。 このメソッドは、永続化されたワークフロー インスタンス ID の一覧を返します。

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. `LoadMap` クラス (または `Program`) に次の `Module1` メソッドを追加します。 このメソッドは、更新マップに `v1` ワークフロー ID をマップするディクショナリと、対応する永続化されたワークフロー インスタンスの更新に使用される新しいワークフロー ID を作成します。

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. `LoadMaps` クラス (または `Program`) に次の `Module1` メソッドを追加します。 このメソッドは、3 つの更新マップを読み込み、更新マップに `v1` ワークフロー ID をマップするディクショナリを作成します。

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. `Main` に次のコードを追加します。 このコードでは、永続化されたワークフロー インスタンスを反復処理し、それぞれの `WorkflowIdentity` を調べます。 `WorkflowIdentity` が `v1` ワークフロー インスタンスにマップされると、`WorkflowApplication` は、更新されたワークフロー定義と更新されたワークフロー ID を使用して構成されます。 次に、`WorkflowApplication.Load` がそのインスタンスと更新マップを使用して呼び出され、動的更新マップが適用されます。 更新が適用されると、更新されたインスタンスは `Unload` の呼び出しによって永続化されます。

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. 右クリックして**ApplyDynamicUpdate**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**します。

21. Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `ApplyDynamicUpdate` アプリケーションを実行して、永続化されたワークフロー インスタンスを更新します。 表示される出力は、次のようになります。 バージョン 1.0.0.0 のワークフローはバージョン 1.5.0.0 に更新されますが、バージョン 2.0.0.0 のワークフローは更新されません。

    **検査するには。StateMachineNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。StateMachineNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。FlowchartNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。FlowchartNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。SequentialNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。SequentialNumberGuessWorkflow;バージョン 1.5.0.0 を =**\
    **検査するには。SequentialNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。SequentialNumberGuessWorkflow;バージョン 1.5.0.0 を =**\
    **検査するには。SequentialNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。SequentialNumberGuessWorkflow;バージョン 1.5.0.0 を =**\
    **検査するには。StateMachineNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。StateMachineNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。FlowchartNumberGuessWorkflow;バージョン 1.0.0.0 を =**\
    **更新されます。FlowchartNumberGuessWorkflow; Version=1.5.0.0**\
    **検査するには。StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **検査するには。StateMachineNumberGuessWorkflow; Version=2.0.0.0**\
    **検査するには。FlowchartNumberGuessWorkflow; Version=2.0.0.0**\
    **検査するには。FlowchartNumberGuessWorkflow; Version=2.0.0.0**\
    **検査するには。SequentialNumberGuessWorkflow; Version=2.0.0.0**\
    **検査するには。SequentialNumberGuessWorkflow; Version=2.0.0.0**\
    **続行する任意のキーを押してください.**

### <a name="BKMK_BuildAndRun"></a> 更新されたワークフローでアプリケーションを実行するには

1. 右クリックして**NumberGuessWorkflowHost**で**ソリューション エクスプ ローラー**選択**スタートアップ プロジェクトとして設定**します。

2. Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。

3. クリックして**新しいゲーム**を新しいワークフローを開始し、ワークフローを示すステータス ウィンドウが次のバージョン情報に注意してください、`v2`ワークフロー。

4. いずれかの選択、`v1`の先頭で開始されたワークフロー、[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)トピック。 ステータス ウィンドウの下のバージョン情報がワークフローにバージョンがあることを示すことに注意してください**1.5.0.0**ワークフロー。 前の推定値については、その値が大きすぎるか小さすぎるかという点以外の情報はありません。

    **1 から 10 までの数値を入力してください。**\
    **推定値が小さすぎます。**

5. 
  `InstanceId` を書き留めておき、ワークフローが完了するまで推定値を入力します。 ステータス ウィンドウには、`WriteLine` アクティビティが動的更新によって更新されたため、推測の内容に関する情報が表示されます。

    **1 から 10 までの数値を入力してください。**\
    **推定値が小さすぎます。**\
    **1 から 10 までの数値を入力してください。**\
    **5 は低いままです。**\
    **1 から 10 までの数値を入力してください。**\
    **7 が多すぎます。**\
    **1 から 10 までの数値を入力してください。**\
    **これで、4 つの交替で数を推測します。**

6. Windows エクスプ ローラーを開きに移動、 **numberguessworkflowhost \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって) と、対応するメモ帳を使用して追跡ファイルを開く完了したワークフロー。 メモして行っていない場合、`InstanceId`を使用して正しい追跡ファイルを識別できる場合があります、**に変更された日付**Windows エクスプ ローラーの情報。 追跡情報の最後の行には、新しく追加した `WriteLine` アクティビティの出力が含まれます。

    **1 から 10 までの数値を入力してください。**\
    **推定値が小さすぎます。**\
    **1 から 10 までの数値を入力してください。**\
    **5 は低いままです。**\
    **1 から 10 までの数値を入力してください。**\
    **7 が多すぎます。**\
    **1 から 10 までの数値を入力してください。**\
    **6 は正しいです。察しのように 4 になります。**

### <a name="BKMK_StartPreviousVersions"></a> 以前のバージョンのワークフローを開始できるようにするには

更新するワークフローがなくなったら、ワークフローの以前のバージョンを開始できるように `NumberGuessWorkflowHost` アプリケーションを変更できます。

1. ダブルクリック**WorkflowHostForm**で**ソリューション エクスプ ローラー**を選択し、 **WorkflowType**コンボ ボックス。

2. **プロパティ**ウィンドウで、**項目**プロパティおよび編集する、省略記号のボタンをクリックし、**項目**コレクション。

3. コレクションに次の 3 つの項目を追加します。

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    完成した `Items` コレクションには 6 個の項目があります。

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. ダブルクリック**WorkflowHostForm**で**ソリューション エクスプ ローラー**を選択し、**コードの表示**します。

5. 次の 3 つの新しいケースを追加、 `switch` (または`Select Case`) 内のステートメント、`NewGame_Click`ハンドラーの新しい項目をマップする、 **WorkflowType**コンボ ボックスに一致するワークフローの id。

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    完成した `switch` (または `Select Case`) ステートメントを次の例に示します。

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。 これで、ワークフローの現在のバージョンに加え、`v1` バージョンを開始できるようになりました。 これらの新しいインスタンスを動的に更新するには、実行、 **ApplyDynamicUpdate**アプリケーション。
