---
title: WPF で Win32 コントロールをホストする
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186750"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>チュートリアル: WPF で Win32 コントロールをホストする
Windows プレゼンテーション基盤 (WPF) は、アプリケーションを作成するための豊富な環境を提供します。 ただし、Win32 コードに多大な投資を行う場合は、WPF アプリケーションでコードを完全に書き直すのではなく、少なくとも一部のコードを再利用する方が効果的な場合があります。 WPFWPF は、WPF ページで Win32 ウィンドウをホストするための簡単なメカニズムを提供します。  
  
 このトピックでは[、Win32 リスト ボックス コントロールをホストするアプリケーション「WPF サンプルで Win32 リスト ボックス コントロールをホスト](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)する」を説明します。 この一般的な手順は、任意の Win32 ウィンドウをホストするように拡張できます。  

<a name="requirements"></a>
## <a name="requirements"></a>必要条件  
 このトピックでは、WPF と Windows API プログラミングの両方に関する基本的な知識があることを前提としています。 WPF プログラミングの基本的な概要については、「[はじめに](../getting-started/index.md)」を参照してください。 Windows API プログラミングの概要については、この問題に関する多数の書籍、特にチャールズ ペトゾルドによる*プログラミング Windows*を参照してください。  
  
 このトピックに付属するサンプルは C# で実装されているため、プラットフォーム呼び出しサービス (PInvoke) を使用して Windows API にアクセスします。 PInvoke に関する知識はある程度役に立ちますが、必須ではありません。  
  
> [!NOTE]
> このトピックには、関連するサンプルのコード例が含まれています。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 WPF サンプルで[Win32 リスト ボックス コントロールをホストする](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)から、完全なコードを取得または表示できます。  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>基本手順  
 ここでは、WPF ページで Win32 ウィンドウをホストするための基本的な手順について説明します。 残りのセクションでは、各手順の詳細を確認します。  
  
 基本的なホスティング手順は次のとおりです。  
  
1. ウィンドウをホストする WPF ページを実装します。 1 つの手法は、<xref:System.Windows.Controls.Border>ホストされるウィンドウのページのセクションを予約する要素を作成することです。  
  
2. から<xref:System.Windows.Interop.HwndHost>継承するコントロールをホストするクラスを実装します。  
  
3. そのクラスで、クラス<xref:System.Windows.Interop.HwndHost>メンバ<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>をオーバーライドします。  
  
4. WPF ページを含むウィンドウの子としてホストされたウィンドウを作成します。 従来の WPF プログラミングでは、明示的に使用する必要はありませんが、ホスト ページはハンドル (HWND) を持つウィンドウです。 メソッドの`hwndParent`パラメータを使用してページ HWND<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>を受け取ります。 ホストされたウィンドウは、この HWND の子として作成する必要があります。  
  
5. ホスト ウィンドウを作成したら、ホストされたウィンドウの HWND を返します。 1 つ以上の Win32 コントロールをホストする場合は、通常、HWND の子としてホスト ウィンドウを作成し、そのホスト ウィンドウの子コントロールを作成します。 コントロールをホスト ウィンドウにラップすると、WPF ページがコントロールから通知を受け取る簡単な方法が提供されます。  
  
6. 子コントロールからの通知など、ホスト ウィンドウに送信される選択したメッセージを処理します。 2 つの方法があります。  
  
    - ホスト クラスでメッセージを処理する場合は、クラスの<xref:System.Windows.Interop.HwndHost.WndProc%2A>メソッドをオーバーライド<xref:System.Windows.Interop.HwndHost>します。  
  
    - WPF でメッセージを処理する場合は、分離コードで<xref:System.Windows.Interop.HwndHost>クラス<xref:System.Windows.Interop.HwndHost.MessageHook>イベントを処理します。 このイベントは、ホストされたウィンドウが受信するすべてのメッセージに対して発生します。 このオプションを選択した場合でも、 を<xref:System.Windows.Interop.HwndHost.WndProc%2A>オーバーライドする必要がありますが、必要な実装は最小限に抑えます。  
  
7. の<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>メソッド<xref:System.Windows.Interop.HwndHost.WndProc%2A>と<xref:System.Windows.Interop.HwndHost>メソッドをオーバーライドします。 <xref:System.Windows.Interop.HwndHost>コントラクトを満たすためには、これらのメソッドをオーバーライドする必要がありますが、最小限の実装を提供するだけで済む場合があります。  
  
8. 分離コード ファイルで、コントロール ホスト クラスのインスタンスを作成し、ウィンドウを<xref:System.Windows.Controls.Border>ホストする要素の子にします。  
  
