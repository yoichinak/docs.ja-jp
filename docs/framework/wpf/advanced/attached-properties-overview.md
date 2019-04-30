---
title: 添付プロパティの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: de17fb30358bdf1a8e2a1d6cfc4f5f80fefa1268
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032236"
---
# <a name="attached-properties-overview"></a>添付プロパティの概要

添付プロパティは、XAML によって定義された概念です。 添付プロパティは、任意のオブジェクトに設定可能なグローバル プロパティの型として使用されることを意図しています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では通常、添付プロパティは従来のプロパティ "ラッパー" を含まない依存関係プロパティの特殊な形式として定義されています。

## 前提条件 <a name="prerequisites"></a>

このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」トピックを通読していることを前提としています。 このトピックの例を実行するにも XAML を理解して、WPF アプリケーションを作成する方法を理解する必要があります。

## 添付プロパティを使用する理由 <a name="attached_properties_usage"></a>

添付プロパティの目的の 1 つは、親要素に実際に定義されているプロパティに対する一意の値を、異なる子要素が指定できるようにすることです。 このシナリオの適用例として、子要素から親要素に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] での表示方法を通知させることがあります。 1 つの例は、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>プロパティ。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>内に含まれる要素に設定することが目的のため、プロパティが添付プロパティとして作成された、<xref:System.Windows.Controls.DockPanel>ではなくで<xref:System.Windows.Controls.DockPanel>自体。 <xref:System.Windows.Controls.DockPanel>クラス定義、静的な<xref:System.Windows.DependencyProperty>という名前のフィールド<xref:System.Windows.Controls.DockPanel.DockProperty>、し、説明、<xref:System.Windows.Controls.DockPanel.GetDock%2A>と<xref:System.Windows.Controls.DockPanel.SetDock%2A>添付プロパティのパブリック アクセサーとしてメソッド。

## XAML の添付プロパティ <a name="attached_properties_xaml"></a>

XAML では、構文 *AttachedPropertyProvider*.*PropertyName* を使用して添付プロパティを設定します

設定する方法の例を次に<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>XAML で。

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

使用状況は、静的プロパティに少し似ています常に、型を参照する<xref:System.Windows.Controls.DockPanel>が所有し、添付プロパティを登録する名前で指定したインスタンスを参照するのではなく。

さらに、XAML の添付プロパティはマークアップに設定する属性であるため、設定操作にのみ関連性があります。 XAML でプロパティを直接取得することはできませんが、スタイルのトリガー (詳細については、「[スタイルとテンプレート](../controls/styling-and-templating.md)」を参照) などの値を比較するための間接的な機構があります。

### <a name="attached-property-implementation-in-wpf"></a>WPF での添付プロパティの実装

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、UI プレゼンテーションに関連する WPF 型に存在する添付プロパティのほとんどは、依存関係プロパティとして実装されます。 添付プロパティは XAML の概念では、依存関係プロパティは、WPF の概念です。 接続されている WPF のプロパティは、依存関係プロパティであるために、プロパティ メタデータ、およびそのプロパティのメタデータからの既定値などの依存関係プロパティの概念をサポートしています。

## 所有する型による添付プロパティの使用方法 <a name="howused"></a>

添付プロパティはどのオブジェクトにも設定できますが、プロパティを設定したことによって自動的に意味のある結果が得られるわけでも、値が別のオブジェクトによって使用されるわけでもありません。 一般に、添付プロパティの目的は、想定されるさまざまなクラス階層または論理関係から生じるオブジェクトが、添付プロパティを定義する型に共通する情報をレポートできるようにすることです。 添付プロパティを定義する型は、一般的に次のいずれかのモデルに従っています。

- 添付プロパティを定義する型が、添付プロパティの値を設定する要素の親要素になるように設計されている。 この型の子オブジェクトは、一部のオブジェクト ツリー構造で内部ロジックを反復し、値を取得して、その値に対する処理を実行します。

- 添付プロパティを定義する型が、想定されるさまざまな親要素およびコンテンツ モデルの子要素として使用される。

- 添付プロパティを定義する型が、サービスを表す。 その他の型は、添付プロパティの値を設定します。 プロパティを設定する要素がサービスのコンテキストで評価されると、添付プロパティの値がサービス クラスの内部ロジックにより取得されます。

### <a name="an-example-of-a-parent-defined-attached-property"></a>親定義の添付プロパティの例

WPF が添付プロパティを定義する最も一般的なシナリオは親要素の子要素のコレクションをサポートしているし、も動作を実装するときに各子要素の動作の詳細を個別に報告される場所です。

