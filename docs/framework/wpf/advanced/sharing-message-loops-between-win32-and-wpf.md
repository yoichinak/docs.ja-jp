---
title: Win32 と WPF 間でのメッセージ ループの共有
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 74055ec3facb7db9145c4c0e969d57da24eccbc8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115077"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Win32 と WPF 間でのメッセージ ループの共有
このトピックとの相互運用のメッセージ ループを実装する方法を説明します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、既存を使用していずれかのメッセージ ループ危険にさらされる<xref:System.Windows.Threading.Dispatcher>またはで個別のメッセージ ループを作成して、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]の相互運用コード側。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher とメッセージ ループ  
 相互運用性とキーボード イベントのサポートの通常のシナリオは、実装する<xref:System.Windows.Interop.IKeyboardInputSink>、または既にを実装するクラスからサブクラスに<xref:System.Windows.Interop.IKeyboardInputSink>など<xref:System.Windows.Interop.HwndSource>または<xref:System.Windows.Interop.HwndHost>します。 しかし、キーボード シンクのサポートは、相互運用の境界を越えてメッセージを送受信するときにする必要がありますすべてのメッセージ ループの要件を解決していません。 アプリケーション メッセージ ループのアーキテクチャを形式化する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供、<xref:System.Windows.Interop.ComponentDispatcher>クラスは、メッセージ ループを次の単純なプロトコルを定義します。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 静的クラスで公開されるいくつかのメンバーです。 各メソッドのスコープは暗黙的に呼び出し元のスレッドに関連付けられています。 メッセージ ループは、その中の一部を呼び出す必要があります[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)](として、次のセクションで定義) の重要な場面でします。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> (キーボード シンク) などの他のコンポーネントがリッスンできるイベントを提供します。 <xref:System.Windows.Threading.Dispatcher>クラスが呼び出す、すべての適切な<xref:System.Windows.Interop.ComponentDispatcher>適切なシーケンス内のメソッド。 コードが通話を担当は、独自のメッセージ ループを実装する場合<xref:System.Windows.Interop.ComponentDispatcher>同様の方法でメソッド。  
  
 呼び出す<xref:System.Windows.Interop.ComponentDispatcher>スレッド上のメソッドはそのスレッドで登録されたイベント ハンドラーを呼び出すだけです。  
  
## <a name="writing-message-loops"></a>メッセージ ループの記述  
 次のチェックリストは、<xref:System.Windows.Interop.ComponentDispatcher>独自のメッセージ ループを記述する場合に使用するメンバー。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: メッセージ ループは、このスレッドがモーダルであることを示すを呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>:、メッセージ ループには、これを、スレッドが nonmodal を元に戻ることを示すために呼び出す必要があります。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>:、メッセージ ループには、このことを示すために呼び出す必要があります<xref:System.Windows.Interop.ComponentDispatcher>を発生させる、<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>イベント。 <xref:System.Windows.Interop.ComponentDispatcher> 発生しません<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>場合<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>は`true`、メッセージ ループ呼び出しすることもできますが、<xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>場合でも<xref:System.Windows.Interop.ComponentDispatcher>モーダルの状態のときにそれに応答できません。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: メッセージ ループは、この新しいメッセージが使用できることを示すを呼び出す必要があります。 戻り値を示しますリスナーがあるかどうかを<xref:System.Windows.Interop.ComponentDispatcher>イベントは、メッセージを処理します。 場合<xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>返します`true`(処理)、ディスパッチャーは何もさらに、メッセージを使用します。 場合は、戻り値は`false`、ディスパッチャーの呼び出しが想定されて、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]関数`TranslateMessage`、呼び出して`DispatchMessage`します。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>ComponentDispatcher を使用して、既存のメッセージの処理  
 次のチェックリストは、<xref:System.Windows.Interop.ComponentDispatcher>固有に依存する場合に使用するメンバー[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージ ループします。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: アプリケーションをモーダルになったかどうかを返します (モーダルのメッセージ ループのプッシュなど)。 <xref:System.Windows.Interop.ComponentDispatcher> クラスの数を保持しているために、この状態を追跡できます<xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>と<xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>メッセージ ループからの呼び出し。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>イベント デリゲートの呼び出しの標準的な規則に従います。 デリゲートが不特定の順序で呼び出され、処理済みとして、1 つ目は、メッセージをマークする場合でも、すべてのデリゲートが呼び出されます。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: アイドル処理を行う、適切かつ効率的な時間を示します (その他の保留中のスレッドのメッセージはありません)。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 発生しませんスレッドがモーダルの場合。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: メッセージ ポンプを処理するすべてのメッセージに対して発生します。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: 中に処理されていないすべてのメッセージに対して発生<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>します。  
  
 メッセージと見なされます後の処理済みの場合、<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>イベントまたは<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>イベント、`handled`イベント データの参照によって渡されたパラメーターが`true`します。 場合、イベント ハンドラーは、メッセージを無視する必要があります`handled`は`true`別のハンドラーが最初に、メッセージを処理するため、します。 両方のイベントをイベント ハンドラーは、メッセージを変更することができます。 変更されたメッセージと元変更されていないメッセージではなく、ディスパッチャーのディスパッチする必要があります。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> すべてのリスナーがアーキテクチャの目的に配信を対象となるメッセージがメッセージへの応答内のコードを呼び出す必要がある HWND を含むトップレベルのウィンドウのみです。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource が ComponentDispatcher イベントを処理する方法  
 場合、 <xref:System.Windows.Interop.HwndSource> (親なし HWND)、トップレベル ウィンドウが登録されます<xref:System.Windows.Interop.ComponentDispatcher>します。 場合<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>が発生するとのメッセージを使用する場合、<xref:System.Windows.Interop.HwndSource>または子ウィンドウ、<xref:System.Windows.Interop.HwndSource>呼び出しその<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>、 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>キーボード シンクのシーケンス。  
  
 場合、<xref:System.Windows.Interop.HwndSource>がトップレベル ウィンドウ (HWND を親がある)、処理ことはありません。 処理を行う最上位レベルのウィンドウのみが必要ですし、任意の相互運用シナリオの一部として上位レベルのウィンドウでキーボード シンクのサポートを有効にする予定ですがあります。  
  
 場合<xref:System.Windows.Interop.HwndHost.WndProc%2A>上、<xref:System.Windows.Interop.HwndSource>呼びますしなくても最初に呼び出されている、適切なキーボード シンク メソッドでは、アプリケーションが受信より高いレベルのキーボード イベントなど<xref:System.Windows.UIElement.KeyDown>。 ただし、キーボード シンク メソッドが呼び出されますなし、アクセス キーのサポートなどの望ましいキーボード入力モデル機能を回避します。 メッセージ ループでは正常に関連するスレッド上に通知されないしなかった可能性があります、 <xref:System.Windows.Interop.ComponentDispatcher>、または親 HWND には、適切なキーボード シンクの応答を呼び出しませんでした。  
  
 使用してそのメッセージ フックを追加した場合、キーボード シンクに移動するメッセージを HWND に送信しない場合があります、<xref:System.Windows.Interop.HwndSource.AddHook%2A>メソッド。 直接および not に送信されたメッセージ ポンプ レベルでメッセージが処理される可能性がありますが、`DispatchMessage`関数。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF と Win32 の相互運用性](wpf-and-win32-interoperation.md)
- [スレッド モデル](threading-model.md)
- [入力の概要](input-overview.md)
