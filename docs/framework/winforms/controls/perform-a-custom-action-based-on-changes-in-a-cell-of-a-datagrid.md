---
title: '方法: Windows フォーム DataGridView コントロールのセルの変更に基づくカスタム動作を実行します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: ad1c60c34fc5461de21e2ad5d4d02f5b2abd6dfd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705585"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールのセルの変更に基づくカスタム動作を実行します。
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
  
-   
  `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。 C#、対応するイベントにイベント ハンドラーを接続する必要があります。  
  
-   
  <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [チュートリアル: Windows フォームの DataGridView コントロールのデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
