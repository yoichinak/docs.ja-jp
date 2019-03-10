---
title: '方法: ColorDialog コンポーネントを使用して、カラー パレットを表示します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 35f6f81c2b13234b23b3b2295e45caf5f16abd9e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708328"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>方法: ColorDialog コンポーネントを使用して、カラー パレットを表示します。
[ColorDialog](colordialog-component-windows-forms.md)コンポーネントは、色のパレットが表示され、ユーザーが選択した色を含むプロパティを返します。  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>ColorDialog コンポーネントを使用して色を選択するには  
  
1.  使用して、ダイアログ ボックスを表示、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。  
  
2.  使用して、 <xref:System.Windows.Forms.DialogResult>  ダイアログ ボックスが閉じられた方法を決定するプロパティ。  
  
3.  使用して、<xref:System.Windows.Forms.ColorDialog.Color%2A>のプロパティ、<xref:System.Windows.Forms.ColorDialog>選択した色を設定するコンポーネント。  
  
     次の例で、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが表示されます、<xref:System.Windows.Forms.ColorDialog>コンポーネント。 色が選択されると、ユーザーの場合、クリックした**OK**、<xref:System.Windows.Forms.Button>コントロールの背景色が、選択した色に設定されています。 この例では、フォームに、<xref:System.Windows.Forms.Button>コントロールと<xref:System.Windows.Forms.ColorDialog>コンポーネント。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog コンポーネント](colordialog-component-windows-forms.md)
