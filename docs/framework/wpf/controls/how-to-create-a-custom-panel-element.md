---
title: '方法: カスタム パネル要素を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2e778adfb79a64c8f248992aee92de9471906129
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368702"
---
# <a name="how-to-create-a-custom-panel-element"></a>方法: カスタム パネル要素を作成する
## <a name="example"></a>例  
 この例の既定のレイアウト動作をオーバーライドする方法を示しています、<xref:System.Windows.Controls.Panel>要素から派生したカスタム レイアウト要素を作成および<xref:System.Windows.Controls.Panel>します。  
  
 例では、定義の単純なカスタム<xref:System.Windows.Controls.Panel>と呼ばれる要素`PlotPanel`、に従って 2 つハード コーディングされた x 座標と y 座標の子要素を配置します。 この例で`x`と`y`に設定されて`50`。 したがって、すべての子要素は、x と y でその場所に配置される軸。  
  
 ユーザー設定を実装する<xref:System.Windows.Controls.Panel>動作、例では、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッド。 各メソッドを返します、<xref:System.Windows.Size>データを配置および子要素をレンダリングする必要があります。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.Panel>
- [パネルの概要](panels-overview.md)
- [カスタム コンテンツ折り返しパネルのサンプルを作成します。](https://go.microsoft.com/fwlink/?LinkID=159979)