<xref:System.Windows.Controls.DockPanel> 定義、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティ、および<xref:System.Windows.Controls.DockPanel>そのレンダリング ロジックの一部としてクラスレベルのコードを持つ (具体的には、<xref:System.Windows.Controls.DockPanel.MeasureOverride%2A>と<xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>)。 A<xref:System.Windows.Controls.DockPanel>インスタンスは直下の子要素のいずれかの値を設定がかどうかを必ず確認<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>します。 設定されている場合は、その値が、その子要素に適用されるレンダリング ロジックの入力になります。 入れ子になった<xref:System.Windows.Controls.DockPanel>インスタンスはそれぞれが独自の直接の子要素のコレクションを扱いますが、その動作は実装固有方法<xref:System.Windows.Controls.DockPanel>プロセス<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>値。 直接の親以外の要素に影響を与える添付プロパティを所有することは、理論上は可能です。 場合、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>を持たない要素で添付プロパティを設定<xref:System.Windows.Controls.DockPanel>がないエラーや例外に対して操作を実行する親要素が発生します。 グローバル プロパティの値が設定されたが、現在は持たないこれは<xref:System.Windows.Controls.DockPanel>情報を利用できる親。

## コードの添付プロパティ <a name="attached_properties_code"></a>

WPF で添付プロパティには、一般的なありません[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]取得/設定を簡単にアクセスするための「ラッパー」メソッドです。 これは、添付プロパティが、プロパティが設定されているインスタンスの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間の一部とは限らないためです。 ただし、XAML の解析時に XAML プロセッサがその値を設定できる必要があります。 有効な添付プロパティの使用をサポートする添付プロパティの所有者の種類は、フォームで専用のアクセサー メソッドを実装する必要があります**Get_PropertyName_** と**Set_PropertyName_** します。 この専用のアクセサー メソッドは、コード内の添付プロパティの取得/設定でも役立ちます。 コードの観点では、添付プロパティはプロパティ アクセサーではなくメソッド アクセサーを含むバッキング フィールドに似ており、そのバッキング フィールドは特に定義することなくすべてのオブジェクトに存在することができます。

次の例は、コードに添付プロパティを設定する方法を示しています。 この例で`myCheckBox`のインスタンスである、<xref:System.Windows.Controls.CheckBox>クラス。

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

同様に、XAML の場合する場合、`myCheckBox`としての子要素が既に追加されていなかった`myDockPanel`コードの 3 番目の行でコードの 4 行目は例外を発生させないがないプロパティの値とのやり取りを<xref:System.Windows.Controls.DockPanel>親と、それに伴って何も実行します。 のみ、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>値の存在し、子要素のセットを<xref:System.Windows.Controls.DockPanel>親要素によってレンダリングされたアプリケーションで有効な動作が発生します。 (この場合、添付プロパティを設定してからツリーに接続するか、 ツリーに接続してから添付プロパティを設定することができます。 どちらの操作でも、結果は同じです。)

## 添付プロパティのメタデータ <a name="attached_properties_metadata"></a>

プロパティを登録するときに<xref:System.Windows.FrameworkPropertyMetadata>プロパティがレンダリング、測定、そして具合にどのように影響するかどうかなど、プロパティの特性を指定に設定されます。 添付プロパティのメタデータは、一般的に依存関係プロパティとの違いがありません。 オーバーライドの既定値を添付プロパティのメタデータに指定すると、その値がオーバーライドするクラスのインスタンスの暗黙的な添付プロパティの既定値になります。 具体的には、一部のプロセスが添付プロパティの `Get` メソッド アクセサーを使用してそのプロパティの値のクエリを行った場合に、メタデータを指定したクラスのインスタンスが指定されており、その添付プロパティの値が設定されていないと、既定値がレポートされます。

プロパティでプロパティ値の継承を有効にする場合は、未接続の依存関係プロパティではなく添付プロパティを使用する必要があります。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。

## カスタム添付プロパティ <a name="custom"></a>

### 添付プロパティを作成する場合 <a name="create_attached_properties"></a>

添付プロパティは、定義クラスではないクラスで使用できるプロパティ設定機構を用意する理由がある場合に作成できます。 この最も一般的なシナリオが、レイアウトです。 既存のレイアウト プロパティの例は、 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>、および<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>します。 これによって実現するシナリオは、レイアウト制御要素の子要素として存在する要素が、レイアウト親要素に対して個別にレイアウト要件を表現するというものです。親が添付プロパティとして定義したプロパティ値を、個々の子要素が設定します。

クラスがサービスを表しており、クラスでサービスをより透過的に統合できるようにしたい場合にも、添付プロパティを使用します。

別のシナリオがなど、Visual Studio の WPF デザイナーのサポートを受けるにはまだ**プロパティ**ウィンドウを編集します。 詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。

