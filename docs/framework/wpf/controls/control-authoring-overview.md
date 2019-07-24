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
ms.openlocfilehash: 3ea5519259ba2ee31bfd6bc25f6bedf1f1250799
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401548"
---
# <a name="control-authoring-overview"></a>コントロールの作成の概要

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コントロール モデルの機能拡張により、新しいコントロールを作成する必要性が大幅に削減されます。 ただし、場合によっては、カスタム コントロールを作成する必要があります。 このトピックでは、カスタム コントロールを作成する必要性を最小限に抑える機能と、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまなコントロール作成モデルについて説明します。 また、新しいコントロールを作成する方法も示します。

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>新しいコントロールの作成に代わる方法

従来は、既存のコントロールをカスタマイズする場合、背景色、境界線の幅、フォントのサイズなど、コントロールの標準プロパティを変更するなどの範囲に制限されていました。 これらの定義済みのパラメーター以外に、コントロールの外観や動作にまでカスタマイズを拡張しようとすると、通常、既存のコントロールを継承し、コントロールを描画するメソッドをオーバーライドして、新しいコントロールを作成する必要がありました。  その方法は今でも選択できますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の場合、リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用して、既存のコントロールをカスタマイズできます。 新しいコントロールを作成しなくても、これらの機能を使用して、カスタマイズされた一貫性のあるエクスペリエンスを得られる方法としては、次のような例が挙げられます。

- **リッチ コンテンツ。** 標準の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くがリッチ コンテンツをサポートしています。 たとえば、の<xref:System.Windows.Controls.Button> content プロパティは型<xref:System.Object>であるため、理論上は任意のものをに表示<xref:System.Windows.Controls.Button>できます。  ボタンにイメージとテキストを表示させるには、イメージ<xref:System.Windows.Controls.TextBlock>とを<xref:System.Windows.Controls.StackPanel>に追加<xref:System.Windows.Controls.ContentControl.Content%2A>し、をプロパティ<xref:System.Windows.Controls.StackPanel>に割り当てることができます。 コントロールには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の視覚的要素と任意のデータを表示できるため、複雑な視覚化をサポートするために、新しいコントロールを作成したり、既存のコントロールを変更したりする必要性が少なくなります。 の<xref:System.Windows.Controls.Button>コンテンツモデルとその他のコンテンツ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]モデルの詳細については、「 [WPF コンテンツモデル](wpf-content-model.md)」を参照してください。

- **スタイル** <xref:System.Windows.Style>は、コントロールのプロパティを表す値のコレクションです。 スタイルを使用すると、新しいコントロールを作成しなくても、必要なコントロールの外観と動作を備えた再利用可能な表現を作成できます。 たとえば、すべての<xref:System.Windows.Controls.TextBlock>コントロールに対して、フォントサイズが14の赤い Arial フォントを使用するとします。 そこで、リソースとしてスタイルを作成し、それに応じて、適切なプロパティを設定します。 次に<xref:System.Windows.Controls.TextBlock> 、アプリケーションに追加するすべての外観が同じになります。

- **データ テンプレート。** を<xref:System.Windows.DataTemplate>使用すると、コントロールにデータを表示する方法をカスタマイズできます。 たとえば<xref:System.Windows.DataTemplate> 、を使用して、 <xref:System.Windows.Controls.ListBox>でのデータの表示方法を指定できます。  この例については、「[データ テンプレートの概要](../data/data-templating-overview.md)」を参照してください。  には<xref:System.Windows.DataTemplate> 、データの外観をカスタマイズするだけでなく、UI 要素を含めることができます。これにより、カスタム ui の柔軟性が大幅に向上します。  たとえば、を使用<xref:System.Windows.DataTemplate>すると、各項目にチェックボックスが含まれているを<xref:System.Windows.Controls.ComboBox>作成できます。

