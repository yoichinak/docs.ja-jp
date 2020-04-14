---
title: コントロールの作成の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: 2326520039085beb5f5294e23db67b67f9d7d7da
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243272"
---
# <a name="control-authoring-overview"></a>コントロール作成の概要

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コントロール モデルの機能拡張により、新しいコントロールを作成する必要性が大幅に削減されます。 ただし、場合によっては、カスタム コントロールを作成する必要があります。 このトピックでは、カスタム コントロールを作成する必要性を最小限に抑える機能と、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまなコントロール作成モデルについて説明します。 また、新しいコントロールを作成する方法も示します。

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>新しいコントロールの作成に代わる方法

従来は、既存のコントロールをカスタマイズする場合、背景色、境界線の幅、フォントのサイズなど、コントロールの標準プロパティを変更するなどの範囲に制限されていました。 これらの定義済みのパラメーター以外に、コントロールの外観や動作にまでカスタマイズを拡張しようとすると、通常、既存のコントロールを継承し、コントロールを描画するメソッドをオーバーライドして、新しいコントロールを作成する必要がありました。  その方法は今でも選択できますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の場合、リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用して、既存のコントロールをカスタマイズできます。 新しいコントロールを作成しなくても、これらの機能を使用して、カスタマイズされた一貫性のあるエクスペリエンスを得られる方法としては、次のような例が挙げられます。

- **リッチ コンテンツ。** 標準の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くがリッチ コンテンツをサポートしています。 たとえば、 の<xref:System.Windows.Controls.Button>content プロパティは 型<xref:System.Object>、 の場合、理論的には何でも<xref:System.Windows.Controls.Button>表示できます。  ボタンに<xref:System.Windows.Controls.TextBlock>イメージとテキストを表示するには、イメージと a を に<xref:System.Windows.Controls.StackPanel>追加して、<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.ContentControl.Content%2A>プロパティに割り当てます。 コントロールには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の視覚的要素と任意のデータを表示できるため、複雑な視覚化をサポートするために、新しいコントロールを作成したり、既存のコントロールを変更したりする必要性が少なくなります。 のコンテンツ モデル<xref:System.Windows.Controls.Button>と他のコンテンツ モデルの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細については、「 [WPF コンテンツ モデル](wpf-content-model.md)」を参照してください。

- **スタイル。** A<xref:System.Windows.Style>は、コントロールのプロパティを表す値のコレクションです。 スタイルを使用すると、新しいコントロールを作成しなくても、必要なコントロールの外観と動作を備えた再利用可能な表現を作成できます。 たとえば、すべての<xref:System.Windows.Controls.TextBlock>コントロールに赤、Arial フォント、フォント サイズ 14 を使用する必要があるとします。 そこで、リソースとしてスタイルを作成し、それに応じて、適切なプロパティを設定します。 その後<xref:System.Windows.Controls.TextBlock>、アプリケーションに追加する場合は、すべての外観が同じになります。

- **データ テンプレート。** A<xref:System.Windows.DataTemplate>を使用すると、コントロール上でのデータの表示方法をカスタマイズできます。 たとえば、 を<xref:System.Windows.DataTemplate>使用して、 でのデータの表示方法を<xref:System.Windows.Controls.ListBox>指定できます。  この例については、「[データ テンプレートの概要](../data/data-templating-overview.md)」を参照してください。  データの外観をカスタマイズするだけでなく、UI 要素を<xref:System.Windows.DataTemplate>含めることができ、カスタム UI に多くの柔軟性を提供します。  たとえば、 を<xref:System.Windows.DataTemplate>使用して、 各項目に<xref:System.Windows.Controls.ComboBox>チェック ボックスを含む を作成できます。

