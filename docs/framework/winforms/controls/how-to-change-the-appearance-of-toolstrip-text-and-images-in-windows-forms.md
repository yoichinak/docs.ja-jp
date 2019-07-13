---
title: '方法: Windows フォーム内の ToolStrip テキストとイメージの外観を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: cf2f332b17bf6ff5b6ffb7cbc2d5777649728ec6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650856"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>方法: Windows フォーム内の ToolStrip テキストとイメージの外観を変更する
テキストとイメージを表示するかどうかを制御できます、<xref:System.Windows.Forms.ToolStripItem>と相対的な配置と<xref:System.Windows.Forms.ToolStrip>します。  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Toolstripitem の表示される内容を定義するには  
  
- 設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを目的の値にします。 可能性は`Image`、 `ImageAndText`、 `None`、および`Text`します。 既定値は `ImageAndText` です。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Toolstripitem のテキストを配置するには  
  
- 設定、<xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>プロパティを目的の値にします。 可能性は、上部、中央、およびでは、left、center、および右下の任意の組み合わせです。 既定値は `MiddleCenter` です。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Toolstripitem のイメージを配置するには  
  
- 設定、<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>プロパティを目的の値にします。 可能性は、上部、中央、およびでは、left、center、および右下の任意の組み合わせです。 既定値は `MiddleLeft` です。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>相互に比較した ToolStripItem テキストとイメージを表示する方法を定義するには  
  
- 設定、<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>プロパティを目的の値にします。 可能性は`ImageAboveText`、 `ImageBeforeText`、 `Overlay`、 `TextAboveImage`、および`TextBeforeImage`します。 既定値は `ImageBeforeText` です。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
