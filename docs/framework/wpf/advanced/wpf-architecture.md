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
ms.openlocfilehash: f4a6e6c2a63e58c40e0cca9c67b12d1f65af0d2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199428"
---
# <a name="wpf-architecture"></a>WPF アーキテクチャ
このトピックでは、Windows Presentation Foundation (WPF) クラスの階層構造のガイド付きツアーを提供します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の主要なサブシステムの大半に対応し、それらがどのようにやり取りするかについて説明します。 また、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の構造設計者によって行われた選択についての幾つかを詳細に説明します。  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 主要な[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プログラミング モデルがマネージ コードを通じて公開されます。 初期の設計段階で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のさまざまなシステムのマネージ コンポーネントとアンマネージのコンポーネントとの線引きについての論争がありました。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]は生産性と堅牢性 (メモリ管理、エラー処理、共通型システムなどを含む) のある開発を行う数多くの機能を提供しますが、それらはコストの増加を招きます。  
  
 主要コンポーネント[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は次の図のようになります。 (PresentationFramework、PresentationCore、および milcore) の図の赤のセクションではの大規模なコード部分[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 これらのうち、1 つだけは、アンマネージ コンポーネント – milcore です。 緊密な統合を有効にするには Milcore がアンマネージ コードで記述された[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]します。 すべて表示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を行う、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]エンジン、効率的なハードウェアとソフトウェア レンダリングすることができます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] メモリと実行を細かく制御も必要です。 Milcore 合成エンジンは、非常に機密性の高い、やの多くの利点をあきらめる必要なパフォーマンス、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]パフォーマンスを向上させます。  
  
 ![WPF、.NET Framework 内の位置。](./media/wpf-architect1.PNG "wpf_architect1")  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のマネージ コードとアンマネージの部分の間の通信はこのトピックの後半で説明します。 マネージ プログラミング モデルの残りの部分を以下に示します。  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 多くのオブジェクトに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から派生<xref:System.Windows.Threading.DispatcherObject>、同時実行を処理して、スレッド処理の基本的な構造を提供します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ディスパッチャーによって実装されたメッセージング システムに基づいています。 これは非常によく似た、使い慣れた[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]メッセージ ポンプは実際には、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ディスパッチャーが User32 メッセージをスレッド間の呼び出しを実行するために使用します。  
  
 本当に 2 つの主要で同時実行を検討する場合を理解する概念がある[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– ディスパッチャーとスレッド アフィニティ。  
  
 デザイン フェーズ中に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]目標は、実行の 1 つのスレッドに移動することでしたが、非スレッド「関連付け」モデル。 スレッドの関係は、コンポーネントの状態の保存するために実行中のスレッドの id を使用するときに発生します。 これの最も一般的な形式では、状態を格納する、スレッド ローカル ストア (TLS) を使用します。 スレッドの関係では、実行の各論理スレッドの所有、オペレーティング システム、メモリ集中型になることで、1 つだけの物理スレッドである必要があります。 最後に、WPF のスレッド モデルがスレッドの関係を持つシングル スレッド実行の既存の User32 スレッド モデルとの同期が保持されます。 その理由は、プライマリ相互運用性のされました – などのシステム[!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)]クリップボード、および Internet Explorer のすべて 1 つのスレッド アフィニティ (STA) の実行が必要です。  
  
 STA スレッドでオブジェクトがあること必要があります、スレッド間で通信および検証する方法、適切なスレッドであります。 ディスパッチャーのロールが生じます。 ディスパッチャーは、複数の優先順位キューでのシステムをディスパッチする基本的なメッセージです。 メッセージの例には、生の入力の通知 (マウスの移動)、framework 関数 (レイアウト)、またはユーザー コマンドが含まれます (このメソッドを実行)。 派生することによって<xref:System.Windows.Threading.DispatcherObject>、作成する、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] STA の動作を持つオブジェクトし、は指定のポインターをディスパッチャーに作成時にします。  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 ビルドで使用されるプライマリ アーキテクチャ哲学の 1 つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティの基本設定がメソッドまたはイベントを超えました。 プロパティ宣言を簡単にアクションではなく、インテントを指定できます。 これは、モデル駆動型、またはデータ ドリブンでユーザー インターフェイスのコンテンツを表示するためのシステムにもサポートされます。 この理念は、アプリケーションの動作をより細かく制御するために、バインドが複数のプロパティの作成の目的の効果がありました。  
  
 高度なプロパティ システムのプロパティによって駆動システムの詳細を確保するために、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]提供が必要でした。 この豊富な機能の簡単な例では、変更通知です。 双方向バインディングを有効にするには、変更通知をサポートするバインドの両方の側を作成する必要があります。 プロパティの値に関連付けられている動作を確保するためには、プロパティ値が変更されたときに通知する必要があります。 Microsoft .NET Framework には、インターフェイス、 **INotifyPropertyChange**、これは省略可能な変更の通知を発行するオブジェクトを許可します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 派生したより豊富なプロパティ システムの提供、<xref:System.Windows.DependencyObject>型。 プロパティ システムは、プロパティ式間の依存関係の追跡、依存関係を変更するときに、プロパティ値を自動的に再評価という点で、「依存関係」プロパティのシステムでは本当に。 例では、継承したプロパティがある場合 (など<xref:System.Windows.Controls.Control.FontSize%2A>) には、値を継承する要素の親プロパティが変更された場合、システムが自動的に更新します。  
  
 基盤となる、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティ システムは、プロパティ式の概念です。 この最初のリリースの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プロパティ式のシステムが閉じられるし、式はすべて、framework の一部として提供します。 式は、プロパティ システムがデータ バインディング、スタイル設定がないか、継承はハード コーディングしていますがではなく、framework 内の以降のレイヤーによって提供される理由です。  
  
 プロパティ システムのプロパティの値のスパース ストレージも提供します。 オブジェクトは、数十 (ない場合は数百) のプロパティを持つことができ、値のほとんどは、既定の状態であるため (など、スタイルで設定を継承) オブジェクトのすべてのインスタンスが定義されたすべてのプロパティの完全な重みは、する必要があります。  
  
 プロパティ システムの最終的な新しい機能とは、添付プロパティの概念です。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素は、構成とコンポーネントの再利用の原則に基づいて構築されます。 多くの場合は、の一部の要素を含む (のように、<xref:System.Windows.Controls.Grid>レイアウト要素) 子要素 (行/列の情報) のような動作を制御する追加のデータが必要です。 すべての要素では、これらすべてのプロパティを関連付ける、代わりに、他のオブジェクトのプロパティの定義を提供する任意のオブジェクトが許可されています。 これは、JavaScript の"expando"機能に似ています。  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 定義されているシステムでは、次の手順は画面に描画されるピクセルになっています。 <xref:System.Windows.Media.Visual>クラスがそれぞれ必要に応じて描画命令とこれらの手順 (クリッピング、変換など) をレンダリングする方法についてのメタデータを含む、ビジュアル オブジェクトのツリーを構築するために提供します。 <xref:System.Windows.Media.Visual> ほとんどの機能には、パブリックあるありませんので非常に軽量で柔軟なをするのには設計されています[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]公開し、保護されているコールバック関数に大きく依存します。  
  
 <xref:System.Windows.Media.Visual> エントリ ポイントは、実際に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コンポジション システム。 <xref:System.Windows.Media.Visual> マネージこれらの 2 つサブシステム間の接続ポイントは、[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]まさに、します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] milcore によって管理されるアンマネージ データ構造を走査して、データを表示します。 コンポジションのノードと呼ばれるこれらの構造は、各ノードでレンダリング指示の階層表示にはツリーを表します。 右側にある次の図のように、このツリーはメッセージング プロトコルを介してアクセスできます。  
  
 プログラミング[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、作成する<xref:System.Windows.Media.Visual>要素、および派生型は、このメッセージング プロトコルを使って構成ツリーに内部的に通信します。 各<xref:System.Windows.Media.Visual>で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]1 つのフィルターまたはいくつかの構成ノードを作成することがあります。  
  
 ![Windows Presentation Foundation のビジュアル ツリー。](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 ここでのビジュアル ツリー全体を通知する非常に重要なアーキテクチャの詳細は、描画命令はキャッシュします。 グラフィックスの用語で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]保持モードのレンダリング システムを使用します。 これにより、高いリフレッシュ レートを合成システムによってユーザー コードにコールバックをブロックせずに再描画するシステムです。 これは、応答しないアプリケーションの外観を回避できます。  
  
 ダイアグラムで非常に顕著ではないもう 1 つの重要な詳細情報は、システムが実際に合成を実行する方法です。  
  
 User32 でと[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]、イミディ エイト モードのクリッピング システムで、システムが動作します。 コンポーネントは、表示する必要があります、システムは、外側には、コンポーネントがタッチ (ピクセル単位) 許可されていないし、コンポーネントがそのボックス内のピクセルの描画によく寄せられる、クリッピングの境界を確立します。 このシステムのメモリの制約があるシステムで非常にうまく動作のみ影響を受けるコンポーネントをタッチする必要がある変更が生じた場合のため – これまでの 1 つのピクセルの色に関与して 2 つのコンポーネントではありません。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] モデルの描画の「ペインタ アルゴリズム」を使用します。 これは、各コンポーネントをクリッピングするには、代わりに各コンポーネントは、表示の前に、バックアップから表示を要求はことを意味します。 これにより、前のコンポーネントの表示を描画するには、各コンポーネントができます。 このモデルの利点は、使用できる、部分的に透明な複雑な図形にあることです。 今日の最新のグラフィックス ハードウェアでは、このモデルは比較的高速な (ケースではないときに User32/[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]作成された)。  
  
 以前は、中核となる考え方を説明したように[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]プログラミングより宣言型「プロパティを中心とした」モデルに移動することです。 ビジュアルのシステムでは、これは表示されます興味深い部分はいくつかあります。  
  
 最初に、保持モード グラフィックス システムに関する場合は、これは本当に、命令型の DrawLine/DrawLine 型モデルからモデルへの移行、データ指向 – 新しい行 ()/新しい Line() します。 データ ドリブンのレンダリングには、この移動は、複雑な操作を表すプロパティを使用して描画命令にできます。 派生する型<xref:System.Windows.Media.Drawing>表示オブジェクト モデルでは実質的にします。  
  
 次に、アニメーション システムを評価する場合に、ほぼ完全な宣言型であるが表示されます。 次の場所、または次の色を計算する開発者を要求するには、代わりには、アニメーション オブジェクトのプロパティのセットとしてアニメーションを表現できます。 これらのアニメーションは、開発者やデザイナーの意図を表現できます (このボタンをクリックここからに移動が 5 秒間)、システムはこれを実現する最も効率的な方法を決定したりします。  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> レイアウト、入力、およびイベントを含むコア サブシステムを定義します。  
  
 レイアウトの中核となる概念は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 多くのシステムでは、モデルのレイアウトの固定のセット (HTML では、レイアウトの 3 つのモデルがサポートしています。 フロー、絶対、およびテーブル) またはレイアウトのモデルのない (User32 だけでは絶対配置)。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 開発者および設計者が、命令型のロジックではなく、プロパティの値で制御できる、柔軟で拡張性の高いレイアウト モデルを求めていることを想定して開始します。 <xref:System.Windows.UIElement>レベル、レイアウトの基本的なコントラクトが導入 – でモデルをフェーズ 2<xref:System.Windows.UIElement.Measure%2A>と<xref:System.Windows.UIElement.Arrange%2A>を渡します。  
  
 <xref:System.Windows.UIElement.Measure%2A> により、コンポーネントを実行するどの程度のサイズを決定できます。 これは、別のフェーズから<xref:System.Windows.UIElement.Arrange%2A>が多くの場合の最適な位置とサイズを決定するいくつかの時間を測定する子を親要素が求められます。 親要素が子要素を測定するよう要求するという事実がもう 1 つの重要な理念を示します[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– コンテンツのサイズ。 すべてのコントロール[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]サイズがコンテンツの通常サイズにする機能をサポートします。 これにより、ローカライズをより簡単と、項目のサイズ変更、要素の動的レイアウトできます。 <xref:System.Windows.UIElement.Arrange%2A>フェーズでは、親を配置し、それぞれの子の最終サイズを決定します。  
  
 多くの時間は、出力側の話に費やされた多くの場合、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] –<xref:System.Windows.Media.Visual>および関連するオブジェクト。 ただしも入力側で大量のイノベーションがあります。 入力モデルで最も基本的な変更ではおそらく[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]はシステムを経由する入力イベントのルーティング、一貫性のあるモデルです。  
  
 入力は、カーネル モード デバイス ドライバーのシグナルとして開始され、正しいプロセスと Windows カーネルと User32 が関係する複雑なプロセスのスレッドにルーティングされます。 入力に対応する User32 メッセージにルーティングされると[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]に変換されます、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]未加工入力メッセージと、ディスパッチャーに送信します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 生の入力イベント配信の保証とシステムの低レベルで実装するには、"MouseEnter"などの機能を有効にする、実際の複数のイベントに変換できます。  
  
 各入力イベントは、"preview"イベントと、実際のイベントには少なくとも 2 つのイベントに変換されます。 すべてのイベント[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]要素ツリーを通じてルーティングの概念があります。 ルートにツリーをターゲットから走査、ルートで開始し、ターゲットまで走査、使用している「トンネル」と言われています"を"バブル イベントといいます。 ツリーをフィルター処理またはイベントに対してアクションを実行する機会の任意の要素を有効にすると、プレビュー イベントのトンネルを入力します。 通常の (非プレビュー) のイベントは、ルートまでターゲットから、バブルします。  
  
 この分割トンネルとバブル フェーズの間では、キーボード アクセラレータは、複合の世界で一貫性のある方法で動作などの機能の実装です。 User32 でグローバル含む単一のテーブルをサポートするすべてのアクセラレータ (Ctrl + N の「新規」へのマッピング) することでキーボード アクセラレータを実装します。 呼び出すことは、アプリケーションのディスパッチャーで**TranslateAccelerator**は User32 で入力メッセージを傍受し、登録済みのアクセラレータが一致するかどうかはいずれかを判断します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]システムが完全に「コンポーザブル」– 任意の要素を処理し、キーボード アクセラレータを使用できますので、これはうまくいきません。 この 2 つのフェーズのモデルの入力を持つことはできますが独自の"TranslateAccelerator"を実装するコンポーネントです。  
  
 さらに、この 1 つの手順を実行する<xref:System.Windows.UIElement>も CommandBindings の概念が導入されています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]コマンド システムにより、開発者は何かのコマンドの終了ポイント – という観点から機能を定義する、実装する<xref:System.Windows.Input.ICommand>します。 コマンド バインディングには、入力ジェスチャ (Ctrl + N) とコマンドを (新規) 間のマッピングを定義する要素が有効にします。 入力ジェスチャとコマンドの定義は拡張可能なおよび使用時にまとめることができます。 これにより、たとえば、エンドユーザーがアプリケーション内で使用すると、キー バインドのカスタマイズを許可します。  
  
 このトピックの時点「コア」機能の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]– PresentationCore アセンブリに実装されている機能は、フォーカスされています。 構築するときに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、基礎となる部分の間の分離のクリーンアップ (などのレイアウトでのコントラクト**メジャー**と**配置**) と (特定の実装などのフレームワーク要素ようなレイアウト<xref:System.Windows.Controls.Grid>) が目的の結果。 目標のために必要な場合は、独自のフレームワークを作成する外部の開発者は、スタックの低い機能拡張ポイントを提供することでした。  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> 2 つの方法で参照できます。 ポリシーとの下位層で導入されたサブシステムでのカスタマイズのセットが導入[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 一連の新しいサブシステムも導入されています。  
  
 導入されたプライマリ ポリシー<xref:System.Windows.FrameworkElement>アプリケーション レイアウトの周りが。 <xref:System.Windows.FrameworkElement> 導入された基本的なレイアウトのコントラクトに基づいて<xref:System.Windows.UIElement>レイアウト プロパティのレイアウトのセマンティクスを駆動型の一貫性のあるセットがレイアウトの作成者が簡単です「スロット」の概念を追加します。 などのプロパティ<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、 <xref:System.Windows.FrameworkElement.MinWidth%2A>、および<xref:System.Windows.FrameworkElement.Margin%2A>(をいくつかの名前を付ける) から派生したすべてのコンポーネントを提供<xref:System.Windows.FrameworkElement>レイアウト コンテナー内で一貫性のある動作。  
  
 <xref:System.Windows.FrameworkElement> 簡単に用意されています[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]の基本レイヤーについては、多くの機能への露出[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 たとえば、<xref:System.Windows.FrameworkElement>アニメーションに直接アクセスできる、<xref:System.Windows.FrameworkElement.BeginStoryboard%2A>メソッド。 A<xref:System.Windows.Media.Animation.Storyboard>プロパティのセットに対して複数のアニメーションのスクリプトを作成する方法を提供します。  
  
 2 つの最も重要なことを<xref:System.Windows.FrameworkElement>紹介はデータ バインドとスタイル。  
  
 データ バインディング サブシステム[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]が使用するユーザーにとって比較的馴染みがある[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]アプリケーションを作成する[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 これらのシステムの各でのデータにバインドする指定された要素から 1 つまたは複数のプロパティをすることを表現する簡単な方法があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プロパティのバインド、変換、およびリストのバインドを完全にサポートしています。  
  
 データ バインディングの最も興味深い機能の 1 つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]データ テンプレートの導入です。 データ テンプレートを使用して、データを視覚化する方法を宣言によって指定できます。 データにバインドできるカスタム ユーザー インターフェイスを作成する代わりに代わりに問題を有効にし、データが作成される表示を決定できるようにできます。  
  
 スタイル設定は、簡易形式のデータ バインディングです。 スタイルを使用するのにバインドできますプロパティのセットを共有定義の要素の 1 つまたは複数のインスタンス。 要素に適用されるスタイルを明示的に参照するか (設定して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ) のスタイルを関連付けることによって暗黙的にまたは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]要素の型。  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 コントロールの最も重要な機能とは、テンプレートです。 保持モードのレンダリング システムとしての WPF のコンポジション システムについて考えると、テンプレートには、パラメーター化された宣言型の方法で、レンダリングを記述するコントロールができるようにします。 A<xref:System.Windows.Controls.ControlTemplate>実際には、コントロールによって提供されるプロパティへのバインドで一連の子要素を作成するスクリプトにすぎません。  
  
 <xref:System.Windows.Controls.Control> ストック プロパティのセットを提供します<xref:System.Windows.Controls.Control.Foreground%2A>、 <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Padding%2A>テンプレートの作成者がコントロールの表示のカスタマイズを使用できる、いくつかの名前。 コントロールの実装では、データ モデルと対話モデルを提供します。 対話モデルでは、(ウィンドウの隅に赤い X 印をクリックする) などのジェスチャを入力するには、(ウィンドウを閉じる) のようなコマンドとバインディングのセットを定義します。 データ モデルでは、相互作用モデルをカスタマイズまたは (テンプレートによって決まります) の表示をカスタマイズするプロパティのセットを提供します。  
  
 データ モデル (プロパティ)、相互作用モデル (コマンドとイベント)、および表示モデル (テンプレート) の間には、この分割により、コントロールの外観と動作のカスタマイズを完了します。  
  
 コントロールのデータ モデルの一般的な側面は、コンテンツ モデルです。 などのコントロールを見る場合<xref:System.Windows.Controls.Button>、型の場合は"Content"という名前のプロパティを使用しているが表示されます<xref:System.Object>します。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]、このプロパティは文字列である通常 – ボタンに配置することができますが、コンテンツの種類を制限します。 ボタンのコンテンツか単純な文字列、または指定できます、複雑なデータ オブジェクト全体の要素ツリー。 データ オブジェクトの場合は、データ テンプレートは、表示の構築に使用されます。  
  
<a name="Summary"></a>   
## <a name="summary"></a>まとめ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] データ ドリブン プレゼンテーション システムを動的に作成できるように設計されています。 プロパティ セットを通じてオブジェクトを作成するには、動作を制御するには、システムのすべての部分は設計されています。 データ バインディングは、システムの基本的な部分は、され、すべてのレイヤーで統合されます。  
  
 従来のアプリケーションでは、表示を作成し、いくつかのデータにバインドします。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、何らかの種類のデータ バインディングによって生成されるコントロール、ディスプレイのすべての側面に関するすべてのものです。 ボタンの内側にあるテキストは、ボタンの内部で構成されるコントロールを作成し、その表示をボタンの content プロパティにバインドして表示されます。  
  
 開発を開始すると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ベースのアプリケーションでは、非常によくと考える必要があります。 オブジェクトを使用して、すべてのプロパティを設定することができ、データ バインドで同じ方法を使用できる[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]します。 アーキテクチャにさらに調査すると[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、根本的に、アプリケーションの中核となるドライバーとしてデータを処理するより充実したアプリケーションを作成するためにできる可能性があることがわかります。  
  
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
