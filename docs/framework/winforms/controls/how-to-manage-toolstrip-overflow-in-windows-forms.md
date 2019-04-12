---
title: '方法: Windows フォームで ToolStrip オーバーフローを管理します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 53f610a728925d454a8833a49e705818f027aec5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707275"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>方法: Windows フォームで ToolStrip オーバーフローを管理します。

ときにすべての項目を<xref:System.Windows.Forms.ToolStrip>コントロールが与えられたスペースに収まらないでオーバーフロー機能を有効にすることができます、<xref:System.Windows.Forms.ToolStrip>固有のオーバーフロー動作を決定し、 <xref:System.Windows.Forms.ToolStripItem>s。

追加すると<xref:System.Windows.Forms.ToolStripItem>に割り当てられた時間はより多くの領域を必要とする、<xref:System.Windows.Forms.ToolStrip>フォームの現在のサイズを指定、<xref:System.Windows.Forms.ToolStripOverflowButton>で自動的に表示されます、<xref:System.Windows.Forms.ToolStrip>します。 <xref:System.Windows.Forms.ToolStripOverflowButton>が表示されたら、オーバーフローが有効な項目がドロップダウンのオーバーフロー メニューに移動します。 これを使用すると、カスタマイズ、および優先順位を付ける方法、<xref:System.Windows.Forms.ToolStrip>項目は、さまざまなフォームのサイズを正しく調整。 使用して、オーバーフローになったとき、項目の外観を変更することも、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>と<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType>プロパティおよび<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベント。 複数のデザイン時または実行時に、フォームを拡大する場合<xref:System.Windows.Forms.ToolStripItem>s は、メイン表示できる<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripOverflowButton>フォームのサイズを小さくまでも表示されなくなる可能性があります。

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>ToolStrip コントロールのオーバーフローを有効にするには

- いることを確認、<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>プロパティに設定されていない`false`の<xref:System.Windows.Forms.ToolStrip>します。 既定値は `True` です。

     ときに<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>は`True`(既定)、<xref:System.Windows.Forms.ToolStripItem>ドロップダウンのオーバーフロー メニューに送信されるときのコンテンツ、<xref:System.Windows.Forms.ToolStripItem>水平方向の幅を超える<xref:System.Windows.Forms.ToolStrip>または垂直方向の高さ<xref:System.Windows.Forms.ToolStrip>。

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>特定の ToolStripItem のオーバーフロー動作を指定するには

- 設定、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>のプロパティ、<xref:System.Windows.Forms.ToolStripItem>に目的の値。 可能性は`Always`、 `Never`、および`AsNeeded`します。 既定値は `AsNeeded` です。

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip コントロールの概要 (Windows フォーム)](toolstrip-control-overview-windows-forms.md)
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
