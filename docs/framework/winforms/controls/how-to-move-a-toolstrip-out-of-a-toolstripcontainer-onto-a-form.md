---
title: '方法: ToolStrip を ToolStripContainer からフォームに移動する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: c6519add6789485d41146633abb5e11f80913649
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039825"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>方法: ToolStrip を ToolStripContainer からフォームに移動する
をフォームに移動<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripContainer>するには、次の手順に従います。

## <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>ToolStrip を ToolStripContainer からフォームに移動するには

1. <xref:System.Windows.Forms.ToolStrip>を選択します。

2. CTRL キーを押しながら X キーを押し<xref:System.Windows.Forms.ToolStrip> てを切り取るか、を右クリックしてコンテキストメニューの[切り取り]を選択し<xref:System.Windows.Forms.ToolStrip>ます。

3. フォームを選択します。

4. CTRL キー <xref:System.Windows.Forms.ToolStrip>を押しながら V キーを押すか、 **[編集]** メニューの **[貼り付け]** をクリックして、を貼り付けます。

5. のプロパティを**Top**に設定します<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip.Dock%2A> 。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
