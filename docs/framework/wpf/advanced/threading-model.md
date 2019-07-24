---
title: スレッド モデル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 2667417c5d25821f2fed2101e1d485280e171eab
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400649"
---
# <a name="threading-model"></a>スレッド モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、スレッド処理の難しさから開発者を保存するように設計されています。 その結果、多くの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開発者は、複数のスレッドを使用するインターフェイスを作成する必要がなくなります。 マルチスレッドプログラムは複雑でデバッグが困難なため、シングルスレッドソリューションが存在する場合は回避する必要があります。  
  
 しかし、どのように設計されて[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]いても、どのような種類の問題に対しても、シングルスレッドソリューションを提供できるフレームワークはありません。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]これで終わりですが、複数のスレッドが応答性[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]やアプリケーションのパフォーマンスを向上させる状況もあります。 いくつかの背景情報について説明した後、この記事ではこのような状況をいくつか紹介した後、いくつかの下位レベルの詳細について説明します。  

> [!NOTE]
>  このトピックでは、非同期呼び出し<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>のメソッドを使用したスレッド処理について説明します。 <xref:System.Action>また<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> は<xref:System.Func%601>をパラメーターとして受け取るメソッドを呼び出すことにより、非同期呼び出しを行うこともできます。  メソッドは、プロパティ<xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601>を<xref:System.Windows.Threading.DispatcherOperation.Task%2A>持つまたはを返します。 <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> `await`キーワードは、 <xref:System.Windows.Threading.DispatcherOperation>またはに関連付けられ<xref:System.Threading.Tasks.Task>たで使用できます。 <xref:System.Threading.Tasks.Task> または <xref:System.Windows.Threading.DispatcherOperation> によって返される <xref:System.Windows.Threading.DispatcherOperation%601> を同期的に待機する必要がある場合、<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 拡張メソッドを呼び出します。  を<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>呼び出すと、デッドロックが発生します。 を使用した<xref:System.Threading.Tasks.Task>非同期操作の実行の詳細については、「タスクの並列化」を参照してください。  メソッド<xref:System.Windows.Threading.Dispatcher.Invoke%2A>に<xref:System.Action>は、パラメーターとしてまた<xref:System.Func%601>はを受け取るオーバーロードもあります。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>メソッドを使用して、 <xref:System.Action>デリゲートまたは<xref:System.Func%601>を渡すことによって同期呼び出しを行うことができます。  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>概要とディスパッチャー  
 通常、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは2つのスレッドを使用して起動します。 1 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]つはレンダリングの処理用で、もう1つはの管理用です。 レンダリングスレッドは、スレッドが[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]入力を受け取り、イベントを処理し、画面を描画し、アプリケーションコードを実行している間に、バックグラウンドで非表示で実行されます。 ほとんどのアプリケーションは 1 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]つのスレッドを使用しますが、状況によっては複数のを使用するのが最適です。 これについては、後で例を使って説明します。  
  
 スレッド[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は、と呼ばれるオブジェクト内の作業<xref:System.Windows.Threading.Dispatcher>項目をキューに配置します。 <xref:System.Windows.Threading.Dispatcher> は作業項目を優先順位に従って選択し、それぞれを最後まで実行します。  すべて[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のスレッドには少なくと<xref:System.Windows.Threading.Dispatcher>も1つ<xref:System.Windows.Threading.Dispatcher>のが必要であり、それぞれが1つのスレッドで作業項目を実行できます。  
  
 応答性の高いユーザーフレンドリなアプリケーションを構築するには、 <xref:System.Windows.Threading.Dispatcher>作業項目を小さくしてスループットを最大化します。 このようにすると、処理を待機<xref:System.Windows.Threading.Dispatcher>しているキューに項目が古くなることはありません。 入力と応答の間の perceivable 遅延によって、ユーザーの不満が生じる可能性があります。  
  
 アプリケーションでビッグ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]操作を処理するにはどうすればよいでしょうか。 コードに大きな計算が含まれている場合、またはリモートサーバー上のデータベースに対してクエリを実行する必要がある場合は、どうすればよいでしょうか。 通常は、大きな操作を別のスレッド[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]で処理することで、スレッドを<xref:System.Windows.Threading.Dispatcher>キュー内の項目に対して自由に解放できます。 大規模な操作が完了すると、結果を表示のために[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドに報告できます。  
  
 これまで[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]では、作成したスレッドだけが要素にアクセスできるようになりました。 これは、長時間実行されているタスクを実行するバックグラウンドスレッドが、完了時にテキストボックスを更新できないことを意味します。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]は、コンポーネントの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]整合性を確保するためにこれを行います。 コンテンツが描画中にバックグラウンドスレッドによって更新された場合、リストボックスは奇妙に見える可能性があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、この調整を強制する組み込みの相互排他機構があります。 のほとんどの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラスは<xref:System.Windows.Threading.DispatcherObject>、から派生します。 構築時に、 <xref:System.Windows.Threading.DispatcherObject>は現在実行中の<xref:System.Windows.Threading.Dispatcher>スレッドにリンクされているへの参照を格納します。 実際には、 <xref:System.Windows.Threading.DispatcherObject>は、それを作成するスレッドに関連付けられます。 プログラムの実行中、 <xref:System.Windows.Threading.DispatcherObject>はパブリック<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>メソッドを呼び出すことができます。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>現在の<xref:System.Windows.Threading.Dispatcher>スレッドに関連付けられているを調べ<xref:System.Windows.Threading.Dispatcher> 、構築中に格納されている参照と比較します。 一致しない場合、 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>は例外をスローします。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>は、 <xref:System.Windows.Threading.DispatcherObject>に属するすべてのメソッドの先頭で呼び出されることを意図しています。  
  
 を変更できるのが1つ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のスレッドだけの場合、バックグラウンドスレッドはどのようにしてユーザーと対話しますか。 バックグラウンドスレッドは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドに代わって操作を実行するように要求できます。 これを行うには、作業項目<xref:System.Windows.Threading.Dispatcher>を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのに登録します。 クラス<xref:System.Windows.Threading.Dispatcher>には<xref:System.Windows.Threading.Dispatcher.Invoke%2A> 、作業項目を登録するための<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>2 つのメソッドとが用意されています。 どちらのメソッドも、デリゲートの実行をスケジュールします。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A>は同期呼び出しです。つまり、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが実際にデリゲートの実行を終了するまでは戻りません。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>は非同期で、直ちにを返します。  
  
 は<xref:System.Windows.Threading.Dispatcher> 、優先順位によってキュー内の要素を並べ替えます。 <xref:System.Windows.Threading.Dispatcher>キューに要素を追加するときに指定できるレベルは10個あります。 これらの優先順位は、 <xref:System.Windows.Threading.DispatcherPriority>列挙体に保持されます。 レベルの詳細<xref:System.Windows.Threading.DispatcherPriority>については、の[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]ドキュメントを参照してください。  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>動作中のスレッド:サンプル  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>実行時間の長い計算を含むシングルスレッドアプリケーション  
 多く[!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)]の場合、ユーザーの操作に応じて生成されたイベントを待機している間、時間の大部分が費やされます。 プログラムを注意深くプログラミングすると、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の応答性に影響を与えることなく、このアイドル時間を constructively に使用できます。 スレッド[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]処理モデルでは、入力を使用して[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドで発生する操作を中断することはできません。 これは、保留中の入力イベントが古く<xref:System.Windows.Threading.Dispatcher>なる前に処理するために、定期的にに戻る必要があることを意味します。  
  
 次に例を示します。  
  
 ![素数のスレッド処理を示すスクリーンショット。](./media/threading-model/threading-prime-numbers.png)  
  
 この単純なアプリケーションは、3から昇順にカウントし、素数を検索します。 ユーザーが **[スタート]** ボタンをクリックすると、検索が開始されます。 プログラムが素数を検出すると、ユーザーインターフェイスが検出されて更新されます。 どの時点でも、ユーザーは検索を停止できます。  
  
 非常に単純ですが、素数の検索は永久に発生し、いくつかの問題が発生する可能性があります。  ボタンの click イベントハンドラー内で検索全体を処理した場合、他のイベントを処理する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]機会がスレッドに与えられることはありません。 は[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 、入力メッセージまたは処理メッセージに応答できません。 これは再描画せず、ボタンのクリックに応答することもありません。  
  
 素数の検索は別のスレッドで実行できますが、その場合は同期の問題に対処する必要があります。 シングルスレッド方式では、検出された最大素数を一覧表示するラベルを直接更新できます。  
  
 計算作業を管理しやすいチャンクに分割した場合は、 <xref:System.Windows.Threading.Dispatcher>に定期的に戻り、イベントを処理することができます。 入力を再[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]描画して処理する機会を与えることができます。  
  
 計算とイベント処理の間で処理時間を分割する最善の方法は、 <xref:System.Windows.Threading.Dispatcher>から計算を管理することです。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>メソッドを使用すると、イベントが描画される[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のと同じキューで素数のチェックをスケジュールできます。 この例では、一度に1つの素数チェックのみをスケジュールします。 素数の確認が完了したら、すぐに次のチェックをスケジュールします。 このチェックは、保留中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のイベントが処理された後にのみ実行されます。  
  
 ![ディスパッチャーキューを示すスクリーンショット。](./media/threading-model/threading-dispatcher-queue.png)  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)]このメカニズムを使用してスペルチェックを行います。 スペルチェックは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのアイドル時間を使用してバックグラウンドで実行されます。 コードを見てみましょう。  
  
 次の例は、ユーザーインターフェイスを作成する XAML を示しています。  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 次の例は、分離コードを示しています。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 次の例は、 <xref:System.Windows.Controls.Button>のイベントハンドラーを示しています。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 このハンドラーは、の<xref:System.Windows.Controls.Button>テキストを更新するだけでなく、デリゲートを<xref:System.Windows.Threading.Dispatcher>キューに追加することによって最初の素数チェックをスケジュールします。 このイベントハンドラーが処理を完了した後で<xref:System.Windows.Threading.Dispatcher> 、はこのデリゲートを選択して実行します。  
  
 既に説明した<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>ように<xref:System.Windows.Threading.Dispatcher> 、は、実行のためにデリゲートをスケジュールするために使用されるメンバーです。 この場合は、 <xref:System.Windows.Threading.DispatcherPriority.SystemIdle>優先度を選択します。 は<xref:System.Windows.Threading.Dispatcher> 、処理する重要なイベントがない場合にのみ、このデリゲートを実行します。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]応答性は、数値チェックよりも重要です。 また、数値チェックルーチンを表す新しいデリゲートも渡します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 このメソッドは、次の奇数の値が素数かどうかを確認します。 素数の場合、メソッドは、 `bigPrime` <xref:System.Windows.Controls.TextBlock>その検出を反映するためにを直接更新します。 これは、コンポーネントの作成に使用されたのと同じスレッドで計算が行われているためです。 計算に別のスレッドを使用することを選択した場合は、より複雑な同期機構を使用して、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドで更新を実行する必要があります。 この状況を次に示します。  
  
 このサンプルの完全なソースコードについては、「[実行時間の長い計算サンプルを使用したシングルスレッドアプリケーション](https://go.microsoft.com/fwlink/?LinkID=160038)」を参照してください。  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>バックグラウンドスレッドを使用したブロッキング操作の処理  
 グラフィカルアプリケーションでのブロック操作の処理は困難な場合があります。 アプリケーションがフリーズしているように見えるため、イベントハンドラーからブロックメソッドを呼び出す必要はありません。 これらの操作を処理するために別のスレッドを使用できますが、完了したら、ワーカースレッド[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)]からを直接変更することはできないため、スレッドと同期する必要があります。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A>または<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>を使用して、 <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのにデリゲートを挿入できます。 最終的には、これらのデリゲートは、要素を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]変更するためのアクセス許可を使用して実行されます。  
  
 この例では、天気予報を取得するリモートプロシージャ呼び出しを模倣しています。 この呼び出しを実行するために別のワーカースレッドを使用し、終了時に<xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのに更新メソッドをスケジュールします。  
  
 ![気象 UI を示すスクリーンショット。](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 注意する必要がある詳細の一部を次に示します。  
  
- ボタンハンドラーの作成  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 ボタンがクリックされると、時計の描画が表示され、アニメーション化が開始されます。 このボタンは無効になっています。 新しいスレッドで`FetchWeatherFromServer`メソッドを呼び出し、を返します。これにより、は<xref:System.Windows.Threading.Dispatcher> 、天気予報の収集を待機している間にイベントを処理できるようになります。  
  
- 天気予報  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 単純にするために、この例ではネットワークコードを実際に使用していません。 代わりに、新しいスレッドを4秒間スリープ状態にすることで、ネットワークアクセスの遅延をシミュレートします。 この時点で、元[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のスレッドはまだ実行中で、イベントに応答しています。 これを示すために、アニメーションを実行したままにしておき、[最小化] ボタンと [最大化] ボタンも引き続き機能します。  
  
 遅延が終了し、天気予報をランダムに選択した場合は、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドに報告します。 これを行うには、スレッドの`UpdateUserInterface`を使用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]して、スレッドで<xref:System.Windows.Threading.Dispatcher>の呼び出しをスケジュールします。 このスケジュールされたメソッドの呼び出しに、天気を説明する文字列を渡します。  
  
- を更新する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 スレッド内のに時間がある場合は、の<xref:System.Windows.Threading.Dispatcher>スケジュールされた呼び出しが`UpdateUserInterface`実行されます。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] このメソッドは、クロックアニメーションを停止し、天気を説明する画像を選択します。 このイメージが表示され、"フェッチ予測" ボタンが復元されます。  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>複数のウィンドウ、複数のスレッド  
 アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]によっては、複数のトップレベルウィンドウが必要になる場合があります。 1つのスレッド/<xref:System.Windows.Threading.Dispatcher>組み合わせで複数のウィンドウを管理することは完全に許容されますが、複数のスレッドがより適切なジョブを実行する場合もあります。 これは特に、いずれかのウィンドウがスレッドを独占する可能性がある場合に当てはまります。  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]エクスプローラーでは、この方法で動作します。 新しいエクスプローラーウィンドウはそれぞれ元のプロセスに属していますが、独立したスレッドの制御下に作成されます。  
  
 <xref:System.Windows.Controls.Frame>コントロールを使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]して、Web ページを表示できます。 簡単な[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]代替を簡単に作成できます。 まず、重要な機能である、新しいエクスプローラーウィンドウを開く機能について説明します。 ユーザーが [新しいウィンドウ] ボタンをクリックすると、ウィンドウのコピーが別のスレッドで起動されます。 これにより、windows の1つで実行時間の長い操作またはブロック操作によって、他のウィンドウがすべてロックされることはありません。  
  
 実際には、Web ブラウザーモデルには独自の複雑なスレッドモデルがあります。 これは、ほとんどの閲覧者にとって理解しておく必要があるため、選択しました。  
  
 次の例は、コードを示しています。  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 このコードの次のスレッド処理セグメントは、このコンテキストで最も興味深いものです。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 このメソッドは、[新しいウィンドウ] ボタンがクリックされたときに呼び出されます。 新しいスレッドを作成し、非同期的に開始します。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 このメソッドは、新しいスレッドの開始点です。 このスレッドのコントロールの下に新しいウィンドウを作成します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]新しいを<xref:System.Windows.Threading.Dispatcher>自動的に作成し、新しいスレッドを管理します。 ウィンドウを機能させるには、 <xref:System.Windows.Threading.Dispatcher>を起動するだけで済みます。  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>技術的な詳細とむやみポイント  
  
