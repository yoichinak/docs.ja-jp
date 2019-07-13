---
title: '方法: Windows フォームの DataGrid コントロールを使用して入力データを検証する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: dc8c8f157e6673c1bddc68bfb511683e6d2b99be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796475"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>方法: Windows フォームの DataGrid コントロールを使用して入力データを検証する

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。

Windows フォームの使用可能な 2 種類の入力の検証は<xref:System.Windows.Forms.DataGrid>コントロール。 ユーザーがセル、整数、文字列などの許容できないデータ型の値を入力する場合は、古い値を持つ新しい無効な値が置き換えられます。 この種類の入力の検証は、自動的には行われ、カスタマイズすることはできません。

以上の値を 1、または不適切な文字列にする必要があるフィールドの値が 0 など、あらゆる許容できないデータを拒否する他の種類の入力の検証を使用できます。 これは、データセット内のイベント ハンドラーを記述することで、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>イベント。 使用して次の例、<xref:System.Data.DataTable.ColumnChanging>イベント不正な値が"Product"列の具体的には許可されていないためです。 使用する場合があります、 <xref:System.Data.DataTable.RowChanging> 「終了日」の列の値が同じ行の「開始日」の列より後であるかを確認するためのイベント。

## <a name="to-validate-user-input"></a>ユーザー入力を検証するには

1. 処理するコードを記述、<xref:System.Data.DataTable.ColumnChanging>イベントを該当するテーブル。 不適切な入力が検出されたときに呼び出す、<xref:System.Data.DataRow.SetColumnError%2A>のメソッド、<xref:System.Data.DataRow>オブジェクト。

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
             e.Row.SetColumnError(e.Column, "Product cannot be " & _
             CType(badValue, String))
          End If
       End If
    End Sub
    ```

    ```csharp
    //Handle column changing events on the Customers table
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {

       //Only check for errors in the Product column
       if (e.Column.ColumnName.Equals("Product")) {

          //Do not allow "Automobile" as a product
          if (e.ProposedValue.Equals("Automobile")) {
             object badValue = e.ProposedValue;
             e.ProposedValue = "Bad Data";
             e.Row.RowError = "The Product column contains an error";
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);
          }
       }
    }
    ```

2. イベントにイベント ハンドラーを接続します。

    フォームのコード内で、次の場所<xref:System.Windows.Forms.Form.Load>イベントまたはそのコンス トラクター。

    ```vb
    ' Assumes the grid is bound to a dataset called customersDataSet1
    ' with a table called Customers.
    ' Put this code in the form's Load event or its constructor.
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging
    ```

    ```csharp
    // Assumes the grid is bound to a dataset called customersDataSet1
    // with a table called Customers.
    // Put this code in the form's Load event or its constructor.
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);
    ```

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [DataGrid コントロール](datagrid-control-windows-forms.md)
