---
title: ストーリーボードの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 4d5a5ee3f1fcbd09fad9e25773d0e508209e1492
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855838"
---
# <a name="storyboards-overview"></a>ストーリーボードの概要

このトピックでは、オブジェクト<xref:System.Windows.Media.Animation.Storyboard>を使用してアニメーションを整理および適用する方法について説明します。 オブジェクトを対話的に操作<xref:System.Windows.Media.Animation.Storyboard>する方法と、間接的なプロパティのターゲット構文について説明します。

## <a name="prerequisites"></a>必須コンポーネント

このトピックを理解するには、さまざまな種類のアニメーションとその基本的な機能に精通している必要があります。 アニメーションの概要については、「[アニメーションの概要](animation-overview.md)」を参照してください。 また、添付プロパティの使用方法についても理解しておく必要があります。 添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>ストーリーボードとは何か

タイムラインの型で役に立つのは、アニメーションだけではありません。 他にも一連のタイムラインの編成を容易にし、タイムラインをプロパティに適用するための Timeline クラスが提供されています。 コンテナータイムラインは<xref:System.Windows.Media.Animation.TimelineGroup>クラスから派生し、および<xref:System.Windows.Media.Animation.Storyboard>を含み<xref:System.Windows.Media.Animation.ParallelTimeline>ます。

<xref:System.Windows.Media.Animation.Storyboard>は、格納されているタイムラインのターゲット情報を提供するコンテナータイムラインの一種です。 ストーリーボードには、他の<xref:System.Windows.Media.Animation.Timeline>コンテナーのタイムラインやアニメーションなど、任意の種類のを含めることができます。 <xref:System.Windows.Media.Animation.Storyboard>オブジェクトを使用すると、さまざまなオブジェクトやプロパティに影響を与えるタイムラインを1つのタイムラインツリーにまとめることができるため、複雑なタイミングの動作を簡単に整理および制御できます。 たとえば、次の 3 つのことを実行するボタンを必要としているとします。

- ユーザーに選択されると、拡大して色が変わる。

- クリックされると、いったん縮小してから元のサイズに戻る。

- 無効にされると、縮小し、50% の不透明度になる。

この場合、同じオブジェクトに適用するアニメーションのセットを複数用意し、ボタンの状態に応じてさまざまな場合に再生します。 <xref:System.Windows.Media.Animation.Storyboard>オブジェクトを使用すると、アニメーションを整理し、グループ内で1つ以上のオブジェクトに適用することができます。

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>ストーリーボードはどこで使用できるか

は<xref:System.Windows.Media.Animation.Storyboard> 、system.windows.media.animation.animatable> クラスの依存関係プロパティをアニメーション化するために使用できます (クラス system.windows.media.animation.animatable> を作成する方法の詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください)。 ただし、storyboarding はフレームワークレベルの機能であるため、オブジェクトは<xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>のに属している必要があります。

たとえば、を<xref:System.Windows.Media.Animation.Storyboard>使用して次の操作を行うことができます。

- ボタン (の<xref:System.Windows.FrameworkElement>型) の背景を描画する(非フレームワーク要素)をアニメーション化します。<xref:System.Windows.Media.SolidColorBrush>

- (<xref:System.Windows.FrameworkElement>) <xref:System.Windows.Media.SolidColorBrush>を使用して<xref:System.Windows.Controls.Image>表示される<xref:System.Windows.Media.GeometryDrawing> (非フレームワーク要素) の塗りつぶしを描画する (非フレームワーク要素) をアニメーション化します。

- <xref:System.Windows.Media.SolidColorBrush>コードで、が<xref:System.Windows.FrameworkElement>含まれているクラスによって宣言<xref:System.Windows.Media.SolidColorBrush>されたをアニメーション化し<xref:System.Windows.FrameworkElement>ます (その名前がに登録されている場合)。

ただし、 <xref:System.Windows.Media.Animation.Storyboard>を使用して、名前を<xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement>また<xref:System.Windows.Media.SolidColorBrush>は<xref:System.Windows.FrameworkContentElement>に登録していないをアニメーション化すること<xref:System.Windows.FrameworkContentElement>はできません。または、またはのプロパティの設定には使用されませんでした。

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>ストーリーボードを使用してアニメーションを適用する方法

