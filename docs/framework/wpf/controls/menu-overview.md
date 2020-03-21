---
title: メニューの概要
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186971"
---
# <a name="menu-overview"></a>メニューの概要
この<xref:System.Windows.Controls.Menu>クラスを使用すると、コマンドとイベント ハンドラーに関連付けられた要素を階層的な順序で整理できます。 各<xref:System.Windows.Controls.Menu>要素には、要素の<xref:System.Windows.Controls.MenuItem>コレクションが含まれています。  

<a name="menu_control"></a>
## <a name="menu-control"></a>メニュー コントロール  
 コントロール<xref:System.Windows.Controls.Menu>は、アプリケーションのコマンドまたはオプションを指定する項目のリストを表示します。 通常、をクリック<xref:System.Windows.Controls.MenuItem>するとサブメニューが開き、アプリケーションがコマンドを実行します。  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>メニューの作成  
 次の例では、<xref:System.Windows.Controls.Menu>のテキストを操作<xref:System.Windows.Controls.TextBox>する を作成します。 には<xref:System.Windows.Controls.Menu><xref:System.Windows.Controls.MenuItem.Command%2A>、 、 、 <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>、 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 、 、 <xref:System.Windows.Controls.MenuItem.Checked> <xref:System.Windows.Controls.MenuItem.Unchecked>、および<xref:System.Windows.Controls.MenuItem.Click>イベントを使用するオブジェクトが含まれます<xref:System.Windows.Controls.MenuItem>。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>キーボード ショートカット付きのメニュー項目  
 キーボード ショートカットは、コマンドを呼び出すために<xref:System.Windows.Controls.Menu>キーボードと入力できる文字の組み合わせです。 たとえば、**コピー**のショートカットは CTRL+C です。 キーボード ショートカットとメニュー項目<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>には 2 つのプロパティがあります。 <xref:System.Windows.Controls.MenuItem.Command%2A>  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>InputGestureText  
 <xref:System.Windows.Controls.MenuItem.InputGestureText%2A>次の例は、プロパティを使用してコントロールにキーボード ショートカット<xref:System.Windows.Controls.MenuItem>テキストを割り当てる方法を示しています。 これは、キーボード ショートカットをメニュー項目に配置するだけです。  コマンドは<xref:System.Windows.Controls.MenuItem>. アプリケーションでは、アクションを実行するために、ユーザーの入力を処理する必要があります。  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>command  
 次の例は、プロパティを使用<xref:System.Windows.Controls.MenuItem.Command%2A>して **、Open**コマンドと**Save** <xref:System.Windows.Controls.MenuItem>コマンドをコントロールに関連付ける方法を示しています。 コマンド プロパティは、コマンドを<xref:System.Windows.Controls.MenuItem>に関連付けるだけでなく、ショートカットとして使用する入力ジェスチャ テキストも提供します。  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 この<xref:System.Windows.Controls.MenuItem>クラスには、コマンド<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>が発生する要素を指定するプロパティもあります。 設定<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>されていない場合、キーボード フォーカスを持つ要素がコマンドを受け取ります。 コマンドの詳細については、[Commanding Overview](../advanced/commanding-overview.md)を参照してください。  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>メニューのスタイル指定  
 コントロールのスタイル設定を使用すると、カスタム コントロールを記述しなくても<xref:System.Windows.Controls.Menu>、コントロールの外観や動作を大幅に変更できます。 表示プロパティの設定に加えて、コントロールの個々の<xref:System.Windows.Style>部分に a を適用したり、プロパティを使用してコントロールの一部の動作を変更したり、追加パーツを追加したり、コントロールのレイアウトを変更したりすることもできます。 次の例は、コントロールにを<xref:System.Windows.Style>追加するいくつかの方法<xref:System.Windows.Controls.Menu>を示しています。  
  
 最初のコード例では、<xref:System.Windows.Style>現在`Simple`のシステム設定をスタイルで使用する方法を示す呼び出しを定義します。 このコードは、`MenuHighlightBrush`の色をメニューの背景色として、 `MenuTextBrush`の色をメニューの前景色として割り当てます。 ブラシを割り当てるには、リソース キーを使用することに注意してください。  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 次のサンプルでは<xref:System.Windows.Trigger>、で発生したイベントに応答して、<xref:System.Windows.Controls.MenuItem>の外観を変更できる要素を<xref:System.Windows.Controls.Menu>使用します。 <xref:System.Windows.Controls.Menu>上にマウスを移動すると、前景色とメニュー項目のフォント特性が変わります。  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>関連項目

- [WPF コントロール ギャラリーのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
