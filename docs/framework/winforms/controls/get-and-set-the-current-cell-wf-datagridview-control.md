---
title: '方法: Windows フォーム DataGridView コントロールの現在のセルを取得および設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933697"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの現在のセルを取得および設定する
との対話<xref:System.Windows.Forms.DataGridView>では、現在アクティブなセルをプログラムによって検出する必要があります。 また、現在のセルの変更が必要になる場合もあります。 これらのタスクは、 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティを使用して実行できます。  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridViewBand.Visible%2A>プロパティがに`false`設定されている行または列の現在のセルを設定することはできません。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールの選択モードによっては、現在のセルを変更すると選択範囲が変更される場合があります。 詳細については、「 [Windows フォーム DataGridView コントロールの選択モード](selection-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### <a name="to-get-the-current-cell-programmatically"></a>現在のセルをプログラムで取得するには  
  
- <xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティを使用します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>現在のセルをプログラムによって設定するには  
  
- コントロールのプロパティを<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>設定します。 <xref:System.Windows.Forms.DataGridView> 次のコード例では、現在のセルは行0、列1に設定されています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- <xref:System.Windows.Forms.Button>およびと`getCurrentCellButton` `setCurrentCellButton`いう名前のコントロール。 ビジュアルC#では、各ボタンの<xref:System.Windows.Forms.Control.Click>イベントを、コード例の関連付けられたイベントハンドラーにアタッチする必要があります。  
  
- `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
- <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの選択モード](selection-modes-in-the-windows-forms-datagridview-control.md)
