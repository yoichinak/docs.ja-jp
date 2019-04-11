---
title: '方法: グリッドの子要素を配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202990"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>方法: グリッドの子要素を配置する
この例は、get を使用してで定義されているメソッドを設定する方法を示しています。<xref:System.Windows.Controls.Grid>子要素を配置します。  
  
## <a name="example"></a>例  
 次の例では、親<xref:System.Windows.Controls.Grid>要素 (`grid1`) を持つ 3 つの列と 3 つの行。 子<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) に追加されます、<xref:System.Windows.Controls.Grid>列の位置 0 の行の位置は 0。 <xref:System.Windows.Controls.Button> 要素の位置を指定して呼び出すことができるメソッドを表す、<xref:System.Windows.Shapes.Rectangle>内の要素、<xref:System.Windows.Controls.Grid>します。 ユーザーは、ボタンをクリックすると、関連メソッドは、アクティブ化されます。  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 分離コード例では、次の処理方法をボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生します。 例では、これらのメソッド呼び出しを書き込みます<xref:System.Windows.Controls.TextBlock>使用に関連する要素が文字列として新しいプロパティ値を出力するメソッドを取得します。  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 最終的な結果を次に示します。
 
 ![スクリーン ショットは、2 つの列を含む WPF ユーザー インターフェイスを示しています、右側にある 3 x 3 のグリッドがあり、左の列と、グリッドの行の間、色付きの四角形を移動するボタン](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- [パネルの概要](panels-overview.md)
