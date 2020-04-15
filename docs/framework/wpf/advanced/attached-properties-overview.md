---
title: 添付プロパティの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 5086401f4616074d364c1d387b751116120d5969
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389000"
---
# <a name="attached-properties-overview"></a>添付プロパティの概要

添付プロパティは、XAML によって定義された概念です。 添付プロパティは、任意のオブジェクトに設定可能なグローバル プロパティの型として使用されることを意図しています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では通常、添付プロパティは従来のプロパティ "ラッパー" を含まない依存関係プロパティの特殊な形式として定義されています。

## <a name="prerequisites"></a>前提条件<a name="prerequisites"></a>

このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」を読んでいることを前提としています。 このトピックの例に従うには、XAML を理解し、WPF アプリケーションの作成方法を理解する必要があります。

## <a name="why-use-attached-properties"></a>添付プロパティを使用する理由<a name="attached_properties_usage"></a>

添付プロパティの目的の 1 つは、親要素に実際に定義されているプロパティに対する一意の値を、異なる子要素が指定できるようにすることです。 このシナリオの適用例として、子要素から親要素に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] での表示方法を通知させることがあります。 その一例が<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>プロパティです。 プロパティ<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>は、それ自体ではなく<xref:System.Windows.Controls.DockPanel>、 内に含まれる要素に設定されるように設計されているため、<xref:System.Windows.Controls.DockPanel>添付プロパティとして作成されます。 この<xref:System.Windows.Controls.DockPanel>クラスは、<xref:System.Windows.DependencyProperty>という名前<xref:System.Windows.Controls.DockPanel.DockProperty>の静的フィールドを定義<xref:System.Windows.Controls.DockPanel.GetDock%2A>し<xref:System.Windows.Controls.DockPanel.SetDock%2A>、 と メソッドを添付プロパティのパブリック アクセサーとして提供します。

## <a name="attached-properties-in-xaml"></a>XAML の添付プロパティ<a name="attached_properties_xaml"></a>

XAML では、構文 *AttachedPropertyProvider*.*PropertyName* を使用して添付プロパティを設定します

XAML<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>で設定する方法の例を次に示します。

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

使用法は静的プロパティと似ています。名前で指定されたインスタンス<xref:System.Windows.Controls.DockPanel>を参照するのではなく、常に添付プロパティを所有し、登録する型を参照します。

さらに、XAML の添付プロパティはマークアップに設定する属性であるため、設定操作にのみ関連性があります。 XAML でプロパティを直接取得することはできませんが、スタイルのトリガー (詳細については、「[スタイルとテンプレート](../controls/styling-and-templating.md)」を参照) などの値を比較するための間接的な機構があります。

### <a name="attached-property-implementation-in-wpf"></a>WPF での添付プロパティの実装

