---
title: '方法: Windows フォーム DataGridView コントロールのセルの変更に基づいてカスタム動作を実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: 0573199e9afb7e52c7542d36a2f3e39730dacdc4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229161"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールのセルの変更に基づいてカスタム動作を実行する
<xref:System.Windows.Forms.DataGridView>コントロールが状態の変更を検出するために使用できるイベントの数が<xref:System.Windows.Forms.DataGridView>セル。 2 つの最も一般的に使用される、<xref:System.Windows.Forms.DataGridView.CellValueChanged>と<xref:System.Windows.Forms.DataGridView.CellStateChanged>イベント。  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a>DataGridView セルの値に変更を検出するには  
  
-   ハンドラーを記述、<xref:System.Windows.Forms.DataGridView.CellValueChanged>イベント。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a>DataGridView セルの状態の変更を検出するには  
  
-   ハンドラーを記述、<xref:System.Windows.Forms.DataGridView.CellStateChanged>イベント。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。 C#、対応するイベントにイベント ハンドラーを接続する必要があります。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [チュートリアル: Windows フォームの DataGridView コントロールのデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