- **コントロール テンプレート。** の多くの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールで<xref:System.Windows.Controls.ControlTemplate>は、コントロールの構造と外観を定義するためにを使用して、コントロールの外観をコントロールの機能から分離します。 コントロールの外観は、を再定義<xref:System.Windows.Controls.ControlTemplate>することによって大幅に変更できます。  たとえば、信号機のような外観のコントロールが必要だとします。 このコントロールのユーザー インターフェイスと機能は単純です。  コントロールは 3 つの円で構成され、一度に点灯するのはそのうちの 1 つだけです。 一部のリフレクションでは、は<xref:System.Windows.Controls.RadioButton>一度に1つだけ選択される機能を提供していますが、の既定の外観<xref:System.Windows.Controls.RadioButton>では、信号の光源のように見えません。  は<xref:System.Windows.Controls.RadioButton>コントロールテンプレートを使用して外観を定義するため、コントロールの要件に<xref:System.Windows.Controls.ControlTemplate>合わせてを再定義し、オプションボタンを使用して信号を作成するのは簡単です。

  > [!NOTE]
  > はを<xref:System.Windows.DataTemplate>使用<xref:System.Windows.Controls.RadioButton> できますが、この例では十分では<xref:System.Windows.DataTemplate>ありません。  は<xref:System.Windows.DataTemplate> 、コントロールのコンテンツの外観を定義します。 の<xref:System.Windows.Controls.RadioButton>場合、コンテンツは、 <xref:System.Windows.Controls.RadioButton>が選択されているかどうかを示す円の右側に表示されます。  信号機の例では、オプション ボタンに必要なのは "点灯" する円だけです。 信号の外観要件はの既定の外観<xref:System.Windows.Controls.RadioButton>とは異なるため、を<xref:System.Windows.Controls.ControlTemplate>再定義する必要があります。  一般に、 <xref:System.Windows.DataTemplate>はコントロールのコンテンツ (またはデータ) を定義するために使用さ<xref:System.Windows.Controls.ControlTemplate>れ、を使用してコントロールを構造化する方法を定義します。

- **トリガー。** を<xref:System.Windows.Trigger>使用すると、新しいコントロールを作成せずに、コントロールの外観と動作を動的に変更できます。 たとえば、アプリケーションに複数<xref:System.Windows.Controls.ListBox>のコントロールがあり、それぞれ<xref:System.Windows.Controls.ListBox>の項目を選択したときに太字と赤にする必要があるとします。 最初の性質は、から<xref:System.Windows.Controls.ListBox>継承するクラスを作成し、 <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A>選択した項目の外観を変更するためにメソッドをオーバーライドすることですが、より適切な方法は、の<xref:System.Windows.Controls.ListBoxItem>外観を変更するのスタイルにトリガーを追加することです。選択された項目。 トリガーを使用すると、プロパティ値を変更したり、プロパティ値に基づいた処理を実行したりできます。 を<xref:System.Windows.EventTrigger>使用すると、イベントが発生したときにアクションを実行できます。

スタイル、テンプレート、トリガーの詳細については、「[スタイルとテンプレート](styling-and-templating.md)」を参照してください。

一般に、既存のコントロールと同じ機能を持ち、外観が異なるコントロールが必要な場合は、このセクションで説明した方法のいずれかを使用して、既存のコントロールの外観を変更できないかどうかをまず検討することをお勧めします。

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>コントロール作成モデル

リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用すると、新しいコントロールを作成する必要性が最小限に抑えられます。 ただし、新しいコントロールを作成する必要がある場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種のコントロール作成モデルを理解することが重要です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、コントロールを作成するための一般的なモデルが 3 つあり、各モデルはそれぞれ異なる機能と柔軟性レベルを備えています。 3つのモデルの基本クラスは<xref:System.Windows.Controls.UserControl>、 <xref:System.Windows.Controls.Control>、、 <xref:System.Windows.FrameworkElement>およびです。

### <a name="deriving-from-usercontrol"></a>UserControl からの派生

