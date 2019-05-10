---
title: ルーティング イベントの処理済みとしてのマーキング、およびクラス処理
ms.date: 03/30/2017
helpviewer_keywords:
- tunneling events [WPF]
- class listeners [WPF]
- listeners [WPF]
- Preview routed events [WPF]
- instance listeners [WPF]
- events [WPF], bubbling
- suppressing events [WPF]
- routed events [WPF], Preview
- composited controls [WPF]
- events [WPF], tunneling
- routed events [WPF], marking as handled
- controls [WPF], compositing
- events [WPF], suppressing
- bubbling events [WPF]
ms.assetid: 5e745508-4861-4b48-b5f6-5fc7ce5289d2
ms.openlocfilehash: 8cce3d1effa163c35cd219a6a52504b0f4d98c73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598656"
---
# <a name="marking-routed-events-as-handled-and-class-handling"></a>ルーティング イベントの処理済みとしてのマーキング、およびクラス処理
ルーティング イベントのハンドラーでは、イベント データ内で、イベントを処理済みとしてマークできます。 イベントを処理すると、ルートが事実上短縮されます。 クラス処理は、ルーティング イベントでサポートされているプログラミング概念です。 クラス ハンドラーでは、特定のルーティング イベントをクラス レベルのハンドラーで処理することができます。このハンドラーは、そのクラスのどのインスタンスのどのインスタンス ハンドラーよりも先に呼び出されます。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、「[ルーティング イベントの概要](routed-events-overview.md)」で紹介した概念を詳しく説明します。  
  
