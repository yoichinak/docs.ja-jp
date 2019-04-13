---
title: '方法: グリッド要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: ebb9369da73bd595338e5b6ef42bda639bde6ed4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134538"
---
# <a name="how-to-create-a-grid-element"></a>方法: グリッド要素を作成する
## <a name="example"></a>例  
 次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.Controls.Grid>いずれかを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。 この例は、3 つ<xref:System.Windows.Controls.ColumnDefinition>オブジェクトと 3 <xref:System.Windows.Controls.RowDefinition> 9 個のグリッドを作成するセル、ワークシートなどのオブジェクトします。 各セルが含まれています、<xref:System.Windows.Controls.TextBlock>データ、および、先頭の行を表す要素が含まれています、<xref:System.Windows.Controls.TextBlock>で、<xref:System.Windows.Controls.Grid.ColumnSpan%2A>プロパティを適用します。 各セルの境界を表示する、<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを有効にします。  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  どちらの方法では、非常によく似た次のように、同じユーザー インターフェイスを生成します。

  ![スクリーン ショットは、3 つの列に分割グリッドを含む WPF ユーザー インターフェイスを示しています。  '2018 製品出荷' の最上位の行のすべての列にまたがる見出しであるし、特定の四半期の 3 つの列それぞれの販売成績が。  一番下の行がテキスト メッセージで 2 つの列にまたがる ' の合計ユニット数。300,000'](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- [パネルの概要](panels-overview.md)
