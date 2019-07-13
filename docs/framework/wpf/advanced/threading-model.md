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
ms.openlocfilehash: c74d76cf7c216ed1d4d5c0741ed0ca4f651543e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598632"
---
# <a name="threading-model"></a>スレッド モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] スレッド処理の難しさから開発者を保存する設計されています。 その結果、ほとんどの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開発者は、複数のスレッドを使用するインターフェイスを記述する必要はありません。 マルチ スレッド プログラムは複雑になり、デバッグが困難であるため、シングル スレッドのソリューションが存在する場合、回避する必要があります。  
  
 関係なくどの程度設計、ただし、いいえ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]framework はすべての種類の問題に対してシングル スレッドのソリューションを提供できるようことになります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複数のスレッドを向上させるような状況はまだあります[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]応答性またはアプリケーションのパフォーマンス。 いくつかの背景情報を紹介した後は、このホワイト ペーパーは、このような状況のいくつか解説し、最後にいくつかの下位レベルの詳細の詳細についてはします。  

> [!NOTE]
>  このトピックでは、スレッドを使用して、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>メソッドの非同期呼び出し。 呼び出すことによって、非同期呼び出しを作成することも、<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>メソッドで、実行、<xref:System.Action>または<xref:System.Func%601>をパラメーターとして。  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>メソッドを返します。 を<xref:System.Windows.Threading.DispatcherOperation>または<xref:System.Windows.Threading.DispatcherOperation%601>、を持つ、<xref:System.Windows.Threading.DispatcherOperation.Task%2A>プロパティ。 使用することができます、`await`でいずれかのキーワード、<xref:System.Windows.Threading.DispatcherOperation>または関連付けられた<xref:System.Threading.Tasks.Task>します。 <xref:System.Threading.Tasks.Task> または <xref:System.Windows.Threading.DispatcherOperation> によって返される <xref:System.Windows.Threading.DispatcherOperation%601> を同期的に待機する必要がある場合、<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 拡張メソッドを呼び出します。  呼び出す<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>デッドロックが発生します。 使用しての詳細については、<xref:System.Threading.Tasks.Task>非同期操作を実行するタスクの並列化を参照してください。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>メソッドがありますを受け取るオーバー ロードを<xref:System.Action>または<xref:System.Func%601>をパラメーターとして。  使用することができます、 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 、デリゲートを渡すことで同期させるメソッドを呼び出します<xref:System.Action>または<xref:System.Func%601>します。  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>概要と、ディスパッチャー  
 通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、2 つのスレッドで開始: レンダリングおよび管理用に別の処理の 1 つ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 レンダリング スレッドが効率的に実行中にバック グラウンドで非表示、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの入力を受け取り、イベントを処理、画面を描画およびアプリケーション コードを実行します。 ほとんどのアプリケーションは、1 つを使用して[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド、いくつかの状況ではいくつかの使用を推奨します。 この例を使用して後で説明します。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド キューの作業と呼ばれるオブジェクト内の項目を<xref:System.Windows.Threading.Dispatcher>します。 <xref:System.Windows.Threading.Dispatcher> は作業項目を優先順位に従って選択し、それぞれを最後まで実行します。  すべて[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが少なくとも 1 つあります<xref:System.Windows.Threading.Dispatcher>、および各<xref:System.Windows.Threading.Dispatcher>正確に 1 つのスレッドで作業項目を実行することができます。  
  
 最大化するの応答性の高い、使いやすいアプリケーションを構築することが重要です、<xref:System.Windows.Threading.Dispatcher>小さな作業項目を保持することでスループット。 により、この項目は決して内に留まっている古い取得、<xref:System.Windows.Threading.Dispatcher>キュー処理を待機しています。 ユーザーが入力と応答の間に遅延のストレスを感じることができます。  
  
 どのようにして[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが大規模な操作を処理するべきでしょうか。 場合、コードを使用するか、大量の計算は、または、いくつかのリモート サーバー上のデータベースのクエリを実行する必要がありますか。 大きなまま、別のスレッドで操作を処理するために、応答が通常は、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド内の項目になる傾向に無料、<xref:System.Windows.Threading.Dispatcher>キュー。 大規模な操作が完了したら、その結果を報告できるに戻す、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のスレッドを表示します。  
  
 従来、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]により[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素を作成したスレッドからのみアクセスします。 これは意味が完了したら、いくつかの実行時間の長いタスクを担当のバック グラウンド スレッドにテキスト ボックスを更新できません。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 整合性を確保[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コンポーネント。 奇妙なは、その内容は、描画中にバック グラウンド スレッドによって更新された場合、リスト ボックスになります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] この調整を適用する組み込みの相互排他メカニズムを持っていません。 ほとんどのクラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から派生<xref:System.Windows.Threading.DispatcherObject>します。 構築時に、<xref:System.Windows.Threading.DispatcherObject>への参照を格納、<xref:System.Windows.Threading.Dispatcher>現在実行中のスレッドにリンクさせます。 実際には、<xref:System.Windows.Threading.DispatcherObject>作成したスレッドを関連付けます。 プログラムの実行中に、<xref:System.Windows.Threading.DispatcherObject>そのパブリックを呼び出すことができます<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>メソッド。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 調べ、 <xref:System.Windows.Threading.Dispatcher> 、現在のスレッドに関連付けられているし、比較する、<xref:System.Windows.Threading.Dispatcher>構築時に格納されている参照。 一致しない場合<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>例外をスローします。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 属するすべてのメソッドの先頭に呼び出すためのものが、<xref:System.Windows.Threading.DispatcherObject>します。  
  
 1 つのスレッドを変更することができますのみの場合、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、方法はバック グラウンド スレッドと対話するユーザーですか? バック グラウンド スレッドを問い合わせることができる、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の代わりに操作を実行するスレッド。 これは作業項目を登録することによって、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 <xref:System.Windows.Threading.Dispatcher>クラスには作業項目を登録するための 2 つのメソッド:<xref:System.Windows.Threading.Dispatcher.Invoke%2A>と<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>します。 どちらの方法では、デリゲートの実行をスケジュールします。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> – 同期呼び出しは、つまりまで返されません、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが実際にデリゲートの実行を終了します。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 非同期し、すぐに返します。  
  
 <xref:System.Windows.Threading.Dispatcher>優先順位によってキューに要素を並べ替えます。 挿入される要素を追加するときに指定できる 10 のレベルがある、<xref:System.Windows.Threading.Dispatcher>キュー。 これらの優先順位が保持されます、<xref:System.Windows.Threading.DispatcherPriority>列挙体。 に関する詳細情報<xref:System.Windows.Threading.DispatcherPriority>で見つかるレベル、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]ドキュメント。  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>スレッドの動作:サンプルは、  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>実行時間の長い計算で、シングル スレッド アプリケーション  
 ほとんど[!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)]大部分のユーザーの操作への応答で生成されるイベントの待機中にアイドル時間を費やしています。 慎重なプログラミング アイドル時間使用できます、建設的の応答性に影響を与えず、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で起こっているか、操作を中断する入力を許可しないスレッド モデル、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 つまりに戻ることを確認する必要があります、<xref:System.Windows.Threading.Dispatcher>入力イベントに古くなる前に保留中のプロセスを定期的にします。  
  
 次に例を示します。  
  
 ![素数のスレッドを示すスクリーン ショット。](./media/threading-model/threading-prime-numbers.png)  
  
 この単純なアプリケーションは、素数を検索して 3 から上方向にカウントされます。 ユーザーがクリックすると、**開始**ボタン、検索を開始します。 プログラムでは、素数を検出すると、その探索でユーザー インターフェイスを更新します。 任意の時点では、ユーザーは、検索を停止できます。  
  
 単純なので、いくつかの問題を表示します。 永続的な素数の検索でした移動します。  ボタンの click イベント ハンドラー内で検索全体を処理した場合は与えられません、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが他のイベントを処理します。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]入力またはプロセスに応答することはできませんメッセージ。 再描画し、ボタンのクリックに応答しません。  
  
 個別のスレッドでの素数の検索を行っていますでしたが、同期の問題に対処する必要がありますが、します。 シングル スレッドのアプローチでは、検出された最大の素数を一覧表示するラベルを直接更新できます。  
  
 定期的に戻る場合は、タスクを管理しやすいチャンクに計算を破ることができます、<xref:System.Windows.Threading.Dispatcher>およびイベントを処理します。 与えられる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を再描画して入力を処理します。  
  
 計算とイベント処理の間の処理時間を分割する最善の方法がから計算を管理するには、<xref:System.Windows.Threading.Dispatcher>します。 使用して、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>メソッド内の素数のチェックをスケジュール同じキューを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]からイベントが描画されます。 この例では、一度に 1 つの素数のチェックのみをスケジュールします。 素数のチェックが完了したら、すぐに [次へ] のチェックをスケジュールします。 このチェックが保留中にした場合のみ続行[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]イベントが処理されました。  
  
 ![ディスパッチャー キューを示すスクリーン ショット。](./media/threading-model/threading-dispatcher-queue.png)  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] スペル チェック、このメカニズムを使用して実現されます。 スペル チェックのアイドル時間を使用してバック グラウンドで行われますが、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 コードを見ていきましょう。  
  
 次の例では、ユーザー インターフェイスを作成する XAML を示します。  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 次の例では、分離コードを示します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 次の例では、イベントのイベント ハンドラー、<xref:System.Windows.Controls.Button>します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 上のテキストを更新するだけでなく、<xref:System.Windows.Controls.Button>へのデリゲートを追加することで、最初の素数のチェックをスケジュールするため、このハンドラーは、<xref:System.Windows.Threading.Dispatcher>キュー。 このイベント ハンドラーには、作業が完了した後、<xref:System.Windows.Threading.Dispatcher>このデリゲートの実行を選択します。  
  
 前に説明したよう<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>は、<xref:System.Windows.Threading.Dispatcher>メンバー デリゲートの実行をスケジュールするために使用します。 この場合は、選択、<xref:System.Windows.Threading.DispatcherPriority.SystemIdle>優先順位。 <xref:System.Windows.Threading.Dispatcher>を処理する重要なイベントがない場合にのみ、このデリゲートは実行されます。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 応答性がチェックの数値よりも重要です。 また、番号のチェックのルーチンを表す新しいデリゲートを渡します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 このメソッドは、[次へ] の数が奇数の素数を確認します。 メソッドを直接更新が素数を場合、 `bigPrime` <xref:System.Windows.Controls.TextBlock>探索を反映するようにします。 これは、計算は、コンポーネントの作成に使用されたものと同じスレッドで発生しているため実行できます。 計算に個別のスレッドを使用して選択したより複雑な同期メカニズムを使用しの更新プログラムを実行する必要が、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 このような状況を次にについて説明します。  
  
 このサンプルの完全なソース コードについては、[実行時間の長い計算のサンプルを使用して、シングル スレッド アプリケーション](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>バック グラウンド スレッドでブロック操作の処理  
 グラフィカル アプリケーションでのブロック操作の処理は難しくなります。 アプリケーションが停止したように表示されるため、イベント ハンドラーからブロック メソッドを呼び出すでしょう。 これらの操作を処理するために別のスレッドを使用しましたと同期する必要があるしたら、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの直接変更できないため、[!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)]ワーカー スレッドから。 使用して<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>にデリゲートを挿入する、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 最終的に、これらのデリゲートを変更する権限を持つ実行は[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。  
  
 この例では、天気予報を取得するリモート プロシージャ コールを模倣します。 この呼び出しを実行する別のワーカー スレッドを使用し、update メソッドのスケジュールを設定、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが完了します。  
  
 ![UI の天気を示すスクリーン ショット。](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 記録する詳細の一部を次に示します。  
  
- ボタンのハンドラーを作成します。  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 このボタンをクリックすると時計の図が表示されしてアニメーション化を開始します。 ボタンを無効にします。 呼び出して、`FetchWeatherFromServer`で新しいスレッドとし、メソッド戻り値が、許可、<xref:System.Windows.Threading.Dispatcher>天気予報を収集するまで待機中にイベントを処理します。  
  
- 天気の取得  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 ネットワーク用のコードでは、実際にこの例では複雑にならないがありません。 代わりに、4 秒間スリープ状態に、新しいスレッドを配置することでネットワーク アクセスの遅延をシミュレートします。 この時点では、元の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドがまだ実行されているとイベントに応答します。 アニメーションの実行と、最小のままに、このメッセージを表示し、最大化するには、ボタンも引き続き機能します。  
  
 元に報告する時間は、遅延が完了したらと、天気予報をランダムに選択したら、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 呼び出しをスケジュールすることによって、これを行って`UpdateUserInterface`で、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのスレッドを使用して<xref:System.Windows.Threading.Dispatcher>します。 このスケジュールされたメソッド呼び出しに天気予報を説明する文字列を渡します。  
  
- 更新します [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 ときに、<xref:System.Windows.Threading.Dispatcher>で、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド時間には、スケジュールされた呼び出しを実行します`UpdateUserInterface`します。 このメソッドは、クロック アニメーションを停止し、天気を表す画像を選択します。 このイメージを表示し、「フェッチ予測」ボタンを復元します。  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>複数の Windows、複数のスレッド  
 いくつか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが複数のトップレベル ウィンドウが必要です。 1 つのスレッドの差し支えありません/<xref:System.Windows.Threading.Dispatcher>も複数のスレッドは複数の windows を管理するための組み合わせの方の操作を行います。 これは、windows の 1 つが、スレッドを独占する可能性がある場合は特に当てはまります。  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] エクスプ ローラーは、この方法で動作します。 新しい各エクスプ ローラー ウィンドウが元のプロセスが属しているが、独立したスレッドの制御下で作成されます。  
  
 使用して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame>コントロール、Web ページを表示します。 単純な簡単に作成できます[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]に置き換えてください。 重要な機能を始めます。 新しいエクスプ ローラー ウィンドウを開くことができます。 ユーザーが、「新しい期間」をクリックするとボタン、個別のスレッドで、ウィンドウのコピーを起動します。 これにより、windows のいずれかで実行時間の長い、またはブロックしている操作は、その他のすべての windows をロックしません。  
  
 実際には、Web ブラウザーのモデルには、独自の複雑なスレッド モデルがあります。 ほとんどの読者にとって馴染み深い必要があるため、これを選択しました。  
  
 次の例では、コードを示します。  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 このコードの次のスレッド セグメントは、最も重要な部分では、このコンテキストです。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 このメソッドが呼び出されます「新しいウィンドウ」ボタンをクリックします。 新しいスレッドを作成し、非同期に開始します。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 このメソッドは、新しいスレッドの開始点です。 このスレッドの制御下で新しいウィンドウを作成します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 自動的に作成、新しい<xref:System.Windows.Threading.Dispatcher>新しいスレッドを管理します。 開始するには、ウィンドウを機能させるために実行する、<xref:System.Windows.Threading.Dispatcher>します。  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>技術的な詳細と障害点  
  
### <a name="writing-components-using-threading"></a>スレッド処理を使用してコンポーネントを記述  
 Microsoft .NET Framework 開発者ガイドには、コンポーネントがそのクライアントに非同期の動作を公開する方法についてのパターンがについて説明します (を参照してください[- イベント ベースの非同期パターンの概要](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md))。 たとえば、パッケージ化したい、`FetchWeatherFromServer`メソッドを再利用可能なノングラフィック コンポーネントにします。 次の標準の Microsoft .NET Framework パターンには、次のようなこれはなります。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` どのように使い分ければなど、バック グラウンド スレッドを作成する前に説明した手法の 1 つ、非同期的に操作を実行する呼び出し元のスレッドをブロックしていません。  
  
 このパターンの最も重要な部分の 1 つを呼び出して、 *MethodName* `Completed`メソッドを呼び出した同じスレッドで、 *MethodName* `Async`で開始するメソッド。 この方法を使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]格納することで非常に簡単<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— しノングラフィック コンポーネントのみに含まれる可能性しますが、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、アプリケーションではなく[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]プログラム。  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext>クラスがこのニーズに対処 — の簡略化されたバージョンとのことを考えてみてください<xref:System.Windows.Threading.Dispatcher>他と連動する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]フレームワークもします。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>ポンプを入れ子になった  
 ない完全にロック可能な場合があります、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 について考えてみましょう、<xref:System.Windows.MessageBox.Show%2A>のメソッド、<xref:System.Windows.MessageBox>クラス。 <xref:System.Windows.MessageBox.Show%2A> [ok] ボタンをクリックするまでを返しません。 対話型にするには、メッセージ ループが必要なウィンドウは、作成ただし。 ユーザーが [ok] をクリックする、待っている間に、元のアプリケーション ウィンドウはユーザー入力に応答しません。 ペイント メッセージを処理するには、ただし、引き続き。 元のウィンドウでは、含まれており、明らかになるときに再描画します。  
  
 ![[Ok] のボタンでメッセージ ボックスのスクリーン ショット](./media/threading-model/threading-message-loop.png)  
  
 一部のスレッドは、メッセージ ボックス ウィンドウを担当する必要があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] だけ、メッセージ ボックス ウィンドウに新しいスレッドを作成できますが、このスレッドは元のウィンドウで無効になっている要素を描画することはできません (前の章の相互排除を思い出してください)。 代わりに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]入れ子になったメッセージ処理システムを使用します。 <xref:System.Windows.Threading.Dispatcher>クラスにはと呼ばれる特殊なメソッドが含まれています<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>、新しいメッセージ ループを開始し、アプリケーションの現在の実行ポイントを格納します。 元の後に実行が再開される入れ子になったメッセージ ループが完了したら、<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>呼び出します。  
  
 この場合、<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>への呼び出しでプログラムのコンテキストを維持<xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>、背景ウィンドウを再描画して、メッセージ ボックス ウィンドウへの入力を処理する新しいメッセージ ループを開始します。 ユーザーは、[ok] をクリックするし、ポップアップ ウィンドウをクリア、入れ子になったループを終了し、コントロールがへの呼び出し後に再開<xref:System.Windows.MessageBox.Show%2A>します。  
  
### <a name="stale-routed-events"></a>古いイベントのルーティング  
 ルーティング イベント システム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベントが発生したときに、ツリー全体を通知します。  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 楕円の上でマウスの左ボタンが押されたときに`handler2`を実行します。 後`handler2`が終了したら、イベントに渡されます、<xref:System.Windows.Controls.Canvas>を使用して、オブジェクト`handler1`これを処理します。 これは、場合にのみに発生`handler2`は明示的にマーク イベント オブジェクトを処理済みとします。  
  
 できますを`handler2`かなりのこのイベントの処理時間がかかります。 `handler2` 使用して<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>時間を返さない入れ子になったメッセージ ループを開始します。 場合`handler2`イベント完了の場合、このメッセージ ループが処理済みとしてマークされませんが、非常に古い場合でも、ツリーをイベントが渡されます。  
  
### <a name="reentrancy-and-locking"></a>再入とロック  
 ロック メカニズム、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]とまったく同じように動作しない 1 つご想像; 期待されるスレッドのロックを要求するときに、操作を完全に停止します。 実際には、スレッドを受信し、優先度の高いメッセージの処理が続行されます。 これにより、デッドロックを回避し、インターフェイスの最小応答が、微妙なバグの可能性が生じます。  についてがまれな状況で何も知る必要はありません時間の大半 (通常は[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ メッセージまたは COM の STA コンポーネント) 価値を知ることができます。  
  
 開発者の作業を前提としているために、ほとんどのインターフェイスはスレッド セーフに注意してくださいでビルドされませんが、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は複数のスレッドからはアクセスできません。 この場合は、1 つのスレッドが、予期しないときに環境変更を行うことがあることで、不正の原因の効果、<xref:System.Windows.Threading.DispatcherObject>相互排他のメカニズムを解決することは想定されています。 次の疑似コードを検討してください。  
  
 ![され、スレッドの再入をダイアグラムします。](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 ほとんどの場合、正しいことですが、時間がある[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]このような予期しない再入本当に問題が発生します。 特定の時間で、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呼び出し<xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>、使用するには、そのスレッドのロックの命令を変更する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ではなく、通常の再入のないロック[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]ロックします。  
  
 では、なぜでした、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]チームは、この動作を選択しますか? COM の STA オブジェクトとファイナライザーのスレッドで実行する必要があります。 オブジェクトがガベージ コレクトされるときにその`Finalize`メソッドがない、専用のファイナライザー スレッドで実行、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 その中に問題があります、オブジェクトの COM の STA で作成された、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]でスレッドを破棄することができますのみ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッド。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]等しく、 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (ここでの Win32 を使用して`SendMessage`)。 しかし、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドがビジー状態、ファイナライザー スレッドが停止し、深刻なメモリ リークが発生、COM の STA オブジェクトを破棄することはできません。 そのため、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]チームは、ロック動作をさせる難しい呼び出しを行った。  
  
 タスクを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]させず、すべての場所で再入をブロックしないため、メモリ リークの予期しない再入を回避するためには。  
  
## <a name="see-also"></a>関連項目

- [実行時間の長い計算のサンプルを使用して、シングル スレッド アプリケーション](https://go.microsoft.com/fwlink/?LinkID=160038)
