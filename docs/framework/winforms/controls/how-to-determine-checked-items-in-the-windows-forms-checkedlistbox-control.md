---
title: CheckedListBox コントロールでチェックされた項目を確認する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182192"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する
Windows フォーム<xref:System.Windows.Forms.CheckedListBox>コントロールにデータを表示する場合は、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>プロパティに格納されているコレクションを反復処理するか、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>メソッドを使用してリストをステップ実行して、チェックされる項目を決定できます。 この<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>メソッドは、項目のインデックス番号を引数として受`true`け`false`取り、または を返します。 期待する内容とは対照的に<xref:System.Windows.Forms.ListBox.SelectedItems%2A>、<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>および プロパティはどの項目がチェックされるのかを決定しません。ハイライト表示される項目を決定します。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox コントロール内のチェックされた項目を確認するには  
  
1. コレクションが<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>0 から始まるので、0 から順に反復します。 このメソッドは、全体のリストではなく、チェックされた項目のリスト内の項目番号を示します。 リストの最初の項目がチェックされておらず、2 番目の項目がチェックされている場合、以下のコードは"チェックされた項目 1 = MyListItem2" のようなテキストを表示します。  
  
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
  
     - - または -  
  
2. コレクションが<xref:System.Windows.Forms.CheckedListBox.Items%2A>0 から始まるコレクションをステップ実行し、各項目のメソッドを<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>呼び出します。 このメソッドは、リスト全体の項目番号を示すため、リストの最初の項目がチェックされず、2 番目の項目がチェックされている場合は、"Item 2 = MyListItem2" のような項目が表示されます。  
  
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
