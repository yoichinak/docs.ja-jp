---
title: '方法 : グリッドの子要素を配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186717"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>方法 : グリッドの子要素を配置する
この例では、子要素を配置するために定義されている get メソッド<xref:System.Windows.Controls.Grid>と set メソッドを使用する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、3<xref:System.Windows.Controls.Grid>つの`grid1`列と 3 つの行を持つ親要素 ( ) を定義します。 子<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) が列<xref:System.Windows.Controls.Grid>位置 0、行位置 0 に追加されます。 <xref:System.Windows.Controls.Button>要素は、要素を内部で再配置<xref:System.Windows.Shapes.Rectangle>するために呼び出すことができるメソッド<xref:System.Windows.Controls.Grid>を表します。 ユーザーがボタンをクリックすると、関連するメソッドがアクティブになります。  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 次のコード ビハインドの例では、ボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生するメソッドを処理します。 この例では、関連する<xref:System.Windows.Controls.TextBlock>get メソッドを使用して新しいプロパティ値を文字列として出力する要素に、これらのメソッド呼び出しを書き込みます。  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 完成した結果はこちら!

 ![スクリーンショットは 2 つの列を持つ WPF ユーザー インターフェイスを示し、右側には 3 x 3 のグリッドがあり、左側にはグリッドの列と行の間に色付きの四角形を移動するボタンがあります](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- [パネル概要](panels-overview.md)
