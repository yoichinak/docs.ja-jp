---
title: '方法: パネルの OnRender メソッドをオーバーライドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666716"
---
# <a name="how-to-override-the-panel-onrender-method"></a>方法: パネルの OnRender メソッドをオーバーライドする
この例では、レイアウト要素<xref:System.Windows.Controls.Panel.OnRender%2A>にカスタム<xref:System.Windows.Controls.Panel>のグラフィカル効果を追加するために、のメソッドをオーバーライドする方法を示します。  
  
## <a name="example"></a>例  
 レンダリングさ<xref:System.Windows.Controls.Panel.OnRender%2A>れた panel 要素にグラフィカルな効果を追加するには、メソッドを使用します。 たとえば、このメソッドを使用して、カスタムの罫線または背景効果を追加できます。 <xref:System.Windows.Media.DrawingContext>オブジェクトは、図形、テキスト、画像、またはビデオを描画するためのメソッドを提供する引数として渡されます。 このため、このメソッドは、panel オブジェクトをカスタマイズする場合に便利です。  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Panel>
- [パネルの概要](panels-overview.md)
- [方法トピック](panel-how-to-topics.md)
