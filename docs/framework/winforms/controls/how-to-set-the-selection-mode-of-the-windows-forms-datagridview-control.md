---
title: '方法: Windows フォーム DataGridView コントロールの選択モードを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 2e430dfb170943178f6db27c0bd2c1ef0f972882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013115"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの選択モードを設定する
次のコード例は、構成する方法を示します、<xref:System.Windows.Forms.DataGridView>コントロールに自動的に、行内でクリックしてできるようには、全体の行を選択し、一度に 1 つだけその行を選択できるようにします。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
- <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの選択モード](selection-modes-in-the-windows-forms-datagridview-control.md)