で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールを作成する最も簡単な方法は、から<xref:System.Windows.Controls.UserControl>派生することです。 から<xref:System.Windows.Controls.UserControl>継承するコントロールを作成する場合は、既存のコンポーネント<xref:System.Windows.Controls.UserControl>をに追加し、コンポーネントに名前を付けると共[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]に、でイベントハンドラーを参照します。 次に、指定の要素を参照し、コードでイベント ハンドラーを定義します。 この開発モデルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーション開発に使用されるモデルとよく似ています。

が正しく構築され<xref:System.Windows.Controls.UserControl>ていれば、はリッチコンテンツ、スタイル、およびトリガーの利点を活用できます。 ただし、コントロールがから<xref:System.Windows.Controls.UserControl>継承されている場合、コントロールを使用するユーザーは、 <xref:System.Windows.DataTemplate>または<xref:System.Windows.Controls.ControlTemplate>を使用してその外観をカスタマイズすることはできません。  テンプレートをサポートするカスタムコントロールを<xref:System.Windows.Controls.Control>作成するには、クラスまたはその派生<xref:System.Windows.Controls.UserControl>クラス (を除く) から派生する必要があります。

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl からの派生の利点

次のすべて<xref:System.Windows.Controls.UserControl>に該当する場合は、から派生することを検討してください。

- アプリケーションの構築と同じ方法でコントロールをビルドする必要がある場合。

- コントロールが既存のコンポーネントのみで構成されている場合。

- 複雑なカスタマイズをサポートする必要がない場合。

### <a name="deriving-from-control"></a>Control からの派生

