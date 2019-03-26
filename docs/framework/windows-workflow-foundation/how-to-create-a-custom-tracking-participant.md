---
title: '方法: カスタム追跡参加要素を作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: c4c6a8d17180ee00942c1bfd9ddc7bfa04bb962f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720957"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>方法: カスタム追跡参加要素を作成します。
ワークフロー追跡により、ワークフロー実行の状態が視覚的に示されます。 ワークフロー ランタイムによって、ワークフローのライフサイクル イベント、アクティビティのライフサイクル イベント、ブックマークの再開、およびエラーについて説明する追跡レコードが出力されます。 これらの追跡レコードは、追跡参加要素によって使用されます。 Windows Workflow Foundation (WF) には、追跡レコードを Event Tracing for Windows (ETW) イベントとして書き込む標準の追跡参加要素が含まれています。 これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。 チュートリアルのこの手順では、`WriteLine` アクティビティの出力をキャプチャするカスタム追跡参加要素と追跡プロファイルを作成して、ユーザーに表示できるようにする方法について説明します。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。 このトピックを完了する前に、これまでのトピックを完了する必要があります。 完成版をダウンロードまたはチュートリアルのビデオ チュートリアルを表示を参照してください。 [Windows Workflow Foundation (WF45) - チュートリアル入門](https://go.microsoft.com/fwlink/?LinkID=248976)します。  
  
## <a name="to-create-the-custom-tracking-participant"></a>カスタム追跡参加要素を作成するには  
  
1.  右クリックして**NumberGuessWorkflowHost**で**ソリューション エクスプ ローラー**選択**追加**、**クラス**します。 型`StatusTrackingParticipant`に、**名前**ボックス、およびクリックして**追加**します。  
  
2.  次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  `StatusTrackingParticipant` クラスを変更して、`TrackingParticipant` から継承されるようにします。  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  次の `Track` メソッド オーバーライドを追加します。 追跡レコードには、いくつかの種類があります。 ここでは、アクティビティ追跡レコードに含まれる `WriteLine` アクティビティの出力に注目します。 `TrackingRecord` が `ActivityTrackingRecord` アクティビティの `WriteLine` である場合は、ワークフローの `Text` に基づいた名前の付いたファイルに `WriteLine` の `InstanceId` が追加されます。 このチュートリアルでは、ファイルはホスト アプリケーションの現在のフォルダーに保存されます。  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     追跡プロファイルを指定しない場合は、既定の追跡プロファイルが使用されます。 既定の追跡プロファイルを使用する場合は、すべての `ActivityStates` に関する追跡レコードが出力されます。 ここでは、`WriteLine` アクティビティのライフサイクル中に 1 回だけテキストをキャプチャする必要があるため、`ActivityStates.Executing` 状態からテキストを抽出するだけです。 [追跡プロファイルを作成し、追跡参加要素を登録する](#to-create-the-tracking-profile-and-register-the-tracking-participant)、だけを指定する追跡プロファイルが作成された`WriteLine``ActivityStates.Executing`追跡レコードが生成されます。  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>追跡プロファイルを作成して追跡参加要素を登録するには  
  
1.  右クリックして**WorkflowHostForm**で**ソリューション エクスプ ローラー**選択**コードの表示**します。  
  
2.  次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  ワークフロー拡張機能に `ConfigureWorkflowApplication` を追加するコードの直後で、ワークフロー ライフサイクル ハンドラーの前に、`StringWriter` に次のコードを追加します。  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     この追跡プロファイルでは、`WriteLine` 状態の `Executing` アクティビティのアクティビティ状態レコードのみがカスタム追跡参加要素に出力されるように指定します。  
  
     このコードを追加した後、`ConfigureWorkflowApplication` の先頭は次の例のようになります。  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a>追跡情報を表示するには  
  
1.  右クリックして**WorkflowHostForm**で**ソリューション エクスプ ローラー**選択**コードの表示**します。  
  
2.  `InstanceId_SelectedIndexChanged` ハンドラーで、ステータス ウィンドウをクリアするコードの直後に次のコードを追加します。  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     ワークフローの一覧で新しいワークフローを選択すると、そのワークフローの追跡レコードがステータス ウィンドウに読み込まれて表示されます。 完成した `InstanceId_SelectedIndexChanged` ハンドラーは次のようになります。  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a>アプリケーションをビルドして実行するには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドします。  
  
2.  Ctrl キーを押しながら F5 キーを押してアプリケーションを起動します。  
  
3.  推測ゲームとワークフローを開始、およびクリックしての種類の範囲を選択**新しいゲーム**します。 推定値を入力、**推測**ボックスし、をクリックして**移動**推定値を送信します。 ワークフローの状態がステータス ウィンドウに表示されます。 この出力は、`WriteLine` アクティビティからキャプチャされます。 いずれかから選択して、別のワークフローに切り替えて、**ワークフロー インスタンス Id**コンボ ボックスと、現在のワークフローの状態が削除されたことに注意してください。 以前のワークフローに戻して、次の例のように、状態が復元されることを確認します。  
  
    > [!NOTE]
    > 追跡が有効になる前に開始されたワークフローに切り替えた場合、状態は表示されません。 ただし、推定値を追加すると、この時点では追跡が有効になっているため、その状態が保存されます。  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > この情報は、乱数の範囲を決定する場合に役立ちますが、これまでに作成された推定値に関する情報を含んでいません。 この情報は、次の手順では[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)します。

    ワークフロー インスタンス ID を書き留め、ゲームを最後まで実行します。
  
4.  Windows エクスプ ローラーを開きに移動し、 **numberguessworkflowhost \bin\debug**フォルダー (または**bin \release**プロジェクトの設定によって)。 プロジェクトの実行可能ファイルに加え、GUID ファイル名が付いたファイルがあることに注意します。 前の手順で完了したワークフローのワークフロー インスタンス ID に対応するファイルを特定してメモ帳で開きます。 追跡情報は、次のような情報が含まれています。  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    この追跡データには、ユーザーの推定値だけでなく、ワークフローの最後の推定値に関する情報も含まれていません。 これは、追跡情報がワークフローからの `WriteLine` 出力のみで構成されており、表示される最後のメッセージがワークフロー完了後に `Completed` ハンドラーから表示されるためです。 チュートリアルの次の手順で[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)、既存の`WriteLine`アクティビティは、ユーザーの推定値と追加を表示する変更`WriteLine`最終的な結果を表示するアクティビティを追加します。 これらの変更が統合されると、[方法。ワークフロー サイド バイ サイドの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)と同時に複数のバージョンのワークフローをホストする方法を示します。
