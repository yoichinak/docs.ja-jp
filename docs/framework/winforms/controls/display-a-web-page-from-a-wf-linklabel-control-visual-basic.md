---
title: '方法: Windows フォームの LinkLabel コントロールから Web ページを表示する (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: 1be9ff06e749d14b46946e899c6ffb6c3a950d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170028"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>方法: Windows フォームの LinkLabel コントロールから Web ページを表示する (Visual Basic)
この例では、ユーザーが Windows フォームをクリックすると、既定のブラウザーで Web ページを表示<xref:System.Windows.Forms.LinkLabel>コントロール。  
  
## <a name="example"></a>例  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   という名前の Windows フォーム`Form1`します。  
  
-   `LinkLabel1` という名前の <xref:System.Windows.Forms.LinkLabel> コントロール。  
  
-   インターネットに接続します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し、<xref:System.Diagnostics.Process.Start%2A>メソッドには、完全な信頼が必要です。 詳細については、「 <xref:System.Security.SecurityException> 」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel コントロール](linklabel-control-windows-forms.md)
