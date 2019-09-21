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
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917335"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名前スコープ
XAML 名前スコープは、XAML で定義されているオブジェクトを識別する概念です。 XAML 名前スコープ内の名前を使用すると、オブジェクトの XAML 定義の名前と、オブジェクトツリー内のそのインスタンスに対応するオブジェクトの間のリレーションシップを確立できます。 通常、xaml アプリケーションの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個々の xaml ページルートを読み込むときに、マネージコードの xaml 名前スコープが作成されます。 プログラミングオブジェクトとしての XAML 名前スコープは<xref:System.Windows.Markup.INameScope> 、インターフェイスで定義され、実用的<xref:System.Windows.NameScope>なクラスによっても実装されます。  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>読み込まれた XAML アプリケーションでの名前スコープ  
 より広範なプログラミングまたはコンピューターサイエンスのコンテキストでは、プログラミングの概念には、オブジェクトへのアクセスに使用できる一意の識別子または名前の原則が含まれることがよくあります。 識別子または名前を使用するシステムでは、名前スコープによって、その名前のオブジェクトが要求された場合にプロセスまたは技法が検索する境界、または識別名の一意性が強制される境界が定義されます。 これらの一般的な原則は、XAML 名前スコープに当てはまります。 WPF では、XAML 名前スコープは、ページが読み込まれるときに XAML ページのルート要素に作成されます。 ページルートから開始する XAML ページ内で指定された各名前は、関連する XAML 名前スコープに追加されます。  
  
 WPF xaml では、一般的なルート要素 ( <xref:System.Windows.Controls.Page>や<xref:System.Windows.Window>など) である要素は常に XAML 名前スコープを制御します。 や<xref:System.Windows.FrameworkElement> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>などの要素がマークアップ内のページのルート要素である場合、プロセッサは暗黙的にルートを追加して、が動作する XAML 名前スコープを提供できるようにします。 <xref:System.Windows.FrameworkContentElement>  
  
