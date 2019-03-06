---
title: '方法: ドラッグされた GridView 列ヘッダーのスタイルを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 442fff7a36a48d5df7ba9e07426e50f602cb93e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357496"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>方法: ドラッグされた GridView 列ヘッダーのスタイルを作成する
この例は、ドラッグ中の外観を変更する方法を示しています。<xref:System.Windows.Controls.GridViewColumnHeader>にユーザーが列の位置を変更します。  
  
## <a name="example"></a>例  
 別の場所に列ヘッダーをドラッグすると、<xref:System.Windows.Controls.ListView>を使用して<xref:System.Windows.Controls.GridView>その表示モードの列が新しい位置に移動します。 列ヘッダーをドラッグするだけでなく、元のヘッダー、ヘッダーの浮動小数点のコピーが表示されます。 内の列ヘッダーを<xref:System.Windows.Controls.GridView>で表される、<xref:System.Windows.Controls.GridViewColumnHeader>オブジェクト。  
  
 浮動小数点と元の両方のヘッダーの外観をカスタマイズするに設定することができます<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、 <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>します。 これら<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>場合に適用されます、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値が`true`と<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティの値が<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>します。  
  
 ユーザーがマウス ボタンを押すし、マウスの上に置いたときにそれを保持、 <xref:System.Windows.Controls.GridViewColumnHeader>、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値に変更`true`します。 同様に、ユーザーが、ドラッグ操作を開始すると、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティに対する変更を<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>します。  
  
 次の例は、設定する方法を示します<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.Background%2A>元および浮動小数点のヘッダー、ユーザーが列の新しい位置にドラッグしたときの色。  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [方法トピック](listview-how-to-topics.md)
- [ListView の概要](listview-overview.md)
- [GridView の概要](gridview-overview.md)
