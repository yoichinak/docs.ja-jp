---
title: 依存関係プロパティ値の優先順位
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 1d7c644c7f7581a96ffff1a0fe1fcf2adfe071e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186140"
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
 次の例では[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、同じプロパティ<xref:System.Windows.Controls.Control.Background%2A>( ) に値に影響を与える可能性のある 3 つの異なる "set" 操作があります。  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 さて、赤、緑、青のどの色になるでしょうか。  
  
 アニメーション化された値および強制型変換の場合を除き、ローカル プロパティ セットは最高の優先順位で設定されます。 ローカルに値を設定する場合は、スタイルまたはコントロール テンプレートであっても、その値が採用されるものと期待できます。 この例では、<xref:System.Windows.Controls.Control.Background%2A>ローカルで Red に設定されています。 したがって、このスコープで定義されているスタイルは、そのスコープ内のその型のすべての要素に適用される暗黙的なスタイルであっても、<xref:System.Windows.Controls.Control.Background%2A>プロパティに値を与える場合の優先順位が最も高いわけではありません。  Button インスタンスからローカル値の Red を削除すると、スタイルが優先されるようになり、ボタンの Background の値はスタイルから取得されます。  スタイル内ではトリガーが優先されるので、ボタンはマウスでポイントすると青になり、それ以外の場合は緑になります。  
  
<a name="listing"></a>
## <a name="dependency-property-setting-precedence-list"></a>依存関係プロパティの設定の優先順位一覧  
 次に示すのは、依存関係プロパティの実行時の値を割り当てるときにプロパティ システムが使う明確な順序です。 優先順位が高いものから順に示されています。 この一覧では、「[依存関係プロパティの概要](dependency-properties-overview.md)」で一般化されていたものを拡張してあります。  
  
1. **プロパティ システムの強制型変換。** 強制型変換について詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
2. **アクティブなアニメーション、または保留動作のアニメーション。** 実際的な効果を得るためには、プロパティのアニメーションは、基本 (アニメーション化されていない) 値 (ローカルに設定された値であっても) より高い優先順位を持つことができる必要があります。 詳しくは、後の「[強制型変換、アニメーション、基本値](#animations)」をご覧ください。  
  
3. **ローカル値。** ローカル値は、 で属性またはプロパティ要素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として設定すること、または特定のインスタンスのプロパティを使用して<xref:System.Windows.DependencyObject.SetValue%2A>API を呼び出すことによっても同じ "ラッパー" プロパティの利便性によって設定できます。 バインドまたはリソースを使ってローカル値を設定する場合、これらは直接値が設定された場合のように優先されます。  
  
4. **TemplatedParent テンプレート プロパティ。** 要素には、テンプレート<xref:System.Windows.FrameworkElement.TemplatedParent%2A>(<xref:System.Windows.Controls.ControlTemplate>または<xref:System.Windows.DataTemplate>) の一部として作成された if が含まれています。 これが適用されるケースについて詳しくは、後の「[TemplatedParent](#templatedparent)」をご覧ください。 テンプレート内では、次の優先順位が適用されます。  
  
    1. テンプレートからトリガー<xref:System.Windows.FrameworkElement.TemplatedParent%2A>します。  
  
    2. テンプレートのプロパティ セット[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)](通常は<xref:System.Windows.FrameworkElement.TemplatedParent%2A>属性を介して)。  
  
5. **暗黙的スタイル。** `Style` プロパティのみに適用されます。 `Style` プロパティは、その要素の型と一致するキーを持つスタイル リソースによって設定されます。 そのスタイル リソースは、ページまたはアプリケーション内に存在する必要があります。暗黙的スタイル リソースの参照はテーマまでは及びません。  
  
6. **スタイルのトリガー。** ページまたはアプリケーションに含まれるスタイル内のトリガー (これらのスタイルは、明示的スタイルまたは暗黙的スタイルどちらの場合もありますが、優先順位の低い既定スタイルではありません)。  
  
7. **テンプレートのトリガー。** スタイル内のテンプレートまたは直接適用されたテンプレートからのトリガーです。  
  
8. **スタイルのセッター。** ページまたはアプリケーション<xref:System.Windows.Setter>の内のスタイルからの値。  
  
9. **既定 (テーマ) のスタイル。** これが適用される場合、およびテーマ スタイルとテーマ スタイル内のテンプレートの関係について詳しくは、後の「[既定 (テーマ) のスタイル](#themestyles)」をご覧ください。 既定のスタイル内では、次の優先順位が適用されます。  
  
    1. テーマ スタイル内のアクティブなトリガー。  
  
    2. テーマ スタイル内のセッター。  
  
10. **継承。** いくつかの依存関係プロパティは親要素から子要素に値を継承するので、アプリケーション全体で各要素に値を明示的に設定する必要はありません。 詳しくは、「[プロパティ値の継承](property-value-inheritance.md)」をご覧ください。  
  
11. **依存関係プロパティのメタデータの既定値。** どの依存関係プロパティも、その特定のプロパティがプロパティ システムに登録されるときに設定される既定値を持つことができます。 また、依存関係プロパティを継承する派生クラスには、型ごとにそのメタデータ (既定値を含む) をオーバーライドするオプションがあります。 詳しくは、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」をご覧ください。 継承は既定値の前にチェックされるため、継承されるプロパティの場合、親要素の既定値の方が子要素より優先されます。  その結果、継承可能なプロパティがどこでも設定されていない場合は、ルートまたは親で指定されている既定値が、子要素の既定値の代わりに使われます。  
  
<a name="templatedparent"></a>
## <a name="templatedparent"></a>TemplatedParent  
 優先順位の項目としての TemplatedParent は、標準アプリケーション マークアップで直接宣言された要素のプロパティには適用されません。 TemplatedParent の概念は、テンプレートの適用によって作成されるビジュアル ツリー内の子項目に対してのみ存在します。 プロパティ システムがテンプレートで<xref:System.Windows.FrameworkElement.TemplatedParent%2A>値を検索する場合、その要素を作成したテンプレートを検索します。 <xref:System.Windows.FrameworkElement.TemplatedParent%2A>テンプレートのプロパティ値は、通常、子要素のローカル値として設定されたかのように動作しますが、テンプレートが共有される可能性があるため、この優先順位がローカル値に比べて低い場合があります。 詳細については、<xref:System.Windows.FrameworkElement.TemplatedParent%2A> を参照してください。  
  
<a name="style_property"></a>
## <a name="the-style-property"></a>スタイル プロパティ  
 前述のルックアップの順序は、1 つを除くすべての可能な依存関係プロパティ<xref:System.Windows.FrameworkElement.Style%2A>に適用されます。 プロパティ<xref:System.Windows.FrameworkElement.Style%2A>はスタイルを設定できないという特徴で一意であるため、優先順位の項目 5 ~ 8 は適用されません。 また、アニメーション化または強制操作<xref:System.Windows.FrameworkElement.Style%2A>は推奨されません (アニメーション化<xref:System.Windows.FrameworkElement.Style%2A>にはカスタム アニメーション クラスが必要です)。 この場合、<xref:System.Windows.FrameworkElement.Style%2A>プロパティを設定する 3 つの方法が残ります。  
  
- **明示的スタイル。** プロパティ<xref:System.Windows.FrameworkElement.Style%2A>は直接設定されます。 ほとんどの場合、スタイルはインラインでは定義されず、代わりにリソースとして明示的なキーにより参照されます。 この場合、スタイル プロパティ自体は、ローカル値と同じように扱われます (優先順位の項目 3)。  
  
- **暗黙的スタイル。** プロパティ<xref:System.Windows.FrameworkElement.Style%2A>は直接設定されません。 ただし、リソース<xref:System.Windows.FrameworkElement.Style%2A>ルックアップシーケンス (ページ、アプリケーション) の一部のレベルに存在し、スタイルを適用する型に一致するリソースキーを使用してキー設定されます。 この場合、プロパティ自体<xref:System.Windows.FrameworkElement.Style%2A>は、シーケンスで項目 5 として識別される優先順位によって動作します。 この状態は、<xref:System.Windows.DependencyPropertyHelper><xref:System.Windows.FrameworkElement.Style%2A>プロパティに対してを使用して、結果<xref:System.Windows.BaseValueSource.ImplicitStyleReference>を探すことによって検出できます。  
  
- **既定のスタイル** (別称**テーマ スタイル**)。 プロパティ<xref:System.Windows.FrameworkElement.Style%2A>は直接設定されず、実際には実行時まで読み取`null`られます。 この場合、スタイルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プレゼンテーション エンジンの一部である実行時テーマ評価によって決定されます。  
  
 テーマに含まれていない暗黙的なスタイルの場合、型は完全に`MyButton``Button`一致する`Button`必要があります。  
  
<a name="themestyles"></a>
## <a name="default-theme-styles"></a>既定 (テーマ) のスタイル  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するすべてのコントロールには、既定のスタイルがあります。 既定のスタイルはテーマによって異なる場合があり、そのため、この既定のスタイルはテーマのスタイルとも呼ばれます。  
  
 コントロールの既定のスタイルに含まれる最も重要な情報は、<xref:System.Windows.Controls.Control.Template%2A>そのコントロール テンプレートです。 既定のスタイルにテンプレートがない場合、カスタム スタイルの一部としてカスタム テンプレートがないコントロールは、まったく表示されません。 既定のスタイルのテンプレートは、各コントロールの外観に基本的な構造を提供し、テンプレートのビジュアル ツリーで定義されているプロパティと、対応するコントロール クラスの間の接続を定義します。 各コントロールでは、テンプレートを完全に置き換えることなくコントロールの外観に影響を与えることができる、一連のプロパティが公開されています。 たとえば、<xref:System.Windows.Controls.Primitives.Thumb>コントロールの既定の外観を考えてみます<xref:System.Windows.Controls.Primitives.ScrollBar>。  
  
 は<xref:System.Windows.Controls.Primitives.Thumb>、特定のカスタマイズ可能なプロパティを持ちます。 のデフォルトテンプレートは、<xref:System.Windows.Controls.Primitives.Thumb>ベベルの外観を作成するために、いくつかのネストされた<xref:System.Windows.Controls.Border>コンポーネントを持つ基本的な構造/ビジュアルツリーを作成します。 テンプレートの一部であるプロパティが<xref:System.Windows.Controls.Primitives.Thumb>クラスによってカスタマイズするために公開される場合、そのプロパティは[TemplateBinding](templatebinding-markup-extension.md)によってテンプレート内で公開される必要があります。 の<xref:System.Windows.Controls.Primitives.Thumb>場合、これらの境界のさまざまなプロパティは、 や<xref:System.Windows.Controls.Border.Background%2A><xref:System.Windows.Controls.Border.BorderThickness%2A>などのプロパティに対するテンプレート バインディングを共有します。 しかし、他の特定のプロパティや視覚的な配置は、コントロール テンプレートにハードコードされているか、またはテーマから直接取得される値にバインドされており、テンプレート全体を置き換えない限り変更できません。 一般に、プロパティがテンプレート化された親から取得され、テンプレートのバインドによって公開されない場合は、それをターゲットにする簡単な方法がないため、そのプロパティをスタイルによって調整することはできません。 ただし、適用されるテンプレートのプロパティ値継承または既定値によって、そのプロパティに影響を与えることはできます。  
  
 テーマのスタイルでは、定義のキーとして型を使います。 ただし、特定の要素インスタンスにテーマを適用すると、コントロールのプロパティをチェックすることによって、この型の<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>テーマの検索が実行されます。 これは、暗黙的スタイルで行われるリテラル型の使用とは対照的です。 の値は<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>、実装者が変更しなかった場合でも派生クラスに継承されます (プロパティを変更する意図された方法は、プロパティ レベルでオーバーライドするのではなく、プロパティ メタデータの既定値を変更することです)。 この間接参照により、基底クラスは、他の方法ではスタイルを持たない派生要素に対してテーマのスタイルを定義できます (または、さらに重要なのは、スタイル内にテンプレートを持たず、既定の外観がないということです)。 したがって、既定のテンプレート`MyButton`から<xref:System.Windows.Controls.Button>派生し、引き<xref:System.Windows.Controls.Button>続き取得できます。 コントロールの作成者で、別の`MyButton`動作をする場合は、on の依存関係プロパティメタデータ<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>`MyButton`をオーバーライドして別のキーを返し、コントロールと共にパッケージ化`MyButton`する必要があるテンプレートを含む関連テーマ スタイルを`MyButton`定義できます。 テーマ、スタイル、コントロールの作成について詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」をご覧ください。  
  
<a name="resources"></a>
## <a name="dynamic-resource-references-and-binding"></a>動的リソース参照とバインド  
 動的リソース参照とバインド操作には、それらが設定される場所での優先順位が適用されます。 たとえば、ローカル値に適用される動的リソースは優先順位の項目 3 に準拠し、テーマ スタイル内のプロパティ セッターに対するバインドには優先順位の項目 9 が適用されます。 動的リソース参照とバインドはどちらもアプリケーションの実行時状態から値を取得できる必要があるので、特定のプロパティに対するプロパティ値の優先順位を決定する実際のプロセスは、実行時まで拡張されます。  
  
 厳密に言うと、動的リソース参照はプロパティ システムの一部ではありませんが、上で示したシーケンスに対応する独自の参照順序を持ちます。 その優先順位について詳しくは、「[XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)」をご覧ください。 基本的な優先順位をまとめると、ページ ルートの要素、アプリケーション、テーマ、システムになります。  
  
 動的リソースとバインドには設定された場所での優先順位がありますが、値は遅延されます。 その 1 つの帰結として、ローカル値に動的リソースまたはバインドを設定した場合、ローカル値を変更すると動的リソースまたはバインドが完全に置き換えられます。 ローカルに設定された値<xref:System.Windows.DependencyObject.ClearValue%2A>をクリアするメソッドを呼び出しても、動的リソースまたはバインディングは復元されません。 実際、動的リソースまたはバインド<xref:System.Windows.DependencyObject.ClearValue%2A>が設定されているプロパティを呼び出すと (ローカル値がリテラルなし)、<xref:System.Windows.DependencyObject.ClearValue%2A>呼び出しによってもクリアされます。  
  
<a name="setcurrentvalue"></a>
## <a name="setcurrentvalue"></a>SetCurrentValue  
 この<xref:System.Windows.DependencyObject.SetCurrentValue%2A>メソッドは、プロパティを設定する別の方法ですが、優先順位の順序ではありません。 代わりに<xref:System.Windows.DependencyObject.SetCurrentValue%2A>、以前の値のソースを上書きせずに、プロパティの値を変更できます。 値をローカル<xref:System.Windows.DependencyObject.SetCurrentValue%2A>値の優先順位に指定せずに、いつでも値を設定できます。 たとえば、プロパティがトリガによって設定され、<xref:System.Windows.DependencyObject.SetCurrentValue%2A>によって別の値が割り当てられた場合、プロパティ システムは引き続きトリガを尊重し、トリガの動作が発生するとプロパティは変更されます。 <xref:System.Windows.DependencyObject.SetCurrentValue%2A>では、プロパティの値を、より高い優先順位のソースに指定せずに変更できます。 同様<xref:System.Windows.DependencyObject.SetCurrentValue%2A>に、バインドを上書きせずにプロパティの値を変更することもできます。  
  
<a name="animations"></a>
## <a name="coercion-animations-and-base-value"></a>強制型変換、アニメーション、基本値  
 強制変換とアニメーションはどちらも、この SDK 全体で 「基本値」と呼ばれる値に作用します。 したがって、基本値とは、項目 2 に達するまで項目をさかのぼって評価されることにより決定される値です。  
  
 アニメーションの場合、アニメーションで特定の動作に対して "From" と "To" の両方が指定されていない場合、またはアニメーションが完了すると基本値に意図的に戻る場合は、基本値を使ってアニメーション化される値に影響を及ぼすことができます。 実際にどうなるのかを見るには、「[From, To, and By Animation Target Values Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)」(アニメーション ターゲット値 From、To、By のサンプル) をご覧ください。 この例で、四角形の高さのローカル値を、初期ローカル値がアニメーションの "From" と異なるように設定してみます。 アニメーションが "From" の値を使ってすぐに開始し、開始すると基本値を置き換えることがわかります。 アニメーションは、Stop<xref:System.Windows.Media.Animation.FillBehavior>を指定してアニメーションが完了した後、アニメーションの前に見つかった値に戻るように指定できます。 その後は、通常の優先順位が基本値の決定に使用されます。  
  
 1 つのプロパティに複数のアニメーションが適用され、各アニメーションが値の優先順位の異なるポイントから定義されている場合があります。 ただし、これらのアニメーションは、優先順位の高いアニメーションから単純に適用されるのではなく、値が合成される可能性があります。 これは、アニメーションの定義方法と、アニメーション化される値の型に依存します。 プロパティのアニメーション化の詳細については、「[アニメーションの概要](../graphics-multimedia/animation-overview.md)」を参照してください。  
  
 強制型変換は、すべての最高レベルで適用されます。 既に実行されているアニメーションであっても値の強制型変換が適用されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の特定の既存の依存関係プロパティには、組み込みの強制型変換があります。 カスタム依存関係プロパティの場合、カスタム依存関係プロパティの強制動作を定義するには、プロパティの作成時にコールバックを<xref:System.Windows.CoerceValueCallback>記述し、メタデータの一部として渡します。 派生クラスでプロパティのメタデータをオーバーライドすることにより、既存のプロパティの強制型変換の動作をオーバーライドすることもできます。 強制型変換と基本値の相互作用は、その時点で強制型変換に対する制約が存在するものとして適用されるように行われますが、基本値はそれでも保持されます。 したがって、強制型変換の制約が後で無効になった場合、強制型変換はその基本値に可能な最も近い値を返し、プロパティに対する強制型変換の影響はすべての制約が無効になるとすぐに終了する可能性があります。 強制型変換の動作について詳しくは、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」をご覧ください。  
  
<a name="triggers"></a>
## <a name="trigger-behaviors"></a>トリガー動作  
 コントロールでは、テーマの既定のスタイルの一部としてトリガー動作が定義されていることがよくあります。 コントロールにローカル プロパティを設定すると、ユーザー駆動のイベントに対してトリガーが視覚的または動作的に応答できなくなる可能性があります。 プロパティ トリガーの最も一般的な用途は、 などのコントロール<xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>プロパティまたは状態プロパティの使用です。 たとえば、既定では、 が<xref:System.Windows.Controls.Button>無効になっている (<xref:System.Windows.UIElement.IsEnabled%2A>の`false`トリガ )<xref:System.Windows.Controls.Control.Foreground%2A>の場合、テーマ スタイルの値がコントロールの "灰色表示" になります。 ただし、ローカル<xref:System.Windows.Controls.Control.Foreground%2A>値を設定した場合、このプロパティによってトリガーされるシナリオであっても、通常のグレーアウト色はローカル プロパティ セットによって優先されて除外されます。 テーマ レベルのトリガー動作があるプロパティの値を設定するときは注意し、そのコントロールの目的のユーザー エクスペリエンスに過度に干渉していないことを確認する必要があります。  
  
<a name="clearvalue"></a>
## <a name="clearvalue-and-value-precedence"></a>ClearValue と値の優先順位  
 この<xref:System.Windows.DependencyObject.ClearValue%2A>メソッドは、要素に設定されている依存関係プロパティからローカルに適用された値をクリアする便利な手段を提供します。 ただし、呼<xref:System.Windows.DependencyObject.ClearValue%2A>び出しは、プロパティ登録時にメタデータで確立された既定値が新しい有効値であることを保証するものではありません。 値の優先順位に関係する他のすべての要因はアクティブなままです。 ローカルで設定された値が優先順位のシーケンスから削除されるだけです。 たとえば、プロパティがテーマ<xref:System.Windows.DependencyObject.ClearValue%2A>スタイルによって設定されているプロパティを呼び出すと、テーマの値はメタデータ ベースの既定値ではなく、新しい値として適用されます。 すべてのプロパティ値の構成要素をプロセスから除外し、その値を登録済みメタデータの既定値に設定する場合は、依存関係プロパティのメタデータをクエリすることで、その既定値を<xref:System.Windows.DependencyObject.SetValue%2A>確実に取得できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)
