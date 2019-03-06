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
ms.openlocfilehash: 53d31d00729485e99b76305c45eeeb3659a41b7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362943"
---
# <a name="storyboards-overview"></a>ストーリーボードの概要
このトピックでは、使用する方法を示します<xref:System.Windows.Media.Animation.Storyboard>オブジェクトを編成およびアニメーションを適用します。 対話的に操作する方法を説明<xref:System.Windows.Media.Animation.Storyboard>オブジェクトおよび構文を対象とする間接的なプロパティについて説明します。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、さまざまな種類のアニメーションとその基本的な機能に精通している必要があります。 アニメーションの概要については、「[アニメーションの概要](animation-overview.md)」を参照してください。 また、添付プロパティの使用方法についても理解しておく必要があります。 添付プロパティの詳細については、「[添付プロパティの概要](../advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>ストーリーボードとは何か  
 タイムラインの型で役に立つのは、アニメーションだけではありません。 他にも一連のタイムラインの編成を容易にし、タイムラインをプロパティに適用するための Timeline クラスが提供されています。 コンテナー タイムラインから派生して、<xref:System.Windows.Media.Animation.TimelineGroup>クラス、および含める<xref:System.Windows.Media.Animation.ParallelTimeline>と<xref:System.Windows.Media.Animation.Storyboard>します。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>が含まれているタイムラインの対象情報を提供するコンテナー タイムラインの一種です。 ストーリー ボードの任意の型を含めることができます<xref:System.Windows.Media.Animation.Timeline>、他のコンテナー タイムラインやアニメーションなど。 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、オブジェクトとプロパティのさまざまなやすく整理し、複雑なタイミング動作を制御するため、1 つのタイムライン ツリーに影響を与えるタイムラインを組み合わせることができます。 たとえば、次の 3 つのことを実行するボタンを必要としているとします。  
  
-   ユーザーに選択されると、拡大して色が変わる。  
  
-   クリックされると、いったん縮小してから元のサイズに戻る。  
  
-   無効にされると、縮小し、50% の不透明度になる。  
  
 この場合、同じオブジェクトに適用するアニメーションのセットを複数用意し、ボタンの状態に応じてさまざまな場合に再生します。 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用するアニメーションを編成し、1 つまたは複数のオブジェクトをグループに適用されます。  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>ストーリーボードはどこで使用できるか  
 A<xref:System.Windows.Media.Animation.Storyboard>アニメーション クラスの依存関係プロパティをアニメーション化に使用できます (アニメーション化できるクラスは、詳細については、次を参照してください。、[アニメーションの概要](animation-overview.md))。 ただし、ストーリーボーディング フレームワーク レベルの機能があるため、オブジェクトに属する必要があります、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。  
  
 たとえば、使用する、<xref:System.Windows.Media.Animation.Storyboard>以下を実行します。  
  
-   アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景を描画する (非フレームワーク要素) (一種の<xref:System.Windows.FrameworkElement>)、  
  
-   アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>の塗りつぶしを描画する (非フレームワーク要素)、 <xref:System.Windows.Media.GeometryDrawing> (非フレームワーク要素) の表示を使用して、 <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>)。  
  
