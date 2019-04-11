---
title: '方法: グリッドを使用して標準 UI ダイアログ ボックスをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149527"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>方法: グリッドを使用して標準 UI ダイアログ ボックスをビルドする
この例は、標準を作成する方法を示します[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ダイアログ ボックスを使用して、<xref:System.Windows.Controls.Grid>要素。  
  
## <a name="example"></a>例  
 次の例のようなダイアログ ボックスの作成、**実行** ダイアログ ボックスで、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]オペレーティング システム。  
  
 例は、作成、<xref:System.Windows.Controls.Grid>を使用して、<xref:System.Windows.Controls.ColumnDefinition>と<xref:System.Windows.Controls.RowDefinition>5 つの列と 4 つの行を定義するクラス。  
  
 例は、追加し、配置、 <xref:System.Windows.Controls.Image>、 `RunIcon.png`、ダイアログ ボックスにある画像を表します。 最初の列との行で、イメージが格納される、 <xref:System.Windows.Controls.Grid> (左上隅)。  
  
 次に、例、<xref:System.Windows.Controls.TextBlock>最初の列は、最初の行の残りの列にまたがる要素。 追加別<xref:System.Windows.Controls.TextBlock>要素を表す、最初の列の 2 つ目の行に、**オープン**テキスト ボックス。 A<xref:System.Windows.Controls.TextBlock>フォローで、データ エントリの領域を表します。  
  
 最後に、3 つ追加例では、<xref:System.Windows.Controls.Button>を表す要素の最後の行を**OK**、**キャンセル**、および**参照**イベント。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [パネルの概要](panels-overview.md)
- [方法のトピック](grid-how-to-topics.md)