<xref:System.Windows.Controls.Control>クラスからの派生は、既存[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のほとんどのコントロールで使用されるモデルです。 <xref:System.Windows.Controls.Control>クラスを継承するコントロールを作成する場合は、テンプレートを使用してそのコントロールの外観を定義します。 これにより、操作ロジックと視覚的表現とが分離されます。 また、イベントではなくコマンドとバインドを使用して、UI とロジックを分離し、可能な限りの<xref:System.Windows.Controls.ControlTemplate>要素の参照を回避することもできます。  コントロールの UI とロジックが適切に分離されている場合、コントロールのユーザーはコントロール<xref:System.Windows.Controls.ControlTemplate>の外観を再定義できます。 カスタム<xref:System.Windows.Controls.Control>を構築することは、を構築する<xref:System.Windows.Controls.UserControl>ほど簡単では<xref:System.Windows.Controls.Control>ありませんが、カスタムでは最も柔軟性があります。

#### <a name="benefits-of-deriving-from-control"></a>Control からの派生の利点

次のいずれ<xref:System.Windows.Controls.Control>かに該当する<xref:System.Windows.Controls.UserControl>場合は、クラスを使用する代わりに、から派生することを検討してください。

- を使用して、 <xref:System.Windows.Controls.ControlTemplate>コントロールの外観をカスタマイズできるようにします。

- コントロールがさまざまなテーマをサポートする必要がある場合。

### <a name="deriving-from-frameworkelement"></a>FrameworkElement からの派生

から派生した<xref:System.Windows.Controls.UserControl>コントロール<xref:System.Windows.Controls.Control> 、または既存の要素の作成に依存しているコントロール。 を継承<xref:System.Windows.FrameworkElement>するすべてのオブジェクトが<xref:System.Windows.Controls.ControlTemplate>に存在する可能性があるので、多くのシナリオではこれは許容できるソリューションです。 しかし、場合によっては、単純な要素コンポジションでは、コントロールの外観に必要な機能を実現できないことがあります。 これらのシナリオでは、のコンポーネント<xref:System.Windows.FrameworkElement>を基にして、適切な選択を行うことができます。

ビルド<xref:System.Windows.FrameworkElement>ベースのコンポーネントには、直接レンダリングとカスタム要素構成という2つの標準的なメソッドがあります。 直接レンダリングでは、 <xref:System.Windows.UIElement.OnRender%2A>の<xref:System.Windows.FrameworkElement>メソッドをオーバーライド<xref:System.Windows.Media.DrawingContext>し、コンポーネントのビジュアルを明示的に定義する操作を提供します。 これは、および<xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border>によって使用されるメソッドです。 カスタム要素の構成では、型<xref:System.Windows.Media.Visual>のオブジェクトを使用して、コンポーネントの外観を構成します。 例については、「[DrawingVisual オブジェクトの使用](../graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。 <xref:System.Windows.Controls.Primitives.Track>は、カスタム要素構成[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用するのコントロールの例です。 同じコントロールでダイレクト レンダリングとカスタム要素コンポジションを混在させることもできます。

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement からの派生の利点

次のいずれ<xref:System.Windows.FrameworkElement>かに該当する場合は、から派生することを検討してください。

- コントロールの外観について、単純な要素コンポジションが提供する以上の厳密な制御を必要とする場合。

- 独自のレンダリング ロジックを定義して、コントロールの外観を定義する必要がある場合。

- <xref:System.Windows.Controls.UserControl> と<xref:System.Windows.Controls.Control>で実現できることを上回る方法で既存の要素を構成する必要があります。

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

- という<xref:System.Windows.DependencyProperty>名前`ValueProperty`の識別子を`public` `readonly`フィールドとして`static`定義します。

- を呼び出し<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>て、プロパティ名をプロパティシステムに登録し、次の値を指定します。

  - プロパティの名前。

  - プロパティの型。

  - プロパティを所有する型。

  - プロパティのメタデータ。 メタデータには、プロパティの既定値<xref:System.Windows.CoerceValueCallback> 、 <xref:System.Windows.PropertyChangedCallback>およびが含まれています。

- という名前`Value`の CLR ラッパープロパティを定義します。これは、プロパティの`get`アクセサーと`set`アクセサーを実装することによって、依存関係プロパティの登録に使用される名前と同じです。 `get`アクセサーと`set`アクセサーは、それぞれと<xref:System.Windows.DependencyObject.GetValue%2A>を<xref:System.Windows.DependencyObject.SetValue%2A>呼び出すだけであることに注意してください。 クライアントと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はアクセサーをバイパスしてとを<xref:System.Windows.DependencyObject.SetValue%2A>直接呼び出す<xref:System.Windows.DependencyObject.GetValue%2A>ことができるため、依存関係プロパティのアクセサーに追加のロジックが含まれないようにすることをお勧めします。 たとえば、プロパティがデータ ソースにバインドされている場合、プロパティの `set` アクセサーは呼び出されません。  Get アクセサーと set アクセサーにロジックを追加する代わりに<xref:System.Windows.ValidateValueCallback>、、 <xref:System.Windows.CoerceValueCallback>、および<xref:System.Windows.PropertyChangedCallback>の各デリゲートを使用して応答するか、値が変更されたときにその値を確認します。  これらのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../advanced/dependency-property-callbacks-and-validation.md)」を参照してください。

- <xref:System.Windows.CoerceValueCallback>という名前`CoerceValue`ののメソッドを定義します。 `CoerceValue` によって、`Value` は `MinValue` 以上で `MaxValue` 以下になります。

- に、という名前<xref:System.Windows.PropertyChangedCallback> `OnValueChanged`のメソッドを定義します。 `OnValueChanged`オブジェクトを<xref:System.Windows.RoutedPropertyChangedEventArgs%601>作成し、ルーティングイベントの`ValueChanged`発生を準備します。 ルーティング イベントについては、次のセクションで説明します。

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

詳細については、「[カスタム依存関係プロパティ](../advanced/custom-dependency-properties.md)」を参照してください。

### <a name="use-routed-events"></a>ルーティング イベントの使用

依存関係プロパティが CLR プロパティの概念を拡張し、機能が追加されるのと同様に、ルーティングイベントは標準の CLR イベントの概念を拡張します。 新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール作成する場合、イベントをルーティング イベントとして実装することをお勧めします。ルーティング イベントは以下の機能をサポートしているためです。

- 複数のコントロールの親でイベントを処理できます。 イベントがバブル イベントの場合、要素ツリー内の単一の親はイベントをサブスクライブできます。 これにより、アプリケーション開発者は、複数のコントロールのイベントに 1 つのハンドラーで対応できます。 たとえば、コントロールが内<xref:System.Windows.Controls.ListBox>の各項目の一部である場合 ( <xref:System.Windows.DataTemplate>に含まれているため)、アプリケーション開発者はに対して<xref:System.Windows.Controls.ListBox>コントロールのイベントのイベントハンドラーを定義できます。 いずれかのコントロールでイベントが発生するたびに、そのイベント ハンドラーが呼び出されます。

- ルーティングイベントは、で<xref:System.Windows.EventSetter>使用できます。これにより、アプリケーション開発者は、スタイル内でイベントのハンドラーを指定できます。

- ルーティングイベントは、で<xref:System.Windows.EventTrigger>使用できます。これは、を使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]してプロパティをアニメーション化する場合に便利です。 詳しくは、「 [アニメーションの概要](../graphics-multimedia/animation-overview.md)」をご覧ください。

次に示す例では、以下の処理を実行して、ルーティング イベントを定義します。

- という<xref:System.Windows.RoutedEvent>名前`ValueChangedEvent`の識別子を`public` `readonly`フィールドとして`static`定義します。

- <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>メソッドを呼び出して、ルーティングイベントを登録します。 この例では、を呼び出す<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>ときに次の情報を指定します。

  - イベントの名前が `ValueChanged` であること。

  - ルーティング方法はです<xref:System.Windows.RoutingStrategy.Bubble>。つまり、ソース (イベントを発生させたオブジェクト) のイベントハンドラーが最初に呼び出され、次に、ソースの親要素のイベントハンドラーが連続して呼び出されます。その後、最も近い親要素。

  - イベントハンドラーの型はで、 <xref:System.Windows.RoutedPropertyChangedEventHandler%601> <xref:System.Decimal>型を使用して構築されます。

  - イベントを所有する型が `NumericUpDown` であること。

- `ValueChanged` という名前のパブリック イベントを宣言し、イベント アクセサー宣言を含めます。 この例で<xref:System.Windows.UIElement.AddHandler%2A>は、 `add`アクセサー宣言と<xref:System.Windows.UIElement.RemoveHandler%2A> `remove`アクセサー宣言でを呼び出して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベントサービスを使用します。

- `ValueChanged`イベントを発生させる、保護された仮想メソッド `OnValueChanged` を作成します。

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

詳細については、「[ルーティング イベントの概要](../advanced/routed-events-overview.md)」および「[カスタム ルーティング イベントを作成する](../advanced/how-to-create-a-custom-routed-event.md)」を参照してください。

### <a name="use-binding"></a>バインディングの使用

コントロールの UI とロジックを分離するには、データ バインディングを使用する方法もあります。 これは、を<xref:System.Windows.Controls.ControlTemplate>使用してコントロールの外観を定義する場合に特に重要です。 データ バインディングを使用すると、コードから UI の特定の部分を参照する必要性がなくなる場合があります。 に含まれる<xref:System.Windows.Controls.ControlTemplate>要素を参照しないようにすることをお勧めします。このコードでは、 <xref:System.Windows.Controls.ControlTemplate>と<xref:System.Windows.Controls.ControlTemplate>に含まれる要素が変更された場合、参照される<xref:System.Windows.Controls.ControlTemplate>要素を新しいに含める必要があるためです。

次の例では<xref:System.Windows.Controls.TextBlock> 、 `NumericUpDown`コントロールのを更新し、それに名前を割り当て、コードで名前を使用してテキストボックスを参照しています。

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

次の例では、バインディングを使用して同じことを実現しています。

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

データ バインディングの詳細については、「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。

### <a name="design-for-designers"></a>デザイナーに対応したデザイン

[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] でカスタム WPF コントロールのサポート (たとえば、[プロパティ] ウィンドウでのプロパティ編集) を利用するには、以下のガイドラインに従います。  の開発[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]の詳細については、「 [Visual Studio での XAML のデザイン](/visualstudio/designers/designing-xaml-in-visual-studio)」を参照してください。

#### <a name="dependency-properties"></a>依存関係プロパティ

前の「依存関係`get`プロパティ`set`の使用」で説明したように、CLR とアクセサーを実装してください。 デザイナーは、ラッパーを使用して依存関係プロパティの存在を検出する場合がありますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] およびコントロールのクライアントと同様、プロパティを取得または設定するときにアクセサーを呼び出す必要はありません。