> [!NOTE]
> WPF のビルドアクション`Name`は`x:Name` 、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ内の要素に属性が定義されていない場合でも、xaml 実稼働の xaml 名前スコープを作成します。  
  
 任意の XAML 名前スコープで同じ名前を2回使用しようとすると、例外が発生します。 分離コードがあり、コンパイルされたアプリケーションの一部である WPF XAML の場合、初期マークアップコンパイル中にページ用に生成されたクラスを作成するときに、WPF ビルドアクションによってビルド時に例外が発生します。 ビルドアクションによってマークアップコンパイルされていない XAML の場合、xaml が読み込まれると、XAML 名前スコープの問題に関連する例外が発生する可能性があります。 Xaml デザイナーは、デザイン時に XAML 名前スコープの問題を予測する場合もあります。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>ランタイムオブジェクトツリーへのオブジェクトの追加  
 XAML が解析される瞬間は、WPF XAML 名前スコープが作成および定義された時点を表します。 オブジェクトを、そのツリーを生成した xaml が解析された後である時点でオブジェクトツリーに追加し`Name`た`x:Name`場合、新しいオブジェクトのまたはの値によって、xaml 名前スコープの情報が自動的に更新されることはありません。 Xaml が読み込まれた後にオブジェクトの名前を WPF XAML 名前スコープに追加するには、xaml 名前<xref:System.Windows.Markup.INameScope.RegisterName%2A>スコープを定義するオブジェクトでの適切な実装を呼び出す必要があります。これは通常、xaml ページルートです。 名前が登録されていない場合は、など<xref:System.Windows.FrameworkElement.FindName%2A>のメソッドを使用して、追加されたオブジェクトを名前で参照することはできません。また、この名前をアニメーションの対象として使用することはできません。  
  
 アプリケーション開発者にとって最も一般的なシナリオでは<xref:System.Windows.FrameworkElement.RegisterName%2A> 、を使用して、ページの現在のルートの XAML 名前スコープに名前を登録します。 <xref:System.Windows.FrameworkElement.RegisterName%2A>は、アニメーションの対象となるストーリーボードの重要なシナリオの一部です。 詳細については、「[ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 Xaml 名前スコープ<xref:System.Windows.FrameworkElement.RegisterName%2A>を定義するオブジェクト以外のオブジェクトでを呼び出すと、その名前は、呼び出し元のオブジェクトが保持されている xaml 名前スコープにまだ登録され<xref:System.Windows.FrameworkElement.RegisterName%2A>ます。これは、オブジェクトを定義する xaml 名前スコープでを呼び出した場合と同様です。  
  
### <a name="xaml-namescopes-in-code"></a>コード内の XAML 名前スコープ  
 XAML 名前スコープを作成し、コードで使用することができます。 Xaml 名前スコープの作成に関係する api と概念は、純粋なコードの使用でも同じです。の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xaml プロセッサでは、xaml 自体を処理するときにこれらの api と概念が使用されるためです。 概念と API は主に、XAML で部分的または完全に定義されているオブジェクトツリー内の名前でオブジェクトを検索できるようにするために存在します。  
  
 読み込まれた xaml からではなく、プログラムによって作成されるアプリケーションでは、xaml 名前<xref:System.Windows.Markup.INameScope>スコープを定義する<xref:System.Windows.FrameworkElement>オブジェクトは、そのクラスでの xaml 名前スコープの作成をサポートするために、または派生クラスのいずれ<xref:System.Windows.FrameworkContentElement>かを実装する必要があります。選ぶ.  
  
 また、XAML プロセッサによって読み込まれて処理されない要素については、オブジェクトの XAML 名前スコープが既定で作成または初期化されることはありません。 後で名前を登録するオブジェクトに対して、新しい XAML 名前スコープを明示的に作成する必要があります。 XAML 名前スコープを作成するには、静的<xref:System.Windows.NameScope.SetNameScope%2A>メソッドを呼び出します。 `dependencyObject`パラメーターとしてオブジェクトを所有するオブジェクトと、 `value`パラメーターとし<xref:System.Windows.NameScope.%23ctor%2A>て新しいコンストラクター呼び出しを指定します。  
  
 に`dependencyObject` <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement.RegisterName%2A> <xref:System.Windows.FrameworkElement> <xref:System.Windows.Markup.INameScope>として指定されたオブジェクトが実装でない場合、または子要素でを呼び出すと、効果はありません。 <xref:System.Windows.NameScope.SetNameScope%2A> 新しい XAML 名前スコープを明示的に作成できない場合は、 <xref:System.Windows.FrameworkElement.RegisterName%2A>を呼び出すと例外が発生します。  
  
 コードで XAML 名前スコープ Api を使用する例については、「[名前スコープの定義](../graphics-multimedia/how-to-define-a-name-scope.md)」を参照してください。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>スタイルとテンプレートでの XAML 名前スコープ  
 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイルとテンプレートを使用すると、簡単な方法でコンテンツを再利用したり、再適用したりできます。 ただし、スタイルやテンプレートには、テンプレートレベルで定義された XAML 名を持つ要素が含まれる場合もあります。 同じテンプレートを1ページで複数回使用することもできます。 このため、スタイルとテンプレートは、スタイルまたはテンプレートが適用されているオブジェクトツリー内の任意の場所に関係なく、独自の XAML 名前スコープを定義します。  
  
 次に例を示します。  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 ここでは、同じテンプレートが2つの異なるボタンに適用されます。 テンプレートに個別の xaml 名前スコープがない場合`TheBorder` 、テンプレートで使用される名前によって、xaml 名前スコープで名前の競合が発生します。 テンプレートの各インスタンス化には独自の XAML 名前スコープがあるため、この例では、インスタンス化されたテンプレートの XAML 名前スコープには名前が1つだけ含まれます。  
  
 また、スタイルは独自の XAML 名前スコープも定義します。これは、ストーリーボードの一部に特定の名前を割り当てることができるようにするためです。 これらの名前を使用すると、コントロールのカスタマイズの一部としてテンプレートを再定義した場合でも、その名前の要素を対象とするコントロール固有の動作が有効になります。  
  
 個別の XAML 名前スコープがあるため、テンプレート内の名前付き要素を検索する方が、ページ内でテンプレート化されていない名前付き要素を見つけるよりも困難です。 まず、テンプレートが適用されているコントロールの<xref:System.Windows.Controls.Control.Template%2A>プロパティ値を取得して、適用するテンプレートを決定する必要があります。 次に、テンプレートバージョンの<xref:System.Windows.FrameworkTemplate.FindName%2A>を呼び出して、テンプレートが適用されたコントロールを2番目のパラメーターとして渡します。  
  
 コントロールの作成者であり、適用されるテンプレート内の特定の名前付き要素が、コントロール自体で定義されている動作のターゲットである場合は、コントロールの<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>実装コードからメソッドを使用できます。 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>メソッドは保護されているので、コントロールの作成者だけがアクセスできます。  
  
 テンプレート内から作業していて、テンプレートが適用されている XAML 名前スコープにアクセスする必要がある場合は<xref:System.Windows.FrameworkElement.TemplatedParent%2A>、の値を<xref:System.Windows.FrameworkElement.FindName%2A>取得し、そこでを呼び出します。 テンプレート内での作業の例として、適用されるテンプレートの要素からイベントが発生するイベントハンドラーの実装を記述する場合があります。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名前スコープと名前関連 Api  
 <xref:System.Windows.FrameworkElement>、、 <xref:System.Windows.FrameworkElement.RegisterName%2A> および<xref:System.Windows.FrameworkElement.UnregisterName%2A>メソッド。 <xref:System.Windows.FrameworkElement.FindName%2A> これらのメソッドを呼び出すオブジェクトが XAML 名前スコープを所有している場合、メソッドは、関連する XAML 名前スコープのメソッドを呼び出します。 それ以外の場合は、親要素が XAML 名前スコープを所有しているかどうかがチェックされ、xaml 名前スコープが見つかるまで、このプロセスが再帰的に繰り返されます (XAML プロセッサの動作により、ルートに XAML 名前スコープがあることが保証されます)。 <xref:System.Windows.FrameworkContentElement>には類似した動作があります<xref:System.Windows.FrameworkContentElement>が、では XAML 名前スコープが存在しないという例外があります。 メソッドはに<xref:System.Windows.FrameworkContentElement>存在するため、呼び出しを最終的に<xref:System.Windows.FrameworkElement>親要素に転送できます。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>は、新しい XAML 名前スコープを既存のオブジェクトにマップするために使用されます。 XAML 名前スコープ<xref:System.Windows.NameScope.SetNameScope%2A>をリセットまたはクリアするために複数回呼び出すことができますが、これは一般的な使用方法ではありません。 また、 <xref:System.Windows.NameScope.GetNameScope%2A>は通常、コードから使用されません。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名前スコープの実装  
 次のクラスは<xref:System.Windows.Markup.INameScope> 、直接を実装します。  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>XAML 名または名前スコープを使用しません。キーは、ディクショナリの実装であるため、代わりにキーを使用します。 を実装<xref:System.Windows.ResourceDictionary> <xref:System.Windows.Markup.INameScope>する唯一の理由は、ユーザーコードに対して例外を発生させることができるためです。これは、 <xref:System.Windows.ResourceDictionary>実際の xaml 名前スコープとがキーを処理する方法と、xaml 名前スコープがに適用されないことを保証するために役立ちます。<xref:System.Windows.ResourceDictionary>親要素別。  
  
 <xref:System.Windows.FrameworkTemplate>および<xref:System.Windows.Style>は<xref:System.Windows.Markup.INameScope> 、明示的なインターフェイス定義を通じて実装します。 明示的な実装では、これらの xaml 名前スコープが<xref:System.Windows.Markup.INameScope>インターフェイスを介してアクセスされるときに、従来の動作を実行できます。これは、xaml 名前スコープが内部プロセスによって[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]伝達される方法です。 ただし、明示的なインターフェイス定義はとの従来の API サーフェイス<xref:System.Windows.FrameworkTemplate>の<xref:System.Windows.Style>一部ではありません。これ<xref:System.Windows.Markup.INameScope>は、 <xref:System.Windows.FrameworkTemplate>と<xref:System.Windows.Style>のメソッドを直接呼び出す必要がなく、代わりに他の api を使用するためです。<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>など。  
  
 次のクラスは、 <xref:System.Windows.NameScope?displayProperty=nameWithType>ヘルパークラスを使用し、 <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>添付プロパティを使用してその xaml 名前スコープの実装に接続することによって、独自の xaml 名前スコープを定義します。  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>関連項目

- [XAML 名前空間および WPF XAML の名前空間の割り当て](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)
