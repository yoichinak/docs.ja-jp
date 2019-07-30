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
ms.openlocfilehash: 440a6d76e5295613d2887c0a77d9a49e870e580b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629824"
---
# <a name="wpf-architecture"></a>WPF アーキテクチャ
このトピックでは、Windows Presentation Foundation (WPF) クラスの階層構造のガイド付きツアーを提供します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の主要なサブシステムの大半に対応し、それらがどのようにやり取りするかについて説明します。 また、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の構造設計者によって行われた選択についての幾つかを詳細に説明します。  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 主要な[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プログラミング モデルがマネージ コードを通じて公開されます。 初期の設計段階で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のさまざまなシステムのマネージ コンポーネントとアンマネージのコンポーネントとの線引きについての論争がありました。 CLR には、開発の生産性と堅牢性を高めるさまざまな機能が用意されています (メモリ管理、エラー処理、共通型システムなどを含む) が、コストが発生します。  
  
 の主要なコンポーネント[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を次の図に示します。 図の赤いセクション (プレゼンテーションフレームワーク、プレゼンテーションコア、およびミルコア) は、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]主要なコード部分です。 これらのうちの1つだけがアンマネージコンポーネント–ミルコアです。 ミルコアは、DirectX との緊密な統合を可能にするためにアンマネージコードで記述されています。 のすべての[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ディスプレイは DirectX エンジンによって実行されるため、ハードウェアとソフトウェアを効率的にレンダリングできます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]また、メモリと実行を細かく制御する必要もあります。 密度の高い合成エンジンは、パフォーマンスに大きな影響を与えます。そのため、パフォーマンスを得るためには、CLR の多くの利点が必要です。  
  
 ![.NET Framework 内の WPF の位置。](./media/wpf-architect1.PNG "wpf_architect1")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のマネージ コードとアンマネージの部分の間の通信はこのトピックの後半で説明します。 マネージ プログラミング モデルの残りの部分を以下に示します。  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ほとんどのオブジェクトは<xref:System.Windows.Threading.DispatcherObject>、同時実行とスレッド処理を行うための基本的な構成要素を提供するから派生します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、ディスパッチャーによって実装されるメッセージングシステムに基づいています。 これは、使い慣れ[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]たメッセージポンプとよく似ています。実際には、ディスパッチャーは[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、user32.dll メッセージを使用して、スレッド間の呼び出しを実行します。  
  
 での同時実行に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ついては、ディスパッチャーとスレッドアフィニティの2つの主要概念を理解しておく必要があります。  
  
 の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]設計フェーズでは、目標は実行の1つのスレッドに移動しましたが、非スレッド "関連付け済み" モデルに移行することでした。 スレッドアフィニティは、コンポーネントが実行中のスレッドの id を使用して何らかの種類の状態を格納するときに発生します。 最も一般的な形式は、スレッドローカルストア (TLS) を使用して状態を格納することです。 スレッドアフィニティでは、実行の各論理スレッドが、オペレーティングシステムの1つの物理スレッドによって所有されている必要があります。これは、メモリを集中的に使用する可能性があります。 最終的には、WPF のスレッドモデルは、スレッドアフィニティを使用したシングルスレッド実行の既存の User32.dll スレッドモデルと同期した状態に保たれます。 これの主な理由は相互運用性でした[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)]。クリップボードや Internet Explorer のようなシステムでは、すべてシングルスレッドアフィニティ (STA) を実行する必要があります。  
  
 STA スレッドを持つオブジェクトがある場合は、スレッド間で通信を行い、正しいスレッドであることを検証する方法が必要です。 ここでは、ディスパッチャーの役割があります。 ディスパッチャーは、優先順位の高い複数のキューを持つ基本的なメッセージディスパッチシステムです。 メッセージの例としては、未加工の入力通知 (マウス移動)、フレームワーク関数 (レイアウト)、ユーザーコマンド (このメソッドの実行) などがあります。 から<xref:System.Windows.Threading.DispatcherObject>派生することによって、STA の動作を持つ CLR オブジェクトを作成し、作成時にディスパッチャーへのポインターを与えます。  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 構築[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]で使用される主要なアーキテクチャ思想の1つは、メソッドまたはイベントのプロパティを優先することでした。 プロパティは宣言型であり、アクションではなく意図を簡単に指定できます。 また、ユーザーインターフェイスのコンテンツを表示するための、モデル駆動型またはデータ駆動型のシステムもサポートされています。 この哲学には、アプリケーションの動作をより適切に制御するために、バインドできるプロパティを作成することを意図した効果がありました。  
  
 プロパティによってより多くのシステムを使用するためには、CLR が提供するよりも豊富なプロパティシステムが必要でした。 この豊富な例として、変更通知があります。 双方向のバインドを有効にするには、変更通知をサポートするために、バインドの両側が必要です。 プロパティ値に関連付けられた動作を使用するには、プロパティ値が変更されたときに通知を受け取る必要があります。 Microsoft .NET Framework には**INotifyPropertyChange**というインターフェイスがあります。これにより、オブジェクトは変更通知を発行できますが、これは省略可能です。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<xref:System.Windows.DependencyObject>型から派生した、豊富なプロパティシステムを提供します。 プロパティシステムは、プロパティ式間の依存関係を追跡し、依存関係が変更されたときにプロパティ値を自動的に再検証するという、本当に "依存関係" プロパティシステムです。 たとえば、(など<xref:System.Windows.Controls.Control.FontSize%2A>の) を継承するプロパティがある場合、値を継承する要素の親でプロパティが変更されると、システムは自動的に更新されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティシステムの基礎は、プロパティ式の概念です。 この最初のリリースの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、プロパティ式システムが閉じられており、式はすべてフレームワークの一部として提供されています。 式は、プロパティシステムがデータバインディング、スタイル設定、継承をハードコーディングしていなくても、フレームワーク内の後のレイヤーによって提供されるためです。  
  
 プロパティシステムでは、プロパティ値のスパースストレージも提供されます。 オブジェクトは多数のプロパティを持つことができ、ほとんどの値は既定の状態 (継承、スタイルによる設定など) であるため、オブジェクトのすべてのインスタンスで定義されているすべてのプロパティの完全な重みを持つ必要があるわけではありません。  
  
 プロパティシステムの最後の新機能は、添付プロパティの概念です。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]要素は、合成とコンポーネントの再利用の原則に基づいて構築されます。 多くの場合、含まれている要素 ( <xref:System.Windows.Controls.Grid>レイアウト要素など) は、その動作を制御するために子要素の追加データを必要とします (行または列の情報など)。 これらのすべてのプロパティをすべての要素に関連付けるのではなく、すべてのオブジェクトで他のオブジェクトのプロパティ定義を提供できます。 これは、JavaScript の "expando" 機能に似ています。  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 システムが定義されている場合、次の手順では画面にピクセルが描画されます。 クラス<xref:System.Windows.Media.Visual>は、ビジュアルオブジェクトのツリーを構築するためのを提供します。各オブジェクトには、必要に応じて、これらの命令 (クリッピング、変換など) のレンダリング方法に関する描画命令とメタデータが含まれています。 <xref:System.Windows.Media.Visual>は、非常に軽量で柔軟性があるように設計されています。そのため、ほとんどの機能はパブリック API を公開せず、保護されたコールバック関数に大きく依存しています。  
  
 <xref:System.Windows.Media.Visual>は、実際には[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コンポジションシステムへのエントリポイントです。 <xref:System.Windows.Media.Visual>は、マネージ API とアンマネージドミルコアの2つのサブシステム間の接続ポイントです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、ミルコアによって管理されているアンマネージデータ構造を走査することによってデータを表示します。 これらの構造体は、合成ノードと呼ばれ、各ノードでレンダリング命令を含む階層表示ツリーを表します。 次の図の右側に示されているこのツリーは、メッセージングプロトコルを使用してのみアクセスできます。  
  
 プログラミング[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]時には、 <xref:System.Windows.Media.Visual>このメッセージングプロトコルを使用して内部的に合成ツリーに通信する要素と派生型を作成します。 の<xref:System.Windows.Media.Visual>各[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、1つ、なし、または複数の合成ノードを作成できます。  
  
 ![Windows Presentation Foundation のビジュアルツリー。](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 ここで注目すべき非常に重要なアーキテクチャの詳細があります。ビジュアルのツリー全体と描画命令がキャッシュされます。 グラフィックス用語では[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、は保持されたレンダリングシステムを使用します。 これにより、ユーザーコードへのコールバックでコンポジションシステムがブロックされることなく、高いリフレッシュレートでシステムを再描画できます。 これにより、応答しないアプリケーションの外観を防ぐことができます。  
  
 図には実際にはわかりませんが、実際にはシステムが合成を実行する方法も重要です。  
  
 User32.dll と[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]では、システムはイミディエイトモードのクリッピングシステムで動作します。 コンポーネントをレンダリングする必要がある場合、システムは、コンポーネントがピクセルに触れることができないクリッピングの範囲を確立し、そのボックス内のピクセルを描画するようにコンポーネントに要求します。 このシステムは、メモリの制約付きシステムで非常に適しています。影響を受けるコンポーネントに触れる必要があるのは、1つのピクセルの色に寄与する2つのコンポーネントがないためです。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]"塗装のアルゴリズム" の描画モデルを使用します。 これは、各コンポーネントをクリッピングするのではなく、各コンポーネントが画面の前面に戻るように求められることを意味します。 これにより、各コンポーネントで前のコンポーネントの表示を描画できます。 このモデルの利点は、複雑で部分的に透明な図形を持つことができることです。 現在の最新のグラフィックスハードウェアでは、このモデルは比較的高速です (user32.dll/ [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]が作成されたときのケースではありません)。  
  
 前述のように、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中核となる理念は、より宣言的な "プロパティ中心" のプログラミングモデルに移行することです。 ビジュアルシステムでは、これがいくつかの興味深い場所に表示されます。  
  
 まず、保持モードグラフィックシステムについて考えてみると、これは本当に命令型の DrawLine/DrawLine 型モデルからデータ指向モデル (new Line ()/new Line ()) に移動します。 このデータドリブンレンダリングへの移行により、プロパティを使用して描画命令に対する複雑な操作を表すことができます。 から<xref:System.Windows.Media.Drawing>派生する型は、実際にはレンダリングのためのオブジェクトモデルです。  
  
 次に、アニメーションシステムを評価すると、完全に宣言されていることがわかります。 開発者が次の位置または次の色を計算する必要はなく、アニメーションオブジェクトの一連のプロパティとしてアニメーションを表現できます。 これらのアニメーションは、開発者またはデザイナーの意図を表すことができます (このボタンをここから5秒に移動します)。また、システムは、これを実現するための最も効率的な方法を決定できます。  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>レイアウト、入力、イベントなどのコアサブシステムを定義します。  
  
 レイアウトは、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中心的な概念です。 多くのシステムでは、固定されたレイアウトモデルのセットがあります (HTML はレイアウト用に3つのモデル、flow、absolute、テーブル)、またはレイアウトのモデルがありません (User32.dll は絶対配置のみをサポートします)。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開発者や設計者が、命令型ロジックではなくプロパティ値によって駆動される、柔軟で拡張可能なレイアウトモデルを必要としていることを前提としています。 このレベルでは、レイアウトの基本的なコントラクトが導入されます。これ<xref:System.Windows.UIElement.Measure%2A>は<xref:System.Windows.UIElement.Arrange%2A> 、とが成功する2フェーズモデルです。 <xref:System.Windows.UIElement>  
  
 <xref:System.Windows.UIElement.Measure%2A>必要なサイズをコンポーネントで決定できるようにします。 これは、親要素が<xref:System.Windows.UIElement.Arrange%2A>複数回測定して最適な位置とサイズを判断する必要がある状況が多いため、からの独立したフェーズです。 親要素が measure を要求する子要素は、コンテンツに対する別[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の重要な理念を示しています。 の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]すべてのコントロールは、そのコンテンツのサイズに合わせてサイズを変更することをサポートしています。 これにより、ローカライズがはるかに簡単になり、要素のサイズ変更に合わせて動的なレイアウトを行うことができます。 この<xref:System.Windows.UIElement.Arrange%2A>フェーズでは、親が各子の最終的なサイズを配置および決定できます。  
  
 多くの場合、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <xref:System.Windows.Media.Visual>と関連オブジェクトの出力側について説明します。 しかし、入力側にも非常に多くのイノベーションがあります。 の入力モデルの最も基本的な[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]変更は、入力イベントがシステムを経由してルーティングされる一貫したモデルです。  
  
 入力は、カーネルモードデバイスドライバーの信号として生成され、Windows カーネルと User32.dll を含む複雑なプロセスを通じて、正しいプロセスとスレッドにルーティングされます。 入力に対応する user32.dll メッセージがに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ルーティングされると、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]未加工の入力メッセージに変換され、ディスパッチャーに送信されます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]生の入力イベントを複数の実際のイベントに変換できます。これにより、"MouseEnter" などの機能を、保証された配信によりシステムの低レベルで実装できます。  
  
 各入力イベントは、少なくとも2つのイベント ("preview" イベントと実際のイベント) に変換されます。 内のすべて[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のイベントには、要素ツリーを通じたルーティングの概念があります。 イベントは、ターゲットからツリーをルートまで走査する場合は "バブル" と呼ばれ、ルートから開始してターゲットを走査する場合は "トンネル" と呼ばれます。 入力プレビューイベントトンネル。ツリー内の任意の要素を有効にして、イベントにフィルターを適用したり、アクションを実行したりすることができます。 通常の (非プレビュー) イベントは、ターゲットからルートまでバブルされます。  
  
 このトンネルとバブルフェーズを分割することにより、キーボードアクセラレータなどの機能の実装が、複合環境で一貫した方法で実行されます。 User32.dll では、サポートするすべてのアクセラレータを含む単一のグローバルテーブルを使用して、キーボードアクセラレータを実装します (Ctrl + N を "New" にマッピングします)。 アプリケーションのディスパッチャーで、 **TranslateAccelerator**を呼び出します。これは、user32.dll の入力メッセージをスニッフィングし、登録されているアクセラレータに一致したかどうかを判断します。 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、システムが完全に "コンポーザブル" であるため、この機能は動作しません。すべての要素は、任意のキーボードアクセラレータを処理して使用できます。 この2つのフェーズモデルを入力にすると、コンポーネントは独自の "TranslateAccelerator" を実装できます。  
  
 もう1つの手順を実行<xref:System.Windows.UIElement>するために、には commandbindings の概念も導入されています。 コマンド[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]システムを使用すると、開発者はコマンドエンドポイント (を実装<xref:System.Windows.Input.ICommand>するもの) の観点から機能を定義できます。 コマンドバインドを使用すると、要素で入力ジェスチャ (Ctrl + N) とコマンド (New) の間のマッピングを定義できます。 入力ジェスチャとコマンド定義はどちらも拡張可能であり、使用時に同時に接続することができます。 これにより、たとえば、エンドユーザーがアプリケーション内で使用するキーバインドをカスタマイズできるようにすることが簡単になります。  
  
 トピック「」では、「プレゼンテーションコアアセンブリに実装[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]されている機能」の「コア」機能を中心に説明しました。 構築[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]時には、基本要素 (**メジャー**および**配置**によるレイアウトのコントラクトなど) とフレームワークピース (たとえば、のような<xref:System.Windows.Controls.Grid>特定のレイアウトの実装など) を明確に分離する必要がありました。最終. 目標は、外部の開発者が必要に応じて独自のフレームワークを作成できるようにする、スタックの拡張ポイントを小さくすることでした。  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>2つの異なる方法で検索できます。 また、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]下位層で導入されたサブシステムの一連のポリシーとカスタマイズについて説明します。 また、一連の新しいサブシステムも導入されています。  
  
 によって<xref:System.Windows.FrameworkElement>導入される主なポリシーは、アプリケーションのレイアウトに関するものです。 <xref:System.Windows.FrameworkElement>によって<xref:System.Windows.UIElement>導入された基本的なレイアウトコントラクトに基づいて構築されたレイアウト "スロット" の概念を追加します。これにより、レイアウト作成者が一貫した一連のプロパティドリブンレイアウトセマンティクスを簡単に持つことができます。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 、、<xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement>、およびのようなプロパティ (いくつかの名前にするため) は、レイアウトコンテナー内の一貫した動作から派生したすべてのコンポーネントを提供します。 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
  
 <xref:System.Windows.FrameworkElement>また、は、のコアレイヤーにある多くの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]機能に対する API の公開を容易にします。 たとえば、は<xref:System.Windows.FrameworkElement> 、 <xref:System.Windows.FrameworkElement.BeginStoryboard%2A>メソッドを使用してアニメーションへの直接アクセスを提供します。 は<xref:System.Windows.Media.Animation.Storyboard> 、一連のプロパティに対して複数のアニメーションをスクリプト化する方法を提供します。  
  
 導入される<xref:System.Windows.FrameworkElement>最も重要な2つの要素は、データバインディングとスタイルです。  
  
 の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]データバインディングサブシステムは、アプリケーション[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を作成するために使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または ASP.NET したすべてのユーザーにとって、比較的なじみのあるものにする必要があります。 これらの各システムでは、特定の要素の1つ以上のプロパティをデータにバインドすることを簡単に表すことができます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、プロパティバインド、変換、およびリストバインドが完全にサポートされています。  
  
 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のデータバインディングの最も興味深い機能の1つは、データテンプレートの導入です。 データテンプレートを使用すると、データの一部を視覚化する方法を宣言によって指定できます。 データにバインドできるカスタムユーザーインターフェイスを作成する代わりに、問題を解決して、作成される表示をデータが決定できるようにすることができます。  
  
 スタイル設定は、実際には軽量な形式のデータバインドです。 スタイルを使用すると、共有定義の一連のプロパティを、要素の1つ以上のインスタンスにバインドできます。 スタイルは、明示的な参照によって (プロパティを<xref:System.Windows.FrameworkElement.Style%2A>設定することによって) 要素に適用されるか、またはスタイルを要素の CLR 型に関連付けることによって暗黙的に適用されます。  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 コントロールの最も重要な機能は、テンプレートです。 WPF の合成システムを保持モードのレンダリングシステムと考えている場合、テンプレートを使用すると、コントロールは、パラメーター化された宣言型の方法でレンダリングを記述できます。 は、子要素のセットを作成するためのスクリプトにすぎず、コントロールによって提供されるプロパティへのバインドが含まれています。<xref:System.Windows.Controls.ControlTemplate>  
  
 <xref:System.Windows.Controls.Control>いくつかのストックプロパティ<xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Padding%2A>のセットを提供します。ここでは、テンプレート作成者がコントロールの表示をカスタマイズするために使用できます。 コントロールの実装には、データモデルと相互作用モデルが用意されています。 相互作用モデルは、一連のコマンド (ウィンドウの [閉じる] など) と入力ジェスチャへのバインドを定義します (ウィンドウの上隅の赤い X をクリックするなど)。 データモデルには、相互作用モデルをカスタマイズしたり、(テンプレートによって決定される) 表示をカスタマイズしたりするための一連のプロパティが用意されています。  
  
 これにより、データモデル (プロパティ)、相互作用モデル (コマンドとイベント)、および表示モデル (テンプレート) が分割され、コントロールの外観と動作を完全にカスタマイズできるようになります。  
  
 コントロールのデータモデルの一般的な側面は、コンテンツモデルです。 のような<xref:System.Windows.Controls.Button>コントロールを表示すると、型<xref:System.Object>の "Content" という名前のプロパティがあることがわかります。 と[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ASP.NET では、通常、このプロパティは文字列になります。ただし、ボタンに配置できるコンテンツの種類が制限されます。 ボタンのコンテンツは、単純な文字列、複雑なデータオブジェクト、または要素ツリー全体のいずれかになります。 データオブジェクトの場合は、データテンプレートを使用して表示を作成します。  
  
<a name="Summary"></a>   
## <a name="summary"></a>まとめ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、データ駆動型の動的なプレゼンテーションシステムを作成できるように設計されています。 システムのすべての部分は、動作を駆動するプロパティセットを通じてオブジェクトを作成するように設計されています。 データバインディングはシステムの基本的な部分であり、すべてのレイヤーで統合されています。  
  
 従来のアプリケーションでは、ディスプレイを作成し、いくつかのデータにバインドします。 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、コントロールに関するすべての側面が、何らかの種類のデータバインディングによって生成されます。 ボタン内に表示されるテキストは、ボタン内に構築されたコントロールを作成し、その表示をボタンのコンテンツプロパティにバインドすることによって表示されます。  
  
 ベースのアプリケーションの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開発を開始すると、非常になじみのあるアプリケーションです。 または ASP.NET を使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]する場合とほぼ同じ方法で、プロパティの設定、オブジェクトの使用、およびデータバインドを行うことができます。 の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アーキテクチャの詳細な調査では、アプリケーションのコアドライバーとしてデータを根本的に処理する、非常に豊富なアプリケーションを作成するための可能性があることがわかります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [レイアウト](layout.md)
- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
