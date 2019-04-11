---
title: '方法: FontDialog コンポーネントを使用してフォントの一覧を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 40679136ea62a437009b308a8b206cf251b46222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307326"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>方法: FontDialog コンポーネントを使用してフォントの一覧を表示する
[FontDialog](fontdialog-component-windows-forms.md)コンポーネントを重みとサイズなど、表示属性を変更できるだけでなく、フォントを選択してユーザーを使用できます。  
  
 ダイアログ ボックスで選択されているフォントが返されます、<xref:System.Windows.Forms.FontDialog.Font%2A>プロパティ。 したがって、ユーザーが選択されているフォントの利用は、プロパティの読み取りと同じくらい簡単です。  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>FontDialog コンポーネントを使用するフォント プロパティを選択するには  
  
1. 使用して、ダイアログ ボックスを表示、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。  
  
2. 使用して、 <xref:System.Windows.Forms.DialogResult>  ダイアログ ボックスが閉じられた方法を決定するプロパティ。  
  
3. 使用して、<xref:System.Windows.Forms.FontDialog.Font%2A>目的のフォントを設定するプロパティ。  
  
     次の例で、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが表示されます、<xref:System.Windows.Forms.FontDialog>コンポーネント。 フォントが選択されると、ユーザーの場合にクリックする **[ok]**、<xref:System.Windows.Forms.FontDialog.Font%2A>のプロパティを<xref:System.Windows.Forms.TextBox>フォーム上にあるコントロールを選択したフォントを設定します。 この例では、フォームに、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.TextBox>コントロール、および<xref:System.Windows.Forms.FontDialog>コンポーネント。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog コンポーネント](fontdialog-component-windows-forms.md)
