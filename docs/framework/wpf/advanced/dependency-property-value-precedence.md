---
title: 依存関係プロパティ値の優先順位
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 9adcd19ea48d62f4fdcab3380252ae8ec8398296
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315687"
---
# <a name="dependency-property-value-precedence"></a>依存関係プロパティ値の優先順位
<a name="introduction"></a>このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの動作が依存関係プロパティの値に与える影響と、システムのさまざまな部分がプロパティの有効な値に適用する優先順位について説明します。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」を読んでいることを前提としています。 このトピックの例について理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの記述方法について知っておく必要もあります。  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF プロパティ システム  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムは、依存関係プロパティの値をさまざまな要因によって決定し、リアルタイム プロパティの検証や遅延バインディングなどの機能を有効にし、他のプロパティの値の変更を関連プロパティに通知する、強力な手段を提供します。 依存関係プロパティの値の決定に使われる正確な順序とロジックはかなり複雑です。 この順序を知っておくと、不要なプロパティの設定を避けることができ、依存関係プロパティの値を設定または予測しようとしても期待通りにならない正確な理由についての混乱も解決される可能性があります。  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>依存関係プロパティは複数の場所で "設定" される可能性がある  
 次の例は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で同じプロパティ (<xref:System.Windows.Controls.Control.Background%2A>) が 3 つの異なる「設定」操作の値に影響を与える可能性があります。  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 さて、赤、緑、青のどの色になるでしょうか。  
  
 アニメーション化された値および強制型変換の場合を除き、ローカル プロパティ セットは最高の優先順位で設定されます。 ローカルに値を設定する場合は、スタイルまたはコントロール テンプレートであっても、その値が採用されるものと期待できます。 例では、ここで<xref:System.Windows.Controls.Control.Background%2A>ローカルは赤に設定します。 そのため、それ以外の場合、そのスコープでその型のすべての要素に適用される暗黙的なスタイルであるにもかかわらず、このスコープで定義されているスタイルは最高の優先順位を提供するため、<xref:System.Windows.Controls.Control.Background%2A>プロパティの値。  Button インスタンスからローカル値の Red を削除すると、スタイルが優先されるようになり、ボタンの Background の値はスタイルから取得されます。  スタイル内ではトリガーが優先されるので、ボタンはマウスでポイントすると青になり、それ以外の場合は緑になります。  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>依存関係プロパティの設定の優先順位一覧  
 次に示すのは、依存関係プロパティの実行時の値を割り当てるときにプロパティ システムが使う明確な順序です。 優先順位が高いものから順に示されています。 この一覧では、「[依存関係プロパティの概要](dependency-properties-overview.md)」で一般化されていたものを拡張してあります。  
  
1. **プロパティ システムの強制型変換。** 強制型変換について詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
2. **アクティブなアニメーション、または保留動作のアニメーション。** 実際的な効果を得るためには、プロパティのアニメーションは、基本 (アニメーション化されていない) 値 (ローカルに設定された値であっても) より高い優先順位を持つことができる必要があります。 詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
3. **ローカル値。** ローカル値を属性またはプロパティ要素として設定することに相当「ラッパー」プロパティの利便性を設定する可能性があります[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、またはへの呼び出しによって、 <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]特定のインスタンスのプロパティを使用します。 バインドまたはリソースを使ってローカル値を設定する場合、これらは直接値が設定された場合のように優先されます。  
  
