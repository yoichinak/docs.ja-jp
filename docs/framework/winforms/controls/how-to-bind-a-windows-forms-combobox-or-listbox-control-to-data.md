---
title: '方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922754"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドする
<xref:System.Windows.Forms.ComboBox> と<xref:System.Windows.Forms.ListBox>をデータにバインドすると、データベース内のデータの参照、新しいデータの入力、既存のデータの編集などのタスクを実行できます。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox または ListBox コントロールをバインドするには  
  
1. `DataSource`プロパティをデータソースオブジェクトに設定します。 使用できるデータソースに<xref:System.Windows.Forms.BindingSource>は、データへのバインド、データテーブル、データビュー、データセット、データビューマネージャー、配列、または<xref:System.Collections.IList>インターフェイスを実装する任意のクラスが含まれます。 詳細については、「 [Windows フォームでサポートされるデータソース](../data-sources-supported-by-windows-forms.md)」を参照してください。  
  
2. テーブルにバインドする場合は、 `DisplayMember`プロパティをデータソース内の列の名前に設定します。  
  
     \- または -  
  
     にバインドする場合は<xref:System.Collections.IList>、表示メンバーをリスト内の型のパブリックプロパティに設定します。  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > など、 <xref:System.ComponentModel.IBindingList>インターフェイス<xref:System.Collections.ArrayList>を実装していないデータソースにバインドされている場合、データソースの更新時にバインドされたコントロールのデータは更新されません。 たとえば、に<xref:System.Collections.ArrayList>バインドされたコンボボックスがあり、 <xref:System.Collections.ArrayList>にデータが追加されている場合、これらの新しい項目はコンボボックスに表示されません。 ただし、コントロールがバインドされている<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingContext>クラスのインスタンスでメソッドと<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>メソッドを呼び出すことにより、コンボボックスを強制的に更新できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [データ連結と Windows フォーム](../data-binding-and-windows-forms.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
