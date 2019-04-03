---
title: '方法: データ バインド Windows フォーム DataGridView コントロールにバインドされていない列を追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: d7f96aa8d11cee9427a9e51f8e79fc55adc79355
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712004"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>方法: データ バインド Windows フォーム DataGridView コントロールにバインドされていない列を追加します。
<xref:System.Windows.Forms.DataGridView> コントロールに表示するデータは、通常なんらかのデータ ソースから取得されるデータですが、データ ソース以外からのデータの列を表示する必要が生じることがあります。 この種類の列は、非バインド列と呼ばれます。 非バインド列の形式はさまざまです。 しばしば、データ行の詳細へのアクセスに使用されます。  
  
 次のコード例のバインドされていない列を作成する方法を示します**詳細**マスター/詳細シナリオを実装するときに親テーブルで特定の行に関連する子テーブルを表示するボタン。 ボタンのクリックに応答するには、子テーブルを含むフォームを表示する <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> イベント ハンドラーを実装します。  
  
 Visual Studio では、このタスクに対するサポートが用意されています。  参照してください[方法。削除列で、Windows フォーム DataGridView コントロールのデザイナーを使用してを追加および](add-and-remove-columns-in-the-datagrid-using-the-designer.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)
