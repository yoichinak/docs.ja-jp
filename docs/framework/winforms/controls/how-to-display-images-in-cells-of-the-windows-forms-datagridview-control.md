---
title: '方法: Windows フォーム DataGridView コントロールのセルにイメージを表示'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 280f274a0957f098add7fbf2e3b919c33c4c5233
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704406"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールのセルにイメージを表示
画像またはグラフィックは、データの行で表示できる値のいずれか。 多くの場合、これらのグラフィックな従業員の写真や会社のロゴの形式になります。  
  
 内のデータを表示するときに画像を組み込むことは簡単、<xref:System.Windows.Forms.DataGridView>コントロール。 <xref:System.Windows.Forms.DataGridView>コントロールがネイティブでサポートされている任意のイメージ形式を処理、 <xref:System.Drawing.Image> OLE と同様に、クラス図の一部のデータベースで使用される形式。  
  
 場合、<xref:System.Windows.Forms.DataGridView>コントロールのデータ ソースのイメージの列がある、によって自動的に表示されます、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 次のコード例では、埋め込みリソースからアイコンを抽出し、image 列のすべてのセルに表示するためのビットマップに変換する方法を示します。 対応するイメージとテキストのセルの値を置換する別の例では、次を参照してください。[方法。Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズ](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   
  `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   という名前の埋め込まれたアイコン リソース`tree.ico`します。  
  
-   
  <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Drawing?displayProperty=nameWithType> の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズします。](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