9. ホストされたウィンドウと通信するには、Microsoft Windows メッセージを送信し、コントロールから送信された通知などの子ウィンドウからメッセージを処理します。  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>ページ レイアウトの実装  
 リスト ボックス コントロールをホストする WPF ページのレイアウトは、2 つの領域で構成されます。 ページの左側には、Win32 コントロールを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]操作できる WPF コントロールがいくつかホストされています。 ページの右上隅には、ホストされた ListBox コントロールの正方形の領域があります。  
  
 このレイアウトを実装するコードは非常に簡単です。 ルート要素は、2<xref:System.Windows.Controls.DockPanel>つの子要素を持つ 要素です。 最初の要素は<xref:System.Windows.Controls.Border>、リスト ボックス コントロールをホストする要素です。 ページの右上隅に 200x200 の正方形を占めています。 2 つ目<xref:System.Windows.Controls.StackPanel>は、情報を表示し、公開された相互運用プロパティを設定して ListBox コントロールを操作できるようにする一連の WPF コントロールを含む要素です。 子要素の各要素については、これらの要素の<xref:System.Windows.Controls.StackPanel>内容や動作の詳細については、さまざまな要素のリファレンス資料を参照してください。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 コントロールをホストするクラスを実装する  
 このサンプルの中核となるのは、実際にコントロールをホストするクラス ControlHost.csです。 <xref:System.Windows.Interop.HwndHost> から継承します。 コンストラクターは、高さと幅の 2 つのパラメーターを<xref:System.Windows.Controls.Border>受け取ります。 これらの値は、コントロールのサイズが要素と一致することを確認するために<xref:System.Windows.Controls.Border>後で使用されます。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 定数のセットもあります。 これらの定数は、主に Winuser.h から取得され、Win32 関数を呼び出すときに従来の名前を使用できます。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>ビルドウィンドウコアをオーバーライドして、Win32 ウィンドウを作成します。  
 このメソッドをオーバーライドして、ページでホストされる Win32 ウィンドウを作成し、ウィンドウとページの間に接続を作成します。 このサンプルでは ListBox コントロールをホストする必要があるため、2 つのウィンドウが作成されます。 1 つ目は、WPF ページによって実際にホストされるウィンドウです。 リスト ボックス コントロールは、そのウィンドウの子として作成されます。  
  
 この方法の理由は、コントロールから通知を受信するプロセスを簡略化するためです。 クラス<xref:System.Windows.Interop.HwndHost>を使用すると、ホストしているウィンドウに送信されるメッセージを処理できます。 Win32 コントロールを直接ホストする場合は、コントロールの内部メッセージ ループに送信されたメッセージを受信します。 コントロールを表示してメッセージを送信することはできますが、コントロールが親ウィンドウに送信する通知は受信しません。 これは、特に、ユーザーがコントロールと対話するタイミングを検出する方法がないことを意味します。 代わりに、ホスト ウィンドウを作成し、コントロールをそのウィンドウの子にします。 これにより、コントロールから送信された通知を含む、ホスト ウィンドウのメッセージを処理できます。 便宜上、ホスト ウィンドウはコントロールの単純なラッパーに過ぎないため、パッケージは ListBox コントロールと呼ばれます。  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>ホスト ウィンドウとリスト ボックス コントロールを作成する  
 PInvoke を使用して、ウィンドウ クラスを作成および登録して、コントロールのホスト ウィンドウを作成できます。 しかし、より簡単なアプローチは、定義済みの「静的」ウィンドウクラスを持つウィンドウを作成することです。 これにより、コントロールから通知を受け取るために必要なウィンドウ プロシージャが提供され、コーディングが最小限に抑えられます。  
  
 コントロールの HWND は読み取り専用プロパティを通じて公開され、ホスト ページは、コントロールにメッセージを送信するために使用できます。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox コントロールは、ホスト ウィンドウの子として作成されます。 両方のウィンドウの高さと幅は、上で説明したコンストラクターに渡される値に設定されます。 これにより、ホスト ウィンドウとコントロールのサイズが、ページ上の予約領域と同じになります。  ウィンドウが作成されると、サンプルはホスト ウィンドウ<xref:System.Runtime.InteropServices.HandleRef>の HWND を含むオブジェクトを返します。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>デストロイウィンドウと WndProc を実装する  
 また、<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>の メソッド<xref:System.Windows.Interop.HwndHost.WndProc%2A>および<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>メソッドもオーバーライドする<xref:System.Windows.Interop.HwndHost>必要があります。 この例では、コントロールのメッセージは<xref:System.Windows.Interop.HwndHost.MessageHook>ハンドラーによって処理されるため、実装<xref:System.Windows.Interop.HwndHost.WndProc%2A><xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>は最小限です。 の場合<xref:System.Windows.Interop.HwndHost.WndProc%2A>は、`handled``false`メッセージが処理されないことを示すためにに設定し、0 を返します。 の<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>場合は、単にウィンドウを破壊します。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>ページ上のコントロールをホストする  
 ページ上のコントロールをホストするには、まずクラスの新しいインスタンスを作成`ControlHost`します。 コントロール (`ControlHostElement`) を含む境界線要素の高さと幅を`ControlHost`コンストラクターに渡します。 これにより、ListBox のサイズが正しく設定されます。 その後、`ControlHost`オブジェクトをホストのプロパティに割り当てることによって、<xref:System.Windows.Controls.Decorator.Child%2A>ページ上のコントロール<xref:System.Windows.Controls.Border>をホストします。  
  
 このサンプルでは、ハンドラーをの<xref:System.Windows.Interop.HwndHost.MessageHook>イベントにアタッチ`ControlHost`して、コントロールからメッセージを受信します。 このイベントは、ホストされたウィンドウに送信されるすべてのメッセージに対して発生します。 この場合、これらは、コントロールからの通知を含む、実際の ListBox コントロールをラップするウィンドウに送信されるメッセージです。 このサンプルでは、SendMessage を呼び出してコントロールから情報を取得し、その内容を変更します。 ページがコントロールと通信する方法の詳細については、次のセクションで説明します。  
  