4. **TemplatedParent テンプレート プロパティ。** 要素に、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートの一部として作成された場合 (、<xref:System.Windows.Controls.ControlTemplate>または<xref:System.Windows.DataTemplate>)。 これが適用されるケースについて詳しくは、後の「[TemplatedParent](#templatedparent)」をご覧ください。 テンプレート内では、次の優先順位が適用されます。  
  
    1.  トリガー、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレート。  
  
    2.  プロパティ セット (通常を通じて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性) で、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレート。  
  
5. **暗黙的なスタイル。** `Style` プロパティのみに適用されます。 `Style` プロパティは、その要素の型と一致するキーを持つスタイル リソースによって設定されます。 そのスタイル リソースは、ページまたはアプリケーション内に存在する必要があります。暗黙的スタイル リソースの参照はテーマまでは及びません。  
  
6. **スタイルのトリガー。** ページまたはアプリケーションに含まれるスタイル内のトリガー (これらのスタイルは、明示的スタイルまたは暗黙的スタイルどちらの場合もありますが、優先順位の低い既定スタイルではありません)。  
  
7. **テンプレートにトリガーされます。** スタイル内のテンプレートまたは直接適用されたテンプレートからのトリガーです。  
  
8. **スタイルのセッター。** 値から、<xref:System.Windows.Setter>ページまたはアプリケーションからのスタイル内。  
  
9. **既定 (テーマ) のスタイル。** これが適用される場合、およびテーマ スタイルとテーマ スタイル内のテンプレートの関係について詳しくは、後の「[既定 (テーマ) のスタイル](#themestyles)」をご覧ください。 既定のスタイル内では、次の優先順位が適用されます。  
  
    1.  テーマ スタイル内のアクティブなトリガー。  
  
    2.  テーマ スタイル内のセッター。  
  
10. **継承。** いくつかの依存関係プロパティは親要素から子要素に値を継承するので、アプリケーション全体で各要素に値を明示的に設定する必要はありません。 詳しくは、「[プロパティ値の継承](property-value-inheritance.md)」をご覧ください。  
  
11. **依存関係プロパティ メタデータの既定値。** どの依存関係プロパティも、その特定のプロパティがプロパティ システムに登録されるときに設定される既定値を持つことができます。 また、依存関係プロパティを継承する派生クラスには、型ごとにそのメタデータ (既定値を含む) をオーバーライドするオプションがあります。 詳しくは、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」をご覧ください。 継承は既定値の前にチェックされるため、継承されるプロパティの場合、親要素の既定値の方が子要素より優先されます。  その結果、継承可能なプロパティがどこでも設定されていない場合は、ルートまたは親で指定されている既定値が、子要素の既定値の代わりに使われます。  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 優先順位の項目としての TemplatedParent は、標準アプリケーション マークアップで直接宣言された要素のプロパティには適用されません。 TemplatedParent の概念は、テンプレートの適用によって作成されるビジュアル ツリー内の子項目に対してのみ存在します。 プロパティ システムを検索すると、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートで値には、要素を作成したテンプレートが検索されます。 プロパティの値から、<xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートは、一般に、子要素でローカル値として設定されたが、テンプレートが共有される可能性があるために、ローカル値と低い優先順位が存在するかのように動作します。 詳細については、「<xref:System.Windows.FrameworkElement.TemplatedParent%2A>」を参照してください。  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>スタイル プロパティ  
 1 つを除くすべての可能な依存関係プロパティに適用される前に説明した参照の順序は、:<xref:System.Windows.FrameworkElement.Style%2A>プロパティ。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティは、そのことはできません自体スタイル設定するため、優先順位の項目 5 ~ 8 は適用されません。 また、アニメーション化または強制型変換<xref:System.Windows.FrameworkElement.Style%2A>はお勧めしません (アニメーション化と<xref:System.Windows.FrameworkElement.Style%2A>カスタム アニメーション クラスが必要になります)。 これにより、3 つの方法を<xref:System.Windows.FrameworkElement.Style%2A>プロパティを設定することがあります。  
  
-   **明示的なスタイル。** <xref:System.Windows.FrameworkElement.Style%2A>プロパティは直接設定します。 ほとんどの場合、スタイルはインラインでは定義されず、代わりにリソースとして明示的なキーにより参照されます。 この場合、スタイル プロパティ自体は、ローカル値と同じように扱われます (優先順位の項目 3)。  
  
-   **暗黙的なスタイル。** <xref:System.Windows.FrameworkElement.Style%2A>プロパティは直接設定されません。 ただし、<xref:System.Windows.FrameworkElement.Style%2A>リソース参照シーケンス (ページ、アプリケーション) のいくつかのレベルで存在しに適用されるスタイルは、型と一致するリソース キーを使用して、キーになります。 ここで、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ自体は、項目 5 としてシーケンスで識別される優先順位で動作します。 使用して、この条件を検出できる<xref:System.Windows.DependencyPropertyHelper>に対して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティと探して<xref:System.Windows.BaseValueSource.ImplicitStyleReference>結果にします。  
  
-   **既定のスタイル** (別称**テーマ スタイル**)。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティを直接設定されていないととして実際に読み取られます`null`実行時までです。 この場合、スタイルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プレゼンテーション エンジンの一部である実行時テーマ評価によって決定されます。  
  
 テーマではなく暗黙的なスタイルの型に一致する -、 `MyButton` `Button`-派生クラスは暗黙的にスタイルを使用しません`Button`します。  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>既定 (テーマ) のスタイル  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するすべてのコントロールには、既定のスタイルがあります。 既定のスタイルはテーマによって異なる場合があり、そのため、この既定のスタイルはテーマのスタイルとも呼ばれます。  
  
 コントロールは、コントロール テンプレートのセッターとしてテーマ スタイル内に存在するために、既定のスタイル内で検出された最も重要な情報、<xref:System.Windows.Controls.Control.Template%2A>プロパティ。 既定のスタイルにテンプレートがない場合、カスタム スタイルの一部としてカスタム テンプレートがないコントロールは、まったく表示されません。 既定のスタイルのテンプレートは、各コントロールの外観に基本的な構造を提供し、テンプレートのビジュアル ツリーで定義されているプロパティと、対応するコントロール クラスの間の接続を定義します。 各コントロールでは、テンプレートを完全に置き換えることなくコントロールの外観に影響を与えることができる、一連のプロパティが公開されています。 たとえば、既定の外観を<xref:System.Windows.Controls.Primitives.Thumb>コンポーネントであるコントロールの<xref:System.Windows.Controls.Primitives.ScrollBar>します。  
  
 A<xref:System.Windows.Controls.Primitives.Thumb>は特定のカスタマイズ可能なプロパティがあります。 既定のテンプレート、<xref:System.Windows.Controls.Primitives.Thumb>基本的な構造を作成します。 いくつかのビジュアル ツリーの入れ子になった/<xref:System.Windows.Controls.Border>傾斜の外観を作成するコンポーネント。 テンプレートの一部であるプロパティによるカスタマイズの公開する場合は、<xref:System.Windows.Controls.Primitives.Thumb>クラスでそのプロパティを公開する必要があり、 [TemplateBinding](templatebinding-markup-extension.md)テンプレート内で。 場合に<xref:System.Windows.Controls.Primitives.Thumb>、これらの境界のさまざまなプロパティの共有プロパティにテンプレート バインド<xref:System.Windows.Controls.Border.Background%2A>または<xref:System.Windows.Controls.Border.BorderThickness%2A>します。 しかし、他の特定のプロパティや視覚的な配置は、コントロール テンプレートにハードコードされているか、またはテーマから直接取得される値にバインドされており、テンプレート全体を置き換えない限り変更できません。 一般に、プロパティがテンプレート化された親から取得され、テンプレートのバインドによって公開されない場合は、それをターゲットにする簡単な方法がないため、そのプロパティをスタイルによって調整することはできません。 ただし、適用されるテンプレートのプロパティ値継承または既定値によって、そのプロパティに影響を与えることはできます。  
  
 テーマのスタイルでは、定義のキーとして型を使います。 ただし、特定の要素インスタンスにテーマが適用されると、この型のテーマ参照が実行をチェックして、<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>コントロールのプロパティ。 これは、暗黙的スタイルで行われるリテラル型の使用とは対照的です。 値<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>場合でも、実装者が変更しなかった (のプロパティを変更する方法として意図されていないオーバーライドすることですが、プロパティ レベルでは代わりにプロパティのメタデータでの既定値の変更) は、派生クラスに継承します。 この間接参照により、基底クラスは、他の方法ではスタイルを持たない派生要素に対してテーマのスタイルを定義できます (または、さらに重要なのは、スタイル内にテンプレートを持たず、既定の外観がないということです)。 したがって、派生`MyButton`から<xref:System.Windows.Controls.Button>とが表示されます、<xref:System.Windows.Controls.Button>既定のテンプレート。 コントロールを作成した場合`MyButton`とは異なる動作を必要に応じての依存関係プロパティ メタデータをオーバーライドできます<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>で`MyButton`別のキーを返すし、テンプレートを含む関連するテーマのスタイルを定義するには`MyButton`をパッケージ化する必要があります`MyButton`コントロール。 テーマ、スタイル、コントロールの作成について詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」をご覧ください。  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>動的リソース参照とバインド  
 動的リソース参照とバインド操作には、それらが設定される場所での優先順位が適用されます。 たとえば、ローカル値に適用される動的リソースは優先順位の項目 3 に準拠し、テーマ スタイル内のプロパティ セッターに対するバインドには優先順位の項目 9 が適用されます。 動的リソース参照とバインドはどちらもアプリケーションの実行時状態から値を取得できる必要があるので、特定のプロパティに対するプロパティ値の優先順位を決定する実際のプロセスは、実行時まで拡張されます。  
  
 厳密に言うと、動的リソース参照はプロパティ システムの一部ではありませんが、上で示したシーケンスに対応する独自の参照順序を持ちます。 その優先順位について詳しくは、「[XAML リソース](xaml-resources.md)」をご覧ください。 基本的な優先順位をまとめると、ページ ルートの要素、アプリケーション、テーマ、システムになります。  
  
 動的リソースとバインドには設定された場所での優先順位がありますが、値は遅延されます。 その 1 つの帰結として、ローカル値に動的リソースまたはバインドを設定した場合、ローカル値を変更すると動的リソースまたはバインドが完全に置き換えられます。 呼び出す場合でも、<xref:System.Windows.DependencyObject.ClearValue%2A>ローカルに設定をクリアするメソッドの値では、動的リソースまたはバインドは復元されません。 実際には、呼び出した場合<xref:System.Windows.DependencyObject.ClearValue%2A>によってクリアされます (リテラル ローカル値はありません) を動的リソースまたはバインドのあるプロパティを<xref:System.Windows.DependencyObject.ClearValue%2A>すぎる呼び出し。  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>メソッドは、プロパティを設定することもできますが、優先順位の順序はありません。 代わりに、<xref:System.Windows.DependencyObject.SetCurrentValue%2A>前の値のソースを上書きすることがなく、プロパティの値を変更することができます。 使用することができます<xref:System.Windows.DependencyObject.SetCurrentValue%2A>いつでもローカル値の優先順位値を与えることがなく、値を設定します。 たとえば、プロパティが、トリガーによって設定され、によって別の値が割り当てられます<xref:System.Windows.DependencyObject.SetCurrentValue%2A>、プロパティ システムがまだトリガーを優先し、トリガーのアクションが発生した場合、プロパティが変更されます。 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> 優先順位の高いソースを指定せずに、プロパティの値を変更できます。 同様に、使用<xref:System.Windows.DependencyObject.SetCurrentValue%2A>バインドを上書きすることがなく、プロパティの値を変更します。  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>強制型変換、アニメーション、基本値  
 強制型変換とアニメーションはどちらも、この [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] で "基本値" と呼ぶ値に対して作用します。 したがって、基本値とは、項目 2 に達するまで項目をさかのぼって評価されることにより決定される値です。  
  
 アニメーションの場合、アニメーションで特定の動作に対して "From" と "To" の両方が指定されていない場合、またはアニメーションが完了すると基本値に意図的に戻る場合は、基本値を使ってアニメーション化される値に影響を及ぼすことができます。 実際にどうなるのかを見るには、「[From, To, and By Animation Target Values Sample](https://go.microsoft.com/fwlink/?LinkID=159988)」(アニメーション ターゲット値 From、To、By のサンプル) をご覧ください。 この例で、四角形の高さのローカル値を、初期ローカル値がアニメーションの "From" と異なるように設定してみます。 アニメーションが "From" の値を使ってすぐに開始し、開始すると基本値を置き換えることがわかります。 Stop を指定することによってこれが完了すると、アニメーション前に見つかった値に戻るにアニメーションを指定<xref:System.Windows.Media.Animation.FillBehavior>します。 その後は、通常の優先順位が基本値の決定に使用されます。  
  
 1 つのプロパティに複数のアニメーションが適用され、各アニメーションが値の優先順位の異なるポイントから定義されている場合があります。 ただし、これらのアニメーションは、優先順位の高いアニメーションから単純に適用されるのではなく、値が合成される可能性があります。 これは、アニメーションの定義方法と、アニメーション化される値の型に依存します。 プロパティのアニメーション化について詳しくは、「[アニメーションの概要](../graphics-multimedia/animation-overview.md)」をご覧ください。  
  
 強制型変換は、すべての最高レベルで適用されます。 既に実行されているアニメーションであっても値の強制型変換が適用されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の特定の既存の依存関係プロパティには、組み込みの強制型変換があります。 カスタム依存関係プロパティを記述してカスタム依存関係プロパティの強制型変換動作を定義する、<xref:System.Windows.CoerceValueCallback>プロパティを作成するときに、メタデータの一部としてコールバックを渡します。 派生クラスでプロパティのメタデータをオーバーライドすることにより、既存のプロパティの強制型変換の動作をオーバーライドすることもできます。 強制型変換と基本値の相互作用は、その時点で強制型変換に対する制約が存在するものとして適用されるように行われますが、基本値はそれでも保持されます。 したがって、強制型変換の制約が後で無効になった場合、強制型変換はその基本値に可能な最も近い値を返し、プロパティに対する強制型変換の影響はすべての制約が無効になるとすぐに終了する可能性があります。 強制型変換の動作について詳しくは、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」をご覧ください。  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>トリガー動作  
 コントロールでは、テーマの既定のスタイルの一部としてトリガー動作が定義されていることがよくあります。 コントロールにローカル プロパティを設定すると、ユーザー駆動のイベントに対してトリガーが視覚的または動作的に応答できなくなる可能性があります。 プロパティ トリガーの最も一般的な使用などのコントロールまたは状態プロパティが<xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>します。 たとえば、既定でときに、<xref:System.Windows.Controls.Button>は無効になります (のトリガー<xref:System.Windows.UIElement.IsEnabled%2A>は`false`)、<xref:System.Windows.Controls.Control.Foreground%2A>テーマ スタイル内の値は「グレー」表示するコントロールの原因は何です。 ローカルに設定している場合、<xref:System.Windows.Controls.Control.Foreground%2A>値、このプロパティによってトリガーされるシナリオであっても、ローカル プロパティ セットによって通常のグレー色が優先順位で却下されます。 テーマ レベルのトリガー動作があるプロパティの値を設定するときは注意し、そのコントロールの目的のユーザー エクスペリエンスに過度に干渉していないことを確認する必要があります。  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue と値の優先順位  
 <xref:System.Windows.DependencyObject.ClearValue%2A>メソッドが任意のローカルで適用された要素が設定されている依存関係プロパティ値をクリアする便利な手段を提供します。 ただし、呼び出す<xref:System.Windows.DependencyObject.ClearValue%2A>プロパティの登録中にメタデータで確立されると、既定値は、新しい有効な値である保証はありません。 値の優先順位に関係する他のすべての要因はアクティブなままです。 ローカルで設定された値が優先順位のシーケンスから削除されるだけです。 呼び出す場合など、<xref:System.Windows.DependencyObject.ClearValue%2A>テーマのスタイルによってもそのプロパティを設定し、テーマの値がメタデータに基づく既定ではなく、新しい値として適用されるプロパティ。 依存関係プロパティ メタデータ、その後のクエリを実行して選択肢の既定値が既定値をローカルで使用できることを取得するには、プロセス外のすべてのプロパティ値の参加者を受け取り、登録されているメタデータの既定値を設定する場合は、呼び出しにプロパティを設定<xref:System.Windows.DependencyObject.SetValue%2A>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)
