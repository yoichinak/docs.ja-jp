---
title: '方法: IScrollInfo インターフェイスを使用してコンテンツをスクロールする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098547"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>方法: IScrollInfo インターフェイスを使用してコンテンツをスクロールする
この例を使用してコンテンツをスクロール、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイス。  
  
## <a name="example"></a>例  
 次の例では、機能、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイス。 例は、作成、<xref:System.Windows.Controls.StackPanel>要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]親で入れ子になっている<xref:System.Windows.Controls.ScrollViewer>します。 子要素、<xref:System.Windows.Controls.StackPanel>によって定義されたメソッドを使用して論理的にスクロールできる、<xref:System.Windows.Controls.Primitives.IScrollInfo>インターフェイスとのインスタンスへのキャスト<xref:System.Windows.Controls.StackPanel>(`sp1`) コード。  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 各<xref:System.Windows.Controls.Button>で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルでのスクロール動作を制御する、関連付けられているカスタム メソッドをトリガーする<xref:System.Windows.Controls.StackPanel>します。 次の例は、使用する方法を示します、<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>と<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>メソッドも一般的にすべての配置方法を使用する方法を示します<xref:System.Windows.Controls.Primitives.IScrollInfo>クラスを定義します。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer の概要](scrollviewer-overview.md)
- [方法トピック](scrollviewer-how-to-topics.md)
- [パネルの概要](panels-overview.md)
