---
title: PropertyPath の XAML 構文
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 25214a3c177975505713a444b69a7006c0fd523f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363515"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath の XAML 構文
<xref:System.Windows.PropertyPath>オブジェクトがサポートする、複雑なインライン[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]構文を使用するさまざまなプロパティを設定するため、<xref:System.Windows.PropertyPath>型を値として。 このトピックの「ドキュメント、<xref:System.Windows.PropertyPath>バインディングとアニメーション構文に適用される構文です。  
    
  
<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>PropertyPath を使用する場所  
 <xref:System.Windows.PropertyPath> いくつかで使用される共通オブジェクトは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]機能します。 一般的な使用に関係なく<xref:System.Windows.PropertyPath>プロパティ パス情報を伝達するために使用法は、各機能領域で<xref:System.Windows.PropertyPath>によって変化する型に使用されます。 そのため、機能ごとに構文を説明する方が実際的です。  
  
 主に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用<xref:System.Windows.PropertyPath>オブジェクト モデルのオブジェクト データ ソースのプロパティを走査するパスを記述して、ターゲット アニメーションのターゲット パスについて説明します。  
  
 などのスタイルとテンプレート プロパティ<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType>よう表面的なプロパティの修飾名を取得、<xref:System.Windows.PropertyPath>します。 これは、true ではありませんが、 <xref:System.Windows.PropertyPath>; これは、修飾*owner.property*文字列の形式の使用法、WPF によって有効になっている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの型コンバーターと組み合わせて<xref:System.Windows.DependencyProperty>します。  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>データ バインディングにおけるオブジェクトの PropertyPath  
 データ バインディングは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能であり、依存関係プロパティのターゲット値にバインドできます。 ただし、このようなデータ バインディングのソースが依存関係プロパティである必要はなく、適切なデータ プロバイダーで認識される任意のプロパティ型でかまいません。 プロパティのパスは特にため、 <xref:System.Windows.Data.ObjectDataProvider>、バインディング ソースからの取得に使用される[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクトとそのプロパティです。  
  
 そのデータ バインディングに注意してください[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]は使いません<xref:System.Windows.PropertyPath>は使用されないため、<xref:System.Windows.Data.Binding.Path%2A>で、<xref:System.Windows.Data.Binding>します。 使用する代わりに、<xref:System.Windows.Data.Binding.XPath%2A>に有効な XPath 構文を指定し、[!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)]データ。 <xref:System.Windows.Data.Binding.XPath%2A> 文字列としても指定されますが、ここでは文書化されていません。参照してください[XMLDataProvider と XPath クエリを使用して XML データにバインド](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)します。  
  
 データ バインディングにおけるプロパティ パスを理解するうえで鍵となるのは、個々のプロパティ値をバインドの対象にすることも、リストまたはコレクションを使用するターゲット プロパティにバインドすることもできるということです。 バインド インスタンスのコレクションをバインドする場合、<xref:System.Windows.Controls.ListBox>が、コレクション内にデータ項目の数によって拡張される、プロパティのパスは、個々 のコレクション アイテムのコレクション オブジェクトを参照する必要があります。 データ バインディング エンジンは、データ ソースのバインディング ターゲットの型に自動的に、設定などの動作として使用されるコレクションに一致する<xref:System.Windows.Controls.ListBox>項目配列。  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>データ コンテキストとしての直接のオブジェクト上の単一のプロパティ  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName*現在内にあるプロパティの名前を解決する必要があります<xref:System.Windows.FrameworkElement.DataContext%2A>の<xref:System.Windows.Data.Binding.Path%2A>使用量。 バインドがソースを更新する場合、そのプロパティは読み書き可能であり、ソース オブジェクトは変更可能である必要があります。  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>データ コンテキストとしての直接のオブジェクト上の単一のインデクサー  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` には、ディクショナリまたはハッシュ テーブルに対する型指定されたインデックス、または配列の整数インデックスを指定する必要があります。 また、キーの値は、適用先のプロパティに直接バインドできる型である必要があります。 たとえば、文字列キーと文字列値を格納するハッシュ テーブルはこのように使用するのテキストにバインドする、<xref:System.Windows.Controls.TextBox>します。 キーがコレクションまたはサブインデックスを指す場合は、この構文を使用して、ターゲット コレクション プロパティにバインドできます。 それ以外の場合は、`<Binding Path="[key].propertyName" .../>` などの構文を通じて、特定のプロパティを参照する必要があります。  
  
 必要に応じて、インデックスの型を指定できます。 詳細については、インデックス付きプロパティのパスのこの側面は、<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>を参照してください。  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>複数プロパティ (間接的なプロパティのターゲット設定)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` 現在ではプロパティの名前を解決する必要があります<xref:System.Windows.FrameworkElement.DataContext%2A>します。 パス プロパティ `propertyName` と `propertyName2` は、リレーションシップ内に存在する任意のプロパティにすることができます。`propertyName2` は、`propertyName` の値である型に存在するプロパティです。  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>添付または型修飾された単一のプロパティ  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 いることを示す、かっこ内のこのプロパティを<xref:System.Windows.PropertyPath>部分修飾を使用して構築する必要があります。 XML 名前空間を使用して、適切なマッピングを含む型を検出できます。 `ownerType`型を検索、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサからへのアクセス、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>各アセンブリで宣言します。 ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間にマップされた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。  `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。 この構文は、通常、次のいずれかの場合に使用されます。  
  
-   指定されたターゲット型を持たないスタイルまたはテンプレート内の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でパスが指定されている場合。 通常、これ以外のケースでの修飾子の使用は無効です。スタイルやテンプレート以外のケースでは、プロパティは型ではなくインスタンス上に存在します。  
  
-   プロパティが添付プロパティの場合。  
  
-   静的プロパティにバインドしている場合。  
  
 として指定されるプロパティのストーリー ボード ターゲットとして使用して、`propertyName`必要があります、<xref:System.Windows.DependencyProperty>します。  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>ソースの走査 (コレクションの階層へのバインド)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 この構文で、/ は階層的なデータ ソース オブジェクト内を移動するために使用されます。また、/ 文字を連続で使用することによる階層内での複数ステップの移動がサポートされています。 ソースの走査は現在のレコード ポインター位置に対応しており、これはデータをビューの UI と同期することによって決定されます。 階層的なデータ ソース オブジェクトのバインドおよびデータ バインディングにおける現在のレコード ポインターの概念の詳細については、「[階層データでマスター詳細パターンを使用する](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」または「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。  
  
> [!NOTE]
>  この構文は、一見すると [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] に似ています。 真の[!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]にバインドするための式、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]としてデータ ソースが使用されていない、<xref:System.Windows.Data.Binding.Path%2A>値し、相互に排他的に使用する代わりに<xref:System.Windows.Data.Binding.XPath%2A>プロパティ。  
  
### <a name="collection-views"></a>コレクション ビュー  
 名前付きコレクション ビューを参照するには、コレクション ビュー名の前にハッシュ記号 (`#`) を付けます。  
  