- **コントロール テンプレート。** の多くの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールは<xref:System.Windows.Controls.ControlTemplate>、 コントロールの構造と外観を定義するために使用され、コントロールの外観とコントロールの機能を分離します。 コントロールを再定義することで、コントロールの外観を大幅に<xref:System.Windows.Controls.ControlTemplate>変更できます。  たとえば、信号機のような外観のコントロールが必要だとします。 このコントロールのユーザー インターフェイスと機能は単純です。  コントロールは 3 つの円で構成され、一度に点灯するのはそのうちの 1 つだけです。 いくつかの反射の後、一度に選択<xref:System.Windows.Controls.RadioButton>されている 1 つの機能しか提供していないことに気付くかもしれませんが、既定の外観は<xref:System.Windows.Controls.RadioButton>、信号のライトのようには見えなくなります。  コントロール<xref:System.Windows.Controls.RadioButton>テンプレートを使用して外観を定義するため、コントロールの要件に合わせて<xref:System.Windows.Controls.ControlTemplate>を再定義し、ラジオ ボタンを使用してストップライトを作成できます。

  > [!NOTE]
  > a<xref:System.Windows.Controls.RadioButton>は を<xref:System.Windows.DataTemplate>使用できますが<xref:System.Windows.DataTemplate>、この例では a は十分ではありません。  コントロール<xref:System.Windows.DataTemplate>のコンテンツの外観を定義します。 の<xref:System.Windows.Controls.RadioButton>場合、コンテンツは、選択されているかどうかを示す円の右側に表示<xref:System.Windows.Controls.RadioButton>される内容です。  信号機の例では、オプション ボタンに必要なのは "点灯" する円だけです。 ストップライトの外観要件は<xref:System.Windows.Controls.RadioButton>、 の既定の外観とは非常に異なるため、<xref:System.Windows.Controls.ControlTemplate>を再定義する必要があります。  一般に<xref:System.Windows.DataTemplate>a はコントロールのコンテンツ (またはデータ) を定義するために使用<xref:System.Windows.Controls.ControlTemplate>され、a はコントロールの構造を定義するために使用されます。

- **トリガー。** A<xref:System.Windows.Trigger>を使用すると、新しいコントロールを作成せずに、コントロールの外観と動作を動的に変更できます。 たとえば、アプリケーションに複数<xref:System.Windows.Controls.ListBox>のコントロールがあり、各項目を選択したときに項目<xref:System.Windows.Controls.ListBox>を太字にして赤にする場合を考えます。 最初の本能は、選択した項目の外観を変更する<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>メソッドを継承してオーバーライドするクラスを作成することですが、選択した項目の外観を変更<xref:System.Windows.Controls.ListBoxItem>するスタイルにトリガーを追加する方が良いでしょう。 トリガーを使用すると、プロパティ値を変更したり、プロパティ値に基づいた処理を実行したりできます。 イベント<xref:System.Windows.EventTrigger>が発生したときにアクションを実行できます。

スタイル、テンプレート、トリガーの詳細については、「[スタイルとテンプレート](styling-and-templating.md)」を参照してください。

一般に、既存のコントロールと同じ機能を持ち、外観が異なるコントロールが必要な場合は、このセクションで説明した方法のいずれかを使用して、既存のコントロールの外観を変更できないかどうかをまず検討することをお勧めします。

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>コントロール作成モデル

リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用すると、新しいコントロールを作成する必要性が最小限に抑えられます。 ただし、新しいコントロールを作成する必要がある場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種のコントロール作成モデルを理解することが重要です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、コントロールを作成するための一般的なモデルが 3 つあり、各モデルはそれぞれ異なる機能と柔軟性レベルを備えています。 3 つのモデルの基本クラスは<xref:System.Windows.Controls.UserControl>、 <xref:System.Windows.Controls.Control>、<xref:System.Windows.FrameworkElement>および です。

### <a name="deriving-from-usercontrol"></a>UserControl からの派生

