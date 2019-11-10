---
title: WPF アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
ms.openlocfilehash: 2ec979240b8fead10522817b77eef23e29409411
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740695"
---
# <a name="wpf-architecture"></a>WPF アーキテクチャ
このトピックでは、Windows Presentation Foundation (WPF) クラス階層のガイドツアーについて説明します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の主なサブシステムの大部分について説明し、それらの相互作用について説明します。 また、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のアーキテクトによって行われたいくつかの選択肢についても詳しく説明します。  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 主要な [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プログラミングモデルは、マネージコードを通じて公開されます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の設計フェーズの初期段階では、システムのマネージコンポーネントとアンマネージコンポーネントの間に行を描画する場所について、いくつかの論争がありました。 CLR には、開発の生産性と堅牢性を高めるさまざまな機能が用意されています (メモリ管理、エラー処理、共通型システムなどを含む) が、コストが発生します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主要なコンポーネントを次の図に示します。 図の赤色のセクション (プレゼンテーションフレームワーク、プレゼンテーションコア、およびミルコア) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の主要なコード部分です。 これらのうちの1つだけがアンマネージコンポーネント–ミルコアです。 ミルコアは、DirectX との緊密な統合を可能にするためにアンマネージコードで記述されています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のすべての表示は DirectX エンジンを介して行われるため、ハードウェアとソフトウェアを効率的にレンダリングできます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] メモリと実行を細かく制御する必要もあります。 密度の高い合成エンジンは、パフォーマンスに大きな影響を与えます。そのため、パフォーマンスを得るためには、CLR の多くの利点が必要です。  
  
 ![.NET Framework 内の WPF の位置。](./media/wpf-architect1.PNG "wpf_architect1")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のマネージ部分とアンマネージ部分の間の通信については、このトピックの後半で説明します。 マネージプログラミングモデルの残りの部分を次に示します。  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のほとんどのオブジェクトは <xref:System.Windows.Threading.DispatcherObject>から派生します。これは、同時実行とスレッド処理を行うための基本的な構造を提供します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ディスパッチャーによって実装されるメッセージングシステムに基づいています。 これは、使い慣れた [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] メッセージポンプとよく似ています。実際、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ディスパッチャーは、スレッド間の呼び出しを実行するために User32.dll メッセージを使用します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] での同時実行については、ディスパッチャーとスレッドアフィニティの2つの主要概念を理解しておく必要があります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の設計フェーズでは、目標は実行の1つのスレッドに移動しましたが、非スレッド "関連付け済み" モデルに移行することでした。 スレッドアフィニティは、コンポーネントが実行中のスレッドの id を使用して何らかの種類の状態を格納するときに発生します。 最も一般的な形式は、スレッドローカルストア (TLS) を使用して状態を格納することです。 スレッドアフィニティでは、実行の各論理スレッドが、オペレーティングシステムの1つの物理スレッドによって所有されている必要があります。これは、メモリを集中的に使用する可能性があります。 最終的には、WPF のスレッドモデルは、スレッドアフィニティを使用したシングルスレッド実行の既存の User32.dll スレッドモデルと同期した状態に保たれます。 これの主な理由は相互運用性でした。 OLE 2.0、クリップボード、Internet Explorer はすべて、シングルスレッドアフィニティ (STA) の実行を必要とします。  
  
 STA スレッドを持つオブジェクトがある場合は、スレッド間で通信を行い、正しいスレッドであることを検証する方法が必要です。 ここでは、ディスパッチャーの役割があります。 ディスパッチャーは、優先順位の高い複数のキューを持つ基本的なメッセージディスパッチシステムです。 メッセージの例としては、未加工の入力通知 (マウス移動)、フレームワーク関数 (レイアウト)、ユーザーコマンド (このメソッドの実行) などがあります。 <xref:System.Windows.Threading.DispatcherObject>から派生することによって、STA の動作を持つ CLR オブジェクトを作成し、作成時にディスパッチャーへのポインターを与えます。  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の構築で使用される主要なアーキテクチャ思想の1つは、メソッドまたはイベントのプロパティを優先することでした。 プロパティは宣言型であり、アクションではなく意図を簡単に指定できます。 また、ユーザーインターフェイスのコンテンツを表示するための、モデル駆動型またはデータ駆動型のシステムもサポートされています。 この哲学には、アプリケーションの動作をより適切に制御するために、バインドできるプロパティを作成することを意図した効果がありました。  
  
 プロパティによってより多くのシステムを使用するためには、CLR が提供するよりも豊富なプロパティシステムが必要でした。 この豊富な例として、変更通知があります。 双方向のバインドを有効にするには、変更通知をサポートするために、バインドの両側が必要です。 プロパティ値に関連付けられた動作を使用するには、プロパティ値が変更されたときに通知を受け取る必要があります。 Microsoft .NET Framework には**INotifyPropertyChange**というインターフェイスがあります。これにより、オブジェクトは変更通知を発行できますが、これは省略可能です。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、<xref:System.Windows.DependencyObject> の型から派生した、豊富なプロパティシステムが用意されています。 プロパティシステムは、プロパティ式間の依存関係を追跡し、依存関係が変更されたときにプロパティ値を自動的に再検証するという、本当に "依存関係" プロパティシステムです。 たとえば、を継承するプロパティ (<xref:System.Windows.Controls.Control.FontSize%2A>など) がある場合、その値を継承する要素の親でプロパティが変更されると、システムは自動的に更新されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プロパティシステムの基礎は、プロパティ式の概念です。 この [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の最初のリリースでは、プロパティ式システムが閉じられており、式はすべてフレームワークの一部として提供されています。 式は、プロパティシステムがデータバインディング、スタイル設定、継承をハードコーディングしていなくても、フレームワーク内の後のレイヤーによって提供されるためです。  
  
 プロパティシステムでは、プロパティ値のスパースストレージも提供されます。 オブジェクトは多数のプロパティを持つことができ、ほとんどの値は既定の状態 (継承、スタイルによる設定など) であるため、オブジェクトのすべてのインスタンスで定義されているすべてのプロパティの完全な重みを持つ必要があるわけではありません。  
  
 プロパティシステムの最後の新機能は、添付プロパティの概念です。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素は、合成とコンポーネントの再利用の原則に基づいて構築されます。 多くの場合、含まれている要素 (<xref:System.Windows.Controls.Grid> レイアウト要素など) は、その動作を制御するために、子要素の追加データを必要とします (行または列の情報など)。 これらのすべてのプロパティをすべての要素に関連付けるのではなく、すべてのオブジェクトで他のオブジェクトのプロパティ定義を提供できます。 これは、JavaScript の "expando" 機能に似ています。  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 システムが定義されている場合、次の手順では画面にピクセルが描画されます。 <xref:System.Windows.Media.Visual> クラスは、ビジュアルオブジェクトのツリーを構築するためにを提供します。各オブジェクトは、必要に応じて、これらの命令 (クリッピング、変換など) のレンダリング方法に関する描画命令とメタデータを含んでいます。 <xref:System.Windows.Media.Visual> は非常に軽量で柔軟性があるように設計されています。そのため、ほとんどの機能はパブリック API を公開せず、保護されたコールバック関数に大きく依存しています。  
  
 <xref:System.Windows.Media.Visual> は、実際には [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンポジションシステムへのエントリポイントです。 <xref:System.Windows.Media.Visual> は、マネージ API とアンマネージドミルコアの2つのサブシステム間の接続ポイントです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ミルコアによって管理されているアンマネージデータ構造を走査することによってデータを表示します。 これらの構造体は、合成ノードと呼ばれ、各ノードでレンダリング命令を含む階層表示ツリーを表します。 次の図の右側に示されているこのツリーは、メッセージングプロトコルを使用してのみアクセスできます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のプログラミング時には、このメッセージングプロトコルを使用して内部でコンポジションツリーに通信する <xref:System.Windows.Media.Visual> の要素と派生型を作成します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 内の各 <xref:System.Windows.Media.Visual> は、1つ、1つ、または複数の合成ノードを作成できます。  
  
 ![Windows Presentation Foundation のビジュアルツリー。](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 ここで注目すべき非常に重要なアーキテクチャの詳細があります。ビジュアルのツリー全体と描画命令がキャッシュされます。 グラフィックス用語では、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は保持されたレンダリングシステムを使用します。 これにより、ユーザーコードへのコールバックでコンポジションシステムがブロックされることなく、高いリフレッシュレートでシステムを再描画できます。 これにより、応答しないアプリケーションの外観を防ぐことができます。  
  
 図には実際にはわかりませんが、実際にはシステムが合成を実行する方法も重要です。  
  
 User32.dll と GDI では、システムはイミディエイトモードのクリッピングシステムで動作します。 コンポーネントをレンダリングする必要がある場合、システムは、コンポーネントがピクセルに触れることができないクリッピングの範囲を確立し、そのボックス内のピクセルを描画するようにコンポーネントに要求します。 このシステムは、メモリの制約付きシステムで非常に適しています。影響を受けるコンポーネントに触れる必要があるのは、1つのピクセルの色に寄与する2つのコンポーネントがないためです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、"塗装のアルゴリズム" の描画モデルを使用します。 これは、各コンポーネントをクリッピングするのではなく、各コンポーネントが画面の前面に戻るように求められることを意味します。 これにより、各コンポーネントで前のコンポーネントの表示を描画できます。 このモデルの利点は、複雑で部分的に透明な図形を持つことができることです。 現在の最新のグラフィックスハードウェアでは、このモデルは比較的高速です (User32.dll/GDI が作成されたときには当てはまりません)。  
  
 前述のように、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の中核となる理念は、より宣言的な "プロパティ中心" のプログラミングモデルに移行することです。 ビジュアルシステムでは、これがいくつかの興味深い場所に表示されます。  
  
 まず、保持モードグラフィックシステムについて考えてみると、これは本当に命令型の DrawLine/DrawLine 型モデルからデータ指向モデル (new Line ()/new Line ()) に移動します。 このデータドリブンレンダリングへの移行により、プロパティを使用して描画命令に対する複雑な操作を表すことができます。 <xref:System.Windows.Media.Drawing> から派生する型は、実際にはレンダリングのためのオブジェクトモデルです。  
  
 次に、アニメーションシステムを評価すると、完全に宣言されていることがわかります。 開発者が次の位置または次の色を計算する必要はなく、アニメーションオブジェクトの一連のプロパティとしてアニメーションを表現できます。 これらのアニメーションは、開発者またはデザイナーの意図を表すことができます (このボタンをここから5秒に移動します)。また、システムは、これを実現するための最も効率的な方法を決定できます。  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> は、レイアウト、入力、イベントなどのコアサブシステムを定義します。  
  
 レイアウトは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]での主要な概念です。 多くのシステムでは、固定されたレイアウトモデルのセットがあります (HTML はレイアウト用に3つのモデル、flow、absolute、テーブル)、またはレイアウトのモデルがありません (User32.dll は絶対配置のみをサポートします)。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、開発者やデザイナーが、命令型ロジックではなくプロパティ値によって駆動される柔軟性のある拡張可能なレイアウトモデルを必要としていることを前提としています。 <xref:System.Windows.UIElement> レベルでは、レイアウトの基本的なコントラクトが導入されます。これは、<xref:System.Windows.UIElement.Measure%2A> と <xref:System.Windows.UIElement.Arrange%2A> 成功を持つ2つのフェーズモデルです。  
  
 <xref:System.Windows.UIElement.Measure%2A> を使用すると、コンポーネントでどの程度のサイズを取得するかを指定できます。 これは、<xref:System.Windows.UIElement.Arrange%2A> とは別のフェーズです。親要素が子に複数回計測して最適な位置とサイズを決定することがあるためです。 親要素が子要素に測定を求めるという事実は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の別の重要な理念としてコンテンツに対するものです。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 内のすべてのコントロールは、そのコンテンツのサイズに合わせてサイズを変更する機能をサポートしています。 これにより、ローカライズがはるかに簡単になり、要素のサイズ変更に合わせて動的なレイアウトを行うことができます。 <xref:System.Windows.UIElement.Arrange%2A> フェーズでは、親が各子の最終的なサイズを配置および決定できます。  
  
 多くの場合、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> および関連オブジェクトの出力側について話します。 しかし、入力側にも非常に多くのイノベーションがあります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の入力モデルの最も基本的な変更は、入力イベントをシステム経由でルーティングするための一貫したモデルです。  
  
 入力は、カーネルモードデバイスドライバーの信号として生成され、Windows カーネルと User32.dll を含む複雑なプロセスを通じて、正しいプロセスとスレッドにルーティングされます。 入力に対応する User32.dll メッセージが [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]にルーティングされると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 未加工の入力メッセージに変換され、ディスパッチャーに送信されます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用すると、未加工の入力イベントを複数の実際のイベントに変換できます。これにより、"MouseEnter" などの機能を、保証された配信によりシステムの低レベルで実装できます。  
  
 各入力イベントは、少なくとも2つのイベント ("preview" イベントと実際のイベント) に変換されます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 内のすべてのイベントには、要素ツリーを通じたルーティングの概念があります。 イベントは、ターゲットからツリーをルートまで走査する場合は "バブル" と呼ばれ、ルートから開始してターゲットを走査する場合は "トンネル" と呼ばれます。 入力プレビューイベントトンネル。ツリー内の任意の要素を有効にして、イベントにフィルターを適用したり、アクションを実行したりすることができます。 通常の (非プレビュー) イベントは、ターゲットからルートまでバブルされます。  
  
 このトンネルとバブルフェーズを分割することにより、キーボードアクセラレータなどの機能の実装が、複合環境で一貫した方法で実行されます。 User32.dll では、サポートするすべてのアクセラレータを含む単一のグローバルテーブルを使用して、キーボードアクセラレータを実装します (Ctrl + N を "New" にマッピングします)。 アプリケーションのディスパッチャーで、 **TranslateAccelerator**を呼び出します。これは、user32.dll の入力メッセージをスニッフィングし、登録されているアクセラレータに一致したかどうかを判断します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、システムが完全に "コンポーザブル" であるため、これは機能しません。すべての要素が任意のキーボードアクセラレータを処理して使用できます。 この2つのフェーズモデルを入力にすると、コンポーネントは独自の "TranslateAccelerator" を実装できます。  
  
 もう1つの手順を実行するために、<xref:System.Windows.UIElement> CommandBindings の概念も紹介します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コマンドシステムを使用すると、開発者は、コマンドエンドポイント (<xref:System.Windows.Input.ICommand>を実装するもの) の観点から機能を定義できます。 コマンドバインドを使用すると、要素で入力ジェスチャ (Ctrl + N) とコマンド (New) の間のマッピングを定義できます。 入力ジェスチャとコマンド定義はどちらも拡張可能であり、使用時に同時に接続することができます。 これにより、たとえば、エンドユーザーがアプリケーション内で使用するキーバインドをカスタマイズできるようにすることが簡単になります。  
  
 トピック「」では、「[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] –プレゼンテーションコアアセンブリに実装されている機能」の「コア」機能に焦点を当てました。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の構築時には、基本要素 (**メジャー**と**配置**によるレイアウトのコントラクトなど) とフレームワークの部分 (<xref:System.Windows.Controls.Grid>などの特定のレイアウトの実装など) の明確な分離が目的の結果でした。 目標は、外部の開発者が必要に応じて独自のフレームワークを作成できるようにする、スタックの拡張ポイントを小さくすることでした。  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> は、2つの異なる方法で確認できます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の下位層で導入されたサブシステムの一連のポリシーとカスタマイズについて説明します。 また、一連の新しいサブシステムも導入されています。  
  
 <xref:System.Windows.FrameworkElement> によって導入される主なポリシーは、アプリケーションのレイアウトに関するものです。 <xref:System.Windows.FrameworkElement> は、<xref:System.Windows.UIElement> によって導入された基本的なレイアウトコントラクトに基づいて構築され、レイアウトの作成者が一貫した一連のプロパティドリブンレイアウトセマンティクスを持つことができるレイアウト "スロット" の概念を追加します。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.MinWidth%2A>、および <xref:System.Windows.FrameworkElement.Margin%2A> のようなプロパティ (いくつかの名前を付ける) は、レイアウトコンテナー内のすべてのコンポーネントが一貫した動作を <xref:System.Windows.FrameworkElement> から派生します。  
  
 また <xref:System.Windows.FrameworkElement> は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のコア層にある多くの機能に対する API の公開を容易にします。 たとえば、<xref:System.Windows.FrameworkElement> は、<xref:System.Windows.FrameworkElement.BeginStoryboard%2A> メソッドを使用してアニメーションへの直接アクセスを提供します。 <xref:System.Windows.Media.Animation.Storyboard> には、一連のプロパティに対して複数のアニメーションをスクリプト化する方法が用意されています。  
  
 <xref:System.Windows.FrameworkElement> が導入する最も重要な2つの点は、データバインディングとスタイルです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のデータバインディングサブシステムは、アプリケーション [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を作成するために [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] または ASP.NET を使用しているすべてのユーザーに対して比較的なじみがある必要があります。 これらの各システムでは、特定の要素の1つ以上のプロパティをデータにバインドすることを簡単に表すことができます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、プロパティのバインド、変換、およびリストバインドを完全にサポートしています。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] でのデータバインディングの最も興味深い機能の1つは、データテンプレートの導入です。 データテンプレートを使用すると、データの一部を視覚化する方法を宣言によって指定できます。 データにバインドできるカスタムユーザーインターフェイスを作成する代わりに、問題を解決して、作成される表示をデータが決定できるようにすることができます。  
  
 スタイル設定は、実際には軽量な形式のデータバインドです。 スタイルを使用すると、共有定義の一連のプロパティを、要素の1つ以上のインスタンスにバインドできます。 スタイルは、明示的な参照によって (<xref:System.Windows.FrameworkElement.Style%2A> プロパティを設定することによって) 要素に適用されるか、またはスタイルを要素の CLR 型に関連付けることによって暗黙的に適用されます。  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 コントロールの最も重要な機能は、テンプレートです。 WPF の合成システムを保持モードのレンダリングシステムと考えている場合、テンプレートを使用すると、コントロールは、パラメーター化された宣言型の方法でレンダリングを記述できます。 <xref:System.Windows.Controls.ControlTemplate> は、子要素のセットを作成するためのスクリプトにすぎず、コントロールによって提供されるプロパティへのバインドが含まれています。  
  
 <xref:System.Windows.Controls.Control> には、いくつかのストックプロパティ、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Padding%2A>が用意されています。これを使用すると、テンプレート作成者はコントロールの表示をカスタマイズできます。 コントロールの実装には、データモデルと相互作用モデルが用意されています。 相互作用モデルは、一連のコマンド (ウィンドウの [閉じる] など) と入力ジェスチャへのバインドを定義します (ウィンドウの上隅の赤い X をクリックするなど)。 データモデルには、相互作用モデルをカスタマイズしたり、(テンプレートによって決定される) 表示をカスタマイズしたりするための一連のプロパティが用意されています。  
  
 これにより、データモデル (プロパティ)、相互作用モデル (コマンドとイベント)、および表示モデル (テンプレート) が分割され、コントロールの外観と動作を完全にカスタマイズできるようになります。  
  
 コントロールのデータモデルの一般的な側面は、コンテンツモデルです。 <xref:System.Windows.Controls.Button>のようなコントロールを表示すると、<xref:System.Object>型の "Content" という名前のプロパティがあることがわかります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] と ASP.NET では、通常、このプロパティは文字列になりますが、ボタンに配置できるコンテンツの種類が制限されます。 ボタンのコンテンツは、単純な文字列、複雑なデータオブジェクト、または要素ツリー全体のいずれかになります。 データオブジェクトの場合は、データテンプレートを使用して表示を作成します。  
  
<a name="Summary"></a>   
## <a name="summary"></a>まとめ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、データ駆動型の動的なプレゼンテーションシステムを作成できるように設計されています。 システムのすべての部分は、動作を駆動するプロパティセットを通じてオブジェクトを作成するように設計されています。 データバインディングはシステムの基本的な部分であり、すべてのレイヤーで統合されています。  
  
 従来のアプリケーションでは、ディスプレイを作成し、いくつかのデータにバインドします。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、コントロールに関するすべての側面が、何らかの種類のデータバインディングによって生成されます。 ボタン内に表示されるテキストは、ボタン内に構築されたコントロールを作成し、その表示をボタンのコンテンツプロパティにバインドすることによって表示されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ベースのアプリケーションの開発を開始すると、非常になじみがあります。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] または ASP.NET を使用する場合とほぼ同じ方法で、プロパティの設定、オブジェクトの使用、およびデータバインドを行うことができます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のアーキテクチャについてさらに詳しく調査することで、アプリケーションのコアドライバーとしてデータを根本的に扱う、より豊富なアプリケーションを作成できる可能性があることがわかります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [レイアウト](layout.md)
- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
