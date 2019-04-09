---
title: '方法: MaskedTextBox コントロールにデータをバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: 0350d6e690d54d6176ede3b858f75829326b7556
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090603"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a>方法: MaskedTextBox コントロールにデータをバインドする
データをバインドすることができます、<xref:System.Windows.Forms.MaskedTextBox>他の Windows フォーム コントロールと同様に制御します。 ただし、データベース内のデータの形式で、マスクの定義で予期される形式が一致しない場合は、データの書式を変更する必要があります。 次の手順を使用してこれを行う方法を示して、<xref:System.Windows.Forms.Binding.Format>と<xref:System.Windows.Forms.Binding.Parse>のイベント、<xref:System.Windows.Forms.Binding>クラスを別の電話番号を表示および編集可能なフィールドを 1 つとして、拡張データベースのフィールドを電話します。  
  
 次の手順では、インストールされている Northwind サンプル データベースで SQL Server データベースへのアクセスが必要です。  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a>MaskedTextBox コントロールにデータをバインドするには  
  
1.  新しい Windows フォーム プロジェクトを作成します。  
  
2.  2 つをドラッグ<xref:System.Windows.Forms.TextBox>コントロールをフォームに名前を付けます`FirstName`と`LastName`します。  
  
3.  ドラッグ、<xref:System.Windows.Forms.MaskedTextBox>コントロールをフォームには、名前を付けます`PhoneMask`します。  
  
4.  設定、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティの`PhoneMask`に`(000) 000-0000 x9999`します。  
  
5.  次の名前空間のインポートをフォームに追加します。  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6.  フォームを右クリックし **コードの表示**します。 このコードをフォーム クラスに置きます。  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the   
        // initial load.   
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the   
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7.  イベント ハンドラーを追加、<xref:System.Windows.Forms.Binding.Format>と<xref:System.Windows.Forms.Binding.Parse>したり分割したりするイベント、`PhoneNumber`と`Extension`、バインドからフィールド<xref:System.Data.DataSet>します。  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)   
        {  
            ext = "";  
        } else   
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.   
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.   
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8.  2 つ追加<xref:System.Windows.Forms.Button>フォームのコントロール。 名前を付けます`previousButton`と`nextButton`します。 追加するには、各ボタンをダブルクリックして、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、およびイベント ハンドラーに次のコード例で示すように入力します。  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. サンプルを実行します。 データを編集して、**前**と**次**ボタンのデータが適切に保持されることを確認、 <xref:System.Data.DataSet>。  
  
## <a name="example"></a>例  
 次のコード例は、コード全体を前の手順を完了には、その結果の一覧です。  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   ビジュアルを作成するC#または Visual Basic プロジェクト。  
  
-   追加、<xref:System.Windows.Forms.TextBox>と<xref:System.Windows.Forms.MaskedTextBox>フォームにコントロールを前の手順で説明します。  
  
-   プロジェクトの既定のフォームのソース コード ファイルを開きます。  
  
-   このファイル内のソース コードを前の"Code"セクションに記載されているコードに置き換えます。  
  
-   アプリケーションをコンパイルします。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: MaskedTextBox コントロールの使用](walkthrough-working-with-the-maskedtextbox-control.md)
