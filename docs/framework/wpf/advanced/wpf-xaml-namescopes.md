---
title: WPF XAML 名前スコープ
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: a46942188fd417b46ba4feb44d436800e1362098
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225795"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名前スコープ
XAML 名前スコープは、XAML で定義されているオブジェクトを識別する概念です。 XAML 名前スコープ内の名前は、オブジェクト ツリーで XAML 定義のオブジェクトの名前と、対応するインスタンス間の関係を確立するために使用できます。 通常、XAML 名前スコープ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML アプリケーションのルート個々 の XAML ページの読み込みとマネージ コードが作成されます。 プログラミング オブジェクトとしての XAML 名前スコープが定義されている、<xref:System.Windows.Markup.INameScope>インターフェイスし、実際のクラスによって実装も<xref:System.Windows.NameScope>します。  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>読み込まれた XAML アプリケーションにおける名前スコープ  
 プログラミングの概念より広範なプログラミングまたはコンピューター サイエンスのコンテキストでは、一意の識別子またはオブジェクトへのアクセスに使用できる名前の原則多くの場合があります。 内の境界を定義する名前スコープを識別子または名前を使用するシステム プロセスまたは手法は、その名前のオブジェクトが要求された場合に検索がまたは識別名の一意性を強制する、境界。 これらの一般的な原則は、XAML 名前スコープの場合は true です。 ページが読み込まれるときに、WPF では、XAML ページのルート要素の XAML 名前スコープが作成されます。 ページのルートから始まる XAML ページ内で指定した名前は、関連する XAML 名前スコープに追加されます。  
  
 WPF XAML、共通のルート要素である要素に (など<xref:System.Windows.Controls.Page>、および<xref:System.Windows.Window>) 常に XAML 名前スコープを制御します。 場合など、要素<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>はマークアップでは、ページのルート要素です、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを追加、<xref:System.Windows.Controls.Page>暗黙的にルートように、<xref:System.Windows.Controls.Page>作業の XAML 名前スコープを指定できます。  
  
> [!NOTE]
>  XAML の運用環境用の XAML 名前スコープを作成しない場合でも WPF ビルド アクション`Name`または`x:Name`属性の定義内の各要素には、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 任意の XAML 名前スコープ内で 2 回、同じ名前を使用しようとすると、例外が発生します。 分離コードがあり、コンパイル済みアプリケーションの一部を WPF XAML では、例外がビルド時に、WPF ビルド アクションによって、初期のマークアップのコンパイル時に、ページに対して生成されたクラスを作成するときに発生します。 ない任意のビルド アクションによってマークアップ コンパイルされた XAML、XAML が読み込まれるときに XAML 名前スコープの問題に関連する例外を発生する可能性があります。 XAML デザイナーでは、デザイン時に XAML 名前スコープの問題も予測可能性があります。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>オブジェクトをランタイム オブジェクト ツリーに追加します。  
 XAML が解析される時点では、WPF XAML 名前スコープを作成および定義の時点を表します。 オブジェクト ツリーの時点にそのツリーを生成した XAML が解析された後でオブジェクトを追加した場合、`Name`または`x:Name`新しいオブジェクトの値が XAML 名前スコープ内の情報を自動的に更新されません。 XAML が読み込まれた後に、WPF XAML 名前スコープにオブジェクトの名前を追加するには、適切な実装を呼び出す必要があります<xref:System.Windows.Markup.INameScope.RegisterName%2A>通常を XAML 名前スコープを定義するオブジェクト、XAML ページのルート。 名前が登録されていない場合追加されたオブジェクト名を使って参照できませんメソッドなど<xref:System.Windows.FrameworkElement.FindName%2A>、およびアニメーションのターゲットの名前を使用することはできません。  
  
 アプリケーション開発者向けの最も一般的なシナリオが使用する<xref:System.Windows.FrameworkElement.RegisterName%2A>ページの現在のルートの XAML 名前スコープに名前を登録します。 <xref:System.Windows.FrameworkElement.RegisterName%2A> ストーリー ボードの重要なシナリオの一部のアニメーションには、そのターゲット オブジェクト。 詳細については、次を参照してください。[ストーリー ボードの概要](../graphics-multimedia/storyboards-overview.md)します。  
  
 呼び出す場合<xref:System.Windows.FrameworkElement.RegisterName%2A>XAML 名前スコープを定義するオブジェクト以外のオブジェクトの名前が登録されたまま、呼び出し元のオブジェクトが保持されている XAML 名前スコープにするを呼び出した場合と<xref:System.Windows.FrameworkElement.RegisterName%2A>でオブジェクトを定義する XAML 名前スコープ。  
  
