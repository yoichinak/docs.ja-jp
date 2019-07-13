---
title: '方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: a58522cc17ac379897a89a8e61485a1e271438a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011472"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する
Windows フォーム上ではわかりやすい形式でデータを表示し、一方プログラムにはより意味のある形式でデータを格納すると便利な場合があります。 たとえば、食品の注文書の場合、リスト ボックスにメニュー項目が名前で表示されます。 一方、注文を記録するデータ テーブルには、食品を表す一意の ID 番号が含まれることになります。 次の表は、食品の注文書データを格納および表示する方法の例を示しています。  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|数量|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|名前|  
|--------|----------|  
|12|ポテト|  
|13|チキン|  
  
 このシナリオでは、1 つのテーブルで**OrderDetailsTable**、表示と保存には、実際の情報を格納します。 しかし、スペースを節約するために、これはかなり謎めいた方法で実行されます。 その他のテーブル**ItemTable**、どの id 番号がどの食品名には実際の食品の注文について何も同等外観に関連する情報のみが含まれています。  
  
 **ItemTable**に接続されている、 <xref:System.Windows.Forms.ComboBox>、 <xref:System.Windows.Forms.ListBox>、または<xref:System.Windows.Forms.CheckedListBox>3 つのプロパティを制御します。 `DataSource`プロパティには、このテーブルの名前が含まれています。 `DisplayMember`プロパティには、コントロール (食品名) に表示する、テーブルのデータ列が含まれています。 `ValueMember`プロパティに格納されている情報 (ID 番号) を持つ、テーブルのデータ列が含まれています。  
  
 **OrderDetailsTable**経由でアクセス、そのバインディング コレクションにより、コントロールに接続されている、<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティ。 コントロールのプロパティは、データ ソース内の特定のデータ メンバー (ID 番号の列) に接続するバインディング オブジェクトをコレクションに追加すると (、 **OrderDetailsTable**)。 コントロールで選択がなされる際、このテーブルはフォーム入力が保存される場所です。  
  
### <a name="to-create-a-lookup-table"></a>ルックアップ テーブルを作成するには  
  
1. フォームに <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>、または <xref:System.Windows.Forms.CheckedListBox> コントロールを追加します。  
  
2. データ ソースに接続します。  
  
3. 2 つのテーブル間のデータ リレーションシップを確立します。 参照してください[DataRelation オブジェクトの概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120))します。  
  
4. 次のプロパティを設定します。 これらはコードまたはデザイナーで設定できます。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|どの ID 番号がどの項目に相当するかについての情報を含むテーブル。 これは、前のシナリオで`ItemTable`します。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|コントロールに表示するデータ ソース テーブルの列。 これは、前のシナリオで`"Name"`(コードで設定するには引用符を使用)。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|格納された情報を含むデータ ソース テーブルの列。 これは、前のシナリオで`"ID"`(コードで設定するには引用符を使用)。|  
  
5. プロシージャで <xref:System.Windows.Forms.ControlBindingsCollection> クラスの <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> メソッドを呼び出して、フォーム入力を記録するテーブルにコントロールの <xref:System.Windows.Forms.ListControl.SelectedValue%2A> プロパティをバインドします。 行うこともできますこのコードでは、代わりに、デザイナーでコントロールのアクセスすることによって<xref:System.Windows.Forms.Control.DataBindings%2A>プロパティ、**プロパティ**ウィンドウ。 これは、前のシナリオで`OrderDetailsTable`、列と`"ItemID"`します。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>関連項目

- [データ連結と Windows フォーム](../data-binding-and-windows-forms.md)
- [ListBox コントロールの概要](listbox-control-overview-windows-forms.md)
- [ComboBox コントロールの概要](combobox-control-overview-windows-forms.md)
- [CheckedListBox コントロールの概要](checkedlistbox-control-overview-windows-forms.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
