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
ms.openlocfilehash: 291edaf49fd8de27bfe0dc10f24cb865793cadc6
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660371"
---
# <a name="control-authoring-overview"></a>コントロールの作成の概要

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コントロール モデルの機能拡張により、新しいコントロールを作成する必要性が大幅に削減されます。 ただし、場合によっては、カスタム コントロールを作成する必要があります。 このトピックでは、カスタム コントロールを作成する必要性を最小限に抑える機能と、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまなコントロール作成モデルについて説明します。 また、新しいコントロールを作成する方法も示します。

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>新しいコントロールの作成に代わる方法

従来は、既存のコントロールをカスタマイズする場合、背景色、境界線の幅、フォントのサイズなど、コントロールの標準プロパティを変更するなどの範囲に制限されていました。 これらの定義済みのパラメーター以外に、コントロールの外観や動作にまでカスタマイズを拡張しようとすると、通常、既存のコントロールを継承し、コントロールを描画するメソッドをオーバーライドして、新しいコントロールを作成する必要がありました。  その方法は今でも選択できますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の場合、リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用して、既存のコントロールをカスタマイズできます。 新しいコントロールを作成しなくても、これらの機能を使用して、カスタマイズされた一貫性のあるエクスペリエンスを得られる方法としては、次のような例が挙げられます。

- **リッチ コンテンツ。** 標準の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くがリッチ コンテンツをサポートしています。 コンテンツのプロパティなど、<xref:System.Windows.Controls.Button>の種類は<xref:System.Object>、理論上何も表示できます、<xref:System.Windows.Controls.Button>します。  イメージとテキストの表示 ボタンを表示するには、イメージを追加することができます、<xref:System.Windows.Controls.TextBlock>を<xref:System.Windows.Controls.StackPanel>を割り当てると、<xref:System.Windows.Controls.StackPanel>を<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティ。 コントロールには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の視覚的要素と任意のデータを表示できるため、複雑な視覚化をサポートするために、新しいコントロールを作成したり、既存のコントロールを変更したりする必要性が少なくなります。 コンテンツ モデルの詳細については<xref:System.Windows.Controls.Button>での他のコンテンツ モデルと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[WPF コンテンツ モデル](wpf-content-model.md)します。

- **スタイル** A<xref:System.Windows.Style>はコントロールのプロパティを表す値のコレクションです。 スタイルを使用すると、新しいコントロールを作成しなくても、必要なコントロールの外観と動作を備えた再利用可能な表現を作成できます。 たとえば、すべての必要な<xref:System.Windows.Controls.TextBlock>コントロールにフォント サイズ 14 の赤、Arial フォント。 そこで、リソースとしてスタイルを作成し、それに応じて、適切なプロパティを設定します。 すべてし<xref:System.Windows.Controls.TextBlock>同じ外観をアプリケーションに追加する必要があります。

- **データ テンプレート。** A<xref:System.Windows.DataTemplate>コントロールにデータを表示する方法をカスタマイズすることができます。 たとえば、<xref:System.Windows.DataTemplate>にデータを表示する方法を指定するために使用できる、 <xref:System.Windows.Controls.ListBox>。  この例については、「[データ テンプレートの概要](../data/data-templating-overview.md)」を参照してください。  データの外観のカスタマイズに加え、<xref:System.Windows.DataTemplate>これにより、高度な柔軟性ではカスタム Ui の UI 要素を含めることができます。  などを使用して、 <xref:System.Windows.DataTemplate>、作成することができます、<xref:System.Windows.Controls.ComboBox>でその各項目には、チェック ボックスが含まれています。

