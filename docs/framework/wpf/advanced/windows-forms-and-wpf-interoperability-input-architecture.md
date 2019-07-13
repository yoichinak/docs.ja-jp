---
title: Windows フォームと WPF の相互運用性入力アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: 10c3ced3bc69f12c107b8d49139f829fab4e312a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662219"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows フォームと WPF の相互運用性入力アーキテクチャ
間の相互運用、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]両方のテクノロジは、適切なキーボード入力の処理である必要があります。 このトピックでは、これらのテクノロジがキーボードとメッセージ ハイブリッド アプリケーションでのスムーズな相互運用性を有効にする処理を実装する方法について説明します。  
  
 このトピックは、次の内容で構成されています。  
  
- モードレス フォームとダイアログ ボックス  
  
- WindowsFormsHost のキーボードとメッセージの処理  
  
- ElementHost のキーボードとメッセージの処理  
  
## <a name="modeless-forms-and-dialog-boxes"></a>モードレス フォームとダイアログ ボックス  
 呼び出す、<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>メソッドを<xref:System.Windows.Forms.Integration.WindowsFormsHost>からモードレス フォームまたはダイアログ ボックスを開き、要素、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション。  
  
 呼び出す、<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>メソッドを<xref:System.Windows.Forms.Integration.ElementHost>コントロールを開く、モードレス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ページで、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのアプリケーション。  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost のキーボードとメッセージの処理  
 によってホストされている場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーション、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]キーボードとメッセージの処理は、以下で構成します。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスからのメッセージの取得、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]によって実装されるメッセージ ループ、<xref:System.Windows.Interop.ComponentDispatcher>クラス。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラス作成のためのサロゲート[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]通常そのことを確認するメッセージ ループ[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]キーボード処理が行われます。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>クラスが実装する、<xref:System.Windows.Interop.IKeyboardInputSink>とフォーカス管理を調整するためのインターフェイス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールが自身を登録し、メッセージ ループを開始します。  
  
 次のセクションでは、プロセスの詳細のこれらの部分について説明します。  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>WPF のメッセージ ループからのメッセージを取得します。  
 <xref:System.Windows.Interop.ComponentDispatcher>クラスのメッセージ ループ マネージャー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 <xref:System.Windows.Interop.ComponentDispatcher>クラスの外部クライアントにする前にメッセージをフィルター処理を有効にするフックを提供[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]その処理を行います。  
  
 相互運用の実装のハンドル、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>これにより、イベント[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]する前にメッセージを処理するコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
### <a name="surrogate-windows-forms-message-loop"></a>Windows フォームのメッセージ ループをサロゲート  
 既定で、<xref:System.Windows.Forms.Application?displayProperty=nameWithType>クラスには、プライマリ メッセージ ループが含まれています。[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション。 相互運用性、中に、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]メッセージ ループは、メッセージを処理しません。 そのため、このロジックを再現する必要があります。 ハンドラーは、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベントは、次の手順を実行します。  
  
1. 使用してメッセージをフィルター処理、<xref:System.Windows.Forms.IMessageFilter>インターフェイス。  
  
2. 呼び出し、<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>メソッド。  
  
3. 変換し、必要な場合に、メッセージをディスパッチします。  
  
4. その他のコントロールがメッセージを処理しない場合は、ホスト コントロールにメッセージを渡します。  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink 実装  
 サロゲートのメッセージ ループは、キーボードの管理を処理します。 そのため、<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>メソッドは、唯一<xref:System.Windows.Interop.IKeyboardInputSink>の実装を必要とするメンバー、<xref:System.Windows.Forms.Integration.WindowsFormsHost>クラス。  
  
 既定で、<xref:System.Windows.Interop.HwndHost>クラスを返します。`false`のその<xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>実装します。 これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]への制御、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>の実装、<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>メソッドは、次の手順を実行します。  
  
1. 最初の検索または最後[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]に格納されているコントロール、<xref:System.Windows.Forms.Integration.WindowsFormsHost>とコントロールがフォーカスを受け取ることができます。 コントロールの選択肢は、トラバーサルの情報に依存します。  
  
2. コントロールにフォーカスを設定し、返します`true`します。  
  
3. コントロールがフォーカスを受け取ることはありません、返します`false`します。  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost の登録  
 ウィンドウを処理するときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールが作成された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、メッセージ ループの存在を登録する内部の静的メソッドを呼び出します。  
  
 登録時に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは、メッセージ ループを調べます。 メッセージ ループが開始されていない場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベント ハンドラーを作成します。 メッセージ ループを実行すると見なされます、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>イベント ハンドラーがアタッチされています。  
  
 ウィンドウ ハンドルが破棄されるときに、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールは登録から削除します。  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost のキーボードとメッセージの処理  
 によってホストされている場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]キーボードとメッセージの処理は、以下で構成します。  
  