> [!NOTE]
> SendMessage には 2 つの PInvoke 宣言があることに注意してください。 これは、1 つはパラメーターを`wParam`使用して文字列を渡し、もう 1 つは整数を渡すために使用するためです。 データが正しくマーシャリングされるように、各署名に対して個別の宣言が必要です。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>コントロールとページ間の通信を実装する  
 コントロールを操作するには、Windows メッセージを送信します。 コントロールは、ユーザーがホスト ウィンドウに通知を送信することによって、コントロールと対話したときに通知します。 WPF の[Win32 リスト ボックス コントロールのホスティング](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)のサンプルには、この動作の例を示す UI が含まれています。  
  
- リストに項目を追加します。  
  
- 選択した項目を一覧から削除します  
  
- 現在選択されている項目のテキストを表示します。  
  
- リスト内の項目数を表示します。  
  
 ユーザーは、従来の Win32 アプリケーションの場合と同様に、リスト ボックス内の項目をクリックして選択することもできます。 表示されるデータは、ユーザーが項目を選択、追加、または追加することによってリスト ボックスの状態を変更するたびに更新されます。  
  
 項目を追加するには、リスト ボックスに[`LB_ADDSTRING`メッセージ](/windows/desktop/Controls/lb-addstring)を送信します。 アイテムを削除するには、[`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel)送信して現在の選択範囲のインデックスを取得し[`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring)、アイテムを削除します。 また、サンプルは[`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)を送信し、返された値を使用して、アイテム数を示す表示を更新します。 これらの両方のインスタンスは[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)、前のセクションで説明した PInvoke 宣言のいずれかを使用します。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 ユーザーが項目を選択するか、その選択を変更すると、コントロールはホスト ウィンドウに[`WM_COMMAND`メッセージ](/windows/desktop/menurc/wm-command)を送信して、ページのイベントを<xref:System.Windows.Interop.HwndHost.MessageHook>発生させます。 ハンドラーは、ホスト ウィンドウのメイン ウィンドウ プロシージャと同じ情報を受け取ります。 また、ブール値への参照も渡`handled`します。 メッセージ`true`を`handled`処理し、それ以上の処理は必要なく、を示すように設定します。  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)はさまざまな理由で送信されるため、通知 ID を調べて、処理するイベントかどうかを判断する必要があります。 ID は、パラメーターの上位ワードに`wParam`含まれています。 このサンプルでは、ビットごとの演算子を使用して ID を抽出します。 ユーザーが選択を行ったか、または変更した場合、ID[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)は になります。  
  
 受信[`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)すると、サンプルはコントロールに[`LB_GETCURSEL`メッセージ](/windows/desktop/Controls/lb-getcursel)を送信することによって、選択された項目のインデックスを取得します。 テキストを取得するには、まず<xref:System.Text.StringBuilder>. その後、コントロールに[`LB_GETTEXT`メッセージ](/windows/desktop/Controls/lb-gettext)を送信します。 `wParam`空<xref:System.Text.StringBuilder>のオブジェクトをパラメーターとして渡します。 戻[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)り値<xref:System.Text.StringBuilder>が返されると、 は選択された項目のテキストを格納します。 この使用には[`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage)、さらに別の PInvoke 宣言が必要です。  
  
 最後に`true`、`handled`メッセージが処理されたことを示すように設定します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.HwndHost>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