<a name="When_to_Mark_Events_as_Handled"></a>   
## <a name="when-to-mark-events-as-handled"></a>イベントを処理済みとしてマークする場合  
 値を設定すると、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティを`true`イベントのルーティング イベントのデータと呼ばれるを「イベントを処理済みのマークを付ける」。 アプリケーションの作成者や、既存のルーティング イベントへの応答や新しいルーティング イベントの実装を行うコントロールの作成者が、どのような場合にルーティング イベントを処理済みとしてマークするかについては、絶対的な規則はありません。 ほとんどの場合、ルーティング イベントのイベント データで運ばれる "処理済み" の概念は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] で公開されているさまざまなルーティング イベントやカスタム ルーティング イベントに対するアプリケーションの応答のために、限定的なプロトコルとして使用する必要があります。 また、"処理済み" の問題のもう 1 つの考え方があります。ルーティング イベントに対するコードの応答が重要かつ比較的完全な形で行われた場合は、一般にルーティング イベントを処理済みとしてマークする必要があります。 通常は、1 つのルーティング イベント発生に対して、異なるハンドラー実装を必要とする複数の重要な応答があることは好ましくありません。 複数の応答が必要な場合は、ルーティング イベント システムを使用して転送するのではなく、単一のハンドラー内で一連のアプリケーション ロジックとして必要なコードを実装する必要があります。 また、何が "重要" と考えるかも主観的なもので、アプリケーションやコードに応じて異なります。 一般的に、"重要な応答" の例には、フォーカスの設定、パブリック状態の変更、ビジュアル表現に影響するプロパティの設定、他の新しいイベントの発生などがあります。 重要でない応答の例には、プライベート状態の変更 (ビジュアル表現への影響やプログラムによる表現を伴わない変更) や、イベントのログなどがあります。イベントの引数を確認して応答しないように選択する場合もこれに含まれます。  
  
 ハンドラーが追加されるため、ルーティング イベント システムの動作は、ルーティング イベントの処理済みの状態を使用するためには、この「重要な応答」モデルを補強[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]またはの一般的なシグネチャ<xref:System.Windows.UIElement.AddHandler%2A>ルーティング イベントに対しては呼び出されません、イベントデータは、既に処理済みでマークされます。 ハンドラーを追加するという作業を進める必要があります、`handledEventsToo`パラメーター バージョン (<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>) 以前の参加者によって処理済みとマークされているルーティング イベントのイベントのルーティングを処理するためにします。  
  
 場合によっては、コントロール自体が特定のルーティング イベントを処理済みとしてマークすることもあります。 ルーティング イベントが処理済みとマークされた場合、ルーティング イベントへの応答としてコントロールが行ったアクションは、コントロールの実装の一部として重要、完全なもので、そのイベントにはそれ以上の処理は必要ないと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの作成者が判断したことを表しています。 これは通常、イベントのクラス ハンドラーを追加するか、基底クラスに存在するクラス ハンドラー仮想メソッドの 1 つをオーバーライドすることによって行われます。 このイベント処理は、必要に応じて回避することもできます。詳細については、このトピックの「[コントロールによるイベント抑制の回避](#WorkingAroundEventSuppressionByControls)」をご覧ください。  
  
<a name="Preview_Events_vs__Bubbling_Events_and_Handling"></a>   
## <a name="preview-tunneling-events-vs-bubbling-events-and-event-handling"></a>"プレビュー" (トンネル) イベントとバブル イベントのイベント処理  
 プレビュー ルーティング イベントは、要素ツリーのトンネル ルートをたどるイベントです。 名前付け規則に含まれる "Preview" は、対応するバブル ルーティング イベントより前にプレビュー (トンネル) ルーティング イベントが発生するという入力イベントの原則を表しています。 また、トンネルとバブルのペアを持つ入力ルーティング イベントは、別個の処理ロジックを持ちます。 トンネル/プレビュー ルーティング イベントがイベント リスナーによって処理済みとしてマークされた場合、バブル ルーティング イベントは処理済みとしてマークされます。これは、バブル ルーティング イベントのすべてのリスナーがそのイベントを受け取る前であっても変わりません。 トンネル ルーティング イベントとバブル ルーティング イベントは、厳密には別個のイベントですが、この動作を実現するために、同じイベント データのインスタンスをあえて共有しています。  
  
 このトンネル ルーティング イベントとバブル ルーティング イベントの間の関連は、任意の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスで宣言されたルーティング イベントをそのクラスが発生させる方法の内部実装によって実現されます。これは入力ルーティング イベントのペアにも当てはまります。 このクラスレベルの実装が存在しなければ、名前付けスキームを共有するトンネル ルーティング イベントとバブル ルーティング イベントの間に関連はありません。つまり、そのような実装がなければ、それらは 2 つのまったく別のルーティング イベントとなり、順番に発生することや、イベント データを共有することはなくなります。  
  
 カスタム クラスでトンネル/バブル入力ルーティング イベントのペアを実装する方法の詳細については、「[方法 : カスタム ルーティング イベントを作成する](how-to-create-a-custom-routed-event.md)」をご覧ください。  
  
<a name="Class_Handlers_and_Instance_Handlers"></a>   
## <a name="class-handlers-and-instance-handlers"></a>クラス ハンドラーとインスタンス ハンドラー  
 ルーティング イベントでは、クラス リスナーとインスタンス リスナーという 2 種類のイベント リスナーが考慮されます。 型の特定が呼び出されるために、クラス リスナーが存在して<xref:System.Windows.EventManager> [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 、<xref:System.Windows.EventManager.RegisterClassHandler%2A>、静的コンス トラクターでまたは要素の基本クラスからクラス ハンドラー仮想メソッドをオーバーライドします。 インスタンス リスナーが特定のクラス インスタンス/要素を 1 つまたは複数のハンドラーがアタッチされたルーティング イベントへの呼び出しによって<xref:System.Windows.UIElement.AddHandler%2A>します。 既存の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ルーティング イベントは、呼び出しを行う<xref:System.Windows.UIElement.AddHandler%2A>の一部として、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]イベント ラッパーの追加{}および削除{}も方法は、イベントの実装、単純な[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アタッチのメカニズム属性構文を使用してイベント ハンドラーが有効になっているとします。 そのため、単純なであっても[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用量は、最終的に相当、<xref:System.Windows.UIElement.AddHandler%2A>呼び出します。  
  
 登録されたハンドラー実装があるかどうか、ビジュアル ツリー内の各要素がチェックされます。 ハンドラーはルート全体で呼び出される可能性があり、呼び出される順序は、ルーティング イベントのルーティング戦略によってあらかじめ決まっています。 たとえば、バブル ルーティング イベントでは、ルーティング イベントを発生させた要素と同じ要素にアタッチされているハンドラーが最初に呼び出されます。 その後、ルーティング イベントは次の親要素に "浮上" します。アプリケーションのルート要素に到達するまで、これが繰り返されます。  
  
 バブル ルートのルート要素の視点から見ると、イベント引数を処理済みとしてマークするハンドラーが、クラス処理や、よりルーティング イベント ソースに近い要素によって呼び出された場合、ルート要素のハンドラーは呼び出されません。これにより、イベント ルートは、ルート要素に到達する前に事実上短縮されます。 しかし、イベント ルートが完全に停止するわけではありません。クラス ハンドラーやインスタンス ハンドラーによってルーティング イベントが処理済みとしてマークされた場合にも呼び出されるように、特別な条件を使用してハンドラーが追加されている可能性があるためです。 詳細については、このトピックで後述する「[イベントが処理済みとしてマークされていても呼び出されるインスタンス ハンドラーの追加](#AddingInstanceHandlersthatAreRaisedEvenWhenEventsareMarkedHandled)」をご覧ください。  
  
 イベント ルートより深いレベルでは、クラスの特定のインスタンスに対して、複数のクラス ハンドラーが作用している可能性もあります。 なぜなら、ルーティング イベントのクラス処理モデルでは、クラスの階層構造に属するすべてのクラスが、各ルーティング イベントに対して独自のクラス ハンドラーをそれぞれ登録できるためです。 各クラス ハンドラーは内部ストアに追加され、アプリケーションのイベント ルートが構築されたときには、すべてのクラス ハンドラーがイベント ルートに追加されます。 クラス ハンドラーは、最派生クラスのクラス ハンドラーが最初に呼び出され、以下それぞれの基底クラスのクラス ハンドラーが順に呼び出されていくように、ルートに追加されます。 一般に、クラス ハンドラーは、既に処理済みとしてマークされたルーティング イベントにも反応するようには登録されません。 したがって、このクラス処理のしくみでは、次の 2 つの方法のいずれかを実現できます。  
  
- 派生クラスでは、基底クラスから継承されたクラス処理を補完するために、ルーティング イベントを処理済みとしてマークしないハンドラーを追加することができます。これは、派生クラスのハンドラーより後に基底クラスのハンドラーが呼び出されるためです。  
  
- 派生クラスでは、ルーティング イベントを処理済みとしてマークするクラス ハンドラーを追加することで、基底クラスのクラス処理を置き換えることができます。 この方法を使用する場合には注意が必要です。外観、状態のロジック、入力処理、コマンド処理などの部分で、基底コントロールが意図した設計と変わってしまう可能性があります。  
  
<a name="Class_Handling_of_Routed_Events"></a>   
## <a name="class-handling-of-routed-events-by-control-base-classes"></a>コントロールの基底クラスでのルーティング イベントのクラス処理  
 イベント ルートの各要素ノードでは、クラス リスナーに、その要素のどのインスタンス リスナーよりも先にルーティング イベントに応答する機会が与えられます。 このため、特定のコントロール クラス実装でそれ以上伝達されないようにルーティング イベントを抑制したり、ルーティング イベントに対してそのクラスの機能である特別な処理を提供したりするために、クラス ハンドラーが使用されることもあります。 たとえば、クラス固有の独自のイベントを発生させて、特定のクラスのコンテキストでユーザー入力の状態が持つ意味についてより具体的な情報をそのイベントに含めることができます。 この場合、そのクラス実装によって、より一般的なルーティング イベントが処理済みとしてマークされます。 クラス ハンドラーは、通常、追加のルーティングが呼び出されないように、共有イベント データが既にマークされたイベントの処理が、特殊なケースがあります、<xref:System.Windows.EventManager.RegisterClassHandler%28System.Type%2CSystem.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>署名ルーティング イベントがいるときでもを呼び出すためのクラス ハンドラーを登録します。処理済みとしてマークします。  
  
### <a name="class-handler-virtuals"></a>クラス ハンドラー仮想メソッド  
 一部の要素に、基本要素など、特に<xref:System.Windows.UIElement>、公開空"の * イベント"と"OnPreview\*イベント"パブリック ルーティング イベントの一覧に対応する仮想メソッド。 これらの仮想メソッドをオーバーライドすれば、そのルーティング イベントに対するクラス ハンドラーを実装することができます。 基本要素クラスのこれらの各クラス ハンドラーを使用してイベント ルーティングされるため、これらの仮想メソッドを登録する<xref:System.Windows.EventManager.RegisterClassHandler%28System.Type%2CSystem.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>前述のとおりです。 On\*Event 仮想メソッドを使用すると、対応するルーティング イベントのクラス処理の実装が大幅に簡略化され、それぞれの型の静的コンストラクターで特別な初期化を行う必要がなくなります。 クラス処理を追加するなど、<xref:System.Windows.UIElement.DragEnter>いずれかでイベント<xref:System.Windows.UIElement>派生クラスをオーバーライドすることで、<xref:System.Windows.UIElement.OnDragEnter%2A>仮想メソッド。 オーバーライドの中では、ルーティング イベントを処理する、他のイベントを発生させる、インスタンスの要素プロパティを変更する可能性があるクラス固有のロジックを開始するなどのアクションや、これらのアクションの任意の組み合わせを実行できます。 一般に、こうしたオーバーライドでは、イベントを処理済みとしてマークする場合でも、基本実装を呼び出す必要があります。 これらの仮想メソッドは基底クラスで定義されているため、基本実装を呼び出すことを強くお勧めします。 プロテクト仮想メソッドの標準的な呼び出しパターンでは、それぞれの仮想メソッドから、基本実装を呼び出す形になります。これは、ルーティング イベントのクラス処理の固有のしくみ (任意のインスタンスに対して、最派生クラスのハンドラーから基底クラスのハンドラーへという順で、クラス階層構造のすべてのクラスのクラス ハンドラーが呼び出される) を実質的に置き換え、同様の処理を実現することになります。 基本実装の呼び出しを省略するのは、基底クラスの処理ロジックを意図的に変更する必要がある場合だけにしてください。 基本実装をオーバーライド コードの前と後のどちらで呼び出すかは、それぞれの実装の性質によって異なります。  
  
#### <a name="input-event-class-handling"></a>入力イベント クラスの処理  
 すべてのクラス ハンドラー仮想メソッドは、すべての共有イベント データが処理済みとしてマークされていない場合にのみ呼び出されるように登録されます。 また、入力イベントに固有のしくみとして、一般に、トンネル バージョンとバブル バージョンのイベントが順番に発生し、両方のバージョンでイベント データが共有されます。 このため、トンネル バージョンとバブル バージョンの入力イベント用のクラス ハンドラーの特定のペアについて、イベントがすぐに処理済みとしてマークされないようにしたい場合があります。 イベントを処理済みとしてマークするようにトンネル クラス処理の仮想メソッドを実装すると、バブル クラスのハンドラーが呼び出されなくなります (トンネル イベントやバブル イベントに対して通常の方法で登録したインスタンス ハンドラーも呼び出されません)。  
  
 ノードでのクラス処理が完了すると、インスタンス リスナーが考慮されます。  
  
<a name="AddingInstanceHandlersthatAreRaisedEvenWhenEventsareMarkedHandled"></a>   
## <a name="adding-instance-handlers-that-are-raised-even-when-events-are-marked-handled"></a>イベントが処理済みとしてマークされていても呼び出されるインスタンス ハンドラーの追加  
 <xref:System.Windows.UIElement.AddHandler%2A>メソッドが呼び出されるイベント システムによってイベントがルートの処理中の要素に達するたびをマークするイベント データを他のハンドラーが既に調整されている場合でもハンドラーを追加することを許可する特定のオーバー ロードを提供イベントを処理します。 この方法は通常は使用されません。 一般にハンドラーは、イベントが要素ツリーのどこで処理されるかに関係なく、そのイベントによって影響を受ける可能性があるアプリケーション コードのすべての領域を調整するように作成することができます。これは、複数の結果が求められる場合でも同じです。 また、通常は、そのイベントに応答する必要がある要素は実際に 1 つだけなので、適切なアプリケーション ロジックが既に発生していることになります。 しかし、イベントが要素ツリーやコントロール複合の他の要素によって既に処理済みとしてマークされていても、要素ツリーのもっと上 (ルートによってはもっと下) にある他の要素のハンドラーを呼び出す必要がある場合もあります。そうした例外的なケースに対しては、`handledEventsToo` オーバーロードを使用することができます。  
  
#### <a name="when-to-mark-handled-events-as-unhandled"></a>処理済みのイベントを未処理としてマークする場合  
 一般に、処理済みとマークされているルーティング イベント マークしないでハンドルされていない (<xref:System.Windows.RoutedEventArgs.Handled%2A>戻して`false`) で動作するハンドラーによっても`handledEventsToo`します。 しかし、一部の入力イベントでは、高レベルのイベント表現と低レベルのイベント表現が重複することがあります。ツリー内のある位置では高レベルのイベントが取得され、別の位置では低レベルのイベントが取得される場合です。 たとえば、高度なキー イベントで子要素をリッスンなどを検討<xref:System.Windows.UIElement.TextInput>など、親要素が低レベルのイベントを待機中に<xref:System.Windows.UIElement.KeyDown>します。 親要素が低レベルのイベントを処理した場合、直感的には子要素が先にイベントを処理するはずであるにもかかわらず、高レベルのイベントが子要素で抑制されてしまうことがあります。  
  
 このような状況では、親要素と子要素の両方に低レベルのイベントのハンドラーを追加する必要があります。 この場合、子要素のハンドラー実装によって低レベルのイベントが処理済みとしてマークされる可能性がありますが、親要素のハンドラー実装がそれを再び未処理に設定して、ツリーのもっと上にある要素 (および高レベルのイベント) がそのイベントに応答できるようにします。 この状況は通常はあまりありません。  
  
<a name="Deliberately_Suppressing_Input_Events_for_Control"></a>   
## <a name="deliberately-suppressing-input-events-for-control-compositing"></a>コントロール複合の入力イベントの意図的な抑制  
 ルーティング イベントのクラス処理は、主に入力イベントと複合コントロールに対して使用されます。 複合コントロールは、その名のとおり、複数の実用的なコントロールまたはコントロールの基底クラスで構成されています。 コントロールを作成する際に、それらの各サブコンポーネントで発生するすべての入力イベントを 1 つにまとめて、コントロール全体が 1 つのイベント ソースとしてイベントを報告するように作る場合があります。 また、コンポーネントからのイベントを完全に抑制する場合や、コンポーネントで定義された別のイベント (より多くの情報を含むイベントや、より具体的な動作を表すイベント) に置き換える場合もあります。 コンポーネント作成者はすぐに表示されている標準的な例は、方法、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>のすべてのボタンのある直感的なイベントを解決する最終的に任意のマウス イベントの処理:<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 <xref:System.Windows.Controls.Button>基底クラス (<xref:System.Windows.Controls.Primitives.ButtonBase>) から派生した<xref:System.Windows.Controls.Control>から派生した順番<xref:System.Windows.FrameworkElement>と<xref:System.Windows.UIElement>、コントロールの入力の処理は、必要なイベント インフラストラクチャの大半、<xref:System.Windows.UIElement>レベル。 具体的には、<xref:System.Windows.UIElement>全般処理<xref:System.Windows.Input.Mouse> ボタン、アクションをなど、その境界内でマウス カーソルのヒット テストを処理し、最も一般的なに対する個別のイベントを提供するイベント<xref:System.Windows.UIElement.MouseLeftButtonDown>します。 <xref:System.Windows.UIElement> 仮想、空にも提供<xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A>の登録済みクラス ハンドラーとして<xref:System.Windows.UIElement.MouseLeftButtonDown>、および<xref:System.Windows.Controls.Primitives.ButtonBase>をオーバーライドします。 同様に、<xref:System.Windows.Controls.Primitives.ButtonBase>はクラスのハンドラー<xref:System.Windows.UIElement.MouseLeftButtonUp>します。 イベント データに渡される、上書き、実装をマークする<xref:System.Windows.RoutedEventArgs>インスタンスを設定して処理済みとして<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`、および同じイベント データがどのような継続するその他のクラス ハンドラーへのルートの残りの部分とインスタンス ハンドラーや、イベント setter にも また、<xref:System.Windows.Controls.Primitives.ButtonBase.OnMouseLeftButtonUp%2A>オーバーライドを次に発生させる、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 ほとんどのリスナーの最終結果になります、<xref:System.Windows.UIElement.MouseLeftButtonDown>と<xref:System.Windows.UIElement.MouseLeftButtonUp>イベントが「消滅」し代わりに置き換えられます<xref:System.Windows.Controls.Primitives.ButtonBase.Click>、ことがわかっているのでこのイベントの発生元を本当のボタンとその一部ではないからより多くの意味を保持するイベント複合はピース全体またはその他の要素から、ボタンのです。  
  
<a name="WorkingAroundEventSuppressionByControls"></a>   
### <a name="working-around-event-suppression-by-controls"></a>コントロールによるイベント抑制の回避  
 個々のコントロール内で行われるこのイベントの抑制の動作が、アプリケーションのイベント処理ロジックの全体的な目的の妨げになることがあります。 たとえば、何らかの理由のかどうかと、アプリケーションがハンドラーを<xref:System.Windows.UIElement.MouseLeftButtonDown>アプリケーションのルート要素にある、<xref:system.windows.uielement.mouseleftbuttondown> のボタンをマウスでクリックは呼び出しません<xref:System.Windows.UIElement.MouseLeftButtonDown>または<xref:System.Windows.UIElement.MouseLeftButtonUp>ルート レベルのハンドラー。 イベント自体は実際に "浮上" しました (既に説明したように、処理済みとしてマークされた後、イベント ルートは終了するのではなく、ルーティング イベント システムによってハンドラー呼び出しの動作が変更されます)。 ルーティング イベントに達すると、ボタン、<xref:System.Windows.Controls.Primitives.ButtonBase>クラス処理がマークされている、<xref:System.Windows.UIElement.MouseLeftButtonDown>を置き換えるためにの処理、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>詳細の意味を持つイベント。 そのため、任意の標準<xref:System.Windows.UIElement.MouseLeftButtonDown>へのルート ハンドラーをさらには呼び出されなくなります。 このような状況でもハンドラーが呼び出されるようにするには 2 つの方法があります。  
  
 最初の手法がハンドラーを使用して、意図的に追加するには、`handledEventsToo`のシグネチャ<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>します。 この方法には、イベント ハンドラーの追加をコードからしか行えず、マークアップからは行うことができないという制限があります。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でイベント属性の値としてイベント ハンドラー名を指定する単純な構文では、この動作は実現できません。  
  
 2 つ目の方法は、トンネル バージョンとバブル バージョンのルーティング イベントがペアになっている入力イベントでのみ使用できます。 これらのルーティング イベントについて、対応するプレビュー/トンネル ルーティング イベントにハンドラーを追加することができます。 そのルーティング イベントはルートからトンネリングを開始するため、アプリケーション要素ツリーの先祖要素のレベルにプレビュー ハンドラーをアタッチしておけば、イベントがボタン クラス処理コードによってインターセプトされなくなります。 この方法を使用する場合は、プレビュー イベントを処理済みとしてマークする際に注意が必要です。 指定の例の<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>としてイベントをマークされている場合、ルート要素で処理される<xref:System.Windows.RoutedEventArgs.Handled%2A>ハンドラーの実装では実際に抑制する、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 通常これは望ましくない動作です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.EventManager>
- [プレビュー イベント](preview-events.md)
- [カスタム ルーティング イベントを作成する](how-to-create-a-custom-routed-event.md)
- [ルーティング イベントの概要](routed-events-overview.md)