### <a name="current-record-pointer"></a>現在のレコード ポインター  
 コレクション ビューまたはマスター詳細データ バインディング シナリオの現在のレコード ポインターを参照するには、パス文字列の先頭にスラッシュ (`/`) を追加します。 スラッシュより後ろのパスは、現在のレコード ポインターから開始して走査されます。  
  
### <a name="multiple-indexers"></a>複数のインデクサー  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 あるオブジェクトが複数のインデクサーをサポートする場合、それらのインデクサーは、配列参照構文のように、順番に指定できます。 該当のオブジェクトは、現在のコンテキスト、または複数のインデックス オブジェクトが含まれるプロパティの値です。  
  
 既定では、インデクサー値は、基になるオブジェクトの特性を使用して型指定されます。 必要に応じて、インデックスの型を指定できます。 インデクサーの詳細については、「<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>します。  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>構文の混合  
 上記の各構文は、混在させることができます。 特定の x、y の色にプロパティのパスを作成する例を次に、`ColorGrid`のピクセル グリッド配列を含むプロパティ<xref:System.Windows.Media.SolidColorBrush>オブジェクト。  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>プロパティ パス文字列のエスケープ  
 特定のビジネス オブジェクトでは、正しく解析するために、プロパティ パス文字列にエスケープ シーケンスが必要な場合があります。 このような文字の多くには、通常ビジネス オブジェクトを定義するために使用される言語において、名前付けの相互作用に関する同様の問題があるため、エスケープが必要になることはほとんどありません。  
  