前述のように、プロパティ値の継承を使用する場合には、添付プロパティを登録する必要があります。

### 添付プロパティを作成する方法 <a name="how_do_i_create_attached_properties"></a>

派生するクラスが必要ない場合、クラスが他の種類で使用する目的のみで添付プロパティを定義する<xref:System.Windows.DependencyObject>します。 派生する必要がある操作を行いますが、<xref:System.Windows.DependencyObject>の添付プロパティを依存関係プロパティでもある WPF の全体的なモデルに従う場合。

依存関係プロパティとして宣言することで、添付プロパティを定義、`public static readonly`型のフィールド<xref:System.Windows.DependencyProperty>します。 戻り値を使用してこのフィールドを定義する、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッド。 フィールド名は文字列が付加され、添付プロパティの名前と一致する必要があります`Property`を表していると識別フィールドの名前付けの確立された WPF パターンに従います。 添付プロパティのプロバイダーは、静的にも提供する必要があります**Get_PropertyName_** と**Set_PropertyName_** ; 添付プロパティのアクセサー メソッド、プロパティに失敗が発生システムが添付プロパティを使用することができません。

> [!NOTE]
> 添付プロパティの get アクセサーを省略した場合、プロパティのデータ バインディングは、Visual Studio および Expression Blend などのデザイン ツールでは機能しません。

#### <a name="the-get-accessor"></a>Get アクセサー

署名、 **Get_PropertyName_** アクセサーを指定する必要があります。

`public static object GetPropertyName(object target)`

- `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType>メソッドの型パラメーターとして<xref:System.Windows.UIElement>添付プロパティに設定する目的のみであるため、<xref:System.Windows.UIElement>インスタンス。

- 戻り値は、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A>メソッドの型としては<xref:System.Windows.Controls.Dock>のため、値は、その列挙体にのみ設定できます。

#### <a name="the-set-accessor"></a>Set アクセサー

署名、 **Set_PropertyName_** アクセサーを指定する必要があります。

`public static void SetPropertyName(object target, object value)`

- `target` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの型としては<xref:System.Windows.UIElement>添付プロパティに設定する目的のみであるため、<xref:System.Windows.UIElement>インスタンス。

- `value` オブジェクトは、実装のより具体的な型として指定することができます。 たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A>メソッドの型としては<xref:System.Windows.Controls.Dock>のため、値は、その列挙体にのみ設定できます。 このメソッドの値は、マークアップの添付プロパティの使用で添付プロパティが検出されたときに XAML ローダーから生じる入力であることに注意してください。 この入力はマークアップの XAML 属性値として指定された値です。 したがって、適切な型を属性値 (最終的には単なる文字列) から作成できるように、使用する型の型変換、値シリアライザー、またはマークアップ拡張サポートが必要です。

次の例では、依存関係プロパティの登録 (を使用して、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッド)、だけでなく**Get_PropertyName_** と**Set_PropertyName_** アクセサー。 この例では、添付プロパティ名は `IsBubbleSource` です。 したがって、アクセサーの名前は `GetIsBubbleSource` および `SetIsBubbleSource` である必要があります。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>添付プロパティの属性

WPF では、いくつかを定義します[!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]添付プロパティをリフレクション プロセス、およびデザイナーなどのリフレクションおよびプロパティ情報の一般的なユーザーに関する情報を提供するためのものですが。 添付プロパティに含まれる型は膨大な範囲に及ぶため、デザイナーには XAML を使用する特定のテクノロジの実装に定義されたすべての添付プロパティのグローバル リストがユーザーに表示されないようにするための手段が必要となります。 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]その WPF を添付プロパティを使用して、スコープのプロパティ ウィンドウで特定の添付プロパティを表示する必要があります、状況を定義します。 また、この属性をカスタム添付プロパティに適用するという選択肢もあります。 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]の目的および構文は、次の参照ページに記載されています。

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## 添付プロパティの詳細情報 <a name="more"></a>

- 添付プロパティの作成の詳細については、「[方法: 添付プロパティを登録する](how-to-register-an-attached-property.md)」を参照してください。

- 依存関係プロパティおよび添付プロパティの高度な使用シナリオについては、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。

- プロパティは添付プロパティとしても依存関係プロパティとしても登録できますが、"ラッパー" 実装は公開したままにすることができます。 この場合、プロパティをその要素に設定することも、XAML の添付プロパティの構文を使用して任意の要素に設定することもできます。 標準と接続の両方の使用状況を適切なシナリオでのプロパティの例は、<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyProperty>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [方法: 添付プロパティを登録する](how-to-register-an-attached-property.md)