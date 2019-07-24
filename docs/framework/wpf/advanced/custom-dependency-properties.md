---
title: カスタム依存関係プロパティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 1352876b79e103d20d08382ab088f7777c6fe2ae
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401570"
---
# <a name="custom-dependency-properties"></a>カスタム依存関係プロパティ

このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーション開発者およびコンポーネントの作成者が、カスタム依存関係プロパティを作成したくなる理由を説明し、実装手順にくわえ、プロパティのパフォーマンス、使いやすさ、または多用性を向上させることができるいくつかの実装オプションについて説明します。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>必須コンポーネント

このトピックは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」というトピックを読んでいることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>依存関係プロパティとは

それ以外の場合は、共通言語ランタイム (CLR) プロパティを有効にして、スタイル設定、データバインディング、継承、アニメーション、および既定値をサポートすることができます。これは、依存関係プロパティとして実装することによって行います。 依存[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]関係プロパティは、 <xref:System.Windows.DependencyProperty.Register%2A>メソッド (または<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> <xref:System.Windows.DependencyProperty> ) を呼び出すことによってプロパティシステムに登録され、識別子フィールドによってサポートされるプロパティです。 依存関係プロパティは型によっ<xref:System.Windows.DependencyObject>てのみ使用<xref:System.Windows.DependencyObject>できますが、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラス階層では非常に高いため、で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用できるクラスの大部分は依存関係プロパティをサポートできます。 依存関係プロパティと、これらをこの [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] で説明するために使用されている用語と規則の詳細については、「[依存関係プロパティの概要](dependency-properties-overview.md)」を参照してください。

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>依存関係プロパティの例

クラスに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実装されている依存関係プロパティの<xref:System.Windows.Controls.Control.Background%2A>例と<xref:System.Windows.Controls.TextBox.Text%2A>し<xref:System.Windows.FrameworkElement.Width%2A>ては、プロパティ、プロパティ、プロパティなどがあります。 クラスによって公開される各依存関係プロパティには、その<xref:System.Windows.DependencyProperty>同じクラスで公開される型の対応するパブリック静的フィールドがあります。 これが依存関係プロパティの識別子です。 この識別子は規則を使用して命名されます。依存関係プロパティの名前と文字列 `Property` がこれに付加されます。 たとえば、 <xref:System.Windows.Controls.Control.Background%2A>プロパティの対応<xref:System.Windows.DependencyProperty>する識別子フィールドは<xref:System.Windows.Controls.Control.BackgroundProperty>です。 識別子は、登録されたときの依存関係プロパティに関する情報を格納します。この識別子は、の呼び出し<xref:System.Windows.DependencyObject.SetValue%2A>など、依存関係プロパティに関連する他の操作に対して後で使用されます。

