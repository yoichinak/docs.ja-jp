---
title: メニューの概要
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: a3250cfd3fd651cb4ed3c4fd6975f5b5c89195f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942156"
---
# <a name="menu-overview"></a>メニューの概要
<xref:System.Windows.Controls.Menu>クラスでは、コマンドおよび階層の順序でイベント ハンドラーに関連付けられている要素を整理することができます。 各<xref:System.Windows.Controls.Menu>要素のコレクションを含みます<xref:System.Windows.Controls.MenuItem>要素。  

<a name="menu_control"></a>   
## <a name="menu-control"></a>メニュー コントロール  
 <xref:System.Windows.Controls.Menu>コントロールには、コマンドまたはアプリケーションのオプションを指定する項目の一覧が表示されます。 通常をクリックすると、<xref:System.Windows.Controls.MenuItem>サブメニューを開くまたはによりアプリケーションは、コマンドを実行します。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>メニューの作成  
 次の例では、作成、<xref:System.Windows.Controls.Menu>内のテキストを操作する、<xref:System.Windows.Controls.TextBox>します。 <xref:System.Windows.Controls.Menu>が含まれています<xref:System.Windows.Controls.MenuItem>使用するオブジェクト、 <xref:System.Windows.Controls.MenuItem.Command%2A>、 <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>、および<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティおよび<xref:System.Windows.Controls.MenuItem.Checked>、 <xref:System.Windows.Controls.MenuItem.Unchecked>、および<xref:System.Windows.Controls.MenuItem.Click>イベント。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>キーボード ショートカット付きのメニュー項目  
 キーボード ショートカットは、キーボードで入力できる文字の組み合わせ<xref:System.Windows.Controls.Menu>コマンド。 たとえば、**コピー**のショートカットは CTRL+C です。 キーボード ショートカットやメニュー項目を使用する 2 つのプロパティ-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>または<xref:System.Windows.Controls.MenuItem.Command%2A>します。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 次の例は、使用する方法を示します、<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>にキーボード ショートカットのテキストを割り当てるプロパティを<xref:System.Windows.Controls.MenuItem>コントロール。 これは、キーボード ショートカットをメニュー項目に配置するだけです。  コマンドには関連付けられません、<xref:System.Windows.Controls.MenuItem>します。 アプリケーションでは、アクションを実行するために、ユーザーの入力を処理する必要があります。  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>コマンド  
 次の例は、使用する方法を示します、<xref:System.Windows.Controls.MenuItem.Command%2A>プロパティに関連付ける、**オープン**と**保存**コマンドと<xref:System.Windows.Controls.MenuItem>コントロール。 Command プロパティは、コマンドに関連付けするだけでなく、 <xref:System.Windows.Controls.MenuItem>、ショートカットとして使用する入力ジェスチャのテキストも提供します。  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem>クラスがあります、<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>プロパティで、コマンドが発生する要素を指定します。 場合<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>がキーボード フォーカスを持つ要素がコマンドを受け取り、設定されていません。 コマンドの詳細については、[コマンド実行の概要](../advanced/commanding-overview.md)を参照してください。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>メニューのスタイル指定  
 コントロールのスタイルを設定することができますを大幅に変更の動作と外観<xref:System.Windows.Controls.Menu>カスタム コントロールを記述することがなくコントロール。 ビジュアルのプロパティを設定するだけでなく適用することも、<xref:System.Windows.Style>コントロールの各パーツにプロパティを使用してコントロールのパーツの動作を変更または追加のパーツを追加またはコントロールのレイアウトを変更します。 次の例では、いくつかの方法を追加する、<xref:System.Windows.Style>を<xref:System.Windows.Controls.Menu>コントロール。  
  
 最初のコード例、<xref:System.Windows.Style>と呼ばれる`Simple`スタイルで現在のシステム設定を使用する方法を示すです。 このコードは、`MenuHighlightBrush`の色をメニューの背景色として、 `MenuTextBrush`の色をメニューの前景色として割り当てます。 ブラシを割り当てるには、リソース キーを使用することに注意してください。  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 次のサンプルは<xref:System.Windows.Trigger>要素の外観を変更するための<xref:System.Windows.Controls.MenuItem>で発生するイベントへの応答、<xref:System.Windows.Controls.Menu>します。 上でマウスを移動すると、<xref:System.Windows.Controls.Menu>前景の色とメニュー項目のフォント特性を変更します。  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>関連項目

- [WPF Controls Gallery Sample](https://go.microsoft.com/fwlink/?LinkID=160053)