を使用<xref:System.Windows.Media.Animation.Storyboard>してアニメーションを整理して適用するには、アニメーションを<xref:System.Windows.Media.Animation.Storyboard>の子タイムラインとして追加します。 クラス<xref:System.Windows.Media.Animation.Storyboard>は、添付<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>とアタッチされたプロパティを提供します。 これらのプロパティをアニメーションで設定して、アニメーションのターゲット オブジェクトとターゲット プロパティを指定します。

アニメーションをターゲットに適用するには、トリガー <xref:System.Windows.Media.Animation.Storyboard>アクションまたはメソッドを使用してを開始します。 で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.EventTrigger>は、、 、<xref:System.Windows.Trigger>また<xref:System.Windows.Media.Animation.BeginStoryboard> は<xref:System.Windows.DataTrigger>を含むオブジェクトを使用します。 コードでは、 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを使用することもできます。

次の表は、各<xref:System.Windows.Media.Animation.Storyboard>開始手法がサポートされる場所を示しています。インスタンスごと、スタイル、コントロールテンプレート、データテンプレートです。 "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。

|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>および<xref:System.Windows.EventTrigger>|[はい]|はい|はい|[はい]|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>およびプロパティ<xref:System.Windows.Trigger>|いいえ|はい|はい|[はい]|[プロパティ値が変化したときにアニメーションをトリガーする](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>および<xref:System.Windows.DataTrigger>|いいえ|はい|はい|[はい]|[方法: データが変更したときにアニメーションをトリガーする](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|[はい]|いいえ|いいえ|いいえ|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|

次の例では<xref:System.Windows.Media.Animation.Storyboard> 、を使用<xref:System.Windows.FrameworkElement.Width%2A>して<xref:System.Windows.Shapes.Rectangle> 、要素<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Shapes.Rectangle>と、 <xref:System.Windows.Media.SolidColorBrush>描画に使用されるのをアニメーション化します。

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

以下のセクションでは<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 、 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>プロパティと添付プロパティについて詳しく説明します。

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>フレームワーク要素、フレームワーク コンテンツ要素、およびフリーズ可能オブジェクトの対象化

アニメーションでは、そのターゲットを見つけるために、ターゲットの名前とアニメーション化するプロパティを認識する必要があることについては前のセクションで説明しました。 アニメーション化するプロパティを指定するのは簡単です<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> 。アニメーション化するプロパティの名前を設定するだけです。  アニメーションの<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>プロパティを設定して、アニメーション化するプロパティを持つオブジェクトの名前を指定します。

<xref:System.Windows.Setter.TargetName%2A>プロパティを機能させるには、対象のオブジェクトに名前を付ける必要があります。 <xref:System.Windows.FrameworkElement> <xref:System.Windows.Freezable>のまたはへの名前の割り当ては、オブジェクトへの名前の割り当てとは異なります。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.FrameworkContentElement>

フレームワーク要素は、 <xref:System.Windows.FrameworkElement>クラスを継承するクラスです。 フレームワーク要素の例と<xref:System.Windows.Window>し<xref:System.Windows.Controls.DockPanel>て<xref:System.Windows.Controls.Button> <xref:System.Windows.Shapes.Rectangle>、、、、があります。 基本的に、ウィンドウ、パネル、およびコントロールはすべて要素です。 フレームワークコンテンツ要素は、 <xref:System.Windows.FrameworkContentElement>クラスを継承するクラスです。 フレームワークコンテンツ要素の例と<xref:System.Windows.Documents.FlowDocument>し<xref:System.Windows.Documents.Paragraph>て、やがあります。 型がフレームワーク要素またはフレームワーク コンテンツ要素であるかどうかが明確でない場合は、Name プロパティが含まれているかどうかを確認します。 含まれている場合は、フレームワーク要素またはフレームワーク コンテンツ要素と考えられます。 確かめるには、その型のページの「継承階層」を参照してください。

の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]フレームワーク要素またはフレームワークコンテンツ要素のターゲット設定を有効にするには、 <xref:System.Windows.FrameworkElement.Name%2A>そのプロパティを設定します。 コードでは、 <xref:System.Windows.NameScope.RegisterName%2A>メソッドを使用して、を<xref:System.Windows.NameScope>作成した要素に要素名を登録する必要もあります。

前の例で作成した次の例では、 `MyRectangle`と<xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement>いう名前を割り当てています。

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

名前が割り当てられると、その要素のプロパティはアニメーション化できます。

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>型は、 <xref:System.Windows.Freezable>クラスを継承するクラスです。 の<xref:System.Windows.Freezable>例と<xref:System.Windows.Media.SolidColorBrush>し<xref:System.Windows.Media.RotateTransform>て<xref:System.Windows.Media.GradientStop>、、、などがあります。

<xref:System.Windows.Freezable> の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アニメーションによるのターゲット設定を有効にするには、 [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)を使用して名前を割り当てます。 コードでは、 <xref:System.Windows.NameScope.RegisterName%2A>メソッドを使用して、を<xref:System.Windows.NameScope>作成した要素に名前を登録します。

次の例では、 <xref:System.Windows.Freezable>オブジェクトに名前を割り当てます。

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

これで、オブジェクトをアニメーションのターゲットにすることができます。

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>オブジェクトでは、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティを解決するために名前スコープを使用します。 WPF 名前スコープの詳細については、「[WPF XAML 名前スコープ](../advanced/wpf-xaml-namescopes.md)」を参照してください。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティを省略した場合、アニメーションは、定義されている要素、またはスタイルの場合はスタイルが設定された要素を対象とします。

<xref:System.Windows.Freezable>オブジェクトに名前を割り当てることはできません。 たとえば、 <xref:System.Windows.Freezable>がリソースとして宣言されているか、スタイルでプロパティ値を設定するために使用されている場合、名前を指定することはできません。 名前が割り当てられていないため、それを直接ターゲットにすることができません。ただし、間接的にターゲットにすることはできます。 以下のセクションでは、間接的な対象化の使用方法について説明します。

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>間接的な対象化

がリソースとし<xref:System.Windows.Freezable>て宣言されている場合や、スタイルのプロパティ値を設定するために使用される場合など、がアニメーションによって直接ターゲットになることはありません。 <xref:System.Windows.Freezable> このような場合でも、直接ターゲットにすることはできませんが<xref:System.Windows.Freezable> 、オブジェクトをアニメーション化することはできます。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティをの名前<xref:System.Windows.Freezable>で設定するのではなく、 <xref:System.Windows.Freezable> "所属" の要素の名前を指定します。 たとえば、四角形要素<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Shapes.Shape.Fill%2A>のを設定するために使用されるは、その四角形に属します。 ブラシをアニメーション化するには、アニメーションのを<xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 、フレームワーク要素またはフレームワークコンテンツ要素のプロパティから開始するプロパティのチェーンに設定し<xref:System.Windows.Freezable>ます。これは、アニメーション化する<xref:System.Windows.Freezable>プロパティを設定して終了するために使用されます。

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

<xref:System.Windows.Freezable>がフリーズしている場合は、複製が行われ、その複製がアニメーション化されることに注意してください。 この場合、元のオブジェクトは実際<xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A>にはアニメーション化`false`されていないため、元のオブジェクトのプロパティはを返し続けます。 複製の詳細については、「 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」を参照してください。

また、間接的なプロパティの対象化を使用するとき、存在しないオブジェクトを対象化する可能性があることに注意してください。 たとえば、特定のボタンのが<xref:System.Windows.Controls.Control.Background%2A>で設定<xref:System.Windows.Media.SolidColorBrush>され、その色をアニメーション化しようとするとします。実際には<xref:System.Windows.Media.LinearGradientBrush> 、ボタンの背景を設定するためにが使用されていました。 このような場合、例外はスローされません。は、プロパティへの<xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A>変更に反応しないため、アニメーションは表示されません。

以下のセクションでは、間接的なプロパティの対象化の構文について詳しく説明します。

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML でフリーズ可能オブジェクトのプロパティを間接的に対象化する

で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]freezable のプロパティを対象にするには、次の構文を使用します。

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *Elementpropertyname*は、を設定する<xref:System.Windows.FrameworkElement>ために<xref:System.Windows.Freezable>使用されるのプロパティです。

