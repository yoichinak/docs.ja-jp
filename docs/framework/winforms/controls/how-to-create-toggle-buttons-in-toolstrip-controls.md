---
title: '方法: ToolStrip コントロールにトグル ボタンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: e688e9a220e6c82caa2d107589b5ca9a1e59e72b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091253"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>方法: ToolStrip コントロールにトグル ボタンを作成する
ユーザーには、トグル ボタンがクリックすると、くぼんで表示し、もう一度ボタンをクリックするまで、くぼんだ外観を保持します。  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>切り替えのオブジェクトを作成するには  
  
-   次のコード例などのコードを使用します。 このコードでは、フォームが含まれている前提としています、<xref:System.Windows.Forms.ToolStrip>コントロール、およびその<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクションに含まれる、<xref:System.Windows.Forms.ToolStripButton>と呼ばれる`toolStripButton1`します。 呼ばれるイベント ハンドラーを設定することも想定`toolStripButton1_CheckedChanged`します。  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripButton>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