### <a name="xaml-namescopes-in-code"></a>コードでの XAML 名前スコープ  
 作成し、コードで XAML 名前スコープを使用できます。 Api と XAML 名前スコープの作成に関連する概念は純粋なコードの使用状況の場合でも同じため、XAML プロセッサを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 自体の処理時に、これらの Api と概念を使用します。 概念と API は、XAML では部分的または完全は定義された通常オブジェクト ツリー内で名前によってオブジェクトを検索できるため、主に存在します。  
  
 プログラムで作成したアプリケーションと読み込まれた XAML からではなく、XAML 名前スコープを定義するオブジェクトを実装する必要があります<xref:System.Windows.Markup.INameScope>、でも、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>の XAML 名前スコープの作成をサポートするために派生クラスで、インスタンス。  
  
 また、任意の要素の読み込みおよび XAML プロセッサで処理されないが、オブジェクトの XAML 名前スコープは作成または既定で初期化します。 明示的に名前をその後登録をする任意のオブジェクトの新しい XAML 名前スコープを作成する必要があります。 XAML 名前スコープを作成するには、静的なを呼び出す<xref:System.Windows.NameScope.SetNameScope%2A>メソッド。 それを所有するオブジェクトを指定、`dependencyObject`パラメーター、および新しい<xref:System.Windows.NameScope.%23ctor%2A>としてコンス トラクターの呼び出し、`value`パラメーター。  
  
 として、オブジェクトが指定されている場合`dependencyObject`の<xref:System.Windows.NameScope.SetNameScope%2A>でない、<xref:System.Windows.Markup.INameScope>実装、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>を呼び出すと、<xref:System.Windows.FrameworkElement.RegisterName%2A>ですべての子要素は影響しません。 新しい XAML 名前スコープを明示的に作成に失敗した場合に呼び出して<xref:System.Windows.FrameworkElement.RegisterName%2A>で例外が発生します。  
  
 コードでの XAML 名前スコープの Api を使用しての例は、次を参照してください。[名前スコープを定義する](../graphics-multimedia/how-to-define-a-name-scope.md)します。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>スタイルとテンプレートで XAML 名前スコープ  
 スタイルとテンプレートで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]再利用し、簡単な方法でコンテンツを再適用する機能を提供します。 ただし、スタイルとテンプレートもあります要素テンプレート レベルで定義されている XAML 名。 ページで同じテンプレートを複数回使用可能性があります。 このため、スタイルとテンプレートがスタイルまたはテンプレートが適用される任意の場所、オブジェクト ツリー内の独立した独自の XAML 名前スコープを定義します。  
  
 次に例を示します。  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 ここでは、同じテンプレートでは、2 つの異なるボタンに適用されます。 テンプレートは個別の XAML 名前スコープを持っていなかった場合、 `TheBorder` XAML 名前スコープ内名前の競合が発生すると、テンプレートで使用される名前。 テンプレートには、各インスタンスでは、独自の XAML 名前スコープを持つため、この例の場合、各インスタンス化されたテンプレートの XAML 名前スコープに、名前が 1 つだけ含まれます。  
  
 スタイルは、ストーリー ボードのパーツが割り当てられている特定の名前を持てるようにほとんどの場合も、独自の XAML 名前スコープを定義します。 これらの名前は、テンプレートをコントロールのカスタマイズの一部として再定義した場合でも、その名前の要素が対象とするコントロール固有の動作を有効にします。  
  
 により、別の XAML 名前スコープ、テンプレートの名前付き要素の検索はさらに、テンプレート化されていないページ内の要素をという名前の検索よりも大きな問題です。 まず取得することで、テンプレートを適用したを決定する必要があります、<xref:System.Windows.Controls.Control.Template%2A>テンプレートが適用されているコントロールのプロパティ値。 次のテンプレート バージョンを呼び出す<xref:System.Windows.FrameworkTemplate.FindName%2A>テンプレートが 2 番目のパラメーターとして適用されたコントロールを渡します。  
  
 コントロールの作成者があり、コントロール自体で定義されている動作の対象の特定、適用されたテンプレート内の要素をという名前のある規則を生成している場合は使用できます、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>コントロールの実装コードからメソッド。 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>のみ、コントロールの作成者がアクセスするメソッドは保護されています。  
  
 テンプレート、および、テンプレートが適用されている XAML 名前スコープを取得する必要がある内から作業する場合の値を取得<xref:System.Windows.FrameworkElement.TemplatedParent%2A>を呼び出して<xref:System.Windows.FrameworkElement.FindName%2A>があります。 テンプレート内での作業の例となります、イベント ハンドラーの実装を記述しているかどうか、適用されたテンプレート内の要素から、イベントの発生した場所。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名前スコープと名前関連 Api  
 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.FindName%2A>、<xref:System.Windows.FrameworkElement.RegisterName%2A>と<xref:System.Windows.FrameworkElement.UnregisterName%2A>メソッド。 これらのメソッドを呼び出すオブジェクトに XAML 名前スコープが所有している場合、メソッドは、関連する XAML 名前スコープのメソッドを呼び出します。 それ以外の場合、親要素をチェックして、XAML 名前スコープを所有しているかどうかは、XAML 名前スコープが見つかるまで、このプロセスは再帰的に (により XAML プロセッサの動作が保証されてルートにある XAML 名前スコープにする)。 <xref:System.Windows.FrameworkContentElement> 動作は、例外に似ていますがない<xref:System.Windows.FrameworkContentElement>XAML 名前スコープを所有します。 メソッド上に存在<xref:System.Windows.FrameworkContentElement>呼び出しが最終的に転送できるように、<xref:System.Windows.FrameworkElement>親要素。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> 既存のオブジェクトに新しい XAML 名前スコープをマップに使用されます。 呼び出すことができます<xref:System.Windows.NameScope.SetNameScope%2A>2 回以上をリセットまたは、XAML をオフにするには名前スコープがするではありません一般的な使用方法。 また、<xref:System.Windows.NameScope.GetNameScope%2A>コードからは通常は使用されません。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名前スコープの実装  
 次は、実装をクラス<xref:System.Windows.Markup.INameScope>直接。  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> XAML 名や名前スコープ; を使用しません。使用してキー代わりに、ディクショナリの実装があるためです。 唯一の理由<xref:System.Windows.ResourceDictionary>実装<xref:System.Windows.Markup.INameScope>が true の XAML 名前スコープの違いを明確にするユーザー コードに例外を発生させる可能性が方法と、<xref:System.Windows.ResourceDictionary>キーを処理および XAML 名前スコープに適用されないことを保証することも、<xref:System.Windows.ResourceDictionary>親要素。  
  
 <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style>実装<xref:System.Windows.Markup.INameScope>で明示的なインターフェイスを定義します。 明示的な実装を介してアクセスされるときに従来どおり動作するこれらの XAML 名前スコープを許可する、<xref:System.Windows.Markup.INameScope>インターフェイスとは、XAML 名前スコープをどのように伝達して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内部プロセスです。 明示的なインターフェイスの定義は、従来の API サーフェスの一部ではないが、<xref:System.Windows.FrameworkTemplate>と<xref:System.Windows.Style>ほとんどを呼び出す必要があるため、<xref:System.Windows.Markup.INameScope>メソッド<xref:System.Windows.FrameworkTemplate>と<xref:System.Windows.Style>を直接と代わりには他の API を使用など、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>します。  
  
 次のクラスを使用して、独自の XAML 名前スコープを定義する、<xref:System.Windows.NameScope?displayProperty=nameWithType>ヘルパー クラスおよびその XAML 名前スコープの実装を通じてへの接続、<xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>添付プロパティ。  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>関連項目

- [XAML 名前空間および WPF XAML の名前空間の割り当て](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)