- *FreezablePropertyName*は、 <xref:System.Windows.Freezable>アニメーション化するのプロパティです。

次のコードは、四角形要素の<xref:System.Windows.Media.SolidColorBrush.Color%2A>を<xref:System.Windows.Shapes.Shape.Fill%2A>設定<xref:System.Windows.Media.SolidColorBrush>するために使用されるのをアニメーション化する方法を示しています。

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。

コレクションに含まれるフリーズ可能オブジェクトをターゲットにするには、次のパス構文を使用します。

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

ここで、 *Collectionindex*は、配列またはコレクション内のオブジェクトのインデックスです。

たとえば、四角形<xref:System.Windows.Media.TransformGroup>にリソースが<xref:System.Windows.UIElement.RenderTransform%2A>プロパティに適用されていて、そこに含まれている変換の1つをアニメーション化するとします。

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

次のコードは、前の例<xref:System.Windows.Media.RotateTransform.Angle%2A>で示した<xref:System.Windows.Media.RotateTransform>のプロパティをアニメーション化する方法を示しています。

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>コードでフリーズ可能オブジェクトのプロパティを間接的に対象化する

コードでは、オブジェクトを<xref:System.Windows.PropertyPath>作成します。 を作成<xref:System.Windows.PropertyPath>するときは、 <xref:System.Windows.PropertyPath.Path%2A>と<xref:System.Windows.PropertyPath.PathParameters%2A>を指定します。

