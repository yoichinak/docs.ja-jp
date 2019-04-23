---
title: '方法: Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 10793053934dce0bb83113004a79f1c265f5f267
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316571"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>方法: Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する
Windows フォームでのデータを表示するときに<xref:System.Windows.Forms.CheckedListBox>コントロールすることができますか、コレクションを反復処理に格納されている、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>プロパティ、または手順を使用して、一覧から、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>どの項目がチェックを調べます。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>メソッドの引数として、項目のインデックス番号を受け取り、返します`true`または`false`します。 予想どおり何とは異なり、<xref:System.Windows.Forms.ListBox.SelectedItems%2A>と<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>プロパティはどの項目がチェックを特定できません。 項目が強調表示が決まります。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox コントロールでチェックされた項目を確認するには  
  
1. 反復処理、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>コレクションは、0 から始まるために、0 から始まるコレクション。 このメソッドは数が表示項目の一覧で、メモは、全体的なリストではなく項目を確認します。 次のコードがなどのテキストを表示する場合は、一覧の最初の項目がチェックされないため、2 番目の項目がオンになって、ように"チェックされている項目 1 MyListItem2 ="。  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - または  
  
2. ステップ実行、<xref:System.Windows.Forms.CheckedListBox.Items%2A>コレクション、コレクションは、0 から始まるために、0 から始まるおよび呼び出し、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>項目ごとにメソッド。 このメソッドは数が表示項目全体の一覧では、最初の項目の場合、リストはチェックされませんので実行して、2 番目の項目がオンになって、ようなものが表示されます"項目 2 = MyListItem2"。  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>関連項目

- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
