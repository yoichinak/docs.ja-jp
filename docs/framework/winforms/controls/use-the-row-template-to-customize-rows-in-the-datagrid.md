---
title: '方法: 行テンプレートを使用して Windows フォームの DataGridView コントロール内の行をカスタマイズするには'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 3cd1e9af32cb47f5d81abfc92423ea30e2e599cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707574"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>方法: 行テンプレートを使用して Windows フォームの DataGridView コントロール内の行をカスタマイズするには
<xref:System.Windows.Forms.DataGridView>コントロール データ バインディングを使用または呼び出すときに、コントロールに追加されるすべての行の基礎として行テンプレートを使用して、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>メソッドを使用する既存の行を指定することなしです。  
  
 行テンプレートを使用してよりも行の動作と外観をより細かく制御、<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>プロパティを提供します。 行のテンプレートと、いずれかを設定できます<xref:System.Windows.Forms.DataGridViewRow>を含むプロパティ<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>します。  
  
 これは、状況によっては、特定の効果を実現するために行のテンプレートを使用する必要があります。 行の高さ情報を格納できないなど、<xref:System.Windows.Forms.DataGridViewCellStyle>ので、すべての行で使用される既定の高さを変更する行のテンプレートを使用する必要があります。 行のテンプレートから派生した独自のクラスを作成する際にも役立ちます<xref:System.Windows.Forms.DataGridViewRow>コントロールに新しい行を追加するときに使用してカスタムの型を必要とします。  
  
> [!NOTE]
>  行のテンプレートは、行が追加されたときにのみ使用されます。 行テンプレートを変更することで既存の行を変更することはできません。  
  
### <a name="to-use-the-row-template"></a>行テンプレートを使用するには  
  
-   取得したオブジェクトのプロパティを設定、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>プロパティ。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   
  <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType>、および <xref:System.Windows.Forms?displayProperty=nameWithType> の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
