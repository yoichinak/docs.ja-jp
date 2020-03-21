---
title: XAML 名前スコープ
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
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186275"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名前スコープ
XAML 名前スコープは、XAML で定義されているオブジェクトを識別する概念です。 XAML 名前スコープ内の名前を使用して、オブジェクト ツリー内のオブジェクトの XAML 定義名と、そのオブジェクトのインスタンスと同等の名前の間のリレーションシップを確立できます。 通常、マネージ コード内の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 名前スコープは、XAML アプリケーションの個々の XAML ページ ルートを読み込むときに作成されます。 プログラミング オブジェクトとしての XAML 名前スコープは<xref:System.Windows.Markup.INameScope>インターフェイスによって定義され、実用的なクラス<xref:System.Windows.NameScope>によっても実装されます。  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>読み込まれた XAML アプリケーションの名前スコープ  
 より広範なプログラミングまたはコンピュータ サイエンスのコンテキストでは、プログラミングの概念には、オブジェクトへのアクセスに使用できる一意の識別子または名前の原則が含まれることがよくあります。 識別子または名前を使用するシステムの場合、名前スコープは、プロセスまたは技法が、その名前のオブジェクトが要求された場合、または識別名の一意性が適用される境界を検索する境界を定義します。 これらの一般的な原則は、XAML 名前スコープに当てはまります。 WPF では、ページが読み込まれるときに XAML ページのルート要素に XAML 名前スコープが作成されます。 ページ ルートで始まる XAML ページ内で指定された各名前は、関連する XAML 名前スコープに追加されます。  
  
 WPF XAML では、共通のルート要素である要素<xref:System.Windows.Controls.Page>(<xref:System.Windows.Window>など ) は、常に XAML 名前スコープを制御します。 マークアップ内のページの<xref:System.Windows.FrameworkElement>ルート<xref:System.Windows.FrameworkContentElement>要素またはなどの要素の場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、プロセッサは、作業 XAML<xref:System.Windows.Controls.Page>名前スコープを<xref:System.Windows.Controls.Page>提供できるように、暗黙的にルートを追加します。  
  