を作成<xref:System.Windows.PropertyPath.PathParameters%2A>するには、依存関係プロパティ<xref:System.Windows.DependencyProperty>の識別子フィールドの一覧を含む型の配列を作成します。 最初の識別子フィールドは、 <xref:System.Windows.FrameworkElement>のプロパティに対して、また<xref:System.Windows.Freezable> <xref:System.Windows.FrameworkContentElement>はを設定するために使用されます。 次の識別子フィールドは、対象となる<xref:System.Windows.Freezable>のプロパティを表します。 これは、 <xref:System.Windows.Freezable>を<xref:System.Windows.FrameworkElement>オブジェクトに接続するプロパティのチェーンと考えることができます。

四角形要素<xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Shapes.Shape.Fill%2A>のを設定するために<xref:System.Windows.Media.SolidColorBrush>使用されるのを対象とする依存関係プロパティチェーンの例を次に示します。

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

を指定<xref:System.Windows.PropertyPath.Path%2A>する必要もあります。 は、の解釈<xref:System.Windows.PropertyPath.PathParameters%2A>方法を示すです。 <xref:System.Windows.PropertyPath.Path%2A> <xref:System.Windows.PropertyPath.Path%2A> <xref:System.String> 次の構文が使用されます。

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Where

- *Ownerpropertyarrayindex*は、の<xref:System.Windows.DependencyProperty> <xref:System.Windows.Freezable>設定に使用される<xref:System.Windows.FrameworkElement>オブジェクトのプロパティの識別子を含む配列のインデックスです。

- *FreezablePropertyArrayIndex*は、対象のプロパティ<xref:System.Windows.DependencyProperty>の識別子を含む配列のインデックスです。

次の例は、 <xref:System.Windows.PropertyPath.Path%2A>前の例で<xref:System.Windows.PropertyPath.PathParameters%2A>定義したに付随するを示しています。

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

次の例では、前の例のコードを組み合わせ<xref:System.Windows.Media.SolidColorBrush.Color%2A>て、 <xref:System.Windows.Media.SolidColorBrush>四角形要素<xref:System.Windows.Shapes.Shape.Fill%2A>のを設定するために使用されるのをアニメーション化します。

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。 たとえば、四角形<xref:System.Windows.Media.TransformGroup>にリソースが<xref:System.Windows.UIElement.RenderTransform%2A>プロパティに適用されていて、そこに含まれている変換の1つをアニメーション化するとします。

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

コレクションに含ま<xref:System.Windows.Freezable>れるを対象にするには、次のパス構文を使用します。

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

ここで、 *Collectionindex*は、配列またはコレクション内のオブジェクトのインデックスです。

の2番<xref:System.Windows.Media.RotateTransform.Angle%2A>目の変換<xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.TransformGroup>であるのプロパティを対象にするには、次<xref:System.Windows.PropertyPath.Path%2A>の<xref:System.Windows.PropertyPath.PathParameters%2A>とを使用します。

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

次の例は、内<xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.TransformGroup>に<xref:System.Windows.Media.RotateTransform>含まれるのをアニメーション化するための完全なコードを示しています。

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>開始点として Freezable を使用して間接的に対象化する

