---
title: タスク 3:ツールボックス ペインと PropertyGrid ペインを作成します。
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 45819577c39185a5d95da81521cd541087a64efc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721224"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>タスク 3:ツールボックス ペインと PropertyGrid ペインを作成します。
このタスクでは、作成、**ツールボックス**と**PropertyGrid**ペインがありますし、再ホストされたに追加[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]します。  
  
 リファレンスについては、3 つの完了後に MainWindow.xaml.cs ファイルに登録するコードのタスクで、[ワークフロー デザイナーのホスト変更](rehosting-the-workflow-designer.md)一連のトピックは、このトピックの最後で提供されます。  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>ツールボックスを作成し、グリッドに追加するには  
  
1.  説明されている手順を実行して取得した HostingApplication プロジェクトを開く[タスク 2。ワークフロー デザイナーのホスティング](task-2-host-the-workflow-designer.md)します。  
  
2.  **ソリューション エクスプ ローラー**ウィンドウで、MainWindow.xaml ファイルを右クリックし、選択**コードの表示**します。  
  
3.  追加、`GetToolboxControl`メソッドを`MainWindow`を作成するクラス、 <xref:System.Activities.Presentation.Toolbox.ToolboxControl>、新しく追加**ツールボックス**カテゴリを**ツールボックス**、割り当てます、<xref:System.Activities.Statements.Assign>と<xref:System.Activities.Statements.Sequence>アクティビティの種類をそのカテゴリ。  
  
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
  
4.  追加プライベート`AddToolbox`メソッドを`MainWindow`配置クラス、**ツールボックス**グリッドで左の列にします。  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  次のコードのように、`AddToolBox` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  F5 キーを押して、ソリューションをビルドおよび実行します。 **ツールボックス**を含む、<xref:System.Activities.Statements.Assign>と<xref:System.Activities.Statements.Sequence>のアクティビティを表示する必要があります。  
  
### <a name="to-create-the-propertygrid"></a>PropertyGrid を作成するには  
  
1.  **ソリューション エクスプ ローラー**ウィンドウで、MainWindow.xaml ファイルを右クリックし、選択**コードの表示**します。  
  
2.  追加、`AddPropertyInspector`メソッドを`MainWindow`を配置するクラス、 **PropertyGrid**ウィンドウ グリッドの最も右側の列。  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  次のコードのように、`AddPropertyInspector` クラス コンストラクターに `MainWindow()` メソッドへの呼び出しを追加します。  
  
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
  
4.  F5 キーを押して、ソリューションをビルドおよび実行します。 **ツールボックス**、ワークフロー デザイン キャンバス、および**PropertyGrid**ウィンドウすべて表示するか、およびドラッグすると、<xref:System.Activities.Statements.Assign>アクティビティまたは<xref:System.Activities.Statements.Sequence>デザイン キャンバスにアクティビティ、強調表示されているアクティビティに応じてプロパティ グリッドを更新する必要があります。  
  
## <a name="example"></a>例  
 MainWindow.xaml.cs ファイルに次のコードが含まれます。  
  
```  
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
- [タスク 1:新しい Windows Presentation Foundation アプリケーションを作成します。](task-1-create-a-new-wpf-app.md)
- [タスク 2:ワークフロー デザイナーをホスティングします。](task-2-host-the-workflow-designer.md)
