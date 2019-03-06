---
title: 'チュートリアル: WPF の Win32 コントロールのホスト'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 1bb5def111aad850a5f74afaba352394ac2587e9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377405"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>チュートリアル: WPF の Win32 コントロールのホスト
Windows Presentation Foundation (WPF) は、アプリケーションを作成するための豊富な環境を提供します。 ただし、Win32 コードのかなりの投資を存在する場合があります、少なくともいくつ再利用するより効果的なが、WPF アプリケーションでのコードではなく完全に書き換えます。 WPF には、WPF ページ上の Win32 ウィンドウをホストするための簡単なメカニズムが用意されています。  
  
 このトピックで説明するアプリケーション、 [WPF のサンプルでの Win32 ListBox コントロールをホストしている](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)Win32 のリスト ボックス コントロールがホストされます。 この一般的な手順は、すべての Win32 ウィンドウのホスティングに拡張できます。  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>必要条件  
 このトピックでは、WPF と Win32 の両方のプログラミングの基礎知識を前提とします。 WPF プログラミングに基本的な概要については、次を参照してください。 [Getting Started](../getting-started/index.md)します。 Win32 のプログラミングの概要についてを参照すること、この主題に関する数多くの書籍の特に*プログラミング Windows* Charles Petzold 著。  
  
 このトピックに付属するサンプルがで実装されているためC#、Win32 API にアクセスするプラットフォーム呼び出しサービス (PInvoke) の使用します。 PInvoke の知識は役立ちますが、必須ではありませんが。  
  
> [!NOTE]
>  このトピックには、関連するサンプルからのコード例の数が含まれます。 しかし、読みやすくするため、完全なサンプル コードは含まれていません。 取得するか、完全なコードを閲覧[WPF のサンプルでの Win32 ListBox コントロールをホストしている](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)します。  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>基本手順  
 このセクションでは、WPF ページ上の Win32 ウィンドウをホストするための基本的な手順について説明します。 残りのセクションでは、各手順の詳細を実行します。  
  
 基本的なホスティング手順です。  
  
1.  ウィンドウをホストする WPF ページを実装します。 1 つの方法は、<xref:System.Windows.Controls.Border>にホストされたウィンドウのページのセクションを予約する要素。  
  
2.  継承するコントロールをホストするクラスを実装する<xref:System.Windows.Interop.HwndHost>します。  
  
3.  そのクラスでオーバーライド、<xref:System.Windows.Interop.HwndHost>クラス メンバー<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>します。  
  
4.  WPF ページを含むウィンドウの子としてホストされたウィンドウを作成します。 従来の WPF プログラミングが明示的に作成する必要はありませんが、それを使用して、ホスティング ページは、ウィンドウ ハンドル (HWND) を使用します。 ページの HWND を受け取るを通じて、`hwndParent`のパラメーター、<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>メソッド。 この HWND の子としてホストされたウィンドウを作成する必要があります。  
  
5.  ホスト ウィンドウを作成した後は、ホストされたウィンドウの HWND を返します。 1 つまたは複数の Win32 コントロールをホストする場合を通常 HWND の子としてホスト ウィンドウを作成してそのホスト ウィンドウのコントロールの子。 ホスト ウィンドウで、コントロールをラップするには、HWND の境界にまたがっていくつか特定の Win32 問題の通知を処理する、コントロールから通知を受け取る WPF ページの簡単な方法が提供します。  
  
6.  子コントロールからの通知など、ホスト ウィンドウに送信される選択したメッセージを処理します。 これには、2 つの方法があります。  
  
    -   ホストするクラスでのメッセージを処理する場合は、オーバーライド、<xref:System.Windows.Interop.HwndHost.WndProc%2A>のメソッド、<xref:System.Windows.Interop.HwndHost>クラス。  
  
    -   WPF のメッセージを処理、処理を行う場合、<xref:System.Windows.Interop.HwndHost>クラス<xref:System.Windows.Interop.HwndHost.MessageHook>分離コードでイベント。 このイベントは、ホストされたウィンドウで受信されるすべてのメッセージに対して発生します。 まだをオーバーライドする必要がある場合、このオプションを選択すると、 <xref:System.Windows.Interop.HwndHost.WndProc%2A>、最小限の実装のみ必要しますが、あります。  
  
7.  上書き、<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>と<xref:System.Windows.Interop.HwndHost.WndProc%2A>メソッドの<xref:System.Windows.Interop.HwndHost>します。 満たすためにこれらのメソッドをオーバーライドする必要があります、<xref:System.Windows.Interop.HwndHost>コントラクトが最小限の実装を提供する必要がありますのみです。  
  
8.  分離コード ファイルで、コントロール ホスト クラスのインスタンスを作成しの子、<xref:System.Windows.Controls.Border>ウィンドウをホストするためのものでは、要素。  
  