-   コードでは、アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>も含まれているクラスで宣言された、<xref:System.Windows.FrameworkElement>場合は、<xref:System.Windows.Media.SolidColorBrush>の名前を登録する<xref:System.Windows.FrameworkElement>します。  
  
 ただし、使用できません、<xref:System.Windows.Media.Animation.Storyboard>をアニメーション化する、 <xref:System.Windows.Media.SolidColorBrush> 、その名前を登録しなかった、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、またはのプロパティを設定するには使用されませんでした、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>ストーリーボードを使用してアニメーションを適用する方法  
 使用する、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを編成および適用の子タイムラインとしてアニメーションを追加する、<xref:System.Windows.Media.Animation.Storyboard>します。 <xref:System.Windows.Media.Animation.Storyboard>クラスには、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>添付プロパティ。 これらのプロパティをアニメーションで設定して、アニメーションのターゲット オブジェクトとターゲット プロパティを指定します。  
  
 開始する、ターゲットにアニメーションを適用する、<xref:System.Windows.Media.Animation.Storyboard>トリガー アクションまたはメソッドを使用します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用する、<xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトを<xref:System.Windows.EventTrigger>、 <xref:System.Windows.Trigger>、または<xref:System.Windows.DataTrigger>します。 コードでは、使用することも、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッド。  
  
 次の表に、さまざまな場所を各<xref:System.Windows.Media.Animation.Storyboard>開始手法がサポートされています: インスタンス単位、スタイル、コントロール テンプレート、およびデータ テンプレート。 "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.EventTrigger>|[はい]|はい|はい|[はい]|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> プロパティと、 <xref:System.Windows.Trigger>|いいえ|[はい]|はい|[はい]|[プロパティ値が変化したときにアニメーションをトリガーする](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.DataTrigger>|いいえ|[はい]|はい|[はい]|[方法: データが変更されたときにアニメーションをトリガーします。](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|[はい]|×|×|いいえ|[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard>をアニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>要素と<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を描画するために使用<xref:System.Windows.Shapes.Rectangle>します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 次のセクションで説明します、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>添付プロパティについて詳しく説明します。  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>フレームワーク要素、フレームワーク コンテンツ要素、およびフリーズ可能オブジェクトの対象化  
 アニメーションでは、そのターゲットを見つけるために、ターゲットの名前とアニメーション化するプロパティを認識する必要があることについては前のセクションで説明しました。 アニメーション化するプロパティを指定するは簡単: 設定するだけです<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>アニメーション化するプロパティの名前に置き換えます。  プロパティを設定してアニメーション化するオブジェクトの名前を指定する、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>アニメーションのプロパティ。  
  
 <xref:System.Windows.Setter.TargetName%2A>するのには、プロパティ、ターゲット オブジェクトには名前が必要です。 に対して名前が割り当て、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]する名前の割り当てとは異なります、<xref:System.Windows.Freezable>オブジェクト。  
  
 フレームワーク要素は、これらのクラスを継承するクラス、<xref:System.Windows.FrameworkElement>クラス。 フレームワーク要素の例として、 <xref:System.Windows.Window>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Button>、および<xref:System.Windows.Shapes.Rectangle>します。 基本的に、ウィンドウ、パネル、およびコントロールはすべて要素です。 フレームワーク コンテンツ要素には、これらのクラスを継承するクラス、<xref:System.Windows.FrameworkContentElement>クラス。 フレームワーク コンテンツ要素の例として、<xref:System.Windows.Documents.FlowDocument>と<xref:System.Windows.Documents.Paragraph>します。 型がフレームワーク要素またはフレームワーク コンテンツ要素であるかどうかが明確でない場合は、Name プロパティが含まれているかどうかを確認します。 含まれている場合は、フレームワーク要素またはフレームワーク コンテンツ要素と考えられます。 確かめるには、その型のページの「継承階層」を参照してください。  
  
 フレームワーク要素またはフレームワーク コンテンツ要素内のターゲットを有効にする[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、設定をその<xref:System.Windows.FrameworkElement.Name%2A>プロパティ。 コードでは、するもする必要がありますを使用して、<xref:System.Windows.NameScope.RegisterName%2A>作成した要素を持つ要素の名前を登録するメソッド、 <xref:System.Windows.NameScope>。  
  
 前の例から次の例では、名前を割り当てます`MyRectangle`、 <xref:System.Windows.Shapes.Rectangle>、一種の<xref:System.Windows.FrameworkElement>します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 名前が割り当てられると、その要素のプロパティはアニメーション化できます。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 種類は、これらのクラスを継承するクラス、<xref:System.Windows.Freezable>クラス。 例については<xref:System.Windows.Freezable>含める<xref:System.Windows.Media.SolidColorBrush>、 <xref:System.Windows.Media.RotateTransform>、および<xref:System.Windows.Media.GradientStop>します。  
  
 ターゲットを有効にする、<xref:System.Windows.Freezable>をアニメーションで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用する、 [X:name ディレクティブ](../../xaml-services/x-name-directive.md)名前を指定します。 コードで使用する、<xref:System.Windows.NameScope.RegisterName%2A>メソッドを作成した要素に名前を登録、<xref:System.Windows.NameScope>します。  
  
 次の例は、名前を割り当てて、<xref:System.Windows.Freezable>オブジェクト。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 これで、オブジェクトをアニメーションのターゲットにすることができます。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトでは、名前スコープを使用して、解決するには、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティ。 WPF 名前スコープの詳細については、「[WPF XAML 名前スコープ](../advanced/wpf-xaml-namescopes.md)」を参照してください。 場合、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティが省略された場合、または、要素の定義は、スタイル、スタイル設定された要素の場合、アニメーションのターゲットします。  
  
 名前を割り当てることはできないことがあります、<xref:System.Windows.Freezable>オブジェクト。 たとえば場合、<xref:System.Windows.Freezable>リソースとして宣言またはスタイルのプロパティ値を設定するために使用されている名前を指定することはできません。 名前が割り当てられていないため、それを直接ターゲットにすることができません。ただし、間接的にターゲットにすることはできます。 以下のセクションでは、間接的な対象化の使用方法について説明します。  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>間接的な対象化  
 あります、<xref:System.Windows.Freezable>場合など、アニメーションで直接対象とすることはできません、<xref:System.Windows.Freezable>がリソースとして宣言されているか、スタイルのプロパティ値を設定するために使用します。 このような場合は、直接ターゲットにできない場合でも引き続きをアニメーション化できます、<xref:System.Windows.Freezable>オブジェクト。 設定ではなく、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティの名前を持つ、 <xref:System.Windows.Freezable>、する要素の名前が、付与、 <xref:System.Windows.Freezable> 「属しています」。 たとえば、<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>その四角形に四角形の要素が属しています。 ブラシをアニメーション化するにはアニメーションの設定は<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>フレームワーク要素またはフレームワーク コンテンツ要素のプロパティで始まるプロパティのチェーンを持つ、<xref:System.Windows.Freezable>で終わります設定に使用された、<xref:System.Windows.Freezable>プロパティをアニメーション化します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 場合に、注意してください、<xref:System.Windows.Freezable>は固定されている場合、複製になります、およびその複製がアニメーション化します。 この場合、元のオブジェクトの<xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A>プロパティを返し続けます`false`元のオブジェクトが実際にアニメーション化されないためです。 複製の詳細については、次を参照してください。、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
 また、間接的なプロパティの対象化を使用するとき、存在しないオブジェクトを対象化する可能性があることに注意してください。 などのように見えますが、<xref:System.Windows.Controls.Control.Background%2A>の特定のボタンで設定した、<xref:System.Windows.Media.SolidColorBrush>実際にその色をアニメーション化しようと、<xref:System.Windows.Media.LinearGradientBrush>ボタンの背景を設定するために使用されました。 このような場合は、例外はスローされません。効果は表示であるため、アニメーションが失敗した<xref:System.Windows.Media.LinearGradientBrush>への変更に反応しません、<xref:System.Windows.Media.SolidColorBrush.Color%2A>プロパティ。  
  
 以下のセクションでは、間接的なプロパティの対象化の構文について詳しく説明します。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML でフリーズ可能オブジェクトのプロパティを間接的に対象化する  
 フリーズ可能オブジェクトのプロパティを対象とする[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、次の構文を使用します。  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName*のプロパティである、<xref:System.Windows.FrameworkElement>を<xref:System.Windows.Freezable>を設定するために使用し、  
  
-   *FreezablePropertyName*のプロパティである、<xref:System.Windows.Freezable>をアニメーション化します。  
  
 次のコードは、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> 四角形要素。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。  
  
 コレクションに含まれるフリーズ可能オブジェクトをターゲットにするには、次のパス構文を使用します。  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 場所*CollectionIndex*はその配列またはコレクション内のオブジェクトのインデックスです。  
  
 たとえば、四角形が含まれていること、<xref:System.Windows.Media.TransformGroup>リソースに適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ、およびするが、その変換のいずれかをアニメーション化します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 次のコードは、アニメーション化する方法を示しています、<xref:System.Windows.Media.RotateTransform.Angle%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>前の例に示すようにします。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>コードでフリーズ可能オブジェクトのプロパティを間接的に対象化する  
 コードで作成した、<xref:System.Windows.PropertyPath>オブジェクト。 作成するときに、<xref:System.Windows.PropertyPath>を指定する、<xref:System.Windows.PropertyPath.Path%2A>と<xref:System.Windows.PropertyPath.PathParameters%2A>します。  
  
 作成する<xref:System.Windows.PropertyPath.PathParameters%2A>、型の配列を作成する<xref:System.Windows.DependencyProperty>依存関係プロパティ識別子フィールドの一覧を格納しています。 プロパティの最初の識別子フィールドは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>を<xref:System.Windows.Freezable>を設定するために使用します。 次の識別子フィールドのプロパティを表す、<xref:System.Windows.Freezable>ターゲットにします。 接続プロパティのチェーンを考えて、<xref:System.Windows.Freezable>を<xref:System.Windows.FrameworkElement>オブジェクト。  
  
 対象とする依存関係プロパティのチェーンの例を次に、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>の四角形要素。  
  
 [!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 指定する必要があります、<xref:System.Windows.PropertyPath.Path%2A>します。 A<xref:System.Windows.PropertyPath.Path%2A>は、<xref:System.String>を示す、<xref:System.Windows.PropertyPath.Path%2A>を解釈する方法、<xref:System.Windows.PropertyPath.PathParameters%2A>します。 次の構文が使用されます。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex*のインデックス、<xref:System.Windows.DependencyProperty>の識別子を含む配列、<xref:System.Windows.FrameworkElement>オブジェクトのプロパティを<xref:System.Windows.Freezable>を設定するために使用し、  
  
-   *FreezablePropertyArrayIndex*のインデックス、<xref:System.Windows.DependencyProperty>をターゲットにするプロパティの識別子を含む配列。  
  
 次の例は、<xref:System.Windows.PropertyPath.Path%2A>に付属する、<xref:System.Windows.PropertyPath.PathParameters%2A>前の例で定義されています。
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 次の例は、アニメーション化する前の例のコードを組み合わせて、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>の四角形要素。  
  
 [!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。 たとえば、四角形が含まれていること、<xref:System.Windows.Media.TransformGroup>リソースに適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ、およびするが、その変換のいずれかをアニメーション化します。  
  
 [!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 ターゲットに、<xref:System.Windows.Freezable>コレクション内に含まれている、次のパス構文を使用します。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 場所*CollectionIndex*はその配列またはコレクション内のオブジェクトのインデックスです。  
  
 ターゲットに、<xref:System.Windows.Media.RotateTransform.Angle%2A>のプロパティ、 <xref:System.Windows.Media.RotateTransform>、2 つ目の変換、 <xref:System.Windows.Media.TransformGroup>、以下を使用すると<xref:System.Windows.PropertyPath.Path%2A>と<xref:System.Windows.PropertyPath.PathParameters%2A>します。  
  
 [!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 次の例では、アニメーション化するための完全なコード、<xref:System.Windows.Media.RotateTransform.Angle%2A>の<xref:System.Windows.Media.RotateTransform>内に含まれる、<xref:System.Windows.Media.TransformGroup>します。  
  
 [!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>開始点として Freezable を使用して間接的に対象化する  
 前のセクションでは、間接的にターゲットする方法を説明した、<xref:System.Windows.Freezable>を始めることで、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>プロパティ チェーンを作成して、<xref:System.Windows.Freezable>サブプロパティ。 使用することも、<xref:System.Windows.Freezable>開始ポイントし、間接的にターゲットのいずれかの<xref:System.Windows.Freezable>サブプロパティ。 使用する場合、その他の制限が適用されます、<xref:System.Windows.Freezable>間接的な対象化の開始点として: 開始<xref:System.Windows.Freezable>、毎回<xref:System.Windows.Freezable>と間接的にターゲットのサブプロパティの必要がありますは固定されません。  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML での対話形式でのストーリーボードの制御  
 ストーリー ボードを起動する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を使用する、<xref:System.Windows.Media.Animation.BeginStoryboard>アクションをトリガーします。 <xref:System.Windows.Media.Animation.BeginStoryboard> オブジェクトとプロパティをアニメーション化する、ストーリー ボードを開始するアニメーションを配布します。 (詳細については、このプロセスは、次を参照してください、[アニメーションとタイミング システムの概要](animation-and-timing-system-overview.md)。)。提供する場合、<xref:System.Windows.Media.Animation.BeginStoryboard>名前を指定してその<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>プロパティをできるようにする制御可能なストーリー ボード。 ストーリーボードが開始すると対話的に制御できます。 制御可能なストーリーボード アクションの一覧を次に示します。これらをイベント トリガーで使用して、ストーリーボードを制御します。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>:ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>:一時停止中のストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:ストーリー ボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:ある場合は、その保留期間の末尾にストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>:ストーリー ボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>:ストーリー ボードを削除します。  
  
 次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御しています。  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>コードを使用した対話形式でのストーリーボードの制御  
 トリガー アクションを使用してアニメーション化する方法については、前の例で説明しました。 コードではの対話型のメソッドを使用してストーリー ボードを制御することも、<xref:System.Windows.Media.Animation.Storyboard>クラス。 <xref:System.Windows.Media.Animation.Storyboard>コードで対話できる、ストーリー ボードの適切なオーバー ロードを使用する必要があります<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを指定して`true`制御可能にします。 参照してください、<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>詳細ページ。  
  
 次の一覧を操作するために使用する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>開始後。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 これらのメソッドを使用する利点は、作成する必要があることを<xref:System.Windows.Trigger>または<xref:System.Windows.TriggerAction>オブジェクトは、制御可能なへの参照が必要なだけ<xref:System.Windows.Media.Animation.Storyboard>を操作します。  
  
 **注:** 行われたすべての対話型操作、 <xref:System.Windows.Media.Animation.Clock>、ためにも、<xref:System.Windows.Media.Animation.Storyboard>は、次の描画の少し前に行われるタイミング エンジンの次の目盛りで発生します。 たとえば、使用する場合、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>プロパティの値をアニメーションで別のポイントにジャンプするメソッドはすぐに変更されません、タイミング エンジンの次の目盛りの値を変更する代わりに。  
  
 次の例では、適用およびの対話型のメソッドを使用してアニメーションを制御する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>クラス。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>スタイル内でアニメーション化を行う  
 使用することができます<xref:System.Windows.Media.Animation.Storyboard>でアニメーションを定義するオブジェクト、<xref:System.Windows.Style>します。 アニメーション化、<xref:System.Windows.Media.Animation.Storyboard>で、<xref:System.Windows.Style>使用と似ています、<xref:System.Windows.Media.Animation.Storyboard>次の 3 つの例外で、他の場所。  
  
-   指定しない、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>、<xref:System.Windows.Media.Animation.Storyboard>先の要素をターゲットと常に、<xref:System.Windows.Style>が適用されます。 ターゲットに<xref:System.Windows.Freezable>オブジェクト、間接的な対象化を使用する必要があります。 間接的な対象化の詳細については、次を参照してください。、[間接的な対象化](#pathsyntaxforchangeable)セクション。  
  
-   指定することはできません、<xref:System.Windows.EventTrigger.SourceName%2A>の<xref:System.Windows.EventTrigger>または<xref:System.Windows.Trigger>します。  
  
-   動的リソース参照またはデータ バインディング式を使用して設定することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション プロパティの値。 だ内のすべてを<xref:System.Windows.Style>スレッド セーフである必要がありますとタイミング システムにする必要があります<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>スレッド セーフであるようにするオブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>またはその子タイムラインに動的リソース参照またはデータ バインディング式が含まれている場合に固定することはできません。 フリーズおよびその他の詳細については<xref:System.Windows.Freezable>については、「、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、用のイベント ハンドラーを宣言することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション イベント。  
  
 スタイル内でストーリー ボードを定義する方法を示す例は、次を参照してください。、[スタイル内でアニメーション化](how-to-animate-in-a-style.md)例。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>ControlTemplate 内でアニメーション化を行う  
 使用することができます<xref:System.Windows.Media.Animation.Storyboard>でアニメーションを定義するオブジェクト、<xref:System.Windows.Controls.ControlTemplate>します。 アニメーション化、<xref:System.Windows.Media.Animation.Storyboard>で、<xref:System.Windows.Controls.ControlTemplate>使用と似ています、<xref:System.Windows.Media.Animation.Storyboard>次の 2 つの例外で、他の場所。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>の子オブジェクトしか参照、<xref:System.Windows.Controls.ControlTemplate>します。 場合<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>が指定されていない、アニメーションのターゲット先の要素、<xref:System.Windows.Controls.ControlTemplate>が適用されます。  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A>の<xref:System.Windows.EventTrigger>または<xref:System.Windows.Trigger>の子オブジェクトしか参照、<xref:System.Windows.Controls.ControlTemplate>します。  
  
-   動的リソース参照またはデータ バインディング式を使用して設定することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション プロパティの値。 だ内のすべてを<xref:System.Windows.Controls.ControlTemplate>スレッド セーフである必要がありますとタイミング システムにする必要があります<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>スレッド セーフであるようにするオブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>またはその子タイムラインに動的リソース参照またはデータ バインディング式が含まれている場合に固定することはできません。 フリーズおよびその他の詳細については<xref:System.Windows.Freezable>については、「、 [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)します。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、用のイベント ハンドラーを宣言することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション イベント。  
  
 ストーリー ボードを定義する方法を示す例については、<xref:System.Windows.Controls.ControlTemplate>を参照してください、 [ControlTemplate 内でアニメーション化](how-to-animate-in-a-controltemplate.md)例。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>プロパティ値が変化したときにアニメーション化を行う  
 スタイル内およびコントロール テンプレート内では、トリガー オブジェクトを使用して、プロパティが変化したときにストーリーボードを開始します。 例については、次を参照してください。 [、アニメーションとプロパティ値が変化をトリガー](how-to-trigger-an-animation-when-a-property-value-changes.md)と[ControlTemplate 内でアニメーション化](how-to-animate-in-a-controltemplate.md)します。  
  
 プロパティによって適用されるアニメーション<xref:System.Windows.Trigger>オブジェクトよりもさらに複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションの開始を使用して<xref:System.Windows.Media.Animation.Storyboard>メソッド。  「ハンドオフ」アニメーションによって他の定義、<xref:System.Windows.Trigger>オブジェクトで、compose を<xref:System.Windows.EventTrigger>メソッドによってトリガーされるアニメーションです。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
