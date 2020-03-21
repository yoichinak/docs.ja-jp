---
title: ContextMenu の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185909"
---
# <a name="contextmenu-overview"></a>ContextMenu の概要
この<xref:System.Windows.Controls.ContextMenu>クラスは、コンテキスト固有<xref:System.Windows.Controls.Menu>の を使用して機能を公開する要素を表します。 通常、ユーザーはマウス ボタン<xref:System.Windows.Controls.ContextMenu>を右[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]クリックして で を公開します。 このトピックでは、<xref:System.Windows.Controls.ContextMenu>要素を紹介し、その使用方法[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]とコードの例を示します。  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>ContextMenu コントロール  
 A<xref:System.Windows.Controls.ContextMenu>は特定のコントロールにアタッチされます。 要素<xref:System.Windows.Controls.ContextMenu>を使用すると、特定のコントロールに関連付けられているコマンドやオプションを指定する項目のリストをユーザーに<xref:System.Windows.Controls.Button>表示できます。 ユーザーがコントロールを右クリックすると、メニューが表示されます。 通常、をクリック<xref:System.Windows.Controls.MenuItem>するとサブメニューが開き、アプリケーションがコマンドを実行します。  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>ContextMenu の作成  
 次の例は、サブメニューを<xref:System.Windows.Controls.ContextMenu>使用して を作成する方法を示しています。 コントロール<xref:System.Windows.Controls.ContextMenu>はボタン コントロールにアタッチされます。  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>ContextMenu へのスタイルの適用  
 コントロール を使用<xref:System.Windows.Style>すると、カスタム コントロールを記述せずに、外観や動作<xref:System.Windows.Controls.ContextMenu>を大幅に変更できます。 視覚プロパティの設定に加えて、コントロールの一部にスタイルを適用することもできます。 たとえば、プロパティを使用してコントロールの一部の動作を変更したり、パーツを追加したり、レイアウトを変更したりできます<xref:System.Windows.Controls.ContextMenu>。 次の例は、コントロールにスタイルを追加<xref:System.Windows.Controls.ContextMenu>するいくつかの方法を示しています。  
  
 最初の例では、`SimpleSysResources` という名前のスタイルを定義し、スタイルで現在のシステム設定を使用する方法を示します。 この例では、<xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A><xref:System.Windows.Controls.Control.Background%2A>色として、および<xref:System.Windows.SystemColors.MenuTextBrushKey%2A><xref:System.Windows.Controls.ContextMenu>の<xref:System.Windows.Controls.Control.Foreground%2A>色として割り当てます。  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 次の例では、<xref:System.Windows.Trigger>要素を使用して、 で<xref:System.Windows.Controls.Menu>発生したイベントに対する in<xref:System.Windows.Controls.ContextMenu>の外観を変更します。 ユーザーがメニュー上にマウスを移動すると、項目の外観が<xref:System.Windows.Controls.ContextMenu>変わります。  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [Contextmenu](contextmenu.md)
- [ContextMenu のスタイルとテンプレート](contextmenu-styles-and-templates.md)
- [WPF コントロール ギャラリーのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
