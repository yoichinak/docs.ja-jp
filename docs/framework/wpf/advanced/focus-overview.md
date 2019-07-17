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
ms.openlocfilehash: 8546516124b2156e02446e15d7bdcaf3cdbd717d
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238608"
---
# <a name="focus-overview"></a>フォーカスの概要
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、キーボード フォーカスと論理フォーカスという、フォーカスに関する 2 つの主要な概念があります。  キーボード フォーカスはキーボード入力を受け取る要素を指し、論理フォーカスはフォーカスを持つフォーカス範囲内の要素を指します。  これらの概念については、この概要で詳しく説明します。  フォーカスを取得可能な領域を複数持つ複雑なアプリケーションを作成する場合は、これらの概念の違いを理解することが重要です。  
  
 フォーカス管理に参加する主要なクラスは、<xref:System.Windows.Input.Keyboard>クラス、<xref:System.Windows.Input.FocusManager>クラス、および基本要素クラス、<xref:System.Windows.UIElement>と<xref:System.Windows.ContentElement>します。  基本要素の詳細については、「[基本要素の概要](base-elements-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard>主にキーボード フォーカスを持つクラスでは、および<xref:System.Windows.Input.FocusManager>が論理フォーカスを中心に説明が絶対的な区別はありません。  キーボード フォーカスを持つ要素は論理フォーカスも持ちますが、論理フォーカスを持つ要素は必ずしもキーボード フォーカスを持ちません。  使用する場合に、このことは明らかな、<xref:System.Windows.Input.Keyboard>にキーボード フォーカスがある要素を設定するクラスが要素にも論理フォーカスを設定します。  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>キーボード フォーカス  
 キーボード フォーカスは、現在キーボード入力を受け取っている要素を指します。  キーボード フォーカスを持つ要素は、デスクトップ全体で 1 つしかありません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、 キーボード フォーカスを持つ要素の<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>は`true`に設定されます。  静的プロパティ<xref:System.Windows.Input.Keyboard.FocusedElement%2A>上、<xref:System.Windows.Input.Keyboard>クラスは、現在キーボード フォーカスがある要素を取得します。  
  
 キーボード フォーカスを取得する要素の順序で、<xref:System.Windows.UIElement.Focusable%2A>と<xref:System.Windows.UIElement.IsVisible%2A>に基本要素のプロパティを設定する必要があります`true`します。  などのいくつかのクラス、<xref:System.Windows.Controls.Panel>基底クラスが<xref:System.Windows.UIElement.Focusable%2A>に設定`false`既定ではそのため、する必要があります設定<xref:System.Windows.UIElement.Focusable%2A>に`true`する場合はこのような要素にキーボード フォーカスを取得することになります。  
  
 キーボード フォーカスは、要素への Tab キーでの移動や特定の要素でのマウスのクリックなど、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] でのユーザー操作を通じて取得できます。  また、<xref:System.Windows.Input.Keyboard>クラスの<xref:System.Windows.Input.Keyboard.Focus%2A>メソッドを使用して、 プログラムでキーボード フォーカスを取得することもできます。  <xref:System.Windows.Input.Keyboard.Focus%2A>メソッドは、指定した要素にキーボード フォーカスしようとしています。  返される要素はキーボード フォーカスが設定された要素ですが、古いフォーカス オブジェクトまたは新しいフォーカス オブジェクトが要求をブロックする場合は、要求された要素とは異なる可能性があります。  
  
 次の例では、<xref:System.Windows.Input.Keyboard.Focus%2A>にキーボード フォーカスを設定する方法、<xref:System.Windows.Controls.Button>します。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基本要素クラスのプロパティが要素にキーボード フォーカスがあるかどうかを示す値を取得します。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基本要素クラスのプロパティは、要素またはその子ビジュアル要素のいずれかにキーボード フォーカスがあるかどうかを示す値を取得します。  
  
 フォーカスを受け取る要素が、アプリケーションによって読み込まれる初期ウィンドウのビジュアル ツリーである必要がありますにアプリケーションの起動時に初期フォーカスを設定するときと、要素があります<xref:System.Windows.UIElement.Focusable%2A>と<xref:System.Windows.UIElement.IsVisible%2A>設定`true`します。  初期フォーカスを設定する推奨場所は、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。  A<xref:System.Windows.Threading.Dispatcher>コールバックを呼び出すことによって使用も<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>します。  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>論理フォーカス  
 論理フォーカスは、フォーカス スコープ内の<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>を指します。  フォーカス範囲を追跡する要素とは、<xref:System.Windows.Input.FocusManager.FocusedElement%2A>そのスコープ内で。  キーボード フォーカスがフォーカス範囲を離れると、フォーカスがある要素はキーボード フォーカスを失いますが、論理フォーカスは引き続き保持します。  キーボード フォーカスがフォーカス範囲に戻ると、フォーカスがある要素はキーボード フォーカスを取得します。  これにより、キーボード フォーカスが複数のフォーカス範囲間で変更されても、フォーカスがフォーカス範囲に戻ると、そのフォーカス範囲内のフォーカスがある要素はキーボード フォーカスを取り戻すことができます。  
  
 アプリケーション内の複数の要素が論理フォーカスを持つことがありますが、特定のフォーカス スコープで論理フォーカスを持つ要素は 1 つだけに限られます。  
  
 キーボード フォーカスを持つ要素は、その要素が属するフォーカス範囲の論理フォーカスを持ちます。  
  
 フォーカス範囲内に要素を変換できます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を設定して、<xref:System.Windows.Input.FocusManager>添付プロパティ<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>に`true`します。  コードでは、要素に変換できますフォーカス範囲を呼び出して<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>します。  
  
 次の例では、<xref:System.Windows.Controls.StackPanel>の<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>添付プロパティを設定してフォーカス スコープに変換しています。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> 指定した要素のフォーカス範囲を返します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で、デフォルトでフォーカス スコープであるクラスは、<xref:System.Windows.Window>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.ToolBar>、<xref:System.Windows.Controls.ContextMenu>です。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> 指定したフォーカス範囲のフォーカスがある要素を取得します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 指定したフォーカス範囲でフォーカスがある要素を設定します。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 通常、初期のフォーカスがある要素の設定を使用します。  
  
 フォーカス範囲にフォーカスを持つ要素を設定し、フォーカス範囲のフォーカスを持つ要素を取得する例を次に示します。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>キーボード ナビゲーション  
 <xref:System.Windows.Input.KeyboardNavigation>クラスは、ナビゲーション キーのいずれかが押されたときに既定のキーボード フォーカスのナビゲーションを実装する責任を負います。  ナビゲーション キーは次のとおりです。タブ、SHIFT + TAB、CTRL + TAB、CTRL + SHIFT + TAB、上方向、下方向、LEFTARROW、および右矢印キー。  
  
 ナビゲーション コンテナーのナビゲーション動作は、接続されている設定によって変更できます<xref:System.Windows.Input.KeyboardNavigation>プロパティ<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>、 <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>、および<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>します。  これらのプロパティが型<xref:System.Windows.Input.KeyboardNavigationMode>指定できる値は、 <xref:System.Windows.Input.KeyboardNavigationMode.Continue>、 <xref:System.Windows.Input.KeyboardNavigationMode.Local>、 <xref:System.Windows.Input.KeyboardNavigationMode.Contained>、 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>、 <xref:System.Windows.Input.KeyboardNavigationMode.Once>、および<xref:System.Windows.Input.KeyboardNavigationMode.None>します。  既定値は<xref:System.Windows.Input.KeyboardNavigationMode.Continue>、つまり、要素がナビゲーション コンテナーではありません。  
  
 次の例では、作成、<xref:System.Windows.Controls.Menu>の数が<xref:System.Windows.Controls.MenuItem>オブジェクト。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>添付プロパティに設定されて<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>上、<xref:System.Windows.Controls.Menu>します。  内で tab キーを使用して、フォーカスが変更されたときに、<xref:System.Windows.Controls.Menu>最初の要素にフォーカスが戻りますの最後の要素に達すると、各要素からフォーカスが移動されます。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>プログラムによるフォーカスのナビゲーション  
 フォーカスを使用する追加の API は<xref:System.Windows.UIElement.MoveFocus%2A>と<xref:System.Windows.UIElement.PredictFocus%2A>します。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> アプリケーションでは、次の要素にフォーカスを変更します。  A<xref:System.Windows.Input.TraversalRequest>方向を指定するために使用します。   <xref:System.Windows.Input.FocusNavigationDirection>に渡される<xref:System.Windows.UIElement.MoveFocus%2A>、さまざまな方向フォーカスを移動できるなどを指定します。 <xref:System.Windows.Input.FocusNavigationDirection.First>、 <xref:System.Windows.Input.FocusNavigationDirection.Last>、<xref:System.Windows.Input.FocusNavigationDirection.Up>と<xref:System.Windows.Input.FocusNavigationDirection.Down>します。  
  
 次の例では<xref:System.Windows.FrameworkElement.MoveFocus%2A>フォーカスがある要素を変更します。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> フォーカスが変更された場合にフォーカスを受け取るオブジェクトを返します。  現時点では、のみ<xref:System.Windows.Input.FocusNavigationDirection.Up>、 <xref:System.Windows.Input.FocusNavigationDirection.Down>、 <xref:System.Windows.Input.FocusNavigationDirection.Left>、および<xref:System.Windows.Input.FocusNavigationDirection.Right>でサポートされている<xref:System.Windows.FrameworkElement.PredictFocus%2A>します。  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>フォーカス イベント  
 キーボード フォーカスに関連するイベントは<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>、<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>と<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>、<xref:System.Windows.Input.Keyboard.LostKeyboardFocus>します。  イベントが添付イベントとして定義されている、<xref:System.Windows.Input.Keyboard>クラスしますが、基本要素クラスで同等のルーティング イベントとしてより簡単にアクセスできるようにします。  イベントの詳細については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 要素がキーボード フォーカスを取得するときに発生します。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 要素がキーボード フォーカスを失ったときに発生します。  場合、<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>イベントまたは<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>イベントを処理し、<xref:System.Windows.RoutedEventArgs.Handled%2A>に設定されている`true`、フォーカスは変更されません。  
  
 次の例では、アタッチ<xref:System.Windows.UIElement.GotKeyboardFocus>と<xref:System.Windows.UIElement.LostKeyboardFocus>イベント ハンドラーを<xref:System.Windows.Controls.TextBox>します。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 ときに、<xref:System.Windows.Controls.TextBox>キーボード フォーカス、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>に変更されます<xref:System.Windows.Media.Brushes.LightBlue%2A>します。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 ときに、<xref:System.Windows.Controls.TextBox>がキーボード フォーカスを失う、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>が白に変更します。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 論理フォーカスに関連するイベントは<xref:System.Windows.UIElement.GotFocus>と<xref:System.Windows.UIElement.LostFocus>します。  これらのイベントが定義されている、<xref:System.Windows.Input.FocusManager>として添付イベントですが、 <xref:System.Windows.Input.FocusManager> CLR イベント ラッパーを公開しません。  <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement>より簡単にこれらのイベントを公開します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [入力の概要](input-overview.md)
- [基本要素の概要](base-elements-overview.md)