> [!NOTE]
> WPF ビルド アクションは、マークアップ内の要素に属性が定義`Name`されていない`x:Name`場合でも、XAML の運用環境の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]XAML 名前スコープを作成します。  
  
 XAML 名前スコープで同じ名前を 2 回使用しようとすると、例外が発生します。 分離コードを持ち、コンパイル済みアプリケーションの一部である WPF XAML の場合、最初のマークアップ コンパイル時にページに生成されたクラスを作成するときに、WPF ビルド アクションによってビルド時に例外が発生します。 ビルド アクションによってマークアップ コンパイルされない XAML の場合、XAML が読み込まれるときに、XAML 名前スコープの問題に関連する例外が発生する場合があります。 XAML デザイナーは、デザイン時に XAML 名前スコープの問題を予測する場合もあります。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>ランタイム オブジェクト ツリーへのオブジェクトの追加  
 XAML が解析される瞬間は、WPF XAML 名前スコープが作成され、定義された瞬間を表します。 そのツリーを生成した XAML が解析された時点でオブジェクト ツリーにオブジェクトを追加した場合、新しいオブジェクト`Name`の`x:Name`または 値は XAML 名前スコープの情報を自動的に更新しません。 XAML が読み込まれた後に WPF XAML 名前スコープにオブジェクトの<xref:System.Windows.Markup.INameScope.RegisterName%2A>名前を追加するには、XAML 名前スコープを定義するオブジェクト (通常は XAML ページ ルート) の適切な実装を呼び出す必要があります。 名前が登録されていない場合、追加したオブジェクトは、 などの<xref:System.Windows.FrameworkElement.FindName%2A>メソッドを通じて名前で参照できず、アニメーションのターゲット設定にはその名前を使用できません。  
  
 アプリケーション開発者にとって最も一般的なシナリオは、ページ<xref:System.Windows.FrameworkElement.RegisterName%2A>の現在のルートにある XAML 名前スコープに名前を登録するために使用することです。 <xref:System.Windows.FrameworkElement.RegisterName%2A>は、アニメーションのオブジェクトをターゲットとするストーリーボードの重要なシナリオの一部です。 詳細については、「[ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 XAML 名前<xref:System.Windows.FrameworkElement.RegisterName%2A>スコープを定義するオブジェクト以外のオブジェクトを呼び出した場合、その名前は、XAML 名前スコープ定義オブジェクトで呼び出<xref:System.Windows.FrameworkElement.RegisterName%2A>した場合と同様に、呼び出し元のオブジェクトが保持されている XAML 名前スコープに登録されます。  
  
### <a name="xaml-namescopes-in-code"></a>コード内の XAML 名前スコープ  
 コード内で XAML 名前スコープを作成して使用できます。 XAML の API と XAML 名前スコープの作成に関連する概念は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]純粋なコードの使用でも同じです。 概念と API は、一般的に部分的または完全に XAML で定義されるオブジェクト ツリー内で名前によってオブジェクトを検索できる目的で主に存在します。  
  
 XAML を読み込まずにプログラムによって作成されたアプリケーションの場合、XAML 名前スコープを定義する<xref:System.Windows.Markup.INameScope>オブジェクトは、その<xref:System.Windows.FrameworkElement>インスタンス<xref:System.Windows.FrameworkContentElement>で XAML 名前スコープの作成をサポートするために、を実装するか、または派生クラスである必要があります。  
  
 また、XAML プロセッサによって読み込まれ、処理されない要素の場合、オブジェクトの XAML 名前スコープは既定では作成または初期化されません。 後で名前を登録するオブジェクトに対して、新しい XAML 名前スコープを明示的に作成する必要があります。 XAML 名前スコープを作成するには、静的<xref:System.Windows.NameScope.SetNameScope%2A>メソッドを呼び出します。 パラメーターとして、それを所有するオブジェクトを`dependencyObject`指定し、パラメーターとして新<xref:System.Windows.NameScope.%23ctor%2A>しいコンストラクターを呼`value`び出します。  
  
 `dependencyObject`として<xref:System.Windows.NameScope.SetNameScope%2A>提供されるオブジェクトが<xref:System.Windows.Markup.INameScope>実装でない場合、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、子要素を<xref:System.Windows.FrameworkElement.RegisterName%2A>呼び出しても効果はありません。 新しい XAML 名前スコープを明示的に作成できなかった場合、 を<xref:System.Windows.FrameworkElement.RegisterName%2A>呼び出すと例外が発生します。  
  
 コードで XAML 名前スコープ API を使用する例については、「[名前スコープの定義](../graphics-multimedia/how-to-define-a-name-scope.md)」を参照してください。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>スタイルとテンプレートの XAML 名前スコープ  
 のスタイルとテンプレート[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、コンテンツを簡単に再利用し、再適用する機能を提供します。 ただし、スタイルとテンプレートには、テンプレート レベルで定義された XAML 名の要素も含まれる場合があります。 同一のテンプレートが、ページ内で複数回使われる可能性があります。 このため、スタイルとテンプレートは、スタイルまたはテンプレートが適用されるオブジェクト ツリー内の場所に関係なく、独自の XAML 名前スコープを定義します。  
  
 次の例を確認してください。  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 ここでは、同じテンプレートが 2 つの異なるボタンに適用されます。 テンプレートに個別の XAML 名前スコープがない場合、`TheBorder`テンプレートで使用される名前は、XAML 名前スコープで名前の競合を引き起こします。 テンプレートの各インスタンスは独自の XAML 名前スコープを持つため、この例の場合、インスタンス化された各テンプレートの XAML 名前スコープに、名前が必ず 1 つずつ含まれます。  
  
 スタイルは、ストーリーボードの一部が特定の名前を割り当てることができるように、独自の XAML 名前スコープも定義します。 これらの名前は、テンプレートがコントロールのカスタマイズの一部として再定義された場合でも、その名前の要素を対象とするコントロール固有の動作を有効にします。  
  
 XAML 名前スコープが異なるため、テンプレート内の名前付き要素を見つけることは、テンプレート以外の名前付き要素をページで見つけるよりも困難です。 最初に、テンプレートが適用されるコントロールのプロパティ値を<xref:System.Windows.Controls.Control.Template%2A>取得して、適用されたテンプレートを決定する必要があります。 次に、テンプレートが適用されたコントロール<xref:System.Windows.FrameworkTemplate.FindName%2A>を 2 番目のパラメーターとして渡す テンプレート バージョンを呼び出します。  
  
 コントロールの作成者で、適用されたテンプレート内の特定の名前付き要素がコントロール自体によって定義された動作のターゲットとなるという規則を生成する場合は、コントロール実装コードの<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>メソッドを使用できます。 メソッド<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>は保護されているので、コントロールの作成者だけがアクセスできます。  
  
 テンプレート内から作業していて、テンプレートが適用されている XAML 名前スコープに到達する必要がある場合は、 の<xref:System.Windows.FrameworkElement.TemplatedParent%2A>値を取得し、ここで呼<xref:System.Windows.FrameworkElement.FindName%2A>び出します。 テンプレート内での作業の例としては、適用されたテンプレートの要素からイベントが発生するイベント ハンドラーの実装を記述する場合があります。  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名前スコープと名前関連 API  
 <xref:System.Windows.FrameworkElement>には<xref:System.Windows.FrameworkElement.FindName%2A>、 <xref:System.Windows.FrameworkElement.RegisterName%2A> <xref:System.Windows.FrameworkElement.UnregisterName%2A>および メソッドがあります。 これらのメソッドを呼び出すオブジェクトが XAML 名前スコープを所有している場合、メソッドは関連する XAML 名前スコープのメソッドを呼び出します。 それ以外の場合、親要素は XAML 名前スコープを所有しているかどうかを確認し、XAML 名前スコープが見つかるまでこのプロセスは再帰的に続行されます (XAML プロセッサの動作のため、ルートに XAML 名前スコープが存在することが保証されます)。 <xref:System.Windows.FrameworkContentElement>は、XAML 名前スコープを所有しない<xref:System.Windows.FrameworkContentElement>という例外を除いて、類似した動作を持ちます。 メソッドは、呼<xref:System.Windows.FrameworkContentElement>び出しが最終的に<xref:System.Windows.FrameworkElement>親要素に転送されるように存在します。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>は、新しい XAML 名前スコープを既存のオブジェクトにマップするために使用されます。 XAML 名前<xref:System.Windows.NameScope.SetNameScope%2A>スコープをリセットまたはクリアするために複数回呼び出すことができますが、これは一般的な使用法ではありません。 また、<xref:System.Windows.NameScope.GetNameScope%2A>通常はコードからは使用されません。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名前スコープの実装  
 次のクラスは<xref:System.Windows.Markup.INameScope>直接実装します。  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>XAML 名または名前スコープを使用しません。代わりに、ディクショナリの実装であるため、キーを使用します。 実装する<xref:System.Windows.ResourceDictionary>唯一の理由<xref:System.Windows.Markup.INameScope>は、ユーザー コードに対して例外を発生させ、実際の XAML 名前スコープと<xref:System.Windows.ResourceDictionary>キーの処理方法の区別を明確にし、XAML 名前スコープが親要素<xref:System.Windows.ResourceDictionary>によって適用されないようにするためです。  
  
 <xref:System.Windows.FrameworkTemplate>を<xref:System.Windows.Style>使用<xref:System.Windows.Markup.INameScope>して、明示的なインターフェイス定義を使用して実装します。 明示的な実装では、これらの XAML 名前スコープは<xref:System.Windows.Markup.INameScope>、インターフェイスを通じてアクセスされたときに従来の動作を可能にします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] しかし、明示的なインターフェイス<xref:System.Windows.FrameworkTemplate>定義は、メソッドを<xref:System.Windows.Style><xref:System.Windows.Markup.INameScope><xref:System.Windows.FrameworkTemplate><xref:System.Windows.Style>直接呼び出す必要はほとんどなく、代わりになど<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>他の API を使用するため、 と の従来の API サーフェスの一部ではありません。  
  
 次のクラスは、ヘルパー クラスを使用し、添付<xref:System.Windows.NameScope?displayProperty=nameWithType>プロパティを通じて XAML 名前スコープの実装に接続<xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>することによって、独自の XAML 名前スコープを定義します。  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>関連項目

- [XAML 名前空間および WPF XAML の名前空間の割り当て](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name ディレクティブ](../../../desktop-wpf/xaml-services/xname-directive.md)
