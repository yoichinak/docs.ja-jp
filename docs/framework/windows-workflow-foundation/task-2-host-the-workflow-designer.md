---
title: タスク 2:ワークフロー デザイナーのホスティング
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 3f7964e907fe513679e60c18292f07c84128590b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641578"
---
# <a name="task-2-host-the-workflow-designer"></a>タスク 2:ワークフロー デザイナーのホスティング
このトピックでは、のインスタンスをホストするための手順を説明します、 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] Windows Presentation Foundation (WPF) アプリケーションでします。  
  
 プロシージャを構成、**グリッド**、デザイナーを格納しているコントロールのインスタンスをプログラムで作成する、 <xref:System.Activities.Presentation.WorkflowDesigner> 、既定値を格納している<xref:System.Activities.Statements.Sequence>アクティビティを提供する、デザイナーのメタデータを登録しますすべての組み込みのアクティビティ、およびホストのデザイナー サポート、[!INCLUDE[wfd2](../../../includes/wfd2-md.md)]で、[!INCLUDE[avalon2](../../../includes/avalon2-md.md)]アプリケーション。  
  
### <a name="to-host-the-workflow-designer"></a>ワークフロー デザイナーをホストするには  
  
1. HostingApplication プロジェクトを開きますで作成した[タスク 1。新しい Windows Presentation Foundation アプリケーションを作成する](task-1-create-a-new-wpf-app.md)します。  
  
2. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] が見やすくなるように、ウィンドウのサイズを調整します。 これを行うには、次のように選択します**MainWindow**デザイナーで表示 f4 キーを押して、**プロパティ**ウィンドウで、し、、**レイアウト**ありますセクションで、設定、**幅。** 600 の値に、**高さ**350 の値にします。  
  
3. 選択して、グリッド名を設定、**グリッド**デザイナー内のパネル (内のボックスをクリックして、 **MainWindow**) と設定、**名前**の上部にあるプロパティ、 **プロパティ**ウィンドウを「grid1」.  
  
4. **プロパティ**ウィンドウで、省略記号をクリックします (**.**) 横に、`ColumnDefinitions`プロパティを開き、**コレクション エディター**  ダイアログ ボックス。  
  
5. **コレクション エディター**ダイアログ ボックスで、をクリックして、**追加**ボタンを 3 回、レイアウトに 3 つの列を挿入します。 最初の列には、**ツールボックス**、2 番目の列をホストする、 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]、プロパティ インスペクターの 3 番目の列が使用されます。  
  
6. 設定、`Width`プロパティの値に、中央の列の"4 *"。  
  
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
  
8. **ソリューション エクスプ ローラー**で MainWindow.xaml を右クリックし、選択**コードの表示**します。 次の手順に従ってコードを修正します。  
  
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
  
    3. 次の `AddDesigner` メソッドを `MainWindow` クラスに追加します。 実装のインスタンスを作成する、 <xref:System.Activities.Presentation.WorkflowDesigner>、追加、 <xref:System.Activities.Statements.Sequence> 、アクティビティ、grid1 の中央の列に配置**グリッド**します。  
  
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
  
         アクティビティ デザイナーの登録の詳細については、次を参照してください。[方法。カスタム アクティビティ デザイナーを作成](how-to-create-a-custom-activity-designer.md)です。  
  
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
        >  `RegisterMetadata` メソッドは、<xref:System.Activities.Statements.Sequence> アクティビティを含むビルトイン アクティビティのデザイナーのメタデータを登録します。 `AddDesigner` メソッドは <xref:System.Activities.Statements.Sequence> アクティビティを使用するので、`RegisterMetadata` メソッドを先に呼び出す必要があります。  
  
9. F5 キーを押して、ソリューションをビルドおよび実行します。  
  
10. 参照してください[タスク 3。ツールボックス ペインと PropertyGrid ペインの作成](task-3-create-the-toolbox-and-propertygrid-panes.md)を追加する方法について**ツールボックス**と**PropertyGrid**を再ホストされたワークフロー デザイナーをサポートします。  
  
## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 1:新しい Windows Presentation Foundation アプリケーションを作成します。](task-1-create-a-new-wpf-app.md)
- [タスク 3:ツールボックス ペインと PropertyGrid ペインを作成します。](task-3-create-the-toolbox-and-propertygrid-panes.md)
