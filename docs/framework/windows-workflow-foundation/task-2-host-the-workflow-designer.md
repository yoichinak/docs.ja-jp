---
title: タスク 2:ワークフロー デザイナーのホスティング
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037867"
---
# <a name="task-2-host-the-workflow-designer"></a>タスク 2:ワークフロー デザイナーのホスティング

このトピックでは、 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] Windows Presentation Foundation (WPF) アプリケーションでのインスタンスをホストする手順について説明します。

このプロシージャは、デザイナーを含む**グリッド**コントロールを構成し、既定<xref:System.Activities.Presentation.WorkflowDesigner> <xref:System.Activities.Statements.Sequence>のアクティビティを含むのインスタンスをプログラムで作成し、デザイナーのメタデータを登録して、すべてのデザイナーのサポートを提供します。組み込みのアクティビティは、WPF アプリケーション[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]でをホストします。

### <a name="to-host-the-workflow-designer"></a>ワークフロー デザイナーをホストするには

1. タスク1で[作成した HostingApplication プロジェクトを開きます。新しい Windows Presentation Foundation アプリケーション](task-1-create-a-new-wpf-app.md)を作成します。

2. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] が見やすくなるように、ウィンドウのサイズを調整します。 これを行うには、デザイナーで **[mainwindow.xaml]** を選択し、F4 キーを押して **[プロパティ]** ウィンドウを表示します。次に、 **[レイアウト]** セクションで、 **[幅]** を600に、 **[高さ]** を350の値に設定します。

3. デザイナーで **[グリッド]** パネルを選択し ( **mainwindow.xaml**内のボックスをクリック)、 **[プロパティ]** ウィンドウの上部にある **[名前]** プロパティを "grid1" に設定して、グリッド名を設定します。

4. **[プロパティ]** ウィンドウで、プロパティの`ColumnDefinitions`横にある省略記号 ( **..** .) をクリックして、 **[コレクションエディター]** ダイアログボックスを開きます。

5. **[コレクションエディター]** ダイアログボックスで、 **[追加]** ボタンを3回クリックして、3つの列をレイアウトに挿入します。 最初の列には**ツールボックス**が含まれ、2番目[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]の列はをホストし、3番目の列はプロパティインスペクターに使用されます。

6. 中央の列のプロパティを値"4*"に設定します。`Width`

7. **[OK]** をクリックして変更を保存します。 次の XAML が MainWindow.xaml ファイルに追加されます。

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. **ソリューションエクスプローラー**で、mainwindow.xaml を右クリックし、 **[コードの表示]** を選択します。 次の手順に従ってコードを修正します。

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

    2. <xref:System.Activities.Presentation.WorkflowDesigner> のインスタンスを保持するプライベート メンバー フィールドを宣言するには、次のコードを `MainWindow` クラスに追加します。

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

    3. 次の `AddDesigner` メソッドを `MainWindow` クラスに追加します。 実装では、 <xref:System.Activities.Presentation.WorkflowDesigner>のインスタンスを作成し、アクティビティを<xref:System.Activities.Statements.Sequence>追加して、grid1 **Grid**の中央の列に配置します。

        ```csharp
        private void AddDesigner()
        {
            //Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            //Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            //Load a new Sequence as default.
            this.wd.Load(new Sequence());

            //Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. デザイナーのメタデータを登録して、すべてのビルトイン アクティビティにデザイナー サポートを追加します。 こうすることにより、ツールボックスから<xref:System.Activities.Statements.Sequence>の元の [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] アクティビティに、アクティビティをドロップできるようになります。 この操作を行うには、`RegisterMetadata` メソッドを `MainWindow` クラスに追加します。

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        アクティビティデザイナーの登録の詳細について[は、「」を参照してください。カスタムアクティビティデザイナー](how-to-create-a-custom-activity-designer.md)を作成します。

    5. `MainWindow` クラス コンストラクターで、前に宣言したメソッドへの呼び出しを追加して、デザイナー サポートのメタデータを登録し、<xref:System.Activities.Presentation.WorkflowDesigner> を作成します。

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata
            RegisterMetadata();

            // Add the WFF Designer
            AddDesigner();
        }
        ```

        > [!NOTE]
        > `RegisterMetadata` メソッドは、<xref:System.Activities.Statements.Sequence> アクティビティを含むビルトイン アクティビティのデザイナーのメタデータを登録します。 `AddDesigner` メソッドは <xref:System.Activities.Statements.Sequence> アクティビティを使用するので、`RegisterMetadata` メソッドを先に呼び出す必要があります。

9. F5 キーを押して、ソリューションをビルドおよび実行します。

10. 「 [タスク 3:ツールボックスと PropertyGrid のウィンドウ](task-3-create-the-toolbox-and-propertygrid-panes.md)を作成して、再ホストされたワークフローデザイナーに**ツールボックス**と**PropertyGrid**のサポートを追加する方法を学習します。

## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 1:新しい Windows Presentation Foundation アプリケーションを作成する](task-1-create-a-new-wpf-app.md)
- [タスク 3:ツールボックスペインと PropertyGrid ペインの作成](task-3-create-the-toolbox-and-propertygrid-panes.md)
