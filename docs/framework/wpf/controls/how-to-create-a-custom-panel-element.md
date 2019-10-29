---
title: '方法 : カスタム パネル要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799148"
---
# <a name="how-to-create-a-custom-panel-element"></a>方法 : カスタム パネル要素を作成する
## <a name="example"></a>例  
 この例では、<xref:System.Windows.Controls.Panel> 要素の既定のレイアウト動作をオーバーライドし、<xref:System.Windows.Controls.Panel>から派生したカスタムレイアウト要素を作成する方法を示します。  
  
 この例では、`PlotPanel`と呼ばれる単純なカスタム <xref:System.Windows.Controls.Panel> 要素を定義しています。これは、2つのハードコーディングされた x 座標と y 座標に従って子要素を配置します。 この例では、`x` と `y` の両方が `50`に設定されています。したがって、すべての子要素は、x 軸と y 軸上のその位置に配置されます。  
  
 カスタム <xref:System.Windows.Controls.Panel> 動作を実装するために、この例では <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドと <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドを使用します。 各メソッドは、子要素を配置および表示するために必要な <xref:System.Windows.Size> データを返します。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Panel>
- [パネル概要](panels-overview.md)