でコントロールを作成する最も簡単な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]方法は、<xref:System.Windows.Controls.UserControl>から派生することです。 から<xref:System.Windows.Controls.UserControl>継承するコントロールを構築する場合は、 に既存のコンポーネントを<xref:System.Windows.Controls.UserControl>追加し、 コンポーネントに名前を付け[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、イベント ハンドラを参照します。 次に、指定の要素を参照し、コードでイベント ハンドラーを定義します。 この開発モデルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーション開発に使用されるモデルとよく似ています。

正しく構築されていれば、<xref:System.Windows.Controls.UserControl>はリッチコンテンツ、スタイル、トリガの利点を活用できます。 ただし、コントロールが から<xref:System.Windows.Controls.UserControl>継承されている場合、コントロールを使用するユーザーは、 または<xref:System.Windows.DataTemplate>外観<xref:System.Windows.Controls.ControlTemplate>をカスタマイズできません。  テンプレートをサポートするカスタム コントロール<xref:System.Windows.Controls.Control>を作成するには、クラスまたはその派生クラス (<xref:System.Windows.Controls.UserControl>以外) から派生させる必要があります。

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl からの派生の利点

以下のすべてが当<xref:System.Windows.Controls.UserControl>てはまる場合に派生することを検討してください。

- アプリケーションの構築と同じ方法でコントロールをビルドする必要がある場合。

- コントロールが既存のコンポーネントのみで構成されている場合。

- 複雑なカスタマイズをサポートする必要がない場合。

### <a name="deriving-from-control"></a>Control からの派生

クラスから派生する<xref:System.Windows.Controls.Control>モデルは、既存[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のコントロールの大部分で使用されるモデルです。 <xref:System.Windows.Controls.Control>クラスから継承するコントロールを作成する場合は、テンプレートを使用して外観を定義します。 これにより、操作ロジックと視覚的表現とが分離されます。 イベントの代わりにコマンドとバインディングを使用し、可能な<xref:System.Windows.Controls.ControlTemplate>限り要素を参照しないようにすることで、UI とロジックの分離を確実に行うことができます。  コントロールの UI とロジックが適切に切り離されている場合、コントロールのユーザーはコントロールを再定義<xref:System.Windows.Controls.ControlTemplate>して外観をカスタマイズできます。 カスタム<xref:System.Windows.Controls.Control>の構築は<xref:System.Windows.Controls.UserControl>、 を構築するほど簡単ではありませんが、カスタム<xref:System.Windows.Controls.Control>を使用すると、最も柔軟性が高くなります。

#### <a name="benefits-of-deriving-from-control"></a>Control からの派生の利点

次のいずれかが該当する<xref:System.Windows.Controls.Control>場合は、クラス<xref:System.Windows.Controls.UserControl>を使用する代わりに派生することを検討してください。

- コントロールの外観を<xref:System.Windows.Controls.ControlTemplate>でカスタマイズできるようにする。

- コントロールがさまざまなテーマをサポートする必要がある場合。

### <a name="deriving-from-frameworkelement"></a>FrameworkElement からの派生

既存の要素の<xref:System.Windows.Controls.UserControl>作成<xref:System.Windows.Controls.Control>から派生するコントロール、または既存の要素の作成に依存するコントロール。 多くのシナリオでは、継承するオブジェクト<xref:System.Windows.FrameworkElement>は . <xref:System.Windows.Controls.ControlTemplate> しかし、場合によっては、単純な要素コンポジションでは、コントロールの外観に必要な機能を実現できないことがあります。 これらのシナリオでは、コンポーネントを基に<xref:System.Windows.FrameworkElement>することが正しい選択です。

ベースのコンポーネントを構築<xref:System.Windows.FrameworkElement>するための標準の方法には、直接レンダリングとカスタム要素のコンポジションの 2 つがあります。 直接レンダリングでは、メソッドを<xref:System.Windows.UIElement.OnRender%2A>オーバーライド<xref:System.Windows.FrameworkElement>し、コンポーネント<xref:System.Windows.Media.DrawingContext>ビジュアルを明示的に定義する操作を提供します。 これは、 と で<xref:System.Windows.Controls.Image>使用<xref:System.Windows.Controls.Border>される方法です。 カスタム要素の構成では、型<xref:System.Windows.Media.Visual>のオブジェクトを使用してコンポーネントの外観を構成します。 例については、「[DrawingVisual オブジェクトの使用](../graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。 <xref:System.Windows.Controls.Primitives.Track>は、カスタム要素の構成を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用するコントロールの例です。 同じコントロールでダイレクト レンダリングとカスタム要素コンポジションを混在させることもできます。

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement からの派生の利点

次のいずれかが該当する<xref:System.Windows.FrameworkElement>場合は、派生元を検討してください。

- コントロールの外観について、単純な要素コンポジションが提供する以上の厳密な制御を必要とする場合。

- 独自のレンダリング ロジックを定義して、コントロールの外観を定義する必要がある場合。

- 既存の要素を、可能な点を超えた新しい方法で<xref:System.Windows.Controls.UserControl>構成する<xref:System.Windows.Controls.Control>必要があります。

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>コントロール作成の基本

既に説明したように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の最も強力な機能の 1 つは、コントロールの基本的なプロパティ設定だけでは不可能な外観や動作の変更を実現し、しかもカスタム コントロールを作成する必要がないということです。 スタイル設定、データ バインディング、トリガーの各機能は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムによって実現されています。 以降のセクションでは、カスタム コントロールのユーザーが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属のコントロールと同じように、これらの機能を使用できるようにするために、カスタム コントロールの作成に使用するモデルに関係なく、従う必要があるプラクティスについて説明します。

### <a name="use-dependency-properties"></a>依存関係プロパティの使用

プロパティが依存関係プロパティである場合、以下の操作が可能です。

- スタイルのプロパティを設定する。

- プロパティをデータ ソースにバインドする。

- プロパティの値として、動的リソースを使用する。

- プロパティ名をアニメーション化する。

コントロールのプロパティがこれらの機能のいずれかをサポートす必要がある場合、それを依存関係プロパティとして実装する必要があります。 次の例では、以下の処理を実行して、`Value` という名前の依存関係プロパティを定義します。

- フィールドとして<xref:System.Windows.DependencyProperty>名前を`ValueProperty`付ける`public``static``readonly`識別子を定義します。

- プロパティシステムにプロパティ名を登録するには、 を<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>呼び出して、次の項目を指定します。

  - プロパティの名前。

  - プロパティの型。

  - プロパティを所有する型。

  - プロパティのメタデータ。 メタデータには、プロパティの既定値 、および<xref:System.Windows.CoerceValueCallback>a が含<xref:System.Windows.PropertyChangedCallback>まれています。

- プロパティ`get`と`set`アクセサーを実装`Value`することによって、依存関係プロパティの登録に使用される名前の CLR ラッパー プロパティを定義します。 アクセサーと`get``set`アクセサーは、<xref:System.Windows.DependencyObject.GetValue%2A>それぞれ<xref:System.Windows.DependencyObject.SetValue%2A>呼び出しのみであることに注意してください。 クライアントと呼び出[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.DependencyObject.GetValue%2A>しをバイパスして<xref:System.Windows.DependencyObject.SetValue%2A>直接実行できるため、依存関係プロパティのアクセサーには追加のロジックを含めないことをお勧めします。 たとえば、プロパティがデータ ソースにバインドされている場合、プロパティの `set` アクセサーは呼び出されません。  get アクセサーおよび set アクセサーにロジックを追加する<xref:System.Windows.ValidateValueCallback>代<xref:System.Windows.CoerceValueCallback>わりに、 <xref:System.Windows.PropertyChangedCallback> 、および デリゲートを使用して、値が変更されたときに値に応答したり、チェックしたりします。  これらのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../advanced/dependency-property-callbacks-and-validation.md)」を参照してください。

- 名前付き`CoerceValue`の<xref:System.Windows.CoerceValueCallback>メソッドを定義します。 `CoerceValue` によって、`Value` は `MinValue` 以上で `MaxValue` 以下になります。

- という名前`OnValueChanged`の メソッド<xref:System.Windows.PropertyChangedCallback>を定義します。 `OnValueChanged`オブジェクトを<xref:System.Windows.RoutedPropertyChangedEventArgs%601>作成し、ルーティング イベントを`ValueChanged`発生させる準備をします。 ルーティング イベントについては、次のセクションで説明します。

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

詳細については、「[カスタム依存関係プロパティ](../advanced/custom-dependency-properties.md)」を参照してください。

### <a name="use-routed-events"></a>ルーティング イベントの使用

依存関係プロパティが CLR プロパティの概念を拡張して機能を追加するのと同様に、ルーティング イベントは標準 CLR イベントの概念を拡張します。 新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール作成する場合、イベントをルーティング イベントとして実装することをお勧めします。ルーティング イベントは以下の機能をサポートしているためです。

- 複数のコントロールの親でイベントを処理できます。 イベントがバブル イベントの場合、要素ツリー内の単一の親はイベントをサブスクライブできます。 これにより、アプリケーション開発者は、複数のコントロールのイベントに 1 つのハンドラーで対応できます。 たとえば、コントロールが<xref:System.Windows.Controls.ListBox>の各項目の一部である場合 (コントロールは<xref:System.Windows.DataTemplate>に含まれているため)、アプリケーション開発者は コントロールのイベントのイベント ハンドラを . <xref:System.Windows.Controls.ListBox> いずれかのコントロールでイベントが発生するたびに、そのイベント ハンドラーが呼び出されます。

- ルーティング イベントは<xref:System.Windows.EventSetter>、 で使用でき、アプリケーション開発者はスタイル内でイベントのハンドラーを指定できます。

- ルーティング イベントは<xref:System.Windows.EventTrigger>で使用できます。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 詳細については、「アニメーションの[概要](../graphics-multimedia/animation-overview.md)」を参照してください。

次に示す例では、以下の処理を実行して、ルーティング イベントを定義します。

- フィールドとして<xref:System.Windows.RoutedEvent>名前を`ValueChangedEvent`付ける`public``static``readonly`識別子を定義します。

- メソッドを呼び出してルーティング<xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>イベントを登録します。 この例では、 を呼び出<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>すときに次の情報を指定します。

  - イベントの名前が `ValueChanged` であること。

  - ルーティング戦略は、<xref:System.Windows.RoutingStrategy.Bubble>ソース (イベントを発生させるオブジェクト) のイベント ハンドラが最初に呼び出され、次にソースの親要素のイベント ハンドラが、最も近い親要素のイベント ハンドラから順に連続して呼び出されることを意味します。

  - イベント ハンドラの型は、<xref:System.Windows.RoutedPropertyChangedEventHandler%601>型で構築されます<xref:System.Decimal>。

  - イベントを所有する型が `NumericUpDown` であること。

- `ValueChanged` という名前のパブリック イベントを宣言し、イベント アクセサー宣言を含めます。 この例では<xref:System.Windows.UIElement.AddHandler%2A>、`add`アクセサー宣言と<xref:System.Windows.UIElement.RemoveHandler%2A>アクセサー`remove`宣言を呼び出[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]して、イベント サービスを使用します。

- `ValueChanged`イベントを発生させる、保護された仮想メソッド `OnValueChanged` を作成します。

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

詳細については、「[ルーティング イベントの概要](../advanced/routed-events-overview.md)」および「[カスタム ルーティング イベントを作成する](../advanced/how-to-create-a-custom-routed-event.md)」を参照してください。

### <a name="use-binding"></a>バインディングの使用

コントロールの UI とロジックを分離するには、データ バインディングを使用する方法もあります。 これは、コントロールの外観を をを定義する場合に特に<xref:System.Windows.Controls.ControlTemplate>重要です。 データ バインディングを使用すると、コードから UI の特定の部分を参照する必要性がなくなる場合があります。 の要素を<xref:System.Windows.Controls.ControlTemplate>参照するコードが 変更されると、参照先の要素<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.ControlTemplate>を new <xref:System.Windows.Controls.ControlTemplate>.

次の例では、<xref:System.Windows.Controls.TextBlock>コントロールの`NumericUpDown`を更新し、名前を割り当て、コード内でテキスト ボックスを名前で参照します。

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

次の例では、バインディングを使用して同じことを実現しています。

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

データ バインディングの詳細については、「[データ バインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)」を参照してください。

### <a name="design-for-designers"></a>デザイナーに対応したデザイン

Visual Studio 用の WPF デザイナーでカスタム WPF コントロールのサポートを受ける (プロパティ ウィンドウを使用したプロパティの編集など) には、次のガイドラインに従います。  WPF デザイナーの開発の詳細については、「 Visual [Studio で XAML をデザイン](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)する 」を参照してください。

#### <a name="dependency-properties"></a>依存関係プロパティ

CLR`get`と`set`アクセサーは、前述の「依存関係プロパティの使用」で説明したように実装してください。 デザイナーは、ラッパーを使用して依存関係プロパティの存在を検出する場合がありますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] およびコントロールのクライアントと同様、プロパティを取得または設定するときにアクセサーを呼び出す必要はありません。

#### <a name="attached-properties"></a>アタッチされるプロパティ

以下のガイドラインに従って、カスタム コントロールに添付プロパティを実装する必要があります。

- メソッド`public``static``readonly`を<xref:System.Windows.DependencyProperty>使用して作成したフォーム*PropertyName*`Property`を<xref:System.Windows.DependencyProperty.RegisterAttached%2A>使用します。 渡されるプロパティ名は<xref:System.Windows.DependencyProperty.RegisterAttached%2A>*、プロパティ名*と一致する必要があります。

- `Set`*PropertyName* および `Get`*PropertyName* という名前の `public` `static` CLR メソッドのペアを実装します。 どちらのメソッドも、最初の引数<xref:System.Windows.DependencyProperty>として派生したクラスを受け入れる必要があります。 また、`Set`*PropertyName* メソッドでは、プロパティの登録データ型と同じ型の引数も受け取ります。 `Get`*PropertyName*メソッドでは、同じ型の値を返す必要があります。 `Set`*PropertyName*メソッドがない場合、プロパティは読み取り専用としてマークされます。

- `Set`*PropertyName* `Get`と*PropertyName*は、<xref:System.Windows.DependencyObject.GetValue%2A>ターゲット<xref:System.Windows.DependencyObject.SetValue%2A>依存関係オブジェクトの メソッドとメソッドにそれぞれ直接ルーティングする必要があります。 デザイナーが添付プロパティにアクセスするには、メソッド ラッパー経由で呼び出す場合もあれば、対象の依存関係オブジェクトを直接呼び出す場合もあります。

添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

### <a name="define-and-use-shared-resources"></a>共有リソースの定義と使用

アプリケーションと同じアセンブリにコントロールを含めることも、複数のアプリケーションが使用できる別のアセンブリにコントロールをパッケージ化することもできます。 このトピックで説明した情報の大部分は、使用する方法に関係なく適用されます。  ただし、1 つだけ例外があります。  アプリケーションと同じアセンブリ内にコントロールを配置する場合、App.xaml ファイルにグローバル リソースを自由に追加できます。 ただし、コントロールのみを含むアセンブリには<xref:System.Windows.Application>オブジェクトが関連付けられていないため、App.xaml ファイルは使用できません。

アプリケーションがリソースを検索するときは、次に示す順序で 3 つのレベルを検索します。

1. 要素レベル。

   システムは、リソースを参照する要素から検索を開始し、ルート要素に到達するまで、論理上の親のリソースの検索を継続します。

2. アプリケーション レベル。

   オブジェクトによって定義された<xref:System.Windows.Application>リソース。

3. テーマ レベル。

   テーマ レベルのディクショナリは、Themes という名前のサブフォルダーに格納されています。  Themes フォルダー内のファイルはテーマに対応しています。  たとえば、Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml などのファイルがあります。  generic.xaml という名前のファイルが含まれている場合もあります。  システムがテーマ レベルでリソースを検索するとき、最初にテーマ固有のファイル内を検索し、次に generic.xaml 内を検索します。

アプリケーションとは別のアセンブリ内にコントロールを含めるときは、グローバル リソースを要素レベルまたはテーマ レベルに配置する必要があります。 どちらに配置する場合も、それぞれの利点があります。

#### <a name="defining-resources-at-the-element-level"></a>要素レベルでのリソース定義

ユーザー定義リソース ディクショナリを作成し、それをコントロールのリソース ディクショナリとマージすることで、要素レベルで共有リソースを定義できます。  このメソッドで定義する場合は、リソース ファイルに任意の名前を付けて、コントロールと同じフォルダーに配置できます。 要素レベルでのリソースでは、単純な文字列をキーとして使用することもできます。 次の例では、Dictionary1.xaml という名前の<xref:System.Windows.Media.LinearGradientBrush>リソース ファイルを作成します。

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

ディクショナリを定義したら、それをコントロールのリソース ディクショナリにマージする必要があります。  これには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用します。

次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してリソース ディクショナリを結合します。

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

この方法の欠点は、オブジェクトを<xref:System.Windows.ResourceDictionary>参照するたびにオブジェクトが作成されるということです。  たとえば、ライブラリに 10 個のカスタム コントロールがあり、XAML を使用して各コントロールの共有リソース ディクショナリをマージする場合、10 個の同一<xref:System.Windows.ResourceDictionary>のオブジェクトを作成します。  これを回避するには、コード内のリソースをマージし、結果を<xref:System.Windows.ResourceDictionary>返す静的クラスを作成します。

次の例では、共有<xref:System.Windows.ResourceDictionary>を返すクラスを作成します。

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

次の例では、`InitializeComponent` を呼び出す前に、共有リソースをコントロールのコンス トラクター内でカスタム コントロールのリソースと結合します。  `SharedDictionaryManager.SharedDictionary`は静的プロパティであるため、 は<xref:System.Windows.ResourceDictionary>一度だけ作成されます。 `InitializeComponent` が呼び出される前に、リソース ディクショナリが結合されため、コントロールは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内でリソースを使用できます。

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>テーマ レベルでのリソース定義

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、さまざまな Windows テーマ用にリソースを作成できます。  コントロールの作成者は、特定のテーマ用のリソースを定義して、使用するテーマに応じてコントロールの外観を変更できます。 たとえば、Windows クラシック テーマ<xref:System.Windows.Controls.Button>(Windows 2000 の既定のテーマ) の外観は、Windows の<xref:System.Windows.Controls.Button>ルナ テーマ (Windows XP の既定のテーマ)<xref:System.Windows.Controls.Button>の外観とは異<xref:System.Windows.Controls.ControlTemplate>なります。

テーマ固有のリソースは、固有のファイル名でリソース ディクショナリに保持されます。 これらのファイルは、コントロールが格納されているフォルダーのサブフォルダーである `Themes` フォルダー内に配置する必要があります。 次の表は、リソース ディクショナリ ファイルと、各ファイルに関連付けられているテーマを示しています。

|リソース ディクショナリ ファイル名|Windows テーマ|
|-----------------------------------|-------------------|
|`Classic.xaml`|Windows XP のクラシックな Windows 9x/2000 の外観|
|`Luna.NormalColor.xaml`|Windows XP の既定の青のテーマ|
|`Luna.Homestead.xaml`|Windows XP のオリーブのテーマ|
|`Luna.Metallic.xaml`|Windows XP のシルバーのテーマ|
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition の既定テーマ|
|`Aero.NormalColor.xaml`|Windows Vista の既定テーマ|

すべてのテーマのリソースを定義する必要はありません。 特定のテーマについてリソースが定義されていない場合、コントロールはリソースの `Classic.xaml` を確認します。 現在のテーマに対応するファイルや `Classic.xaml` でリソースが定義されていない場合、コントロールは汎用のリソースを使用します。汎用のリソースは、`generic.xaml` という名前のリソース ディクショナリ ファイルにあります。  `generic.xaml` ファイルは、テーマ固有のリソース ディクショナリ ファイルと同じフォルダーに配置されています。 `generic.xaml` は、特定の Windows テーマには対応していませんが、テーマ レベルのディクショナリであることに変わりありません。

テーマと UI オートメーション のサポート サンプルを含む[C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)または[Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown`NumericUpDown`カスタム コントロールには、コントロール用の 2 つのリソース ディクショナリが含まれています。

テーマ固有のリソース<xref:System.Windows.Controls.ControlTemplate>ディクショナリ ファイルのいずれかに を配置する場合は、次の例に示すように、コントロールの静的コンストラクターを<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29>作成し<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>、 でメソッドを呼び出す必要があります。

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>テーマ リソース用のキーの定義と参照

要素レベルでリソースを定義するときに、文字列をキーとして割り当て、その文字列を使用してリソースにアクセスできます。 テーマ レベルでリソースを定義する場合は、 を<xref:System.Windows.ComponentResourceKey>キーとして使用する必要があります。  次の例では、generic.xaml でリソースを定義します。

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

次の例では、 キーとしてを<xref:System.Windows.ComponentResourceKey>指定してリソースを参照します。

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>テーマ リソースの場所の指定

コントロールのリソースを見つけるには、アセンブリにコントロール固有のリソースが含まれていることを、ホスト アプリケーションが認識する必要があります。 これは、コントロールを含むアセンブリ<xref:System.Windows.ThemeInfoAttribute>に を追加することで実現できます。 <xref:System.Windows.ThemeInfoAttribute>には、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>汎用リソースの場所を指定する<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>プロパティと、テーマ固有のリソースの場所を指定するプロパティがあります。

プロパティ<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>と<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>プロパティをに<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>設定し、ジェネリック リソースとテーマ固有のリソースがコントロールと同じアセンブリに含まれるように指定します。

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>関連項目

- [Visual Studio で XAML をデザインする](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WPF におけるパッケージの URI](../app-development/pack-uris-in-wpf.md)
- [コントロールのカスタマイズ](control-customization.md)
