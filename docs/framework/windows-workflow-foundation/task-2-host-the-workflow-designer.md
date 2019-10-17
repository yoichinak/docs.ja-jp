---
title: タスク 2:ワークフロー デザイナーのホスティング
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 15657ad79632812d3802e4da22b9ef297d08f932
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180260"
---
# <a name="task-2-host-the-workflow-designer"></a>タスク 2:ワークフロー デザイナーのホスティング

このトピックでは、Windows Presentation Foundation (WPF) アプリケーションで [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] のインスタンスをホストする手順について説明します。

このプロシージャは、デザイナーを含む**Grid**コントロールを構成し、既定の @no__t のアクティビティを含む <xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスをプログラムによって作成し、デザイナーのメタデータを登録して、すべての組み込みのデザイナーのサポートを提供します。アクティビティとは、WPF アプリケーションの @no__t 3 をホストします。

## <a name="to-host-the-workflow-designer"></a>ワークフロー デザイナーをホストするには

1. @No__t-0Task 1 で作成した HostingApplication プロジェクトを開きます。新しい Windows Presentation Foundation アプリケーション @ no__t を作成します。

2. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] が見やすくなるように、ウィンドウのサイズを調整します。 これを行うには、デザイナーで **[mainwindow.xaml]** を選択し、F4 キーを押して **[プロパティ]** ウィンドウを表示します。次に、 **[レイアウト]** セクションで、 **[幅]** を600に、 **[高さ]** を350の値に設定します。

3. デザイナーで **[グリッド]** パネルを選択し ( **mainwindow.xaml**内のボックスをクリック)、 **[プロパティ]** ウィンドウの上部にある **[名前]** プロパティを "grid1" に設定して、グリッド名を設定します。

4. **[プロパティ]** ウィンドウで、`ColumnDefinitions` プロパティの横にある省略記号 ( **...** ) をクリックして、 **[コレクションエディター]** ダイアログボックスを開きます。

5. **[コレクションエディター]** ダイアログボックスで、 **[追加]** ボタンを3回クリックして、3つの列をレイアウトに挿入します。 最初の列には**ツールボックス**が含まれ、2番目の列は [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] をホストし、3番目の列はプロパティインスペクターに使用されます。

6. 中央の列の `Width` プロパティを値 "4 *" に設定します。

7. **[OK]** をクリックして変更を保存します。 次の XAML が*mainwindow.xaml*ファイルに追加されます。

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. **ソリューションエクスプローラー**で、 *mainwindow.xaml*を右クリックし、 **[コードの表示]** を選択します。 次の手順に従ってコードを修正します。

    1. 次の名前空間を追加します。

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. @No__t-0 のインスタンスを保持するプライベートメンバーフィールドを宣言するには、次のコードを `MainWindow` クラスに追加します。

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. 次の `AddDesigner` メソッドを `MainWindow` クラスに追加します。 実装によって <xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスが作成され、それに @no__t 1 つのアクティビティが追加され、grid1 **Grid**の中央の列に配置されます。

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. デザイナーのメタデータを登録して、すべてのビルトイン アクティビティにデザイナー サポートを追加します。 こうすることにより、ツールボックスから<xref:System.Activities.Statements.Sequence>の元の [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] アクティビティに、アクティビティをドロップできるようになります。 これを行うには、`RegisterMetadata` メソッドを `MainWindow` クラスに追加します。

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        アクティビティデザイナーの登録の詳細については、@no__t を参照してください。カスタムアクティビティデザイナー @ no__t を作成します。

    5. `MainWindow` クラス コンストラクターで、前に宣言したメソッドへの呼び出しを追加して、デザイナー サポートのメタデータを登録し、<xref:System.Activities.Presentation.WorkflowDesigner> を作成します。

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > `RegisterMetadata` メソッドは、<xref:System.Activities.Statements.Sequence> アクティビティを含むビルトイン アクティビティのデザイナーのメタデータを登録します。 `AddDesigner` メソッドは <xref:System.Activities.Statements.Sequence> アクティビティを使用するので、`RegisterMetadata` メソッドを先に呼び出す必要があります。

9. <kbd>F5</kbd>キーを押して、ソリューションをビルドして実行します。

10. @No__t-0Task 3 を参照してください。ツールボックスと PropertyGrid のペイン @ no__t を作成して、再ホストされたワークフローデザイナーに**ツールボックス**と**PropertyGrid**のサポートを追加する方法を学習します。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [Task 1:新しい Windows Presentation Foundation アプリケーションの作成 @ no__t-0
- [Task 3:ツールボックスペインと PropertyGrid ペインを作成する @ no__t-0
