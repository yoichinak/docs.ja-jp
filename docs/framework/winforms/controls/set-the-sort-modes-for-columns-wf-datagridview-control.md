---
title: '方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: fd627e3aaed7330a05c46b9e2ca0a213404e0bfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625746"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する
<xref:System.Windows.Forms.DataGridView>コントロール、テキスト ボックスの列を使用して、その他の列の型が自動的に並べ替えられていないときに、既定では、自動並べ替え。 これらの既定値をオーバーライドすることがあります。 たとえば、テキスト、数値、または列挙のセル値の代わりにイメージを表示できます。 イメージを並べ替えることはできません、中にそれが表す基になる値を並べ替えることができます。  
  
 <xref:System.Windows.Forms.DataGridView>コントロール、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>列のプロパティの値は、その並べ替えの動作を決定します。  
  
 次の手順に示す、`Priority`列から[方法。Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズ](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)します。 この列は image 列であり、既定では並べ替えられません。 ただし、文字列を実際のセル値を含まれていますので、自動的に並べ替えることができます。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>列の並べ替えモードを設定するには  
  
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `Priority` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
- <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Windows フォームの DataGridView コントロールでのデータの並べ替え](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロール内の列の並べ替えモード](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールでの並べ替えをカスタマイズします。](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