「[依存関係プロパティの概要](dependency-properties-overview.md)」で説明したよう[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に、のすべての依存関係プロパティ (ほとんどの添付プロパティを除く) も、"ラッパー" 実装によって CLR プロパティになります。 そのため、コードから、他の CLR プロパティを使用するのと同じ方法でラッパーを定義する CLR アクセサーを呼び出すことによって、依存関係プロパティを取得または設定できます。 確立された依存関係プロパティのコンシューマーは、通常、基<xref:System.Windows.DependencyObject>に<xref:System.Windows.DependencyObject.GetValue%2A>なるプロパティシステムへの接続ポイントであるメソッドと<xref:System.Windows.DependencyObject.SetValue%2A>を使用しません。 代わりに、CLR プロパティの既存の実装は、識別子フィールドを<xref:System.Windows.DependencyObject.GetValue%2A>適切に使用`get`し`set`て、プロパティのおよびラッパー実装<xref:System.Windows.DependencyObject.SetValue%2A>で既に呼び出されています。 カスタム依存関係プロパティを自分で実装する場合、同様の方法でラッパーを定義します。

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>依存関係プロパティを実装すべき状況

クラスにプロパティを実装する場合、クラスがから<xref:System.Windows.DependencyObject>派生している限り、プロパティを<xref:System.Windows.DependencyProperty>識別子で戻し、依存関係プロパティにすることができます。 シナリオのニーズによっては、プロパティを依存関係プロパティにすることが必要ない場合や適切でない場合もあります。 場合によっては、プロパティをプライベート フィールドでバッキングする一般的な手法で十分な場合もあります。 ただし、プロパティで次の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 機能の 1 つ以上をサポートする場合には、常に依存関係プロパティとしてプロパティを実装する必要があります。

- プロパティをスタイルで設定可能にする。 詳しくは、「 [スタイルとテンプレート](../controls/styling-and-templating.md)」をご覧ください。

- プロパティでデータ バインディングをサポートする。 データ バインディングの依存関係プロパティの詳細については、「[2 つのコントロールのプロパティをバインドする](../data/how-to-bind-the-properties-of-two-controls.md)」を参照してください。

- プロパティを動的リソース参照で設定可能にする。 詳細については、「[XAML リソース](xaml-resources.md)」を参照してください。

- 要素ツリーの親要素からプロパティ値を自動的に継承する。 この場合は、CLR アクセス用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>のプロパティラッパーも作成する場合でも、メソッドに登録します。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。

- プロパティをアニメーション化できるようにする。 詳しくは、「 [アニメーションの概要](../graphics-multimedia/animation-overview.md)」をご覧ください。

- プロパティの前の値が、プロパティ システム、環境、または、ユーザーによって行われたアクションによって変更された場合、または読み取りおよびスタイルの使用によって変更された場合に、プロパティ システムに報告させる。 プロパティのメタデータを使用すると、プロパティ システムがプロパティ値が明らかに変更されたと判断するたびに呼び出されるコールバック メソッドをプロパティで指定できます。 関連する概念は、プロパティ値の強制型変換です。 詳しくは、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。

- プロパティ値の変更に、要素のビジュアルを再構成するためのレイアウト システムが必要かどうかを報告するなど、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロセスでも使用されている確立されたメタデータ規則を使用する。 または、派生クラスが既定値などのメタデータに基づく特性を変更できるように、メタデータのオーバーライドを使用できるようする。

- カスタムコントロールのプロパティを使用して、 **[プロパティ]** ウィンドウの編集など、VISUAL Studio WPF デザイナーのサポートを受ける必要があります。 詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。

これらのシナリオを検討するときに、完全に新しいプロパティを実装するよりも、既存の依存関係プロパティのメタデータをオーバーライドすることで、シナリオを実現できるかどうかも考慮する必要があります。 メタデータのオーバーライドが実用的かどうかは、シナリオとそのシナリオが既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 依存関係プロパティとクラスでの実装にどのくらい似ているかによって異なります。 既存のプロパティでメタデータをオーバーライドする方法の詳細については、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>依存関係プロパティを定義するためのチェックリスト

依存関係プロパティの定義は、次の 4 つの異なる概念で構成されます。 これらの概念は、一部は実装で最終的に 1 行のコードとして結合されるため、必ずしも厳密な手順である必要はありません。

- (省略可能) 依存関係プロパティのプロパティ メタデータを作成します。

- 所有者型とプロパティ値の型を指定して、プロパティ システムにプロパティ名を登録します。 プロパティのメタデータも指定します (使用している場合)。

- 識別子を<xref:System.Windows.DependencyProperty>所有者の`public`種類の`readonly`フィールド`static`として定義します。

- 依存関係プロパティの名前と一致する名前を持つ CLR "ラッパー" プロパティを定義します。 CLR "ラッパー" プロパティの`get`および`set`アクセサーを実装して、それをバッキングする依存関係プロパティと接続します。

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>プロパティ システムにプロパティを登録する

プロパティを依存関係プロパティにするためには、そのプロパティをプロパティ システムが保持するテーブルに登録し、その後のプロパティ システム操作で修飾子として使用する一意の識別子をプロパティに設定します。 これらの操作は、内部操作である場合もあれば、プロパティシステム Api を呼び出す独自のコードである場合もあります。 プロパティを登録するには、クラス<xref:System.Windows.DependencyProperty.Register%2A>の本体 (クラス内で、メンバー定義の外部) でメソッドを呼び出します。 識別子フィールドは、戻り値とし<xref:System.Windows.DependencyProperty.Register%2A>てメソッド呼び出しによっても提供されます。 <xref:System.Windows.DependencyProperty.Register%2A>呼び出しが他のメンバー定義の外部で行われる理由は、この戻り値を使用して、クラスの`public`一部とし<xref:System.Windows.DependencyProperty>て型のフィールドを`static` `readonly`割り当てて作成するためです。 このフィールドは、依存関係プロパティの識別子になります。

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>依存関係プロパティの命名規則

依存関係プロパティについては、確立されている命名規則があり、例外的な状況を除き、必ず従う必要があります。

依存関係プロパティ自体には、の最初の<xref:System.Windows.DependencyProperty.Register%2A>パラメーターとして指定された、この例のように、基本的な名前 "AquariumGraphic" が付けられます。 この名前は、それぞれの登録型内で一意である必要があります。 基本型から継承された依存関係プロパティは、登録型の一部に既になっていると見なされ、継承されたプロパティの名前は、再度登録することはできません。 しかし、その依存関係プロパティが継承されていない場合でも、依存関係プロパティの所有者としてクラスを追加する方法があります。詳細については、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。

識別子フィールドを作成するときに、登録したプロパティの名前にサフィックス `Property` を付けて、このフィールドに名前を付けます。 このフィールドは、依存関係プロパティの識別子です。このフィールドは、 <xref:System.Windows.DependencyObject.SetValue%2A>ラッパーでの入力として後で使用されます。また<xref:System.Windows.DependencyObject.GetValue%2A> 、独自のコードによるプロパティへの他のコードアクセスによって、許可する外部コードアクセスによって使用されます。、プロパティシステム、および可能性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のあるプロセッサ。

> [!NOTE]
> クラス本体で依存関係プロパティを定義することは一般的な実装ですが、クラスの静的コンストラクターで依存関係プロパティを定義することもできます。 依存関係プロパティを初期化するために複数行のコードが必要な場合には、このアプローチが適している場合があります。

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>"ラッパー" を実装する

ラッパーの実装では<xref:System.Windows.DependencyObject.GetValue%2A> 、実装でを呼び<xref:System.Windows.DependencyObject.SetValue%2A>出す必要`set`があります。また、実装ではを呼び出す`get`必要があります (わかりやすくするために、元の登録呼び出しとフィールドもここに表示されます)。

すべての例外的な状況において、ラッパーの実装で<xref:System.Windows.DependencyObject.GetValue%2A>は<xref:System.Windows.DependencyObject.SetValue%2A> 、アクションとアクションだけを実行する必要があります。 この理由については、「[XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)」のトピックで説明しています。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスで提供されているすべての既存のパブリックな依存関係プロパティは、この単純なラッパー実装モデルを使用します。依存関係プロパティのしくみの複雑さの大部分は、本質的にプロパティ システムの動作であるか、強制変換やプロパティ メタデータを通じたプロパティ変更のコールバックなど、その他の概念を通じて実装されます。

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

この場合も、慣例により、ラッパープロパティの名前は、プロパティを登録した<xref:System.Windows.DependencyProperty.Register%2A>呼び出しの最初のパラメーターとして指定された名前と同じである必要があります。 プロパティが規則に従っていない場合、すべての可能な使用を無効にする必要はありませんが、次のような注目すべき問題がいくつか発生します。

- スタイルとテンプレートの一部が機能しない。

- ほとんどのツールとデザイナーは、適切に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] をシリアル化するため、またはプロパティごとのレベルでのデザイナー環境のサポートを提供するために命名規則に依存する必要があります。

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ローダーの現在の実装は、属性値を処理するときに、ラッパーを完全にバイパスして、命名規則に依存しています。 詳しくは、「[XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)」を参照してください。

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>新しい依存関係プロパティのプロパティ メタデータ