-   インデクサー ([ ]) 内では、キャレット文字 (^) は次の文字をエスケープします。  
  
-   XML 言語定義で特別な意味を持つ特定の文字を (XML エンティティを使用して) エスケープする必要があります。 文字 "&" をエスケープするには、`&` を使用します。 終了タグ ">" をエスケープするには、`>` を使用します。  
  
-   マークアップ拡張機能の処理に関する WPF XAML パーサーの動作で特別な意味を持つ文字を、(バックスラッシュ `\` を使用して) エスケープする必要があります。  
  
    -   バックスラッシュ (`\`) は、それ自体がエスケープ文字です。  
  
    -   等号 (`=`) は、プロパティ名とプロパティ値を区切ります。  
  
    -   コンマ (`,`) は、複数のプロパティを区切ります。  
  
    -   右中かっこ (`}`) は、マークアップ拡張機能の終了を示します。  
  
> [!NOTE]
>  厳密に言うと、これらのエスケープはストーリーボードのプロパティ パスに役立ちますが、通常は既存の WPF オブジェクトのオブジェクト モデルを走査するので、エスケープは不要です。  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>アニメーション ターゲットの PropertyPath  
 アニメーションのターゲット プロパティは、依存関係プロパティを受け取るいずれかである必要があります、<xref:System.Windows.Freezable>またはプリミティブ型。 ただし、型のターゲット プロパティと最終的なアニメーション プロパティは異なるオブジェクト上に存在できます。 アニメーションの場合は、プロパティ パスを使用して、プロパティ値内のオブジェクトとプロパティのリレーションシップを走査することによって、名前付きのアニメーション ターゲット オブジェクトのプロパティと目的のターゲット アニメーション プロパティの間の接続が定義されます。  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>アニメーションに関するオブジェクトとプロパティの一般的な注意事項  
 一般的なアニメーションの概念の詳細については、「[ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)」および「[アニメーションの概要](../graphics-multimedia/animation-overview.md)」を参照してください。  
  
 値型またはアニメーション化されているプロパティはいずれかである必要があります、<xref:System.Windows.Freezable>型またはプリミティブです。 パスを開始するプロパティは、指定した上に存在する依存関係プロパティの名前に解決する必要があります<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型。  
  
 アニメーションの複製をサポートするために、<xref:System.Windows.Freezable>が既に固定されているで指定されたオブジェクト<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>必要があります、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>クラスを派生します。  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>ターゲット オブジェクト上の単一プロパティ  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` 指定した上に存在する依存関係プロパティの名前を指定する必要があります<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型。  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>間接的なプロパティのターゲット設定  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` いずれかであるプロパティにする必要があります、<xref:System.Windows.Freezable>値型または指定した上に存在するプリミティブ型<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型。  
  
 `propertyName2` は、`propertyName` の値であるオブジェクトに存在する依存関係プロパティの名前である必要があります。 つまり、`propertyName2`である型の依存関係プロパティとして存在する必要があります、 `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>します。  
  
 適用されるスタイルとテンプレートにより、アニメーションの間接的なターゲット設定が必要です。 必要があるアニメーションを対象にするため、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>によって、ターゲット オブジェクトに名前が確立されている[X:name](../../xaml-services/x-name-directive.md)または<xref:System.Windows.FrameworkElement.Name%2A>します。 テンプレートとスタイルの要素が名前を設定するが、また、その名前は、スタイルとテンプレートの名前スコープ内で有効なだけです。 (テンプレートとスタイルは、アプリケーション マークアップと名前スコープを共有するが場合、名一意ではありません。 スタイルとテンプレートのインスタンス間で共有される文字どおりと重複する名前が永続化します。)このため、アニメーション化する要素の個々のプロパティがスタイルやテンプレートに基づく場合は、スタイル テンプレートに基づかない、名前付きの要素インスタンスで操作を開始し、スタイルまたはテンプレートのビジュアル ツリーに対象を移動し、アニメーション化する目的のプロパティにアクセスします。  
  
 たとえば、<xref:System.Windows.Controls.Panel.Background%2A>のプロパティを<xref:System.Windows.Controls.Panel>がすべてでは<xref:System.Windows.Media.Brush>(実際には、 <xref:System.Windows.Media.SolidColorBrush>)、テーマ テンプレートから付属しています。 アニメーション化する、<xref:System.Windows.Media.Brush>完全には必要があります、BrushAnimation (おそらく 1 つのすべて<xref:System.Windows.Media.Brush>型)、そのような型はありません。 特定のプロパティのアニメーション代わりに、ブラシをアニメーション化する<xref:System.Windows.Media.Brush>型。 取得する必要がある<xref:System.Windows.Media.SolidColorBrush>にその<xref:System.Windows.Media.SolidColorBrush.Color%2A>を適用する、<xref:System.Windows.Media.Animation.ColorAnimation>があります。 この例のプロパティ パスは `Background.Color` です。  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>アタッチされるプロパティ  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 いることを示す、かっこ内のこのプロパティを<xref:System.Windows.PropertyPath>部分修飾を使用して構築する必要があります。 XML 名前空間を使用して型を検出できます。 `ownerType`型を検索、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサからへのアクセス、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>各アセンブリで宣言します。 ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間にマップされた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。 `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。 として指定されたプロパティ`propertyName`必要があります、<xref:System.Windows.DependencyProperty>します。 (すべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]添付プロパティは、依存関係プロパティとして実装されるので、この問題は、カスタム添付プロパティの問題になるだけです)。  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>インデクサー  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 ほとんどの依存関係プロパティまたは<xref:System.Windows.Freezable>型はインデクサーをサポートしていません。 そのため、アニメーション パス内でインデクサーを使用するのは、名前付きターゲット上でチェーンを開始するプロパティと、最終的にアニメーション化されるプロパティの間の中間位置に限られます。 提供される構文の中で、これは `propertyName2` です。 インデクサーの使用を中間プロパティがコレクションなどの場合必要あります、<xref:System.Windows.Media.TransformGroup>などのプロパティのパスで`RenderTransform.Children[1].Angle`します。  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>コード内の PropertyPath  
 コードの使用量<xref:System.Windows.PropertyPath>、構築する方法など、<xref:System.Windows.PropertyPath>のリファレンス トピックに記載されています<xref:System.Windows.PropertyPath>します。  
  
 一般に、<xref:System.Windows.PropertyPath>バインディングでの使用と最も単純なアニメーションと複雑なアニメーションでの使用の 2 つの異なるコンス トラクターを使用するように設計されています。 使用して、<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>オブジェクトが文字列の使用状況をバインドするための署名。 使用して、<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>ワンステップ アニメーション パスでオブジェクトが署名、<xref:System.Windows.DependencyProperty>します。 使用して、<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29>複雑なアニメーションの署名。 後者のコンストラクターでは、先頭のパラメーター用のトークン文字列と、トークン文字列内の位置に設定されるオブジェクトの配列を使用して、プロパティ パスのリレーションシップを定義します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.PropertyPath>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)
