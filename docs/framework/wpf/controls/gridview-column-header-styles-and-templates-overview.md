---
title: GridView の列ヘッダー スタイルおよびテンプレートの概要
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 83643d8acea706bad439683702e4228d240b97bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090323"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView の列ヘッダー スタイルおよびテンプレートの概要
この概要の説明内の列ヘッダーをカスタマイズするために使用するプロパティの優先順位の順序、<xref:System.Windows.Controls.GridView>の表示モード、<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>GridView の列ヘッダーをカスタマイズします。  
 コンテンツ、レイアウト、および内の列ヘッダーのスタイルを定義するプロパティを<xref:System.Windows.Controls.GridView>多くの関連クラス上にあります。 これらのプロパティの一部は、または同一のような機能があります。  
  
 次の表に行は、同じ機能を実行するプロパティのグループを表示します。 これらのプロパティを使用するには列のヘッダーをカスタマイズする、<xref:System.Windows.Controls.GridView>します。 関連するプロパティの優先順位の順序は右から左に一番右側の列のプロパティが最高の優先順位を持ちます。 たとえば場合、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>が設定されて、<xref:System.Windows.Controls.GridViewColumnHeader>オブジェクトと<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>が関連付けられているセット<xref:System.Windows.Controls.GridViewColumn>、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>が優先されます。 このシナリオで、<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>も何も起こりません。  
  
 **GridView の列ヘッダーの関連プロパティ**  
  
|||||  
|-|-|-|-|  
|**クラス**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**コンテキスト メニューのプロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|利用不可|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ヒント**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|利用不可|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**ヘッダーのテンプレート**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**スタイル プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>の**ヘッダー テンプレート プロパティ**両方テンプレートとテンプレート セレクターのプロパティは、テンプレートのプロパティが優先されますを設定します。 たとえば、両方を設定する場合、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>プロパティ、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティが優先されます。  
  
## <a name="see-also"></a>関連項目

- [方法のトピック](listview-how-to-topics.md)
- [ListView の概要](listview-overview.md)
- [GridView の概要](gridview-overview.md)