依存関係プロパティを登録するときに、プロパティ システムを通じて登録すると、プロパティの特性を格納するメタデータ オブジェクトが作成されます。 これらの特性の多くには、プロパティがの<xref:System.Windows.DependencyProperty.Register%2A>単純なシグネチャに登録されている場合に設定される既定値があります。 の<xref:System.Windows.DependencyProperty.Register%2A>その他の署名を使用すると、プロパティを登録するときに必要なメタデータを指定できます。 依存関係プロパティに指定される最も一般的なメタデータは、プロパティを使用する新しいインスタンスに適用される既定値を与えるためのものです。

の<xref:System.Windows.FrameworkElement>派生クラスに存在する依存関係プロパティを作成する場合は、基本<xref:System.Windows.PropertyMetadata>クラスではなく、より特殊<xref:System.Windows.FrameworkPropertyMetadata>なメタデータクラスを使用できます。 <xref:System.Windows.FrameworkPropertyMetadata>クラスのコンストラクターには、さまざまなメタデータ特性を組み合わせて指定できる複数のシグネチャがあります。 既定値のみを指定する場合は、型<xref:System.Object>の1つのパラメーターを受け取る署名を使用します。 そのオブジェクトパラメーターは、プロパティの型固有の既定値として渡します (指定する既定値は、 `propertyType` <xref:System.Windows.DependencyProperty.Register%2A>呼び出しでパラメーターとして指定した型である必要があります)。

