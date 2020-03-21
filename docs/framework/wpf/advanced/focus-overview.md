---
title: フォーカスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186669"
---
# <a name="focus-overview"></a>フォーカスの概要
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、キーボード フォーカスと論理フォーカスという、フォーカスに関する 2 つの主要な概念があります。  キーボード フォーカスはキーボード入力を受け取る要素を指し、論理フォーカスはフォーカスを持つフォーカス範囲内の要素を指します。  これらの概念については、この概要で詳しく説明します。  フォーカスを取得可能な領域を複数持つ複雑なアプリケーションを作成する場合は、これらの概念の違いを理解することが重要です。  
  
 フォーカス管理に参加する主要なクラスは、<xref:System.Windows.Input.Keyboard>クラス、<xref:System.Windows.Input.FocusManager>クラス、および基本要素クラスです<xref:System.Windows.UIElement><xref:System.Windows.ContentElement>。  基本要素の詳細については、「[基本要素の概要](base-elements-overview.md)」を参照してください。  
  
 この<xref:System.Windows.Input.Keyboard>クラスは主にキーボードフォーカスに関係しており、<xref:System.Windows.Input.FocusManager>主に論理フォーカスに関するが、これは絶対的な区別ではない。  キーボード フォーカスを持つ要素は論理フォーカスも持ちますが、論理フォーカスを持つ要素は必ずしもキーボード フォーカスを持ちません。  これは、このクラスを使用して<xref:System.Windows.Input.Keyboard>キーボード フォーカスを持つ要素を設定するときに明らかです。  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>キーボード フォーカス  
 キーボード フォーカスは、現在キーボード入力を受け取っている要素を指します。  キーボード フォーカスを持つ要素は、デスクトップ全体で 1 つしかありません。  では[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、キーボード フォーカスを持つ要素が<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>に`true`設定されます。  クラスの<xref:System.Windows.Input.Keyboard.FocusedElement%2A>static<xref:System.Windows.Input.Keyboard>プロパティは、現在キーボード フォーカスを持つ要素を取得します。  
  
 要素がキーボード フォーカスを取得するには、<xref:System.Windows.UIElement.Focusable%2A>および 基本<xref:System.Windows.UIElement.IsVisible%2A>要素のプロパティを に設定する`true`必要があります。  基本クラスなどの一部の<xref:System.Windows.Controls.Panel>クラスは<xref:System.Windows.UIElement.Focusable%2A>、既定でに`false`設定されています。したがって、このような要素が<xref:System.Windows.UIElement.Focusable%2A>キーボード`true`フォーカスを取得できるようにする場合は、 に設定する必要があります。  
  
 キーボード フォーカスは、要素への Tab キーでの移動や特定の要素でのマウスのクリックなど、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] でのユーザー操作を通じて取得できます。  キーボード フォーカスは、クラスのメソッドを<xref:System.Windows.Input.Keyboard.Focus%2A>使用してプログラムで取得することもできます。 <xref:System.Windows.Input.Keyboard>  メソッド<xref:System.Windows.Input.Keyboard.Focus%2A>は、指定された要素にキーボード フォーカスを与えようとします。  返される要素はキーボード フォーカスが設定された要素ですが、古いフォーカス オブジェクトまたは新しいフォーカス オブジェクトが要求をブロックする場合は、要求された要素とは異なる可能性があります。  
  
 次の例では、<xref:System.Windows.Input.Keyboard.Focus%2A>このメソッドを使用して、<xref:System.Windows.Controls.Button>にキーボード フォーカスを設定します。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 基本<xref:System.Windows.UIElement.IsKeyboardFocused%2A>要素クラスのプロパティは、要素にキーボード フォーカスがあるかどうかを示す値を取得します。  基本<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>要素クラスのプロパティは、要素またはそのビジュアル子要素のいずれかがキーボード フォーカスを持っているかどうかを示す値を取得します。  
  
 アプリケーションの起動時に最初のフォーカスを設定する場合、フォーカスを受け取る要素は、アプリケーションによって読み込まれた最初のウィンドウのビジュアル<xref:System.Windows.UIElement.Focusable%2A>ツリー<xref:System.Windows.UIElement.IsVisible%2A>に含`true`まれ、要素が持ち、に設定されている必要があります。  最初のフォーカスを設定する推奨される場所は<xref:System.Windows.FrameworkElement.Loaded>、イベント ハンドラーです。  コールバック<xref:System.Windows.Threading.Dispatcher>は、 または<xref:System.Windows.Threading.Dispatcher.Invoke%2A><xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>を呼び出すことによっても使用できます。  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>論理フォーカス  
 論理フォーカスは、フォーカス<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>スコープ内の を参照します。  フォーカス スコープは、スコープ内のを追跡する<xref:System.Windows.Input.FocusManager.FocusedElement%2A>要素です。  キーボード フォーカスがフォーカス範囲を離れると、フォーカスがある要素はキーボード フォーカスを失いますが、論理フォーカスは引き続き保持します。  キーボード フォーカスがフォーカス範囲に戻ると、フォーカスがある要素はキーボード フォーカスを取得します。  これにより、キーボード フォーカスが複数のフォーカス範囲間で変更されても、フォーカスがフォーカス範囲に戻ると、そのフォーカス範囲内のフォーカスがある要素はキーボード フォーカスを取り戻すことができます。  
  
 アプリケーションでは、複数の要素が論理フォーカスを持つことがありますが、特定のフォーカス範囲で論理フォーカスを持つ要素は 1 つだけに限られます。  
  
 キーボード フォーカスを持つ要素は、その要素が属するフォーカス範囲の論理フォーカスを持ちます。  
  
 添付プロパティ<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>を に設定`true`[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]することで、要素を<xref:System.Windows.Input.FocusManager>フォーカス スコープに変換できます。  コードでは、要素を呼び出<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>すことによってフォーカス スコープに変換できます。  
  
 次の例では、<xref:System.Windows.Controls.StackPanel>添付プロパティを設定して a<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>をフォーカス スコープにします。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>指定された要素のフォーカス スコープを返します。  
  
 既定で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フォーカス スコープ<xref:System.Windows.Window>であるクラスは<xref:System.Windows.Controls.MenuItem>、 、 <xref:System.Windows.Controls.ToolBar>、および<xref:System.Windows.Controls.ContextMenu>です。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>指定されたフォーカス スコープのフォーカス要素を取得します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>指定したフォーカススコープにフォーカスを設定します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>通常は、最初のフォーカス要素を設定するために使用されます。  
  
 フォーカス範囲にフォーカスを持つ要素を設定し、フォーカス範囲のフォーカスを持つ要素を取得する例を次に示します。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>キーボード ナビゲーション  
 この<xref:System.Windows.Input.KeyboardNavigation>クラスは、ナビゲーション キーの 1 つが押されたときに、既定のキーボード フォーカス ナビゲーションを実装します。  ナビゲーション キーとは、Tab、Shift + Tab、Ctrl + Tab、Ctrl + Shift + Tab、上方向、下方向、左方向、および右方向の各キーを指します。  
  
 ナビゲーション コンテナーのナビゲーション動作は<xref:System.Windows.Input.KeyboardNavigation>、添付プロパティ<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>、 、<xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>および<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>を設定することで変更できます。  これらのプロパティは型<xref:System.Windows.Input.KeyboardNavigationMode>で、使用できる値は<xref:System.Windows.Input.KeyboardNavigationMode.Continue>、 <xref:System.Windows.Input.KeyboardNavigationMode.Local> <xref:System.Windows.Input.KeyboardNavigationMode.Contained>、 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Input.KeyboardNavigationMode.Once>、 <xref:System.Windows.Input.KeyboardNavigationMode.None>、 、および 、 です。  既定値は、<xref:System.Windows.Input.KeyboardNavigationMode.Continue>要素がナビゲーション コンテナーではないことを意味します。  
  
 次の例では、<xref:System.Windows.Controls.Menu>多数の<xref:System.Windows.Controls.MenuItem>オブジェクトを持つ を作成します。  添付<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>プロパティは に設定<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>されます<xref:System.Windows.Controls.Menu>。  内の<xref:System.Windows.Controls.Menu>タブ キーを使用してフォーカスが変更されると、各要素からフォーカスが移動し、最後の要素がフォーカスに達すると、最初の要素に戻ります。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>プログラムによるフォーカスのナビゲーション  
 フォーカスを使用して動作する追加<xref:System.Windows.UIElement.MoveFocus%2A>の<xref:System.Windows.UIElement.PredictFocus%2A>API は、 と です。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>は、アプリケーションの次の要素にフォーカスを変更します。  A<xref:System.Windows.Input.TraversalRequest>は方向を指定するために使用されます。   渡<xref:System.Windows.Input.FocusNavigationDirection>された方向<xref:System.Windows.UIElement.MoveFocus%2A>のフォーカスを指定する 、 、 など<xref:System.Windows.Input.FocusNavigationDirection.First><xref:System.Windows.Input.FocusNavigationDirection.Down>、 <xref:System.Windows.Input.FocusNavigationDirection.Last><xref:System.Windows.Input.FocusNavigationDirection.Up>を移動できます。  
  
 次の例では<xref:System.Windows.FrameworkElement.MoveFocus%2A>、フォーカスのある要素を変更します。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>フォーカスが変更された場合にフォーカスを受け取るオブジェクトを返します。  現在、 <xref:System.Windows.Input.FocusNavigationDirection.Up>、 <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left>、 <xref:System.Windows.Input.FocusNavigationDirection.Right> 、 、 <xref:System.Windows.FrameworkElement.PredictFocus%2A>、 、 がサポートされている場合のみ、  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>フォーカス イベント  
 キーボード フォーカスに関連するイベント<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>は<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>、 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>、 、 です。  イベントは<xref:System.Windows.Input.Keyboard>、クラスの添付イベントとして定義されますが、基本要素クラスの同等のルーティング イベントとして、より簡単にアクセスできます。  イベントの詳細については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>は、要素がキーボード フォーカスを取得したときに発生します。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>は、要素がキーボード フォーカスを失ったときに発生します。  イベントまたは<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>イベントが<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>処理され、 に<xref:System.Windows.RoutedEventArgs.Handled%2A>`true`設定されている場合、フォーカスは変更されません。  
  
 次の例では、<xref:System.Windows.UIElement.GotKeyboardFocus>イベント<xref:System.Windows.UIElement.LostKeyboardFocus>ハンドラーとイベント<xref:System.Windows.Controls.TextBox>ハンドラーを にアタッチします。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 キーボード<xref:System.Windows.Controls.TextBox>フォーカスを取得すると、<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.TextBox>プロパティが に<xref:System.Windows.Media.Brushes.LightBlue%2A>変更されます。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 キーボード<xref:System.Windows.Controls.TextBox>フォーカスが失われると<xref:System.Windows.Controls.Control.Background%2A>、 の<xref:System.Windows.Controls.TextBox>プロパティが白に戻ります。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 論理フォーカスに関連するイベントは<xref:System.Windows.UIElement.GotFocus>、<xref:System.Windows.UIElement.LostFocus>および です。  これらのイベントは、アタッチされた<xref:System.Windows.Input.FocusManager>イベントとして定義されますが、 <xref:System.Windows.Input.FocusManager> CLR イベント ラッパーは公開されません。  <xref:System.Windows.UIElement>また<xref:System.Windows.ContentElement>、これらのイベントをより便利に公開できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [入力の概要](input-overview.md)
- [基本要素の概要](base-elements-overview.md)