#### <a name="attached-properties"></a>アタッチされるプロパティ

以下のガイドラインに従って、カスタム コントロールに添付プロパティを実装する必要があります。

- `public` <xref:System.Windows.DependencyProperty> `readonly` `Property` `static` メソッドを使用して作成された、PropertyName という形式のがあります。 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> に<xref:System.Windows.DependencyProperty.RegisterAttached%2A>渡されるプロパティ名は*PropertyName*と一致する必要があります。

- `Set` *PropertyName* および `Get` *PropertyName* という名前の `public``static` CLR メソッドのペアを実装します。 どちらのメソッドも、から<xref:System.Windows.DependencyProperty>派生したクラスを最初の引数として受け取る必要があります。 また、`Set` *PropertyName* メソッドでは、プロパティの登録データ型と同じ型の引数も受け取ります。 `Get` *PropertyName*メソッドでは、同じ型の値を返す必要があります。 `Set` *PropertyName*メソッドがない場合、プロパティは読み取り専用としてマークされます。

- `Set`*Propertyname*と`Get` *propertyname*は、それぞれ対象の<xref:System.Windows.DependencyObject.GetValue%2A>依存<xref:System.Windows.DependencyObject.SetValue%2A>関係オブジェクトのメソッドとメソッドにそれぞれ直接ルーティングする必要があります。 デザイナーが添付プロパティにアクセスするには、メソッド ラッパー経由で呼び出す場合もあれば、対象の依存関係オブジェクトを直接呼び出す場合もあります。

