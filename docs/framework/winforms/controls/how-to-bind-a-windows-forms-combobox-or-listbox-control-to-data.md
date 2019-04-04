---
title: '方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドします。'
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
ms.openlocfilehash: c8eb224cbb8ec7ab271edaed8bb25f9cc7fb8ddc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709927"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドします。
バインドすることができます、<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>データベース内のデータの参照などのタスクを実行するデータに新しいデータの入力または既存のデータを編集します。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>ComboBox または ListBox コントロールにバインドするには  
  
1.  設定、`DataSource`プロパティをデータ ソース オブジェクト。 データ ソースには、<xref:System.Windows.Forms.BindingSource>データ、データ テーブル、データ ビュー、データセットにバインドするデータ マネージャー、配列、または表示を実装するクラス、<xref:System.Collections.IList>インターフェイス。 詳細については、[Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md)を参照してください。  
  
2.  テーブルにバインドする場合は、設定、`DisplayMember`プロパティをデータ ソース内の列の名前にします。  
  
     \- または -  
  
     バインドしている場合、 <xref:System.Collections.IList>、画面メンバー リスト内の型のパブリック プロパティを設定します。  
  
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
    >  実装されていないデータ ソースにバインドするかどうか、<xref:System.ComponentModel.IBindingList>インターフェイスなど、 <xref:System.Collections.ArrayList>、データ ソースが更新されたときに、バインドされたコントロールのデータは更新されません。 などがある場合、コンボ ボックスにバインドする<xref:System.Collections.ArrayList>にデータを追加し、 <xref:System.Collections.ArrayList>、コンボ ボックスではこれらの新しい項目は表示されません。 ただし、呼び出すことで更新するコンボ ボックスを強制することができます、<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>と<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>のインスタンスでメソッド、<xref:System.Windows.Forms.BindingContext>コントロールがバインドされるクラスします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [データ連結と Windows フォーム](../data-binding-and-windows-forms.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