- **コントロール テンプレート。** コントロールの多く[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して、<xref:System.Windows.Controls.ControlTemplate>コントロールの構造とコントロールの外観では、コントロールの機能から分離の外観を定義します。 再定義コントロールの外観を大幅に変更することができます、<xref:System.Windows.Controls.ControlTemplate>します。  たとえば、信号機のような外観のコントロールが必要だとします。 このコントロールのユーザー インターフェイスと機能は単純です。  コントロールは 3 つの円で構成され、一度に点灯するのはそのうちの 1 つだけです。 いくつかのリフレクションの後を実現可能性があります、<xref:System.Windows.Controls.RadioButton>の 1 つだけが、時刻の既定の外観に選択されている機能を提供、<xref:System.Windows.Controls.RadioButton>信号機のライトとは何も検索します。  <xref:System.Windows.Controls.RadioButton> 、外観を定義して、コントロール テンプレートを使用して再定義するは簡単、<xref:System.Windows.Controls.ControlTemplate>コントロールの要件に合わせておよびラジオ ボタンを使用して、信号機を作成します。

  > [!NOTE]
  > ですが、<xref:System.Windows.Controls.RadioButton>使用できる、 <xref:System.Windows.DataTemplate>、<xref:System.Windows.DataTemplate>はこの例では不十分です。  <xref:System.Windows.DataTemplate>コントロールのコンテンツの外観を定義します。 場合、 <xref:System.Windows.Controls.RadioButton>、コンテンツがその分岐点の円の右側に表示されるかどうか、<xref:System.Windows.Controls.RadioButton>が選択されています。  信号機の例では、オプション ボタンに必要なのは "点灯" する円だけです。 信号機の外観の要件は、既定の外観の異なるため、 <xref:System.Windows.Controls.RadioButton>、再定義する必要がある、<xref:System.Windows.Controls.ControlTemplate>します。  一般に、<xref:System.Windows.DataTemplate>コントロール、およびのコンテンツ (またはデータ) を定義するために使用<xref:System.Windows.Controls.ControlTemplate>コントロールを構成する方法を定義するために使用します。

- **トリガー。** A<xref:System.Windows.Trigger>新しいコントロールを作成せず、コントロールの動作と外観を動的に変更することができます。 たとえば、複数<xref:System.Windows.Controls.ListBox>アプリケーションではコントロールに各項目を追加および<xref:System.Windows.Controls.ListBox>太字、色を赤を選択すると、あります。 まず思いつくが継承するクラスを作成することがあります<xref:System.Windows.Controls.ListBox>をオーバーライドし、<xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>選択した項目がより優れたアプローチの外観を変更する方法は、トリガーのスタイルを追加する、<xref:System.Windows.Controls.ListBoxItem>の外観を変更します。選択された項目。 トリガーを使用すると、プロパティ値を変更したり、プロパティ値に基づいた処理を実行したりできます。 <xref:System.Windows.EventTrigger>イベントが発生したときにアクションを実行することができます。

スタイル、テンプレート、トリガーの詳細については、「[スタイルとテンプレート](styling-and-templating.md)」を参照してください。

一般に、既存のコントロールと同じ機能を持ち、外観が異なるコントロールが必要な場合は、このセクションで説明した方法のいずれかを使用して、既存のコントロールの外観を変更できないかどうかをまず検討することをお勧めします。

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>コントロール作成モデル

リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用すると、新しいコントロールを作成する必要性が最小限に抑えられます。 ただし、新しいコントロールを作成する必要がある場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種のコントロール作成モデルを理解することが重要です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、コントロールを作成するための一般的なモデルが 3 つあり、各モデルはそれぞれ異なる機能と柔軟性レベルを備えています。 基本クラスの 3 つのモデルは<xref:System.Windows.Controls.UserControl>、 <xref:System.Windows.Controls.Control>、および<xref:System.Windows.FrameworkElement>します。

### <a name="deriving-from-usercontrol"></a>UserControl からの派生

コントロールを作成する最も簡単な方法は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から派生するは<xref:System.Windows.Controls.UserControl>します。 継承するコントロールを作成するときに<xref:System.Windows.Controls.UserControl>に既存のコンポーネントを追加する、<xref:System.Windows.Controls.UserControl>でイベント ハンドラーを参照し、コンポーネントという名前を[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 次に、指定の要素を参照し、コードでイベント ハンドラーを定義します。 この開発モデルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーション開発に使用されるモデルとよく似ています。

正しくビルドされている場合、<xref:System.Windows.Controls.UserControl>リッチ コンテンツ、スタイル、およびトリガーの利点を利用できます。 ただしから継承したコントロールの場合<xref:System.Windows.Controls.UserControl>、コントロールを使用するユーザーは使用できません、<xref:System.Windows.DataTemplate>または<xref:System.Windows.Controls.ControlTemplate>その外観をカスタマイズします。  派生する必要があります、<xref:System.Windows.Controls.Control>クラスまたはその派生クラスのいずれか (他にも<xref:System.Windows.Controls.UserControl>) テンプレートをサポートするカスタム コントロールを作成します。

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl からの派生の利点

派生することを検討してください<xref:System.Windows.Controls.UserControl>すべて、次の該当する場合。

- アプリケーションの構築と同じ方法でコントロールをビルドする必要がある場合。

- コントロールが既存のコンポーネントのみで構成されている場合。

- 複雑なカスタマイズをサポートする必要がない場合。

### <a name="deriving-from-control"></a>Control からの派生

派生する、<xref:System.Windows.Controls.Control>クラスは、既存のほとんどで使用されるモデル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。 継承するコントロールを作成する場合、<xref:System.Windows.Controls.Control>クラス テンプレートを使用してその外観を定義します。 これにより、操作ロジックと視覚的表現とが分離されます。 イベントと回避の参照元要素ではなく、コマンドとバインディングを使用して、UI とロジックの分離も確認できます、<xref:System.Windows.Controls.ControlTemplate>可能な場合。  コントロールのユーザーがコントロールの再定義できます、UI と、コントロールのロジックが適切に分離された場合は、<xref:System.Windows.Controls.ControlTemplate>その外観をカスタマイズします。 カスタムのビルドが<xref:System.Windows.Controls.Control>ビルドとして単純ではありませんが、 <xref:System.Windows.Controls.UserControl>、カスタム<xref:System.Windows.Controls.Control>最大限の柔軟性を提供します。

#### <a name="benefits-of-deriving-from-control"></a>Control からの派生の利点

派生することを検討してください<xref:System.Windows.Controls.Control>を使用してではなく、<xref:System.Windows.Controls.UserControl>クラスの場合、以下が適用されます。

- 使用してカスタマイズできるように、コントロールの外観にする、<xref:System.Windows.Controls.ControlTemplate>します。

- コントロールがさまざまなテーマをサポートする必要がある場合。

### <a name="deriving-from-frameworkelement"></a>FrameworkElement からの派生

派生したコントロール<xref:System.Windows.Controls.UserControl>または<xref:System.Windows.Controls.Control>既存の要素の構成に依存します。 多くのシナリオでは、これは、適切な解決策ためから継承する任意のオブジェクト<xref:System.Windows.FrameworkElement>にできる、<xref:System.Windows.Controls.ControlTemplate>します。 しかし、場合によっては、単純な要素コンポジションでは、コントロールの外観に必要な機能を実現できないことがあります。 このようなシナリオのコンポーネントに基づく<xref:System.Windows.FrameworkElement>は適切な選択肢です。

ビルドするための 2 つの標準的なメソッドがある<xref:System.Windows.FrameworkElement>-ベースのコンポーネント: レンダリングとカスタム要素コンポジションをダイレクトします。 ダイレクト レンダリングでは、オーバーライド、<xref:System.Windows.UIElement.OnRender%2A>メソッドの<xref:System.Windows.FrameworkElement>おり<xref:System.Windows.Media.DrawingContext>コンポーネントのビジュアルを明示的に定義する操作。 これは、メソッドで使用される<xref:System.Windows.Controls.Image>と<xref:System.Windows.Controls.Border>します。 カスタム要素コンポジションでは、型のオブジェクトを使用してでは<xref:System.Windows.Media.Visual>コンポーネントの外観を作成します。 例については、「[DrawingVisual オブジェクトの使用](../graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。 <xref:System.Windows.Controls.Primitives.Track> コントロールの例は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]カスタム要素コンポジションを使用します。 同じコントロールでダイレクト レンダリングとカスタム要素コンポジションを混在させることもできます。

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement からの派生の利点

派生することを検討してください<xref:System.Windows.FrameworkElement>場合、以下が適用されます。

- コントロールの外観について、単純な要素コンポジションが提供する以上の厳密な制御を必要とする場合。

- 独自のレンダリング ロジックを定義して、コントロールの外観を定義する必要がある場合。

- 使って何ができる上回る斬新な方法で既存の要素を作成する<xref:System.Windows.Controls.UserControl>と<xref:System.Windows.Controls.Control>します。

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

- 定義、<xref:System.Windows.DependencyProperty>という名前の識別子`ValueProperty`として、 `public` `static` `readonly`フィールド。

- プロパティ名をプロパティ システムを呼び出すことによって登録<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>次を指定します。

  - プロパティの名前。

  - プロパティの型。

  - プロパティを所有する型。

  - プロパティのメタデータ。 メタデータにはプロパティの既定値が含まれています、<xref:System.Windows.CoerceValueCallback>と<xref:System.Windows.PropertyChangedCallback>します。

- プロパティの `get` アクセサーと `set` アクセサーを実装することにより、依存関係プロパティの登録名と同じ `Value` という名前で [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ラッパー プロパティを定義します。 なお、`get`と`set`アクセサーのみを呼び出す<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>それぞれします。 ある依存関係プロパティのアクセサーが含まれていない追加のロジックにはためにお勧めクライアントと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アクセサーと呼び出しをバイパスできる<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>直接します。 たとえば、プロパティがデータ ソースにバインドされている場合、プロパティの `set` アクセサーは呼び出されません。  取得する追加のロジックを追加する代わりに、set アクセサーは、使用、 <xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.CoerceValueCallback>と<xref:System.Windows.PropertyChangedCallback>デリゲートに応答したり、変更するときに、値を確認します。  これらのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../advanced/dependency-property-callbacks-and-validation.md)」を参照してください。

- メソッドを定義、<xref:System.Windows.CoerceValueCallback>という`CoerceValue`します。 `CoerceValue` によって、`Value` は `MinValue` 以上で `MaxValue` 以下になります。

- メソッドを定義、 <xref:System.Windows.PropertyChangedCallback>、名前付き`OnValueChanged`します。 `OnValueChanged` 作成、<xref:System.Windows.RoutedPropertyChangedEventArgs%601>オブジェクトし、発生させる準備、`ValueChanged`ルーティング イベント。 ルーティング イベントについては、次のセクションで説明します。

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

詳細については、「[カスタム依存関係プロパティ](../advanced/custom-dependency-properties.md)」を参照してください。

### <a name="use-routed-events"></a>ルーティング イベントの使用

依存関係プロパティが [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティの概念を追加機能によって拡張するのと同様に、ルーティング イベントは、標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントの概念を拡張します。 新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール作成する場合、イベントをルーティング イベントとして実装することをお勧めします。ルーティング イベントは以下の機能をサポートしているためです。

- 複数のコントロールの親でイベントを処理できます。 イベントがバブル イベントの場合、要素ツリー内の単一の親はイベントをサブスクライブできます。 これにより、アプリケーション開発者は、複数のコントロールのイベントに 1 つのハンドラーで対応できます。 コントロール内の各項目の一部である場合など、 <xref:System.Windows.Controls.ListBox> (に含まれているため、 <xref:System.Windows.DataTemplate>)、アプリケーション開発者は、コントロールのイベントのイベント ハンドラーを定義できます、<xref:System.Windows.Controls.ListBox>します。 いずれかのコントロールでイベントが発生するたびに、そのイベント ハンドラーが呼び出されます。

- ルーティング イベントで使用できる、 <xref:System.Windows.EventSetter>、アプリケーション開発者は、スタイル内のイベントのハンドラーを指定できます。

- ルーティング イベントで使用できる、<xref:System.Windows.EventTrigger>を使用してプロパティをアニメーション化するために便利です[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 詳しくは、「 [アニメーションの概要](../graphics-multimedia/animation-overview.md)」をご覧ください。

次に示す例では、以下の処理を実行して、ルーティング イベントを定義します。

- 定義、<xref:System.Windows.RoutedEvent>という名前の識別子`ValueChangedEvent`として、 `public` `static` `readonly`フィールド。

- 呼び出すことによって、ルーティング イベントを登録、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>メソッド。 呼び出すときに、例を次の情報を指定します<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:

  - イベントの名前が `ValueChanged` であること。

  - ルーティング方法が、<xref:System.Windows.RoutingStrategy.Bubble>ソース (イベントを発生させるオブジェクト) にイベント ハンドラーが最初に、呼び出されることを意味してに、以降の最も近いイベント ハンドラーでソースの親要素のイベント ハンドラーが呼び出されるし、親要素です。

  - イベント ハンドラーの型が<xref:System.Windows.RoutedPropertyChangedEventHandler%601>で構築された、<xref:System.Decimal>型。

  - イベントを所有する型が `NumericUpDown` であること。

- `ValueChanged` という名前のパブリック イベントを宣言し、イベント アクセサー宣言を含めます。 例では、<xref:System.Windows.UIElement.AddHandler%2A>で、`add`アクセサーの宣言と<xref:System.Windows.UIElement.RemoveHandler%2A>で、`remove`アクセサーの宣言を使用する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント サービス。

- `ValueChanged`イベントを発生させる、保護された仮想メソッド `OnValueChanged` を作成します。

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

詳細については、「[ルーティング イベントの概要](../advanced/routed-events-overview.md)」および「[カスタム ルーティング イベントを作成する](../advanced/how-to-create-a-custom-routed-event.md)」を参照してください。

### <a name="use-binding"></a>バインディングの使用

コントロールの UI とロジックを分離するには、データ バインディングを使用する方法もあります。 これを使用して、コントロールの外観を定義する場合に特に重要な<xref:System.Windows.Controls.ControlTemplate>します。 データ バインディングを使用すると、コードから UI の特定の部分を参照する必要性がなくなる場合があります。 含まれている要素の参照を回避することをお勧め、<xref:System.Windows.Controls.ControlTemplate>ため、コードが含まれている要素を参照するときに、<xref:System.Windows.Controls.ControlTemplate>と<xref:System.Windows.Controls.ControlTemplate>が変更されると、新しいに含まれる参照先の要素のニーズ<xref:System.Windows.Controls.ControlTemplate>します。

次の例の更新プログラム、<xref:System.Windows.Controls.TextBlock>の`NumericUpDown`コントロールにその名前を割り当てると、コード内の名前をテキスト ボックスの参照します。

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

次の例では、バインディングを使用して同じことを実現しています。

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

データ バインディングの詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。

### <a name="design-for-designers"></a>デザイナーに対応したデザイン

[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] でカスタム WPF コントロールのサポート (たとえば、[プロパティ] ウィンドウでのプロパティ編集) を利用するには、以下のガイドラインに従います。  用の開発の詳細については、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]を参照してください[Visual Studio で XAML をデザイン](/visualstudio/designers/designing-xaml-in-visual-studio)します。

#### <a name="dependency-properties"></a>依存関係プロパティ

「依存関係プロパティの使用」で説明したように、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の `get` アクセサーと `set` アクセサーを実装します。 デザイナーは、ラッパーを使用して依存関係プロパティの存在を検出する場合がありますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] およびコントロールのクライアントと同様、プロパティを取得または設定するときにアクセサーを呼び出す必要はありません。

#### <a name="attached-properties"></a>アタッチされるプロパティ

以下のガイドラインに従って、カスタム コントロールに添付プロパティを実装する必要があります。

- `public` `static` `readonly` <xref:System.Windows.DependencyProperty>フォームの*PropertyName* `Property`を使用して作成された、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッド。 渡されるプロパティ名<xref:System.Windows.DependencyProperty.RegisterAttached%2A>と一致する必要があります*PropertyName*します。

- `Set` *PropertyName* および `Get` *PropertyName* という名前の `public``static` CLR メソッドのペアを実装します。 どちらの方法から派生したクラスを受け入れる必要があります<xref:System.Windows.DependencyProperty>最初の引数として。 また、`Set` *PropertyName* メソッドでは、プロパティの登録データ型と同じ型の引数も受け取ります。 `Get` *PropertyName*メソッドでは、同じ型の値を返す必要があります。 `Set` *PropertyName*メソッドがない場合、プロパティは読み取り専用としてマークされます。

- `Set` *PropertyName*と`Get` *PropertyName*に直接ルーティングする必要があります、<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>オブジェクトのメソッド ターゲット依存関係に、それぞれします。 デザイナーが添付プロパティにアクセスするには、メソッド ラッパー経由で呼び出す場合もあれば、対象の依存関係オブジェクトを直接呼び出す場合もあります。

添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

### <a name="define-and-use-shared-resources"></a>共有リソースの定義と使用

アプリケーションと同じアセンブリにコントロールを含めることも、複数のアプリケーションが使用できる別のアセンブリにコントロールをパッケージ化することもできます。 このトピックで説明した情報の大部分は、使用する方法に関係なく適用されます。  ただし、1 つだけ例外があります。  アプリケーションと同じアセンブリ内にコントロールを配置する場合、App.xaml ファイルにグローバル リソースを自由に追加できます。 コントロールのみを格納するアセンブリはありませんが、 <xref:System.Windows.Application> App.xaml ファイルが使用できないために、それに関連付けられたオブジェクト。

アプリケーションがリソースを検索するときは、次に示す順序で 3 つのレベルを検索します。

1. 要素レベル。

   システムは、リソースを参照する要素から検索を開始し、ルート要素に到達するまで、論理上の親のリソースの検索を継続します。

2. アプリケーション レベル。

   定義されたリソース、<xref:System.Windows.Application>オブジェクト。

3. テーマ レベル。

   テーマ レベルのディクショナリは、Themes という名前のサブフォルダーに格納されています。  Themes フォルダー内のファイルはテーマに対応しています。  たとえば、Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml などのファイルがあります。  generic.xaml という名前のファイルが含まれている場合もあります。  システムがテーマ レベルでリソースを検索するとき、最初にテーマ固有のファイル内を検索し、次に generic.xaml 内を検索します。

アプリケーションとは別のアセンブリ内にコントロールを含めるときは、グローバル リソースを要素レベルまたはテーマ レベルに配置する必要があります。 どちらに配置する場合も、それぞれの利点があります。

#### <a name="defining-resources-at-the-element-level"></a>要素レベルでのリソース定義

カスタムのリソース ディクショナリを作成し、それをコントロールのリソース ディクショナリと結合することによって、共有リソースを要素レベルで定義できます。  このメソッドで定義する場合は、リソース ファイルに任意の名前を付けて、コントロールと同じフォルダーに配置できます。 要素レベルでのリソースでは、単純な文字列をキーとして使用することもできます。 次の例では、作成、 <xref:System.Windows.Media.LinearGradientBrush> Dictionary1.xaml という名前のリソース ファイル。

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

ディクショナリを定義したら、それをコントロールのリソース ディクショナリにマージする必要があります。  これには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用します。

次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してリソース ディクショナリを結合します。

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

このアプローチの欠点は、<xref:System.Windows.ResourceDictionary>オブジェクトが参照するたびに作成します。  たとえば、10 個のカスタム コントロールをライブラリにある XAML を使用して各コントロールの共有リソース ディクショナリをマージして場合を作成する 10 同一<xref:System.Windows.ResourceDictionary>オブジェクト。  コード内でリソースをマージし、その結果を取得する静的クラスを作成してこれを回避する<xref:System.Windows.ResourceDictionary>します。

次の例は、共有を表すクラスを作成します。<xref:System.Windows.ResourceDictionary>します。

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

次の例では、`InitializeComponent` を呼び出す前に、共有リソースをコントロールのコンス トラクター内でカスタム コントロールのリソースと結合します。  `SharedDictionaryManager.SharedDictionary`は静的なプロパティ、 <xref:System.Windows.ResourceDictionary> 1 回だけ作成されます。 `InitializeComponent` が呼び出される前に、リソース ディクショナリが結合されため、コントロールは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内でリソースを使用できます。

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>テーマ レベルでのリソース定義

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、さまざまな Windows テーマ用にリソースを作成できます。  コントロールの作成者は、特定のテーマ用のリソースを定義して、使用するテーマに応じてコントロールの外観を変更できます。 外観など、 <xref:System.Windows.Controls.Button> Windows クラシックのテーマ (Windows 2000 の既定のテーマ) とは異なります、 <xref:System.Windows.Controls.Button> Windows Luna テーマ (Windows XP の既定のテーマ) のため、<xref:System.Windows.Controls.Button>別使用<xref:System.Windows.Controls.ControlTemplate>各テーマ。

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

[テーマおよび UI オートメーションがサポートされた NumericUpDown カスタム コントロールのサンプル](https://go.microsoft.com/fwlink/?LinkID=160025)には、`NumericUpDown` コントロール用の 2 つのリソース ディクショナリが含まれています。1 つは generic.xaml で、もう 1 つは Luna.NormalColor.xaml です。  アプリケーションを実行し、Windows XP のシルバーのテーマと別のテーマを切り替えて、2 つのコントロール テンプレートの違いを確認できます。 (Windows Vista を使用している場合は、Luna.NormalColor.xaml を Aero.NormalColor.xaml という名前に変更し、Windows クラシック テーマと Windows Vista の既定のテーマなど、2 つのテーマを切り替えることができます)。

配置すると、 <xref:System.Windows.Controls.ControlTemplate> 、テーマ固有のリソース ディクショナリ ファイルのいずれのコントロールと呼び出しの静的コンス トラクターを作成する必要があります、<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29>メソッドを<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>次の例のようにします。

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>テーマ リソース用のキーの定義と参照

要素レベルでリソースを定義するときに、文字列をキーとして割り当て、その文字列を使用してリソースにアクセスできます。 テーマ レベルのリソースを定義する場合は、使用、<xref:System.Windows.ComponentResourceKey>キーとして。  次の例では、generic.xaml でリソースを定義します。

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

次の例は、指定することで、リソースを参照、<xref:System.Windows.ComponentResourceKey>キーとして。

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>テーマ リソースの場所の指定

コントロールのリソースを見つけるには、アセンブリにコントロール固有のリソースが含まれていることを、ホスト アプリケーションが認識する必要があります。 ことを追加することで実現できる、<xref:System.Windows.ThemeInfoAttribute>コントロールを格納するアセンブリ。 <xref:System.Windows.ThemeInfoAttribute>が、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>汎用のリソースの場所を指定するプロパティと<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>テーマ固有のリソースの場所を指定するプロパティ。

次の例のセット、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>と<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>プロパティを<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>ジェネリックとテーマ固有のリソースは、コントロールと同じアセンブリに指定します。

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>関連項目

- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WPF におけるパッケージの URI](../app-development/pack-uris-in-wpf.md)
- [コントロールのカスタマイズ](control-customization.md)