添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

### <a name="define-and-use-shared-resources"></a>共有リソースの定義と使用

アプリケーションと同じアセンブリにコントロールを含めることも、複数のアプリケーションが使用できる別のアセンブリにコントロールをパッケージ化することもできます。 このトピックで説明した情報の大部分は、使用する方法に関係なく適用されます。  ただし、1 つだけ例外があります。  アプリケーションと同じアセンブリ内にコントロールを配置する場合、App.xaml ファイルにグローバル リソースを自由に追加できます。 ただし、コントロールのみを含むアセンブリには<xref:System.Windows.Application>オブジェクトが関連付けられていないため、app.xaml ファイルは使用できません。

アプリケーションがリソースを検索するときは、次に示す順序で 3 つのレベルを検索します。

1. 要素レベル。

   システムは、リソースを参照する要素から検索を開始し、ルート要素に到達するまで、論理上の親のリソースの検索を継続します。

2. アプリケーション レベル。

   <xref:System.Windows.Application>オブジェクトによって定義されたリソース。

3. テーマ レベル。

   テーマ レベルのディクショナリは、Themes という名前のサブフォルダーに格納されています。  Themes フォルダー内のファイルはテーマに対応しています。  たとえば、Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml などのファイルがあります。  generic.xaml という名前のファイルが含まれている場合もあります。  システムがテーマ レベルでリソースを検索するとき、最初にテーマ固有のファイル内を検索し、次に generic.xaml 内を検索します。

アプリケーションとは別のアセンブリ内にコントロールを含めるときは、グローバル リソースを要素レベルまたはテーマ レベルに配置する必要があります。 どちらに配置する場合も、それぞれの利点があります。

