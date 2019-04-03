---
title: x:Name ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: 3d188038526570761c2e50dc607fd4aac165fda5
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58034342"
---
# <a name="xname-directive"></a>x:Name ディレクティブ
XAML 名前スコープ内の XAML で定義された要素を一意に識別します。 XAML 名前スコープとその一意性モデルは、フレームワーク Api を提供または実行時に、XAML で作成されたオブジェクト グラフへのアクセスの動作を実装するときに、インスタンス化されたオブジェクトに適用できます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`XAMLNameValue`|制限に準拠している文字列、 [XamlName の文法](xamlname-grammar.md)します。|  
  
## <a name="remarks"></a>Remarks  
 後`x:Name`に適用されるフレームワークでプログラミング モデルのバッキング、名前は、オブジェクト参照またはコンス トラクターによって返されるインスタンスを保持する変数に相当します。  
  
 値、`x:Name`ディレクティブの使用状況は XAML 名前スコープ内で一意である必要があります。 既定で .NET Framework XAML サービスの API で使用するとき、プライマリ XAML 名前スコープが 1 つの XAML 運用環境の XAML ルート要素で定義されており、その XAML 運用環境で格納されている要素が含まれます。 XAML の個別の名前の 1 つの XAML 運用環境で発生するスコープが追加は、特定のシナリオに対処するフレームワークで定義できます。 たとえば、WPF では、新しい XAML 名前スコープ定義され、XAML の運用環境で定義されている任意のテンプレートで作成されました。 (多くの XAML 名前スコープの概念に関連が記述 for WPF) XAML 名前スコープの詳細については、[WPF XAML 名前スコープ](../wpf/advanced/wpf-xaml-namescopes.md)を参照してください。  
  
 一般に、`x:Name`も使用する場合に適用しない`x:Key`します。 特定の既存のフレームワークでの XAML 実装の間に代替の概念が導入`x:Key`と`x:Name`が、その推奨される方法ではありません。 .NET framework XAML サービスがこのような代替の概念をサポートしていませんなどの名前/キーの情報を処理するときに<xref:System.Windows.Markup.INameScope>または<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>します。  
  
 規則の permittance`x:Name`と名前の一意性の強制が実装する特定のフレームワークによって定義可能性があります。 ただし、.NET Framework XAML サービスで使用するのには、フレームワーク定義の XAML 名前スコープの一意性の定義と一貫性のある<xref:System.Windows.Markup.INameScope>、このドキュメントに情報と場所に関する規則と同じ規則を使用する必要があります、情報が適用されます。 たとえば、[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]実装はさまざまなマークアップ要素を個別に分割<xref:System.Windows.NameScope>範囲は、リソース ディクショナリなど、コンテンツ、ページ レベルの XAML、テンプレート、およびその他の遅延によって作成された、論理ツリーと XAML に適用されますこれらの XAML 名前スコープのそれぞれの名前の一意性  
  
 .NET Framework XAML サービスの XAML オブジェクト ライターを使用するカスタムの型のプロパティにマップされる`x:Name`で型を確立または変更できます。 マップするプロパティの名前を参照することでこの動作を定義する、<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>型定義のコードにします。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 型レベル属性です。  
  
 フレームワークに依存しない方法で実装することで定義できます Using.NET Framework XAML サービスの XAML 名前スコープのサポートのバッキング ロジック、<xref:System.Windows.Markup.INameScope>インターフェイス。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 標準的なビルド構成の下で、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]は、XAML、部分クラス、および分離コードで指定したアプリケーション`x:Name`基になる、生成されるフィールドの名前になるときにコード[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]マークアップによって処理されますコンパイルのビルド タスクとそのフィールドは、オブジェクトへの参照を保持します。 既定では、作成されたフィールドは、内部です。 フィールドへのアクセスを変更するには指定することによって、 [X:fieldmodifier 属性](x-fieldmodifier-directive.md)します。 WPF および Silverlight では、シーケンスは、マークアップ コンパイルの定義の名前、値が部分クラス内のフィールドは最初は空です。 という名前の生成されたメソッド、`InitializeComponent`クラスのコンス トラクター内から呼び出されます。 `InitializeComponent` 成る`FindName`のそれぞれを使用して呼び出し、`x:Name`部分クラスとしての XAML 定義の一部に存在する値が文字列を入力します。 戻り値は、解析中に XAML から作成されたオブジェクトを持つフィールドの値を入力するに似た名前の付いたフィールド参照に割り当てられます。 実行`InitializeComponent`ランタイム オブジェクト グラフを使用して、参照できるように、`x:Name`フィールド名を直接呼び出すのではなく/`FindName`いつでも明示的に XAML 定義のオブジェクトへの参照が必要です。  
  
 WPF の Microsoft Visual Basic を使用するアプリケーションを対象し、XAML ファイルが含まれます`Page`ビルド アクションでは、個別の参照プロパティが追加のコンパイル時に作成された、 `WithEvents` をされているすべての要素にキーワード`x:Name`サポートするために、`Handles`イベント ハンドラー デリゲートの構文。 このプロパティはパブリックでは常にします。 詳細については、「[Visual Basic と WPF のイベント処理](../wpf/advanced/visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
 `x:Name` ページがない場合 (たとえば、loose XAML リソース ディクショナリの) のビルド アクションによってマークアップ コンパイルの場合でも、読み込み時に XAML 名前スコープに名前を登録する WPF XAML プロセッサによって使用されます。 この動作の理由の 1 つがあるため、`x:Name`のために必要な可能性のある<xref:System.Windows.Data.Binding.ElementName%2A>バインドします。 詳細については、[データ バインディングの概要](../wpf/data/data-binding-overview.md)を参照してください。  
  
 前述の`x:Name`(または`Name`) を使用する場合に適用しない`x:Key`します。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> XAML 名前スコープとして定義すること自体が実装されていないまたは null 値を取得するのに特別な動作が<xref:System.Windows.Markup.INameScope>Api としてこの動作を強制する方法。 WPF XAML パーサーが検出した場合`Name`または`x:Name`XAML 定義で<xref:System.Windows.ResourceDictionary>名前は任意の XAML 名前スコープに追加されません。 任意の XAML 名前スコープからその名前を検索しようと`FindName`メソッドでは、有効な結果は返されません。  
  
### <a name="xname-and-name"></a>x: 名前と名前  
 WPF アプリケーションの多くのシナリオで使用されるすべてを回避できます、`x:Name`属性があるため、`Name`依存関係プロパティとして、既定の XAML 名前空間などの指定された重要な基本クラスのいくつか<xref:System.Windows.FrameworkElement>と<xref:System.Windows.FrameworkContentElement>この同じ目的を満たします。 一般的な XAML と WPF のシナリオは引き続き no を持つ要素へのアクセスをコードが`Name`フレームワーク レベルのプロパティが重要です。 たとえば、特定のアニメーションとストーリー ボードのサポート クラスをサポートしていない、`Name`プロパティがアニメーションを制御するためにコードで参照する必要があります。 指定する必要があります`x:Name`タイムラインと後でコードからそれらを参照する場合、XAML 内に作成される変換の属性として。  
  
 場合<xref:System.Windows.FrameworkElement.Name%2A>は、クラスのプロパティとして使用可能な<xref:System.Windows.FrameworkElement.Name%2A>と`x:Name`属性として同じ意味で使用できますが、同じ要素の両方が指定されて場合解析の例外が発生します。 マークアップ コンパイルを XAML には、例外が、それ以外の場合、読み込み時に発生しますマークアップ コンパイル時に発生します。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> XAML 属性の構文を使用して設定することができ、コードを使用して<xref:System.Windows.DependencyObject.SetValue%2A>; ただしその設定、<xref:System.Windows.FrameworkElement.Name%2A>コード内のプロパティは、XAML が既にほとんどの状況での XAML 名前スコープ内で代表的なフィールド参照を作成できません読み込まれます。 設定しようとしてではなく<xref:System.Windows.FrameworkElement.Name%2A>コードでは、次のように使用します。<xref:System.Windows.NameScope>に対して適切な名前スコープのコードからメソッド。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 内部のテキストを含むプロパティ要素構文を使用して設定できますが、一般的でないです。 これに対し、 `x:Name` XAML プロパティ要素構文でまたはを使用してコードで設定することはできません<xref:System.Windows.DependencyObject.SetValue%2A>; のみ設定できますディレクティブであるため、オブジェクトの属性構文を使用します。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Name` に関しては、別途ドキュメントが用意されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF のツリー](../wpf/advanced/trees-in-wpf.md)