では[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、UI プレゼンテーションに関連する WPF 型に存在する添付プロパティのほとんどは、依存関係プロパティとして実装されます。 添付プロパティは XAML の概念ですが、依存関係プロパティは WPF の概念です。 WPF 添付プロパティは依存関係プロパティであるため、プロパティ メタデータなどの依存関係プロパティの概念とそのプロパティ メタデータの既定値をサポートします。

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>所有型で添付プロパティを使用する方法<a name="howused"></a>

添付プロパティはどのオブジェクトにも設定できますが、プロパティを設定したことによって自動的に意味のある結果が得られるわけでも、値が別のオブジェクトによって使用されるわけでもありません。 一般に、添付プロパティの目的は、想定されるさまざまなクラス階層または論理関係から生じるオブジェクトが、添付プロパティを定義する型に共通する情報をレポートできるようにすることです。 添付プロパティを定義する型は、一般的に次のいずれかのモデルに従っています。

- 添付プロパティを定義する型が、添付プロパティの値を設定する要素の親要素になるように設計されている。 この型の子オブジェクトは、一部のオブジェクト ツリー構造で内部ロジックを反復し、値を取得して、その値に対する処理を実行します。

- 添付プロパティを定義する型が、想定されるさまざまな親要素およびコンテンツ モデルの子要素として使用される。

- 添付プロパティを定義する型が、サービスを表す。 その他の型は、添付プロパティの値を設定します。 プロパティを設定する要素がサービスのコンテキストで評価されると、添付プロパティの値がサービス クラスの内部ロジックにより取得されます。

### <a name="an-example-of-a-parent-defined-attached-property"></a>親定義の添付プロパティの例

WPF が添付プロパティを定義する最も一般的なシナリオは、親要素が子要素コレクションをサポートし、動作の詳細が子要素ごとに個別に報告される動作も実装する場合です。

<xref:System.Windows.Controls.DockPanel>は、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティを定義<xref:System.Windows.Controls.DockPanel>し、クラス レベルのコードをレンダリング ロジックの一部<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A>として<xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>持ちます (具体的には、 と )。 インスタンス<xref:System.Windows.Controls.DockPanel>は、その直接の子要素のいずれかがに値を設定しているかどうかを常にチェックします<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>。 設定されている場合は、その値が、その子要素に適用されるレンダリング ロジックの入力になります。 入れ<xref:System.Windows.Controls.DockPanel>子になったインスタンスは、それぞれ直接の子要素コレクションを処理しますが、その動作は、値<xref:System.Windows.Controls.DockPanel>を処理<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>する方法に実装固有です。 直接の親以外の要素に影響を与える添付プロパティを所有することは、理論上は可能です。 添付プロパティ<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>が、親要素を持たない<xref:System.Windows.Controls.DockPanel>要素に対して設定されている場合、エラーまたは例外は発生しません。 これは、グローバル プロパティ値が設定されたが、情報を消費する可能性<xref:System.Windows.Controls.DockPanel>のある現在の親がないことを意味します。

## <a name="attached-properties-in-code"></a>コード内の添付プロパティ<a name="attached_properties_code"></a>

WPF の添付プロパティには、取得/設定を簡単に行うための典型的な CLR の "ラッパー" メソッドはありません。 これは、添付プロパティが、プロパティが設定されているインスタンスの CLR 名前空間の一部であるとは限らないためです。 ただし、XAML の解析時に XAML プロセッサがその値を設定できる必要があります。 添付プロパティの効果的な使用をサポートするには、添付プロパティの所有者の種類が **、Get_PropertyName_** および**Set_PropertyName_** の形式で専用のアクセサ メソッドを実装する必要があります。 この専用のアクセサー メソッドは、コード内の添付プロパティの取得/設定でも役立ちます。 コードの観点では、添付プロパティはプロパティ アクセサーではなくメソッド アクセサーを含むバッキング フィールドに似ており、そのバッキング フィールドは特に定義することなくすべてのオブジェクトに存在することができます。

次の例は、コードに添付プロパティを設定する方法を示しています。 この例では、`myCheckBox`クラスのインスタンスです<xref:System.Windows.Controls.CheckBox>。

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

XAML の場合と同様に`myCheckBox`、コードの 4 行目`myDockPanel`で子要素として追加されていない場合、コードの 5 行目は例外を発生しませんが、プロパティ値は<xref:System.Windows.Controls.DockPanel>親と対話しないため、何も実行されません。 子要素<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>に設定された値と親要素の存在を組み合わせた値だけが、レンダリングされたアプリケーションで有効な動作を引き起こします。 <xref:System.Windows.Controls.DockPanel> (この場合、添付プロパティを設定してからツリーに接続するか、 ツリーに接続してから添付プロパティを設定することができます。 どちらの操作でも、結果は同じです。)

## <a name="attached-property-metadata"></a>添付プロパティメタデータ<a name="attached_properties_metadata"></a>

プロパティを登録するときに、<xref:System.Windows.FrameworkPropertyMetadata>プロパティがレンダリング、計測などに影響するかどうかなど、プロパティの特性を指定するように設定されます。 添付プロパティのメタデータは、一般的に依存関係プロパティとの違いがありません。 オーバーライドの既定値を添付プロパティのメタデータに指定すると、その値がオーバーライドするクラスのインスタンスの暗黙的な添付プロパティの既定値になります。 具体的には、一部のプロセスが添付プロパティの `Get` メソッド アクセサーを使用してそのプロパティの値のクエリを行った場合に、メタデータを指定したクラスのインスタンスが指定されており、その添付プロパティの値が設定されていないと、既定値がレポートされます。

プロパティでプロパティ値の継承を有効にする場合は、未接続の依存関係プロパティではなく添付プロパティを使用する必要があります。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。

## <a name="custom-attached-properties"></a>カスタム添付プロパティ<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>添付プロパティを作成する場合<a name="create_attached_properties"></a>

添付プロパティは、定義クラスではないクラスで使用できるプロパティ設定機構を用意する理由がある場合に作成できます。 この最も一般的なシナリオが、レイアウトです。 既存のレイアウト プロパティの<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>例<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>としては<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>、 、および が挙げられます。 これによって実現するシナリオは、レイアウト制御要素の子要素として存在する要素が、レイアウト親要素に対して個別にレイアウト要件を表現するというものです。親が添付プロパティとして定義したプロパティ値を、個々の子要素が設定します。

クラスがサービスを表しており、クラスでサービスをより透過的に統合できるようにしたい場合にも、添付プロパティを使用します。

さらに別のシナリオは、プロパティ ウィンドウの編集など、Visual Studio WPF デザイナーのサポートを受ける**です**。 詳細については、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。

前述のように、プロパティ値の継承を使用する場合には、添付プロパティを登録する必要があります。

### <a name="how-to-create-an-attached-property"></a>添付プロパティを作成する方法<a name="how_do_i_create_attached_properties"></a>

クラスが他の型で使用するために添付プロパティを厳密に定義している場合、そのクラスは から<xref:System.Windows.DependencyObject>派生する必要はありません。 ただし、アタッチされたプロパティを依存関係<xref:System.Windows.DependencyObject>プロパティにするという WPF モデル全体に従う場合は、から派生する必要があります。

型のフィールドを宣言して、添付プロパティを`public static readonly`依存関係プロパティとして定義<xref:System.Windows.DependencyProperty>します。 このフィールドは、メソッドの戻り値を使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>して定義します。 フィールド名は、識別フィールドとそれらが表すプロパティに名前を付`Property`けるという確立された WPF パターンに従って、文字列を付加した添付プロパティ名と一致する必要があります。 また、添付プロパティ プロバイダは、静的**Get_PropertyName_** および**Set_PropertyName_** メソッドを添付プロパティのアクセサとして提供する必要があります。これを行わないと、プロパティ システムが添付プロパティを使用できなくなります。

> [!NOTE]
> 添付プロパティの get アクセサーを省略すると、Visual Studio や Visual Studio 用ブレンドなどのデザイン ツールでは、プロパティのデータ バインディングは機能しません。

#### <a name="the-get-accessor"></a>Get アクセサー

**Get_PropertyName_** アクセサーのシグネチャは次の指定する必要があります。

`public static object GetPropertyName(object target)`

- `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、アタッチされた<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>プロパティはインスタンスに対<xref:System.Windows.UIElement>してのみ設定されるため、メソッドはパラメーターをとして型指定<xref:System.Windows.UIElement>します。

- 戻り値は、実装のより具体的な型として指定することができます。 たとえば、値はその<xref:System.Windows.Controls.DockPanel.GetDock%2A>列挙型にしか<xref:System.Windows.Controls.Dock>設定できないため、メソッドは 、この型として型を指定します。

#### <a name="the-set-accessor"></a>Set アクセサー

**Set_PropertyName_** アクセサのシグネチャは次の必要があります。

`public static void SetPropertyName(object target, object value)`

- `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、アタッチされた<xref:System.Windows.Controls.DockPanel.SetDock%2A>プロパティはインスタンスに<xref:System.Windows.UIElement>対してのみ設定されるため、メソッドは 、この型として<xref:System.Windows.UIElement>型を指定します。

- `value` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、値はその<xref:System.Windows.Controls.DockPanel.SetDock%2A>列挙型にしか<xref:System.Windows.Controls.Dock>設定できないため、メソッドは 、この型として型を指定します。 このメソッドの値は、マークアップの添付プロパティの使用で添付プロパティが検出されたときに XAML ローダーから生じる入力であることに注意してください。 この入力はマークアップの XAML 属性値として指定された値です。 したがって、適切な型を属性値 (最終的には単なる文字列) から作成できるように、使用する型の型変換、値シリアライザー、またはマークアップ拡張サポートが必要です。

次の例は、依存関係プロパティの登録 (<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッドを使用) と **、Get_PropertyName_** アクセサーと**Set_PropertyName_** アクセサーを示しています。 この例では、添付プロパティ名は `IsBubbleSource` です。 したがって、アクセサーの名前は `GetIsBubbleSource` および `SetIsBubbleSource` である必要があります。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>添付プロパティの属性

WPF では、リフレクション プロセスに添付されたプロパティに関する情報を提供するためのいくつかの .NET 属性を定義し、デザイナーなどのリフレクションおよびプロパティ情報の典型的なユーザーに対して使用します。 添付プロパティに含まれる型は膨大な範囲に及ぶため、デザイナーには XAML を使用する特定のテクノロジの実装に定義されたすべての添付プロパティのグローバル リストがユーザーに表示されないようにするための手段が必要となります。 WPF が添付プロパティに対して定義する .NET 属性を使用すると、特定の添付プロパティをプロパティ ウィンドウに表示する必要がある状況をスコープ指定できます。 また、この属性をカスタム添付プロパティに適用するという選択肢もあります。 NET 属性の目的と構文は、適切なリファレンス ページで説明されています。

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>添付プロパティの詳細<a name="more"></a>

- 添付プロパティの作成の詳細については、「[方法: 添付プロパティを登録する](how-to-register-an-attached-property.md)」を参照してください。

- 依存関係プロパティおよび添付プロパティの高度な使用シナリオについては、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。

- プロパティは添付プロパティとしても依存関係プロパティとしても登録できますが、"ラッパー" 実装は公開したままにすることができます。 この場合、プロパティをその要素に設定することも、XAML の添付プロパティの構文を使用して任意の要素に設定することもできます。 標準と添付の両方の使用法に適したシナリオを持つプロパティの<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>例は です。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyProperty>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [添付プロパティを登録する](how-to-register-an-attached-property.md)
