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
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972361"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>方法: ToolStrip コントロールにトグル ボタンを作成する

ユーザーがトグルボタンをクリックすると、くぼんで表示され、ユーザーがボタンを再度クリックするまで、くぼんだ外観を保持します。

## <a name="to-create-a-toggling-toolstripbutton"></a>切り替え ToolStripButton を作成するには

- 次のコード例のようなコードを使用します。 このコードは<xref:System.Windows.Forms.ToolStrip> 、フォームにコントロールが含まれており、その<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクションに<xref:System.Windows.Forms.ToolStripButton>が`toolStripButton1`呼び出されたが含まれていることを前提としています。 また、という`toolStripButton1_CheckedChanged`イベントハンドラーがあることを前提としています。

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
