---
title: '方法: ウィンドウを水平方向に分割する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: a43d632a82678f362a1cdf6b3ee4486a8db5adde
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321082"
---
# <a name="how-to-split-a-window-horizontally"></a>方法: ウィンドウを水平方向に分割する
次のコード例は、分割するスプリッター、<xref:System.Windows.Forms.SplitContainer>コントロールの水平方向。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer.Orientation%2A>のプロパティ、<xref:System.Windows.Forms.SplitContainer>コントロール、コントロール自体のない、スプリッターの方向を決定します。  
  
### <a name="to-split-a-window-horizontally"></a>ウィンドウを水平方向に分割するには  
  
1. プロシージャ内で、設定、<xref:System.Windows.Forms.SplitContainer.Orientation%2A>のプロパティ、<xref:System.Windows.Forms.SplitContainer>に制御を<xref:System.Windows.Forms.Orientation.Horizontal>。  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer コントロール](splitcontainer-control-windows-forms.md)