9. 送信することで、ホストされたウィンドウとの通信[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]メッセージとコントロールによる通知の送信など、その子ウィンドウからメッセージを処理します。  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>ページ レイアウトを実装します。  
 ListBox コントロールをホストする WPF ページのレイアウトは、2 つのリージョンで構成されます。 ページの左側にあるホストを提供するいくつかの WPF コントロールを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]Win32 コントロールを操作することができます。 ページの右上隅では、ホストされている ListBox コントロールの正方形の領域を持ちます。  
  
 このレイアウトを実装するコードは簡単です。 ルート要素は、<xref:System.Windows.Controls.DockPanel>を持つ 2 つの子要素。 1 つは、 <xref:System.Windows.Controls.Border> ListBox コントロールをホストする要素。 200 x 200 正方形インチのページの右上隅を占有します。 2 つ目は、<xref:System.Windows.Controls.StackPanel>相互運用性のプロパティを公開する一連の情報を表示し、設定して、ListBox コントロールを操作する WPF コントロールを含む要素。 各要素の子である、<xref:System.Windows.Controls.StackPanel>の詳細については、これらの要素とは何かがどのように使用するさまざまな要素のリファレンスを参照してください、、これらは次のサンプル コードに表示がされません (基本的な以下の説明。相互運用のモデルは、これらのいずれかにも必要ありません、提供されるサンプルをいくつかの対話機能を追加する)。  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Microsoft Win32 コントロールをホストするクラスを実装します。  
 このサンプルのコアは、実際には、コントロール、ControlHost.cs をホストするクラスです。 継承<xref:System.Windows.Interop.HwndHost>します。 コンス トラクターは 2 つのパラメーター、高さと幅、高さと幅に対応する、 <xref:System.Windows.Controls.Border> ListBox コントロールをホストする要素。 コントロールの一致項目のサイズを確実にこれらの値は後で使用されて、<xref:System.Windows.Controls.Border>要素。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 定数のセットもします。 これらの定数は大きく Winuser.h からのものし、Win32 関数を呼び出すときに、従来の名前を使用すること。  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Microsoft Win32 ウィンドウを作成する BuildWindowCore をオーバーライドします。  
 Win32 ウィンドウ、ページによってホストされると、ウィンドウと、ページ間の接続を作成するには、このメソッドをオーバーライドするとします。 このサンプルでは、ListBox コントロールのホストは、2 つのウィンドウが作成されます。 最初は、WPF ページによって実際にホストされているウィンドウです。 ListBox コントロールは、そのウィンドウの子として作成されます。  
  
 このアプローチの理由は、コントロールから通知を受信プロセスが簡略化です。 <xref:System.Windows.Interop.HwndHost>クラスを使用してそれをホストしているウィンドウに送信されるメッセージを処理できます。 Win32 ホストを直接制御する場合は、コントロールの内部メッセージ ループに送信されるメッセージが表示されます。 メッセージを送信、コントロールを表示できますが、コントロールの親ウィンドウに送信される通知は表示されません。 この、特に、ことがないということ、ユーザーがコントロールと対話するときの検出方法です。 代わりに、ホスト ウィンドウを作成し、そのウィンドウの子コントロールを作成します。 これにより、コントロールによって送信された通知など、ホスト ウィンドウのメッセージを処理することができます。 便宜上、ホスト ウィンドウは少し上回る、コントロールの単純なラッパーであるため、パッケージは参照に ListBox コントロールとして。  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>ホスト ウィンドウとリスト ボックス コントロールを作成します。  
 PInvoke を使用して、ウィンドウ クラスの登録を作成してコントロールのホスト ウィンドウを作成して、具合ことができます。 ただし、はるかに簡単な方法は、定義済みの「静的」ウィンドウ クラスを使用してウィンドウを作成します。 これにより、ウィンドウ プロシージャし、コントロールから通知を受信するために必要最小限のコーディングが必要です。  
  
 コントロールの HWND は、ホスト ページを使用すると、コントロールにメッセージを送信使用できるように、読み取り専用プロパティを通じて公開されます。  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox コントロールは、ホスト ウィンドウの子として作成されます。 両方のウィンドウの幅と高さは、前に説明した、コンス トラクターに渡される値に設定されます。 これにより、ホスト ウィンドウとコントロールのサイズは、ページ上の予約済み領域と同じです。  サンプルを返します、windows が作成された後、<xref:System.Runtime.InteropServices.HandleRef>ホスト ウィンドウの HWND を含むオブジェクト。  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>実装 DestroyWindow と WndProc  
 ほかに<xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>、オーバーライドすることも必要があります、<xref:System.Windows.Interop.HwndHost.WndProc%2A>と<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>のメソッド、<xref:System.Windows.Interop.HwndHost>します。 によって、この例では、コントロールのメッセージの処理、<xref:System.Windows.Interop.HwndHost.MessageHook>ハンドラーの実装ではそのため<xref:System.Windows.Interop.HwndHost.WndProc%2A>と<xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>は最小限です。 場合に<xref:System.Windows.Interop.HwndHost.WndProc%2A>設定`handled`に`false`をメッセージが処理されないことを示す 0 を返します。 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>、単にウィンドウを破棄します。  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>ページ上のコントロールをホストします。  
 新しいインスタンスの作成最初のページへのコントロールをホストする、`ControlHost`クラス。 コントロールを含む border 要素の幅と高さを渡します (`ControlHostElement`) に、`ControlHost`コンス トラクター。 これにより、リスト ボックスのサイズが正しくなります。 割り当てることで、ページ上のコントロールをホストする、`ControlHost`オブジェクトを<xref:System.Windows.Controls.Decorator.Child%2A>ホストのプロパティ<xref:System.Windows.Controls.Border>します。  
  
 サンプルにはハンドラーを<xref:System.Windows.Interop.HwndHost.MessageHook>のイベント、`ControlHost`コントロールからメッセージを受信します。 このイベントは、ホストされたウィンドウに送信されるすべてのメッセージに対して発生します。 ここでは、これらは、コントロールからの通知など、実際の ListBox コントロールをラップするウィンドウに送信されるメッセージです。 サンプルでは、コントロールから情報を取得し、その内容を変更する 1 つを呼び出します。 ページが、コントロールと通信する方法の詳細については、次のセクションで説明します。  
  
