---
title: '方法: StackPanel にコンテンツを水平方向または垂直方向に配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771034"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>方法: StackPanel にコンテンツを水平方向または垂直方向に配置する
この例を調整する方法を示しています、<xref:System.Windows.Controls.StackPanel.Orientation%2A>内のコンテンツの<xref:System.Windows.Controls.StackPanel>要素、および調整する方法、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>子コンテンツの。  
  
## <a name="example"></a>例  
 次の例では、作成 3<xref:System.Windows.Controls.ListBox>内の要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 各<xref:System.Windows.Controls.ListBox>の有効な値を表す、 <xref:System.Windows.Controls.StackPanel.Orientation%2A>、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>のプロパティを<xref:System.Windows.Controls.StackPanel>します。 ユーザーがいずれの値を選択すると、<xref:System.Windows.Controls.ListBox>要素、関連付けられたプロパティの<xref:System.Windows.Controls.StackPanel>とその子<xref:System.Windows.Controls.Button>要素を変更します。  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 次の分離コード ファイルに関連付けられているイベントに変更を定義する、<xref:System.Windows.Controls.ListBox>選択範囲の変更。 <xref:System.Windows.Controls.StackPanel> 識別される、 <xref:System.Windows.FrameworkElement.Name%2A> `sp1`します。  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [パネルの概要](panels-overview.md)