### <a name="writing-components-using-threading"></a>スレッド処理を使用したコンポーネントの記述  
 Microsoft .NET Framework 開発者ガイドでは、コンポーネントがクライアントに非同期動作を公開する方法のパターンについて説明します (「[イベントベースの非同期パターンの概要](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」を参照してください)。 たとえば、 `FetchWeatherFromServer`メソッドを再利用可能な非グラフィカルコンポーネントにパッケージ化するとします。 標準の Microsoft .NET Framework パターンに従うと、次のようになります。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`バックグラウンドスレッドの作成など、前に説明した手法のいずれかを使用して、非同期的に作業を実行し、呼び出し元のスレッドをブロックしません。  
  
 このパターンの最も重要な部分の1つは、 *methodname* `Async`メソッドを呼び出したのと同じスレッドで*methodname* `Completed`メソッドを呼び出すことです。 これは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を格納<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>することで非常に簡単に行うことができます。ただし、グラフィカルでないコンポーネントは、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または ASP.NET プログラムではなく、アプリケーションで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のみ使用できます。  
  
 クラス<xref:System.Windows.Threading.DispatcherSynchronizationContext>はこのニーズに対応しており、他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のフレームワークで<xref:System.Windows.Threading.Dispatcher>も動作するの簡略化されたバージョンと考えてください。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>入れ子になったポンプ  
 場合によっては、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドを完全にロックすることはできません。 クラスのメソッドに<xref:System.Windows.MessageBox.Show%2A>ついて考えてみましょう。 <xref:System.Windows.MessageBox> <xref:System.Windows.MessageBox.Show%2A>ユーザーが [OK] ボタンをクリックするまでは戻りません。 ただし、対話型にするためにメッセージループが必要なウィンドウを作成します。 ユーザーが [OK] をクリックするのを待機している間、元のアプリケーションウィンドウはユーザー入力に応答しません。 ただし、描画メッセージの処理は続行されます。 元のウィンドウは、カバーされて表示されたときに再描画します。  
  
 ![MessageBox と [OK] ボタンを示すスクリーンショット](./media/threading-model/threading-message-loop.png)  
  
 スレッドによっては、メッセージボックスウィンドウが使用されている必要があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メッセージボックスウィンドウだけに新しいスレッドを作成することもできますが、このスレッドでは、元のウィンドウで無効になっている要素を描画することはできません (前述の相互排他の説明を思い出してください)。 代わりに、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は入れ子になったメッセージ処理システムを使用します。 クラス<xref:System.Windows.Threading.Dispatcher>には、という<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>特殊なメソッドが含まれています。このメソッドは、アプリケーションの現在の実行ポイントを格納し、新しいメッセージループを開始します。 入れ子になったメッセージループが完了すると、元<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>の呼び出しの後に実行が再開されます。  
  
 この場合、は<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>の<xref:System.Windows.MessageBox>呼び出し<xref:System.Windows.MessageBox.Show%2A>でプログラムコンテキストを保持し、新しいメッセージループを開始してバックグラウンドウィンドウを再描画し、メッセージボックスウィンドウへの入力を処理します。 ユーザーが [OK] をクリックしてポップアップウィンドウをクリアすると、入れ子になったループが終了し<xref:System.Windows.MessageBox.Show%2A>、への呼び出しの後で制御が再開されます。  
  
### <a name="stale-routed-events"></a>古いルーティングイベント  
 のルーティングイベントシステムは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、イベントが発生したときにツリー全体に通知します。  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 マウスの左ボタンが楕円上で押されると`handler2` 、が実行されます。 が終了すると、を使用`handler1`して<xref:System.Windows.Controls.Canvas>オブジェクトを処理するオブジェクトにイベントが渡されます。 `handler2` このエラーは、 `handler2`がイベントオブジェクトを処理済みとして明示的にマークしていない場合にのみ発生します。  
  
 このイベントの処理`handler2`には多くの時間がかかる可能性があります。 `handler2`は、 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>を使用して、時間を返さない入れ子になったメッセージループを開始する場合があります。 が`handler2` 、このメッセージループが完了したときにイベントを処理済みとしてマークしていない場合、イベントは非常に古い場合でも、ツリーに渡されます。  
  
### <a name="reentrancy-and-locking"></a>再入とロック  
 共通言語ランタイム (CLR) のロック機構は、まったく同じように動作しません。ロックを要求するときに、スレッドが操作を完全に停止することが予想される場合があります。 実際には、スレッドは、優先度の高いメッセージを受信して処理し続けます。 これにより、デッドロックを防止し、インターフェイスの応答性を最小限にすることができますが、軽度のバグが生じる可能性があります。  ほとんどの場合、この点について知る必要はありませんが、まれな状況 (通常[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]はウィンドウメッセージや COM STA コンポーネントが関係します) では、このことについて理解しておく価値があります。  
  
 多くのインターフェイスは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]が複数のスレッドによってアクセスされることがないという前提で開発者が作業するため、スレッドセーフを考慮して構築されていません。 この場合、1つのスレッドが予期しない時間に環境を変更する可能性があるため<xref:System.Windows.Threading.DispatcherObject> 、相互排他機構が解決されるという不適切な影響が発生する可能性があります。 次の擬似コードを考えてみましょう。  
  
 ![スレッド処理の再入を示す図。](./media/threading-model/threading-reentrancy.png "Threadingreentrancy 入")  
  
 ほとんどの場合、このような予期しない再入に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]よって問題が発生する可能性があります。 そのため、特定のキー回[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で<xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>、はを呼び出します。これにより、通常の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] CLR ロックではなく再入可能なロックを使用するように、そのスレッドのロック命令が変更されます。  
  
 では、CLR チームがこの動作を選択したのはなぜですか。 これは、COM STA オブジェクトと終了スレッドで実行する必要がありました。 オブジェクトがガベージコレクションされると、 `Finalize`そのメソッドは[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドではなく、専用のファイナライザースレッドで実行されます。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド上で作成された COM STA オブジェクトは[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド上でのみ破棄されるため、問題が発生しています。 CLR は、 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (この場合は Win32's `SendMessage`を使用します) に相当します。 しかし、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドがビジーの場合は、ファイナライザースレッドが停止し、COM STA オブジェクトを破棄できないため、深刻なメモリリークが発生します。 そのため、CLR チームは、ロックを機能させるための困難な呼び出しを行っていました。  
  
 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]タスクでは、メモリリークを再導入ずに、予期しない再入を避けることができます。これは、どこでも再入をブロックしないためです。  
  
## <a name="see-also"></a>関連項目

- [実行時間の長い計算サンプルを使用したシングルスレッドアプリケーション](https://go.microsoft.com/fwlink/?LinkID=160038)