<xref:System.Windows.Freezable>前のセクションで<xref:System.Windows.FrameworkElement>は、または<xref:System.Windows.FrameworkContentElement>から開始し、 <xref:System.Windows.Freezable>サブプロパティへのプロパティチェーンを作成することにより、を間接的に対象にする方法について説明しています。 を開始点とし<xref:System.Windows.Freezable>て使用し、その<xref:System.Windows.Freezable>サブプロパティの1つを間接的にターゲットにすることもできます。 間接的なターゲット設定の開始<xref:System.Windows.Freezable>点としてを使用する場合には<xref:System.Windows.Freezable> 、1 <xref:System.Windows.Freezable>つの追加の制限が適用されます。これは、開始位置と、間接的に対象となるサブプロパティの間で固定することはできません。

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML での対話形式でのストーリーボードの制御

で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ストーリーボードを開始するには、 <xref:System.Windows.Media.Animation.BeginStoryboard>トリガーアクションを使用します。 <xref:System.Windows.Media.Animation.BeginStoryboard>アニメーションをアニメーション化するオブジェクトとプロパティに、ストーリーボードを開始します。 (このプロセスの詳細については、「[アニメーションとタイミングシステムの概要](animation-and-timing-system-overview.md)」を参照してください)。プロパティ<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>を指定し<xref:System.Windows.Media.Animation.BeginStoryboard>て名前を指定すると、制御可能なストーリーボードになります。 ストーリーボードが開始すると対話的に制御できます。 制御可能なストーリーボード アクションの一覧を次に示します。これらをイベント トリガーで使用して、ストーリーボードを制御します。

- <xref:System.Windows.Media.Animation.PauseStoryboard>:ストーリーボードを一時停止します。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>:一時停止したストーリーボードを再開します。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:ストーリーボードの速度を変更します。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:ストーリーボードがある場合は、そのストーリーボードをその塗りつぶし期間の末尾に進めます。

- <xref:System.Windows.Media.Animation.StopStoryboard>:ストーリーボードを停止します。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>:ストーリーボードを削除します。

次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御しています。

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>コードを使用した対話形式でのストーリーボードの制御

トリガー アクションを使用してアニメーション化する方法については、前の例で説明しました。 コードでは、 <xref:System.Windows.Media.Animation.Storyboard>クラスの対話型メソッドを使用してストーリーボードを制御することもできます。 をコード内で対話型にするには、ストーリーボードの<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドの適切なオーバーロードを使用し、 `true`を指定して、制御可能にする必要があります。 <xref:System.Windows.Media.Animation.Storyboard> 詳細に<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>ついては、のページを参照してください。

次の一覧は、を開始した後にを<xref:System.Windows.Media.Animation.Storyboard>操作するために使用できるメソッドを示しています。

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

これらのメソッドを使用する利点は、オブジェクトまたは<xref:System.Windows.Trigger> <xref:System.Windows.TriggerAction>オブジェクトを作成する必要がないことです。操作する<xref:System.Windows.Media.Animation.Storyboard>制御可能なの参照だけが必要になります。

> [!NOTE]
> に対し<xref:System.Windows.Media.Animation.Clock>て実行<xref:System.Windows.Media.Animation.Storyboard>されるすべての対話型アクションは、次のレンダリングの直前に発生するタイミングエンジンの次の目盛りでも発生します。 たとえば、 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>メソッドを使用してアニメーション内の別の点に移動した場合、プロパティ値はすぐには変更されず、タイミングエンジンの次の目盛りで値が変化します。

次の例は、 <xref:System.Windows.Media.Animation.Storyboard>クラスの対話型メソッドを使用してアニメーションを適用および制御する方法を示しています。

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>スタイル内でアニメーション化を行う

オブジェクトを使用<xref:System.Windows.Media.Animation.Storyboard>して、 <xref:System.Windows.Style>でアニメーションを定義できます。 でのの<xref:System.Windows.Media.Animation.Storyboard>アニメーション<xref:System.Windows.Media.Animation.Storyboard>化は、次の3つの例外を除き、別のを使用する場合と似<xref:System.Windows.Style>ています。