- <xref:System.Windows.Interop.HwndSource>、 <xref:System.Windows.Interop.IKeyboardInputSink>、および<xref:System.Windows.Interop.IKeyboardInputSite>インターフェイスの実装。  
  
- Tab キーによる移動し、方向キー。  
  
- コマンド キーとダイアログ ボックスのキー。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アクセラレータ処理します。  
  
 次に、これらの部分で詳しく説明します。  
  
### <a name="interface-implementations"></a>インターフェイスの実装  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、フォーカスのあるコントロールのウィンドウ ハンドルにキーボード メッセージをルーティングします。 <xref:System.Windows.Forms.Integration.ElementHost>コントロールでホストされている要素にこれらのメッセージがルーティングされます。 これを実現する、<xref:System.Windows.Forms.Integration.ElementHost>コントロールを提供する<xref:System.Windows.Interop.HwndSource>インスタンス。 場合、<xref:System.Windows.Forms.Integration.ElementHost>コントロールにフォーカスが、<xref:System.Windows.Interop.HwndSource>インスタンスにルーティングほとんどのキーボード入力を処理することができるように、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>クラス。  
  
 <xref:System.Windows.Interop.HwndSource>クラスが実装する、<xref:System.Windows.Interop.IKeyboardInputSink>と<xref:System.Windows.Interop.IKeyboardInputSite>インターフェイス。  
  
 キーボードの相互運用は、実装に依存しています、<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>メソッド ハンドル TAB キーを矢印キーでホストされているすべての要素のフォーカスを移動する入力。  
  
### <a name="tabbing-and-arrow-keys"></a>Tab キーと方向キー  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]選択ロジックにマップされて、<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>と<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> タブと矢印を実装するメソッドは、ナビゲーションをキーします。 オーバーライドする、<xref:System.Windows.Forms.Integration.ElementHost.Select%2A>メソッドは、このマッピングを実現します。  
  
### <a name="command-keys-and-dialog-box-keys"></a>コマンド キーとダイアログ ボックスのキー  
 付与する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コマンド キーとダイアログ キーを処理する最初のチャンス[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]に接続されているコマンドの前処理、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>メソッド。 オーバーライドする、<xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType>メソッドは、2 つのテクノロジを接続します。  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>メソッドでは、ホスト型の要素は、WM_KEYDOWN、WM_KEYUP、WM_SYSKEYDOWN、タブ、ENTER、esc キー、および矢印キーなどのコマンド キーを含む WM_SYSKEYUP など、すべてのキー メッセージを処理できます。 送信する重要なメッセージが処理されない場合、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]処理の先祖の階層。  
  
### <a name="accelerator-processing"></a>アクセラレータの処理  
 アクセラレータを正しく処理する[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アクセラレータ処理に接続する必要があります、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>クラス。 さらに、ホストされている要素にすべての WM_CHAR メッセージを正しくルーティングする必要があります。  
  
 既定<xref:System.Windows.Interop.HwndSource>の実装、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>メソッドを返します。 `false`、WM_CHAR メッセージは、次のロジックを使用して処理されます。  
  
- <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType>メソッドをオーバーライドして、ホストされている要素をすべての WM_CHAR メッセージが転送されることを確認します。  
  
- ALT キーが押された場合、メッセージは WM_SYSCHAR です。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 使用してこのメッセージを前処理せず、<xref:System.Windows.Forms.Control.IsInputChar%2A>メソッド。 そのため、<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>メソッドをオーバーライドするクエリ、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>登録済みのアクセラレータの。 登録済みのアクセラレータが見つかった場合<xref:System.Windows.Input.AccessKeyManager>はそれを処理します。  
  
- ALT キーが押されていない場合、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>クラスは、未処理の入力を処理します。 入力が、アクセラレータの場合、<xref:System.Windows.Input.AccessKeyManager>はそれを処理します。 <xref:System.Windows.Input.InputManager.PostProcessInput>イベントが処理されなかった WM_CHAR メッセージを処理します。  
  
 ユーザーは、ALT キーを押すと、アクセラレータの視覚的な手掛かりがフォーム全体に表示されます。 この動作をサポートするためにすべて<xref:System.Windows.Forms.Integration.ElementHost>アクティブなフォーム上のコントロールがコントロールにフォーカスがある、WM_SYSKEYDOWN のメッセージを受信します。  
  
 メッセージの送信にのみ<xref:System.Windows.Forms.Integration.ElementHost>アクティブ フォーム内のコントロール。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [チュートリアル: WPF で Windows フォーム複合コントロールのホスト](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [チュートリアル: Windows フォームでの WPF 複合コントロールをホストしています。](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
