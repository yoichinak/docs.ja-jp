---
title: ルーティング イベントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: a8ebb0259c1b5f73a2e0329cd1767b0431ba63a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171159"
---
# <a name="routed-events-overview"></a>ルーティング イベントの概要
このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのルーティング イベントの概念について説明します。 ここでは、ルーティング イベントの用語を定義し、要素ツリーを通じたルーティング イベントのルーティング方法、ルーティング イベントの処理方法、カスタム ルーティング イベントの作成方法について説明します。
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 ここでの説明は、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、オブジェクト指向プログラミング、ツリー形式として概念化できる [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素間のリレーションシップに関する基礎知識を前提にしています。 このトピックの例に従うには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し、ごく基本的な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションまたはページを作成できる必要があります。 詳細については、「[チュートリアル:初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)と[XAML の概要 (WPF)](xaml-overview-wpf.md)します。  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>ルーティング イベントとは  
 ルーティング イベントについては、機能または実装の観点から考えることができます。 どちらを便利と感じるかは個人によって異なるため、ここでは両方の見方を提示します。  
  
 機能の定義:ルーティング イベントには、イベントを発生させたオブジェクトだけではなく、要素ツリー内の複数のリスナーのハンドラーを呼び出すことができるイベントの一種です。  
  
 実装の定義:ルーティング イベントは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]のインスタンスによってサポートされるイベント、<xref:System.Windows.RoutedEvent>クラスし、によって処理される、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]イベント システム。  
  
 一般的な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションには、多数の要素が含まれます。 コードで作成したか [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の宣言によって作成したかにかかわらず、これらの要素は互いに要素ツリー リレーションシップにあります。 イベントのルーティングは、イベント定義に従って 2 つの方向のいずれかをたどることができますが、一般にはルーティングは発生元要素から要素ツリーに沿って "浮上" し、最終的には要素ツリーのルート (通常はページまたはウィンドウ) に到達します。 このバブル (浮上) の概念は、DHTML オブジェクト モデルで使用される概念と似ています。  
  
 たとえば、次のような単純な要素ツリーがあるとします。  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 この要素ツリーでは、次のようなものが生成されます。  
  
 ![[Yes]、[No]、[Cancel] ボタン](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 この簡略化された要素のツリーのソースで、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントは、<xref:System.Windows.Controls.Button>要素、およびどちら<xref:System.Windows.Controls.Button>がクリックされたイベントを処理する機会を持つ最初の要素です。 ハンドラーがアタッチされていない場合は、 <xref:System.Windows.Controls.Button> 、イベントは、イベントのバブルが上方にし、 <xref:System.Windows.Controls.Button> 、要素ツリーの親、<xref:System.Windows.Controls.StackPanel>します。 イベント バブル可能性のある、 <xref:System.Windows.Controls.Border>、し (表示されない) 要素ツリーのページ ルートを越えてとします。  
  
 つまり、このイベント ルート<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントします。  
  
 Button-->StackPanel-->Border-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>ルーティング イベントのトップレベルのシナリオ  
 ルーティング イベントの概念が生まれる契機となったシナリオと、このシナリオに通常の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントが適していない理由について簡単に説明します。  
  
 **コントロールの複合とカプセル化します。** さまざまなコントロールに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]リッチ コンテンツ モデルがあります。 たとえば、内の画像を配置することができます、<xref:System.Windows.Controls.Button>ボタンのビジュアル ツリーを効果的に拡張します。 ただし、追加したイメージにはボタンに応答すると、ヒット テストの動作が中断する必要がありますされません、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>技術的には、イメージの一部であるピクセルで、ユーザーがクリックした場合でも、そのコンテンツの。  
  
 **単一のハンドラー アタッチ ポイント:**[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]、複数の要素から発生することがあるイベントを処理する同じハンドラーを複数回アタッチする必要があります。 ルーティング イベントを使用すると、前の例に示したとおり、ハンドラーを一度だけアタッチし、必要に応じてハンドラーのロジックを使用してイベントの発生元を特定することができます。 たとえば、前に示した [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では次のようなハンドラーを使用します。  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **クラスの処理:** イベント許可クラスによって定義されている静的なハンドラーにルーティングされます。 このクラス ハンドラーでは、アタッチされたどのインスタンス ハンドラーよりも先にイベントを処理できます。  
  
 **リフレクションを使用せず、イベントを参照するには。** 特定のコードとマークアップ手法では、特定のイベントを識別する手段が必要です。 ルーティング イベントを作成、<xref:System.Windows.RoutedEvent>フィールドとして、識別子は、静的または実行時のリフレクションを必要としない信頼性の高いイベント識別テクニックを提供します。  
  
### <a name="how-routed-events-are-implemented"></a>ルーティング イベントの実装方法  
 ルーティング イベントは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]のインスタンスによってサポートされるイベント、<xref:System.Windows.RoutedEvent>クラスし、登録されている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システム。 <xref:System.Windows.RoutedEvent>として登録から取得されたインスタンスが保持される通常の`public` `static` `readonly`を登録し、そのため、ルーティング イベントを「所有」するクラスのフィールドのメンバー。 一意の名前を持つ [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント ("ラッパー" イベントとも呼ばれます) への接続は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントの `add` 実装と `remove` 実装をオーバーライドすることにより得られます。 通常、`add` と `remove` は、暗黙の既定のままにされ、そのイベントのハンドラーの追加や削除に言語固有の適切なイベント構文が使用されます。 ルーティング イベントのサポートと接続メカニズムは、依存関係プロパティは、どのような概念的には、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]によってサポートされるプロパティ、<xref:System.Windows.DependencyProperty>クラスし、登録されている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロパティ システム。  
  
 次の例では、カスタムの宣言`Tap`など、登録と露出のルーティング イベント、<xref:System.Windows.RoutedEvent>識別子フィールドと`add`と`remove`の実装、 `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベント。  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>ルーティング イベント ハンドラーと XAML  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してイベントのハンドラーを追加するには、イベント リスナーである要素の属性としてイベント名を宣言します。 属性の値は、実装したハンドラー メソッドの名前です。このメソッドは、分離コード ファイルの部分クラス内に存在する必要があります。  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント ハンドラーを追加する [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文は、ルーティング イベント ハンドラーを追加する構文と同じです。これは、実際にはハンドラーを [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベント ラッパーに追加しているためです。このラッパーの内部にルーティング イベント実装が存在します。 イベント ハンドラーを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で追加する方法の詳細については、「[XAML の概要 (WPF)](xaml-overview-wpf.md)」を参照してください。  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>ルーティング方法  
 ルーティング イベントは、3 つのルーティング方法のいずれかを使用します。  
  
-   **バブル。** イベント ソースのイベント ハンドラーが呼び出されます。 ルーティング イベントは、次に、要素ツリー ルートに到達するまで、連続する親要素にルーティングします。 ほとんどのルーティング イベントでは、このバブル ルーティング方法を使用します。 バブル ルーティング イベントは、一般に個別のコントロールまたはその他の UI 要素からの入力や状態変化を報告するために使用されます。  
  
-   **直接。** ソース要素自体の応答としてハンドラーを呼び出す機会が与えられます。 これは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] がイベントに使用する "ルーティング" と似ています。 標準とは異なり、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベント、クラス処理をサポートするルーティング イベントを直接 (クラス処理を以下のセクションで説明します) で使用できると<xref:System.Windows.EventSetter>と<xref:System.Windows.EventTrigger>します。  
  
-   **トンネリングします。** 最初に、要素ツリーのルートにあるイベント ハンドラーが呼び出されます。 ルーティング イベントは、次に、経路沿いにルーティング イベント ソース (ルーティング イベントを発生させた要素) のノード要素まで、連続する子要素間の経路をたどります。 多くの場合にトンネル ルーティング イベントは、コントロールの複合部分として使用または処理されます。たとえば、複合部分で発生したイベントは、完全なコントロールに固有のイベントによって意図的に抑止されるか置き換えられます。 多くの場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] から提供される入力イベントはトンネルとバブルのペアとして実装されます。 トンネル イベントは、このペアに使用される名前付け規則から、プレビュー イベントと呼ばれることもあります。  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>ルーティング イベントを使用する理由  
 アプリケーションを開発するときに、処理するイベントがルーティング イベントとして実装されているかどうかを常に確認する必要はありません。 ルーティング イベントの動作は独特ですが、イベントを発生元の要素で処理する限り、動作はあまり表面には見えません。  
  
 ルーティング イベントが効果を発揮するのは、共通ハンドラーを共通ルートに定義する、独自のコントロールを複合化する、カスタム コントロール クラスを定義するなどの、特定のシナリオの場合です。  
  
 ルーティング イベント リスナーとルーティング イベント ソースは、階層内で共通イベントを共有する必要はありません。 すべて<xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>どのルーティング イベントのイベント リスナーを指定できます。 したがって、ワーキング [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] セットで使用可能なすべてのルーティング イベントを概念的 "インターフェイス" として使用できます。これにより、アプリケーション内の異なる要素間でイベント情報を交換できます。 ルーティング イベントのこの "インターフェイス" 概念は、特に入力イベントに当てはまります。  
  
 また、ルーティング イベントは、要素ツリー間の通信にも使用できます。これは、イベントのイベント データが経路上の各要素に永続的に保持されるためです。 ある要素でイベント データの一部を変更した場合、この変更は経路上の次の要素で使用できます。  
  
 ルーティングの面以外でも、特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントを標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントではなくルーティング イベントとして実装する理由が他に 2 つあります。 独自のイベントを実装している場合は、次の原則も考慮します。  
  
-   特定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]などのスタイルとテンプレートの機能<xref:System.Windows.EventSetter>と<xref:System.Windows.EventTrigger>参照先のイベントのルーティング イベントである必要があります。 これは、前に説明したイベント識別子シナリオです。  
  
-   ルーティング イベントは、クラス処理機構をサポートしています。この機構により、クラスに静的メソッドを指定して、登録されたインスタンス ハンドラーがルーティング イベントにアクセスする前にこの静的メソッドでイベントを処理することができます。 インスタンスでのイベント処理によって誤って抑止されずにイベント駆動のクラス動作を適用できるため、これはコントロールをデザインするときに便利です。  
  
 前に示した一連の考慮事項については、このトピックのセクションで個別に説明します。  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>ルーティング イベントのイベント ハンドラーの追加と実装  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でイベント ハンドラーを追加するには、次の例に示すように、単にイベント名を要素に属性として追加し、属性の値として、適切なデリゲートを実装するイベント ハンドラーの名前を設定します。  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor` 処理するコードが含まれる実装済みハンドラーの名前を指定します、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 `b1SetColor` 同じシグネチャが必要、<xref:System.Windows.RoutedEventHandler>イベント ハンドラーのデリゲートであるデリゲートを<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 すべてのルーティング イベント ハンドラー デリゲートの 1 番目のパラメーターでは、イベント ハンドラーの追加先の要素を指定し、2 番目のパラメーターでは、イベントのデータを指定します。  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler> 基本的なルーティング イベント ハンドラー デリゲートです。 特定のコントロールやシナリオに特化したルーティング イベントの場合、ルーティング イベント ハンドラーに使用するデリゲートも、より特化したものとなることがあるため、特別なイベント データを転送できます。 たとえば、一般的な入力のシナリオで処理を<xref:System.Windows.UIElement.DragEnter>ルーティング イベント。 ハンドラーを実装する必要があります、<xref:System.Windows.DragEventHandler>を委任します。 最も固有のデリゲートを使用すると、処理することができます、<xref:System.Windows.DragEventArgs>ハンドラーと読み取り、<xref:System.Windows.DragEventArgs.Data%2A>プロパティで、ドラッグ操作のクリップボード ペイロードが含まれています。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してイベント ハンドラーを要素に追加する方法の詳細な例については、「[ルーティング イベントを処理する](how-to-handle-a-routed-event.md)」を参照してください。  
  
 コードで作成されたアプリケーションでルーティング イベントのハンドラーを追加するのは簡単です。 ルーティング イベント ハンドラーは、ヘルパー メソッドを通じて常に追加する<xref:System.Windows.UIElement.AddHandler%2A>(同じメソッドを呼び出す既存のバックアップである`add`)。ただし、一般に既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ルーティング イベントは `add` と `remove` のロジックのサポート実装を持つため、言語固有のイベント構文でルーティング イベントにハンドラーを追加できます。ヘルパー メソッドを使用するよりも、この構文の方がわかりやすく処理できます。 ヘルパー メソッドの使用例を次に示します。  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 例を次に示します、C#演算子 (Visual Basic の逆参照を処理するための若干異なる演算子構文がある)。  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 コードでイベント ハンドラーを追加する方法の例については、「[コードを使用してイベント ハンドラーを追加する](how-to-add-an-event-handler-using-code.md)」を参照してください。  
  
 Visual Basic を使用している場合は、使用することも、`Handles`ハンドラーの宣言の一部としてハンドラーを追加するキーワード。 詳細については、「[Visual Basic と WPF のイベント処理](visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>処理済みの概念  
 すべてのルーティング イベントは、一般的なイベント データ基底クラスを共有<xref:System.Windows.RoutedEventArgs>します。 <xref:System.Windows.RoutedEventArgs> 定義、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティは、ブール値をとります。 目的、<xref:System.Windows.RoutedEventArgs.Handled%2A>プロパティは、ルーティング イベントとしてマークする経路上のすべてのイベント ハンドラーを有効にする、*処理*の値を設定して<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`します。 経路上の 1 つの要素のハンドラーで処理された後、共有イベント データが経路上の各リスナーに再び報告されます。  
  
 値<xref:System.Windows.RoutedEventArgs.Handled%2A>影響ルーティング イベントが報告されるかをたどる際の処理方法をさらに、経路上。 場合<xref:System.Windows.RoutedEventArgs.Handled%2A>は`true`イベントのルーティング イベントの場合は、その他の要素にルーティング イベントをリッスンするハンドラーのデータは通常呼び出されませんの特定のイベント インスタンス。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でアタッチされたハンドラーの場合も、`+=` や `Handles` など、言語固有のイベント ハンドラー アタッチ構文によって追加されたハンドラーの場合も同様です。 ハンドラーの最も一般的なシナリオ用には、イベントを設定して処理済みとしてマーク<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`が「停止」トンネル ルーティングやバブル ルーティングでは、いずれか、および任意の時点におけるルート クラス ハンドラーによって処理されるイベントをルーティングします。  
  
 ただし、というリスナー ハンドラーを実行できるルーティング イベントへの応答で"handledEventsToo"機構がある場所<xref:System.Windows.RoutedEventArgs.Handled%2A>は`true`イベント データ。 つまり、イベント データを処理済みとしてマークしてもイベントのルーティングは完全には停止されません。 コードでは、または handledEventsToo 機構を使用することができますのみ、 <xref:System.Windows.EventSetter>:  
  
-   一般的な動作する言語固有のイベント構文を使用する代わりに、コードで[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントを呼び出し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]メソッド<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>ハンドラーを追加します。 `handledEventsToo` の値として `true` を指定します。  
  
-   <xref:System.Windows.EventSetter>、設定、<xref:System.Windows.EventSetter.HandledEventsToo%2A>属性を`true`します。  
  
 動作に加えを<xref:System.Windows.RoutedEventArgs.Handled%2A>状態での概念のルーティング イベントを生成<xref:System.Windows.RoutedEventArgs.Handled%2A>イベント ハンドラーのコードを記述し、アプリケーションを設計する必要がある方法に影響があります。 考えることができます<xref:System.Windows.RoutedEventArgs.Handled%2A>ルーティング イベントによって公開される単純なプロトコルとして。 方法の概念設計が、このプロトコルを使用する方法に正確には、値<xref:System.Windows.RoutedEventArgs.Handled%2A>使用するものでは、次に示します。  
  
-   ルーティング イベントが処理済みとしてマークされている場合、このイベントを経路上の他の要素でもう一度処理する必要はありません。  
  
-   ルーティング イベントが処理済みとしてマークされていないかどうかは、他のリスナーが経路は、ハンドラーまたはイベント データを操作し、設定が登録されている選択済みハンドラーが登録するいずれかを選択した<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`します。 (または、現在のリスナーが経路上の出発点である可能性もあります)。現在のリスナーのハンドラーでは、次の 3 つのアクションを選択できます。  
  
    -   アクションをまったく行いません。イベントは未処理のまま、次のリスナーにルーティングされます。  
  
    -   イベントに応答してコードを実行しますが、実行したアクションはイベントを処理済みとしてマークするのに十分とは確定されません。 イベントは次のリスナーにルーティングされます。  
  
    -   イベントに応答してコードを実行します。 実行したアクションはイベントを処理済みとしてマークするのに十分と考えられるため、ハンドラーに渡されたイベント データでイベントを処理済みとしてマークします。 イベントは、次のリスナーにまだルーティング<xref:System.Windows.RoutedEventArgs.Handled%2A> = `true`イベント データ、のみで`handledEventsToo`リスナーにさらにハンドラーを呼び出す機会があります。  
  
 この概念設計は前に説明したルーティング動作により補強: 経路上の以前のハンドラーが既にを設定した場合でも呼び出されるルーティングイベントのハンドラーをアタッチするより難しくなります(ただしコードやスタイルでは可能)は<xref:System.Windows.RoutedEventArgs.Handled%2A>に`true`します。  
  
 詳細については<xref:System.Windows.RoutedEventArgs.Handled%2A>、クラス処理のルーティング イベントとルーティング イベントとしてマークする場合に関する推奨事項が適切な<xref:System.Windows.RoutedEventArgs.Handled%2A>を参照してください[ルーティング イベントの処理済み、およびクラス処理としてのマーキング](marking-routed-events-as-handled-and-class-handling.md)します。  
  
 アプリケーションでは、バブル ルーティング イベントを発生元のオブジェクトで処理するのが一般的であり、イベントのルーティング特性についてはまったく考慮されません。 ただし、その場合でも、イベント データでルーティング イベントを処理済みとしてマークすることをお勧めします。そうすれば、要素ツリーの後方にある要素でそれと同じルーティング イベントにハンドラーがアタッチされている場合に起こりうる、予期しない副作用を回避できます。  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>クラス ハンドラー  
 いくつかの方法で派生するクラスを定義するかどうか<xref:System.Windows.DependencyObject>も定義し、クラスの宣言または継承されたイベント メンバーであるルーティング イベントのクラス ハンドラーをアタッチできます。 ルーティング イベントが経路上の要素インスタンスに到達すると、クラスのインスタンスにアタッチされたどのインスタンス リスナー ハンドラーよりも先に、クラス ハンドラーが呼び出されます。  
  
 一部の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールには、特定のルーティング イベントに対する固有のクラス処理が存在します。 このため、ルーティング イベントが発生していないように見えても、実際にはクラス処理されている場合があります。また、特定の手法を使用した場合、インスタンス ハンドラーでも処理される可能性があります。 また、多くの基底クラスとコントロールからは、クラス処理の動作をオーバーライドするために使用できる仮想メソッドが提供されています。 望ましくないクラス処理の回避方法とカスタム クラスを使った独自のクラス処理定義方法の詳細については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>WPF の添付イベント  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 言語は、*添付イベント*と呼ばれる特殊な種類のイベントも定義します。 添付イベントを使用して、任意の要素に特定のイベントのハンドラーを追加できます。 イベントを処理する要素が添付イベントを定義または継承する必要はありません。また、イベントを発生させる可能性のあるオブジェクトでも、インスタンスを処理する添付先でも、そのイベントを定義したりクラス メンバーとして "所有" したりする必要はありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 入力システムでは、添付イベントを多用します。 ただし、ほとんどすべての添付イベントは基本要素間で転送されます。 入力イベントは、基本要素クラスのメンバーである、非添付のルーティング イベントに等しいものとして表されます。 たとえば、基になる添付イベント<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>より簡単に処理できる、特定の<xref:System.Windows.UIElement>を使用して<xref:System.Windows.UIElement.MouseDown>を<xref:System.Windows.UIElement>か、添付イベント構文を処理するのではなくで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]またはコード。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付イベントの詳細については、「[添付イベントの概要](attached-events-overview.md)」を参照してください。  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>XAML の修飾イベント名  
 *typename*.*eventname* 添付イベント構文に似ているが厳密に言えば添付イベントの使用方法ではない、もう 1 つの構文使用方法では、子要素で発生したルーティング イベントのハンドラーをアタッチします。 対応するルーティング イベントが共通の親要素にメンバーとして含まれない場合でも、共通の親要素にハンドラーをアタッチしてイベントのルーティングを利用します。 次の例をもう一度検討します。  
  
 [!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 ここで、親要素のリスナーがハンドラーを追加する位置は、<xref:System.Windows.Controls.StackPanel>します。 ただし、宣言されたから発生するルーティング イベントのハンドラーを追加するには、<xref:System.Windows.Controls.Button>クラス (<xref:System.Windows.Controls.Primitives.ButtonBase>を使用できますが、実際には、<xref:System.Windows.Controls.Button>継承により)。 <xref:System.Windows.Controls.Button> イベントがいずれかに接続するルーティング イベントのルーティング イベント システムによりハンドラーを「所有」<xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>のリスナーをアタッチでした。 それ以外の場合インスタンス リスナー、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]イベント。 これらの修飾イベント属性名の既定の xmlns 名前空間は、通常、既定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns 名前空間ですが、カスタム ルーティング イベント用のプレフィックスを持つ名前空間を指定することもできます。 xmlns の詳細については、「[XAML 名前空間および WPF XAML の名前空間の割り当て](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>WPF の入力イベント  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プラットフォームにおけるルーティング イベントの主な使用例として、入力イベントがあります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、トンネル ルーティング イベントの名前に "Preview" をプレフィックスとして付加するのが慣例です。 入力イベントは、多くの場合、バブル イベントとトンネル イベントがペアになって構成されます。 たとえば、<xref:System.Windows.ContentElement.KeyDown>イベントと<xref:System.Windows.ContentElement.PreviewKeyDown>イベント、前者がバブル入力イベント、同じシグネチャであるし、入力イベントのトンネリング、後者が。 入力イベントによっては、バブル形式だけ、または直接ルーティング形式だけを持つ場合もあります。 このドキュメント内のルーティング イベントに関するトピックでは、他のルーティング方法を使用する類似ルーティング イベントがある場合は相互参照を示します。またマネージド リファレンス ページでは、各ルーティング イベントのルーティング方法について説明します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マウス ボタンを押すなどの入力から 1 人のユーザー アクション シーケンス内のペアの両方のルーティング イベントが発生するように、ペアになっている入力イベントが実装されます。 まず、トンネル イベントが発生し、その経路をたどります。 次に、バブル イベントが発生し、その経路をたどります。 2 つのイベントは、ため、文字どおり同じイベント データ インスタンスを共有、<xref:System.Windows.UIElement.RaiseEvent%2A>バブル イベントを実装するクラスでメソッドの呼び出しは、トンネル イベントからイベント データをリッスンし、新しい発生したイベントでそれを再利用します。 トンネル イベントのハンドラーを持つリスナーは、ルーティング イベントを処理済みとしてマークする機会を最初に与えられます (最初がクラス ハンドラーで、その次がインスタンス ハンドラーです)。 トンネル経路上の要素がルーティング イベントを処理済みとしてマークした場合、処理済みイベントのデータがバブル イベントに送信され、同等のバブル入力イベントにアタッチされた標準のハンドラーは呼び出されません。 外部からは、処理済みのバブル イベントが発生しなかったように見えます。 この処理動作が便利なのは、コントロールの複合化の場合です。この場合、すべてのヒット テスト ベースの入力イベントまたはフォーカス ベースの入力イベントが、コントロールの複合部分ではなく最終的なコントロールから報告される必要があるためです。 最終的なコントロール要素は、複合のルート近くにあるため、トンネル イベントを最初にクラス処理し、コントロール クラスをサポートするコードの一部としてそのルーティング イベントをコントロール固有のイベントで "置き換える" 機会があります。  
  
 入力イベント処理のしくみを説明するため、次の入力イベント例について考えます。 次のツリー図の `leaf element #2` は、`PreviewMouseDown` と `MouseDown` の両方のイベントの発生元です。  
  
 ![イベント ルーティング ダイアグラム](./media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
入力イベントのバブルとトンネル  
  
 次の順序でイベントが処理されます。  
  
1.  `PreviewMouseDown` (トンネル) のルート要素。  
  
2.  `PreviewMouseDown` (トンネル) 中間要素 #1。  
  
3.  `PreviewMouseDown` (トンネル) ソース要素 #2。  
  
4.  `MouseDown` (バブル) ソース要素 #2。  
  
5.  `MouseDown` (バブル) 中間要素 #1。  
  
6.  `MouseDown` (バブル) のルート要素。  
  
 ルーティング イベント ハンドラー デリゲートは、2 つのオブジェクトへの参照を提供します。その 2 つは、イベントを発生したオブジェクトと、ハンドラーが呼び出されたオブジェクトです。 ハンドラーが呼び出されたオブジェクトは、`sender` パラメーターによって報告されるオブジェクトです。 イベントが発生した最初のオブジェクトがによって報告された、<xref:System.Windows.RoutedEventArgs.Source%2A>イベント データのプロパティ。 ルーティング イベントはまだ発生し、場合、同一のオブジェクトによって処理される`sender`と<xref:System.Windows.RoutedEventArgs.Source%2A>は同一 (これは、手順 3. および 4. イベントの一覧の例の処理の場合)。  
  
 トンネルとバブル、により親要素が入力イベントを受信場所、<xref:System.Windows.RoutedEventArgs.Source%2A>要素を子の 1 つです。 アクセスして、ソース要素を識別できますが、ソース要素を知っておく必要が、<xref:System.Windows.RoutedEventArgs.Source%2A>プロパティ。  
  
 通常、入力イベントがマークされると<xref:System.Windows.RoutedEventArgs.Handled%2A>、さらに、ハンドラーは呼び出されません。 一般に、入力イベントが意味することをアプリケーション固有の方法で論理処理するハンドラーが呼び出されたら、直ちに入力イベントを処理済みとしてマークする必要があります。  
  
 例外に関する一般的なこのステートメントを<xref:System.Windows.RoutedEventArgs.Handled%2A>状態が意図的に無視する登録されているイベント ハンドラーの入力を<xref:System.Windows.RoutedEventArgs.Handled%2A>イベント データの状態は、どちらの経路上でも呼び出されます。 詳細については、「[プレビュー イベント](preview-events.md)」または「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
 トンネル イベントとバブル イベント間の共有イベント データ モデルの概念も、トンネル イベントとバブル イベントの順次発生の概念も、すべてのルーティング イベントに当てはまるとは限りません。 そうした動作は、ペアになった入力イベントを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 入力デバイスがどのように発生させ接続するよう選択するかによって、個別に実装されます。 独自の入力イベントの実装は高度なシナリオですが、独自の入力イベントでそうしたモデルを採用することもできます。  
  
 一部のクラスでは、特定の入力イベントをクラス処理します。通常、その目的は、ユーザーによる特定の入力イベントの意味をそのコントロール内で再定義して、新しいイベントを発生させることです。 詳細については、「[ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)」を参照してください。  
  
 入力と一般的なアプリケーション シナリオにおける入力とイベントの対話方法の詳細については、「[入力の概要](input-overview.md)」を参照してください。  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetter と EventTrigger  
 スタイルで、いくつかの事前宣言を含めることができます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]イベント処理を使用して、マークアップでの構文、<xref:System.Windows.EventSetter>します。 そのスタイルを適用すると、参照されているハンドラーが、スタイルが適用されるインスタンスに追加されます。 宣言することができます、<xref:System.Windows.EventSetter>ルーティング イベントに対してのみです。 次に例を示します。 ここで参照されている `b1SetColor` メソッドは、分離コード ファイル内にあります。  
  
 [!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 ここでの利点は、スタイルが多くのアプリケーションでは、いずれかのボタンに適用されるその他の情報が含まれる可能性があることと、<xref:System.Windows.EventSetter>そのスタイルの一部であるマークアップ レベルでもコードを再利用を促進します。 また、<xref:System.Windows.EventSetter>ハンドラー一歩一般的なアプリケーションとページのマークアップのメソッド名を抽象化します。  
  
 ルーティング イベントとアニメーション機能を結合する別の特殊な構文[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、<xref:System.Windows.EventTrigger>します。 同様<xref:System.Windows.EventSetter>、ルーティング イベントだけを使用できます、<xref:System.Windows.EventTrigger>します。 通常、 <xref:System.Windows.EventTrigger> 、スタイルの一部として宣言されていますが、<xref:System.Windows.EventTrigger>の一部としてページ レベルの要素でも宣言する、<xref:System.Windows.FrameworkElement.Triggers%2A>コレクション、または、 <xref:System.Windows.Controls.ControlTemplate>。 <xref:System.Windows.EventTrigger>を指定することができます、<xref:System.Windows.Media.Animation.Storyboard>ルーティング イベントに達するたびにそのルート上で要素を実行が宣言、<xref:System.Windows.EventTrigger>そのイベント。 利点、<xref:System.Windows.EventTrigger>だけイベントを処理およびに開始する原因となる既存のストーリー ボードを<xref:System.Windows.EventTrigger>ストーリー ボードと、実行時の動作の制御が向上します。 詳細については、「[開始後のストーリーボードをイベント トリガーを使用して制御する](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)」を参照してください。  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>ルーティング イベントの詳細  
 このトピックの主な目的は、ルーティング イベントの基本概念を説明し、さまざまな基本要素や基本コントロール内の既存のルーティング イベントに応答する方法とタイミングについて解説することです。 しかし、独自のルーティング イベントを、特殊なイベント データ クラスやデリゲートなど、必要な支援機能すべてと共に、カスタム クラスに作成することもできます。 ルーティング イベントの所有者が任意のクラスを指定できますが、ルーティング イベントの発生しによって処理される必要があります<xref:System.Windows.UIElement>または<xref:System.Windows.ContentElement>便利にするためには、クラスを派生します。 カスタム イベントの詳細については、「[カスタム ルーティング イベントを作成する](how-to-create-a-custom-routed-event.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](marking-routed-events-as-handled-and-class-handling.md)
- [入力の概要](input-overview.md)
- [コマンド実行の概要](commanding-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [WPF のツリー](trees-in-wpf.md)
- [弱いイベント パターン](weak-event-patterns.md)