- を<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>指定し<xref:System.Windows.Style>ないでください。は常に、が適用される要素を対象とします。<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを<xref:System.Windows.Freezable>対象にするには、間接的なターゲット設定を使用する必要があります。 間接的なターゲット設定の詳細については、「[間接ターゲット](#pathsyntaxforchangeable)」セクションを参照してください。

- <xref:System.Windows.EventTrigger>また<xref:System.Windows.EventTrigger.SourceName%2A> は<xref:System.Windows.Trigger>に対してを指定することはできません。

- 動的リソース参照またはデータバインディング式を使用して<xref:System.Windows.Media.Animation.Storyboard>プロパティ値を設定またはアニメーションすることはできません。 これは、 <xref:System.Windows.Style>内のすべてがスレッドセーフである必要があり、タイミングシステム<xref:System.Windows.Freezable.Freeze%2A>がオブジェクトをスレッドセーフにするためにオブジェクトを必要<xref:System.Windows.Media.Animation.Storyboard>とするためです。 に<xref:System.Windows.Media.Animation.Storyboard>動的リソース参照またはデータバインディング式が含まれている場合、またはその子タイムラインには、を固定できません。 フリーズとその他<xref:System.Windows.Freezable>の機能の詳細については、「 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」を参照してください。

- で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、またはアニメーションイベントの<xref:System.Windows.Media.Animation.Storyboard>イベントハンドラーを宣言することはできません。

スタイルでストーリーボードを定義する方法を示す例については、「[スタイルのアニメーション化](how-to-animate-in-a-style.md)の例」を参照してください。

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>ControlTemplate 内でアニメーション化を行う

オブジェクトを使用<xref:System.Windows.Media.Animation.Storyboard>して、 <xref:System.Windows.Controls.ControlTemplate>でアニメーションを定義できます。 でのの<xref:System.Windows.Media.Animation.Storyboard>アニメーション<xref:System.Windows.Media.Animation.Storyboard>化は、次の2つの例外を除き、別のを使用する場合と似<xref:System.Windows.Controls.ControlTemplate>ています。

- は、<xref:System.Windows.Controls.ControlTemplate>の子オブジェクトのみを参照できます。<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> が<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>指定されていない場合、アニメーションはが適用<xref:System.Windows.Controls.ControlTemplate>される要素を対象とします。

- または<xref:System.Windows.EventTrigger> のは、<xref:System.Windows.Controls.ControlTemplate>の子オブジェクトのみを参照できます。<xref:System.Windows.Trigger> <xref:System.Windows.EventTrigger.SourceName%2A>

- 動的リソース参照またはデータバインディング式を使用して<xref:System.Windows.Media.Animation.Storyboard>プロパティ値を設定またはアニメーションすることはできません。 これは、 <xref:System.Windows.Controls.ControlTemplate>内のすべてがスレッドセーフである必要があり、タイミングシステム<xref:System.Windows.Freezable.Freeze%2A>がオブジェクトをスレッドセーフにするためにオブジェクトを必要<xref:System.Windows.Media.Animation.Storyboard>とするためです。 に<xref:System.Windows.Media.Animation.Storyboard>動的リソース参照またはデータバインディング式が含まれている場合、またはその子タイムラインには、を固定できません。 フリーズとその他<xref:System.Windows.Freezable>の機能の詳細については、「 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」を参照してください。

- で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、またはアニメーションイベントの<xref:System.Windows.Media.Animation.Storyboard>イベントハンドラーを宣言することはできません。

で<xref:System.Windows.Controls.ControlTemplate>ストーリーボードを定義する方法を示す例については、「 [ControlTemplate のアニメーション化](how-to-animate-in-a-controltemplate.md)の例」を参照してください。

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>プロパティ値が変化したときにアニメーション化を行う

スタイル内およびコントロール テンプレート内では、トリガー オブジェクトを使用して、プロパティが変化したときにストーリーボードを開始します。 例については、「[プロパティ値が変更されたときにアニメーションをトリガー](how-to-trigger-an-animation-when-a-property-value-changes.md)する」および「 [ControlTemplate でアニメーション化](how-to-animate-in-a-controltemplate.md)する」を参照してください。

プロパティ<xref:System.Windows.Trigger>オブジェクトによって適用されるアニメーションは、メソッド<xref:System.Windows.EventTrigger>を使用して<xref:System.Windows.Media.Animation.Storyboard>開始されたアニメーションまたはアニメーションよりも複雑な方法で動作します。  これらは、他の<xref:System.Windows.Trigger>オブジェクトによって定義されたアニメーションを使用して "ハンドハンド" しますが、メソッドによってトリガーされるアニメーションで<xref:System.Windows.EventTrigger>構成します。

## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
