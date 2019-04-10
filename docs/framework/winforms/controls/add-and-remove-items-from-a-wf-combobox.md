---
title: '方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: bd6614c76c63a44a7367ac7c7113c4db260c9a02
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322733"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する
項目は、Windows フォームのコンボ ボックス、リスト ボックスに追加できるまたはこれらのコントロールは、さまざまなデータ ソースにバインドできるため、さまざまな方法でリスト ボックスをオンにします。 ただし、このトピックでは、最も簡単な方法について説明し、データ バインドは必要ありません。 表示される項目が文字列では、通常、ただし、すべてのオブジェクトを使用できます。 コントロールに表示されるテキストは、オブジェクトのによって返される値`ToString`メソッド。  
  
### <a name="to-add-items"></a>項目を追加するには  
  
1. 使用して、文字列またはオブジェクトを一覧に追加、`Add`のメソッド、`ObjectCollection`クラス。 使用して、コレクションを参照、`Items`プロパティ。  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - または  
  
2. 目的の時点で、リスト内の文字列またはオブジェクトの挿入、`Insert`メソッド。  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - または  
  
3. 配列全体を割り当てる、`Items`コレクション。  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a>アイテムを削除するには  
  
1. 呼び出す、`Remove`または`RemoveAt`アイテムを削除するメソッド。  
  
     `Remove` 削除する項目を指定する 1 つの引数を持ちます。`RemoveAt` 指定したインデックス番号を持つ項目を削除します。  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a>すべての項目を削除するには  
  
1. 呼び出す、`Clear`コレクションからすべての項目を削除する方法。  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [ListBox の代わりに Windows フォーム ComboBox を使用する場合](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
