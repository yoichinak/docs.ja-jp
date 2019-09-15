---
title: タスク 3:ツールボックス ペインと PropertyGrid ペインの作成
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988711"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>タスク 3:ツールボックス ペインと PropertyGrid ペインの作成
このタスクでは、**ツールボックス**ペインと**PropertyGrid**ペインを作成し、再ホスト[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]されたに追加します。  
  
 参考として、このトピックの最後に、ワークフローデザイナーシリーズのトピックの再[ホスト](rehosting-the-workflow-designer.md)に関する3つのタスクを完了した後に MainWindow.xaml.cs ファイルに含まれている必要があるコードについて説明します。  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>ツールボックスを作成し、グリッドに追加するには  
  
1. タスク2で[説明されている手順に従って、取得した HostingApplication プロジェクトを開きます。ワークフローデザイナー](task-2-host-the-workflow-designer.md)をホストします。  
  
2. **ソリューションエクスプローラー**ペインで、mainwindow.xaml ファイルを右クリックし、 **[コードの表示]** を選択します。  
  
3. `MainWindow` <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Assign>を`GetToolboxControl` 作成するクラスにメソッドを追加し、ツールボックスに新しいツールボックスカテゴリを追加して、アクティビティの種類とアクティビティの種類をそのカテゴリ<xref:System.Activities.Presentation.Toolbox.ToolboxControl>に割り当てます。  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4. グリッドの左側`AddToolbox`の列に`MainWindow` **ツールボックス**を配置するプライベートメソッドをクラスに追加します。  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. 次のコードのように、`AddToolBox` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. F5 キーを押して、ソリューションをビルドおよび実行します。 アクティビティ<xref:System.Activities.Statements.Assign> と<xref:System.Activities.Statements.Sequence>アクティビティを含む**ツールボックス**が表示されます。  
  
### <a name="to-create-the-propertygrid"></a>PropertyGrid を作成するには  
  
1. **ソリューションエクスプローラー**ペインで、mainwindow.xaml ファイルを右クリックし、 **[コードの表示]** を選択します。  
  
2. クラスにメソッドを追加して、グリッドの右端の列に [PropertyGrid] ペインを配置します。 `AddPropertyInspector` `MainWindow`  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. 次のコードのように、`AddPropertyInspector` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4. F5 キーを押して、ソリューションをビルドおよび実行します。 **[ツールボックス]** 、ワークフローデザインキャンバス、および  **[PropertyGrid]** の各ウィンドウがすべて<xref:System.Activities.Statements.Assign>表示され<xref:System.Activities.Statements.Sequence>ます。また、アクティビティまたはアクティビティをデザインキャンバスにドラッグすると、プロパティグリッドが更新されます。強調表示されたアクティビティ。  
  
## <a name="example"></a>例  
 MainWindow.xaml.cs ファイルに次のコードが含まれます。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
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
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)
- [タスク 1:新しい Windows Presentation Foundation アプリケーションを作成する](task-1-create-a-new-wpf-app.md)
- [タスク 2:ワークフローデザイナーをホストする](task-2-host-the-workflow-designer.md)