<xref:System.Windows.FrameworkPropertyMetadata>では、プロパティのメタデータオプションフラグを指定することもできます。 これらのフラグは、登録後にプロパティ メタデータで個々のプロパティに変換され、特定の条件をレイアウト エンジンなどの他のプロセスに伝えるために使用されます。

#### <a name="setting-appropriate-metadata-flags"></a>適切なメタデータ フラグの設定

- プロパティ (またはその値の変更[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]) がに影響する場合、特に、レイアウトシステムがページ内の要素のサイズを設定または表示する方法に影響する場合は、 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>、 <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>、のいずれかまたは複数のフラグを設定します。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>このプロパティを変更する際に、親オブジェクトが[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]親の中でより多くの領域を必要とする場合に、表示を変更する必要があることを示します。 たとえば、"Width" プロパティには、このフラグが設定されている必要があります。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>このプロパティを変更するときに、通常は専用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の領域を変更する必要はありませんが、スペース内の位置が変更されたことを示す、表示の変更が必要であることを示します。 たとえば、"Alignment" プロパティには、このフラグが設定されている必要があります。

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>他の変更が行われ、レイアウトとメジャーには影響しませんが、別のレンダリングが必要であることを示します。 "Background" など、既存の要素の色を変更するプロパティはその一例です。

  - これらのフラグは、プロパティ システムやレイアウトのコールバックの独自のオーバーライド実装のためのメタデータのプロトコルとしてよく使用されます。 たとえば、インスタンスのいずれかの<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>プロパティが値の<xref:System.Windows.UIElement.InvalidateArrange%2A>変更を報告し、そのメタデータにが<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>含まれて`true`いる場合、コールバックが呼び出される可能性があります。

- 上記で説明した必要なサイズを変更する方法に加え、一部のプロパティは含まれる親要素のレンダリング特性に影響する場合があります。 例として<xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> 、フロードキュメントモデルで使用されるプロパティがあります。このプロパティを変更すると、その段落を含むフロードキュメントの全体的なレンダリングを変更できます。 また<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> は<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure>を使用して、同様のケースを独自のプロパティで識別します。

- 既定では、依存関係プロパティはデータ バインディングをサポートします。 データ バインディングにとって現実的なシナリオがない場合や、大きなオブジェクトのデータ バインディングのパフォーマンスが問題として認識される場合には、意図的にデータ バインディングを無効にすることができます。

