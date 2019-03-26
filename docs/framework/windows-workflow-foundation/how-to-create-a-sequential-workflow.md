---
title: '方法: シーケンシャル ワークフローの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 3991c16e00f1cbb4f8c1f2c8391f89ea51c1e6f2
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463801"
---
# <a name="how-to-create-a-sequential-workflow"></a>方法: シーケンシャル ワークフローの作成
ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。 このトピックでなど両方の組み込みのアクティビティを使用するワークフローを作成する手順、<xref:System.Activities.Statements.Sequence>アクティビティ、およびカスタム アクティビティ、前の[方法。アクティビティ作成](how-to-create-an-activity.md)トピック。 このワークフローは、数値推測ゲームをモデル化しています。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。 このトピックを完了する必要がありますを完了して[方法。アクティビティ作成](how-to-create-an-activity.md)です。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](https://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
## <a name="to-create-the-workflow"></a>ワークフローを作成するには  
  
1.  右クリック**NumberGuessWorkflowActivities**で**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の**します。  
  
2.  **インストール済み**、**一般的な項目**ノードの **ワークフロー**します。 選択**アクティビティ**から、**ワークフロー**一覧。  
  
3.  型`SequentialNumberGuessWorkflow`に、**名前**ボックスし、をクリックして**追加**します。  
  
4.  ドラッグ、**シーケンス**からのアクティビティ、**制御フロー**のセクション、**ツールボックス**にドロップし、**ここにアクティビティをドロップ**のラベルをワークフロー デザイン サーフェイス。  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a>ワークフロー変数および引数を作成するには  
  
1.  ダブルクリック**SequentialNumberGuessWorkflow.xaml**で**ソリューション エクスプ ローラー**まだ表示されていない場合に、デザイナーでワークフローを表示します。  
  
2.  クリックして**引数**を表示するワークフロー デザイナーの左下で、**引数**ウィンドウ。  
  
3.  クリックして**引数の作成**です。  
  
4.  型`MaxNumber`に、**名前**ボックスで、**で**から、**方向**ドロップダウン リストで、 **Int32** から**引数の型**ドロップダウン リスト、および引数を保存するには ENTER キーを押します。  
  
5.  クリックして**引数の作成**です。  
  
6.  型`Turns`に、**名前**新しく追加された下にあるボックス`MaxNumber`引数で、**アウト**から、**方向**選択ドロップダウンリスト**Int32**から、**引数の型**ドロップダウン リスト、および ENTER キーを押します。  
  
7.  クリックして**引数**を閉じるアクティビティ デザイナーの左下で、**引数**ウィンドウ。  
  
8.  クリックして**変数**を表示するワークフロー デザイナーの左下で、**変数**ウィンドウ。  
  
9. クリックして**変数作成**です。  
  
    > [!TIP]
    >  ない場合は**変数の作成**ボックスが表示されたら、をクリックして、**シーケンス**ことを選択するには、ワークフロー デザイナー画面上のアクティビティ。  
  
10. 型`Guess`に、**名前**ボックスで、 **Int32**から、**変数の型**ドロップダウン リスト、および、変数に保存するには ENTER キーを押します。  
  
11. クリックして**変数作成**です。  
  
12. 型`Target`に、**名前**ボックスで、 **Int32**から、**変数の型**ドロップダウン リスト、および、変数に保存するには ENTER キーを押します。  
  
13. クリックして**変数**を閉じるアクティビティ デザイナーの左下で、**変数**ウィンドウ。  
  
## <a name="to-add-the-workflow-activities"></a>ワークフロー アクティビティを追加するには  
  
1.  ドラッグ、**割り当てる**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**にドロップし、**シーケンス**アクティビティ。 型`Target`に、**に**ボックスし、次の式を**c# 式を入力します**または**VB の式を入力します。** ボックス。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  場合、**ツールボックス**ウィンドウが表示されない場合、選択**ツールボックス**から、**ビュー**メニュー。  
  
2.  ドラッグ、 **DoWhile**からのアクティビティ、**制御フロー**のセクション、**ツールボックス**下に、ワークフローにドロップし、**割り当てる**アクティビティ。  
  
3.  次の式を入力、 **DoWhile**アクティビティの**条件**プロパティ値ボックス。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <xref:System.Activities.Statements.DoWhile> アクティビティはその子アクティビティを実行し、その <xref:System.Activities.Statements.DoWhile.Condition%2A> を評価します。 <xref:System.Activities.Statements.DoWhile.Condition%2A> が `True` と評価される場合、<xref:System.Activities.Statements.DoWhile> 内のアクティビティが再度実行されます。 この例では、ユーザーの推定値が評価され、推定値が正しいと判断されるまで <xref:System.Activities.Statements.DoWhile> が続行されます。  
  
4.  ドラッグ、**プロンプト**からのアクティビティ、 **NumberGuessWorkflowActivities**のセクション、**ツールボックス**にドロップし、 **DoWhile**アクティビティ前の手順。  
  
5.  **プロパティ ウィンドウ**、型`"EnterGuess"`に引用符を含む、 **BookmarkName**のプロパティ値ボックスに、**プロンプト**アクティビティ。 型`Guess`に、**結果**プロパティの値のボックスとには、次の式を入力、**テキスト**プロパティ ボックス。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  場合、**プロパティ ウィンドウ**が表示されている、選択**プロパティ ウィンドウ**から、**ビュー**メニュー。  
  
6.  ドラッグ、**割り当てる**からのアクティビティ、**プリミティブ**のセクション、**ツールボックス**にドロップし、 **DoWhile**アクティビティの後になるように、**プロンプト**アクティビティ。  
  
    > [!NOTE]
    >  ドロップすると、**割り当てる**アクティビティをワークフロー デザイナーが自動的に追加する方法を確認、**シーケンス**両方を含むアクティビティ、**プロンプト**アクティビティと新しく追加されました。**割り当てる**アクティビティ。  
  
7.  型`Turns`に、**に**ボックスと`Turns + 1`に、 **c# 式を入力します**または**VB の式を入力します。** ボックス。  
  
8.  ドラッグ、**場合**からのアクティビティ、**制御フロー**のセクション、**ツールボックス**にドロップし、**シーケンス**アクティビティの後になるように、新しく追加された**割り当てる**アクティビティ。  
  
9. 次の式を入力、**場合**アクティビティの**条件**プロパティ値ボックス。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. もう 1 つドラッグ**場合**からのアクティビティ、**制御フロー**のセクション、**ツールボックス**にドロップし、**し**最初のセクション**場合**アクティビティ。  
  
11. 新しく追加された次の式を入力**場合**アクティビティの**条件**プロパティ値ボックス。  
  
    ```
    Guess < Target  
    ```  
  
12. 2 つをドラッグして**WriteLine**アクティビティから、**プリミティブ**のセクション、**ツールボックス**で 1 つがされるようにドロップし、**し**のセクション新しく追加された**場合**、もう 1 つは、 **Else**セクション。  
  
13. をクリックして、 **WriteLine**内のアクティビティ、**し**セクションを選択しとには、次の式を入力、**テキスト**プロパティ値ボックス。  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. をクリックして、 **WriteLine**内のアクティビティ、 **Else**セクションを選択しとには、次の式を入力、**テキスト**プロパティ値ボックス。  
  
    ```text
    "Your guess is too high."  
    ```  
  
     次の例は、完了したワークフローを示しています。  
  
     ![完成したシーケンシャル ワークフローを示すスクリーン ショット。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a>ワークフローをビルドするには  
  
1.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
     ワークフローを実行する方法について、次のトピックをご覧ください[方法。ワークフローを実行する](how-to-run-a-workflow.md)します。 既に完了している場合、[方法。ワークフローを実行する](how-to-run-a-workflow.md)さまざまなスタイルのワークフローにステップ イン、シーケンシャル ワークフローこの手順を使用してを実行してに進んで、 [、アプリケーションをビルドして実行](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)のセクション[方法。ワークフローを実行する](how-to-run-a-workflow.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation プログラミング](programming.md)
- [ワークフローの設計](designing-workflows.md)
- [チュートリアル入門](getting-started-tutorial.md)
- [方法: アクティビティを作成します。](how-to-create-an-activity.md)
- [方法: ワークフローを実行します。](how-to-run-a-workflow.md)