> [!NOTE]
>  SendMessage の 2 つの PInvoke 宣言があることに注意してください。 これは、1 つを使用しているため、`wParam`文字列と、その他に渡すパラメーターは整数を渡す使用します。 データが正しくマーシャ リングすることを確認するには、各署名の別の宣言する必要があります。  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>コントロールと、ページ間の通信を実装します。  
 Windows メッセージを送信することで、コントロールを操作します。 コントロールは、ユーザーがそのホスト ウィンドウに通知を送信することによってこれと対話するときに通知します。 [WPF での Win32 ListBox コントロールをホストしている](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control)サンプルには、この動作のいくつかの例を提供する UI が用意されています。  
  
-   リストに項目を追加します。  
  
-   一覧から選択した項目を削除します。  
  
-   現在選択されている項目のテキストを表示します。  
  
-   一覧で項目の数を表示します。  
  
 ユーザー選択もできます項目、リスト ボックスをクリックして、従来の Win32 アプリケーションのと同様。 表示されるデータは、項目を追加するかを選択すると、追加すると、によって、ユーザーがリスト ボックスの状態を変更するたびが更新されます。  
  
 項目を追加するリスト ボックスの送信、 [ `LB_ADDSTRING`メッセージ](/windows/desktop/Controls/lb-addstring)します。 項目を削除する送信[ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)現在の選択範囲のインデックスを取得し、 [ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring)アイテムを削除します。 また、サンプルが送信され[ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)、返される値を使用して、項目の数を示す表示を更新するとします。 これら両方のインスタンスの[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)前のセクションで説明されている PInvoke 宣言のいずれかを使用します。  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 ユーザーは、項目を選択するか、その選択を変更、コントロールはホスト ウィンドウを送信することで通知を[`WM_COMMAND`メッセージ](/windows/desktop/menurc/wm-command)を発生させる、<xref:System.Windows.Interop.HwndHost.MessageHook>ページのイベント。 ハンドラーは、ホスト ウィンドウのメイン ウィンドウ プロシージャと同じ情報を受け取ります。 また、ブール値への参照を渡します`handled`します。 設定する`handled`に`true`をメッセージを処理して、それ以上の処理が必要なことを示します。  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) イベントを処理するかどうかを判断する通知 ID を調べる必要がありますので、さまざまな理由から、送信されます。 上位ワードに ID が含まれている、`wParam`パラメーター。 このサンプルでは、ビットごとの演算子を使用して ID を抽出 ユーザーが行われたまたは、自分の選択を変更する場合、ID になります[ `LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)します。  
  
 ときに[ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange)が受信されると、サンプル インデックスを取得、選択した項目のコントロールを送信することによって、 [ `LB_GETCURSEL`メッセージ](/windows/desktop/Controls/lb-getcursel)します。 作成する最初のテキストを取得する、<xref:System.Text.StringBuilder>します。 コントロールを送信、 [ `LB_GETTEXT`メッセージ](/windows/desktop/Controls/lb-gettext)します。 空の渡す<xref:System.Text.StringBuilder>オブジェクトとして、`wParam`パラメーター。 ときに[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)から制御が戻る、<xref:System.Text.StringBuilder>選択された項目のテキストが含まれます。 このように使用[ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage)もう 1 つの PInvoke 宣言が必要です。  
  
 最後に、設定`handled`に`true`をメッセージが処理されたことを示します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Interop.HwndHost>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [チュートリアル: 初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