- 既定では、依存<xref:System.Windows.Data.Binding.Mode%2A>関係プロパティのデータバインディング<xref:System.Windows.Data.BindingMode.OneWay>は既定でに設定されます。 バインドはバインドインスタンスごとにいつで<xref:System.Windows.Data.BindingMode.TwoWay>も変更できます。詳細については、「[バインディングの方向を指定](../data/how-to-specify-the-direction-of-the-binding.md)する」を参照してください。 ただし、依存関係プロパティの作成者は、プロパティが既定でバインド<xref:System.Windows.Data.BindingMode.TwoWay>モードを使用するように選択できます。 既存の依存関係プロパティ<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>の例を次に示します。このプロパティ<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>のシナリオでは、の<xref:System.Windows.Controls.MenuItem>設定ロジックと複合が既定のテーマスタイルと対話します。 プロパティ<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>ロジックは、データバインディングをネイティブで使用して、他の状態プロパティやメソッド呼び出しに従ってプロパティの状態を維持します。 既定でバインド<xref:System.Windows.Data.BindingMode.TwoWay>されるもう1つ<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>のプロパティの例は、です。

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>フラグを設定することによって、カスタム依存関係プロパティでプロパティの継承を有効にすることもできます。 プロパティの継承は、親要素と子要素に共通のプロパティがあるシナリオに便利で、子要素に、親に設定されたのと同じ値に設定した特定のプロパティ値を持たせることは理にかなっています。 継承可能なプロパティの<xref:System.Windows.FrameworkElement.DataContext%2A>例はです。これは、データ表示の重要なマスター詳細シナリオを有効にするためにバインド操作に使用されます。 <xref:System.Windows.FrameworkElement.DataContext%2A>継承可能にすると、子要素はそのデータコンテキストも継承します。 プロパティ値の継承により、ページまたはアプリケーションのルートでデータ コンテキストを指定できます。すべての使用可能な子要素内のバインディングに再度指定する必要はありません。 <xref:System.Windows.FrameworkElement.DataContext%2A>は、継承が既定値をオーバーライドすることを示す良い例でもありますが、常に特定の子要素でローカルに設定できます。詳細については、「[階層データでマスター詳細パターンを使用する](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。 プロパティ値の継承にはパフォーマンスが低下する可能性があるため、控え目に使用する必要があります。詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal>フラグを設定して、ナビゲーションジャーナリングサービスで依存関係プロパティを検出または使用する必要があるかどうかを示します。 例として<xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> 、プロパティがあります。選択コントロールで選択された項目は、履歴履歴がナビゲートされるときに保持される必要があります。

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>読み取り専用の依存関係プロパティ

読み取り専用の依存関係プロパティを定義することができます。 ただし、読み取り専用としてプロパティを定義する理由のシナリオには、プロパティ システムに登録して、識別子を公開するための手順が異なるため、若干の違いがあります。 詳細については、「[読み取り専用の依存関係プロパティ](read-only-dependency-properties.md)」を参照してください。

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>コレクション型依存関係プロパティ

コレクション型依存関係プロパティには、考慮すべき実装問題が他にもいくつかあります。 詳細については、「[コレクション型依存関係プロパティ](collection-type-dependency-properties.md)」を参照してください。

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>依存関係プロパティのセキュリティに関する考慮事項

依存関係プロパティは、パブリック プロパティとして宣言する必要があります。 依存関係プロパティ識別子フィールドは、パブリック静的フィールドとして宣言する必要があります。 他のアクセスレベル (protected など) を宣言しようとしても、依存関係プロパティは、プロパティシステム Api と組み合わせて、識別子を使用していつでもアクセスできます。 メタデータレポートや、プロパティシステムの一部である値の決定 Api (など<xref:System.Windows.LocalValueEnumerator>) が原因で、保護された識別子フィールドにアクセスできる可能性もあります。 詳細については、「[依存関係プロパティのセキュリティ](dependency-property-security.md)」を参照してください。

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>依存関係プロパティとクラス コンストラクター

マネージド コード プログラミングでは、クラス コンストラクターが仮想メソッドを呼び出さないという一般的な方針があります (多くの場合は FxCop などのコード分析ツールによって適用されます)。 これは、派生クラスのコンストラクターの基本の初期化としてコンストラクターを呼び出すことができ、コンストラクターから仮想メソッドを入力することで、構築されるオブジェクトのインスタンスの初期化が不完全な状態で行われる可能性があるためです。 から<xref:System.Windows.DependencyObject>派生したクラスから派生する場合は、プロパティシステム自体がを呼び出し、仮想メソッドを内部で公開していることに注意する必要があります。 これらの仮想メソッドは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システム サービスの一部です。 メソッドをオーバーライドすることで、派生クラスが値の決定に参加できるようになります。 ランタイムの初期化の潜在的な問題を回避するには、非常に特殊なコンストラクター パターンに従っている場合を除き、依存関係プロパティの値をクラスのコンストラクター内で設定しないでください。 詳細については、「[DependencyObject の安全なコンストラクター パターン](safe-constructor-patterns-for-dependencyobjects.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [コレクション型依存関係プロパティ](collection-type-dependency-properties.md)
- [依存関係プロパティのセキュリティ](dependency-property-security.md)
- [XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)
- [DependencyObject の安全なコンストラクター パターン](safe-constructor-patterns-for-dependencyobjects.md)