#### <a name="defining-resources-at-the-element-level"></a>要素レベルでのリソース定義

カスタムのリソース ディクショナリを作成し、それをコントロールのリソース ディクショナリと結合することによって、共有リソースを要素レベルで定義できます。  このメソッドで定義する場合は、リソース ファイルに任意の名前を付けて、コントロールと同じフォルダーに配置できます。 要素レベルでのリソースでは、単純な文字列をキーとして使用することもできます。 次の例では<xref:System.Windows.Media.LinearGradientBrush> 、Dictionary1 という名前のリソースファイルを作成します。

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

ディクショナリを定義したら、それをコントロールのリソース ディクショナリにマージする必要があります。  これには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用します。

次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してリソース ディクショナリを結合します。

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

この方法の欠点は、オブジェクトを<xref:System.Windows.ResourceDictionary>参照するたびにオブジェクトが作成されることです。  たとえば、ライブラリに10個のカスタムコントロールがあり、XAML を使用して各コントロールの共有リソースディクショナリをマージする場合、同<xref:System.Windows.ResourceDictionary>一のオブジェクトを10個作成します。  これを回避するには、コード内のリソースをマージする静的クラスを作成し<xref:System.Windows.ResourceDictionary>、生成されたを返します。

次の例では、共有<xref:System.Windows.ResourceDictionary>を返すクラスを作成します。

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

次の例では、`InitializeComponent` を呼び出す前に、共有リソースをコントロールのコンス トラクター内でカスタム コントロールのリソースと結合します。  は静的プロパティ<xref:System.Windows.ResourceDictionary>であるため、は1回だけ作成されます。 `SharedDictionaryManager.SharedDictionary` `InitializeComponent` が呼び出される前に、リソース ディクショナリが結合されため、コントロールは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内でリソースを使用できます。

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>テーマ レベルでのリソース定義

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、さまざまな Windows テーマ用にリソースを作成できます。  コントロールの作成者は、特定のテーマ用のリソースを定義して、使用するテーマに応じてコントロールの外観を変更できます。 たとえば、windows クラシック<xref:System.Windows.Controls.Button>テーマにおけるの外観 (windows 2000 <xref:System.Windows.Controls.Button>の既定のテーマ) は、windows Luna テーマ (windows XP の既定のテーマ) とは異なります。 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate>テーマごとに。

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

を<xref:System.Windows.Controls.ControlTemplate>テーマ固有のリソースディクショナリファイルに配置する場合は、次の例に示すように、コントロールの静的コンストラクターを作成<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29>し、で<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>メソッドを呼び出す必要があります。

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>テーマ リソース用のキーの定義と参照

要素レベルでリソースを定義するときに、文字列をキーとして割り当て、その文字列を使用してリソースにアクセスできます。 テーマレベルでリソースを定義する場合は、を<xref:System.Windows.ComponentResourceKey>キーとして使用する必要があります。  次の例では、generic.xaml でリソースを定義します。

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

次の例では、 <xref:System.Windows.ComponentResourceKey>キーとしてを指定することによって、リソースを参照しています。

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>テーマ リソースの場所の指定

コントロールのリソースを見つけるには、アセンブリにコントロール固有のリソースが含まれていることを、ホスト アプリケーションが認識する必要があります。 これを行うには、 <xref:System.Windows.ThemeInfoAttribute>コントロールを含むアセンブリにを追加します。 に<xref:System.Windows.ThemeInfoAttribute> は、<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>汎用リソースの場所を指定するプロパティと、テーマ固有のリソースの場所を指定するプロパティがあります。<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>

次の例では<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> 、 <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>プロパティと<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>プロパティをに設定して、汎用およびテーマ固有のリソースがコントロールと同じアセンブリ内にあることを指定します。

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>関連項目

- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WPF におけるパッケージの URI](../app-development/pack-uris-in-wpf.md)
- [コントロールのカスタマイズ](control-customization.md)
