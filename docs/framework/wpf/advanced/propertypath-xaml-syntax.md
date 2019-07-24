---
title: PropertyPath の XAML 構文
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: deebdb690a6ba831730701de2608089af2d6bdfd
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401664"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath の XAML 構文

オブジェクト<xref:System.Windows.PropertyPath>では、 <xref:System.Windows.PropertyPath>型を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]値として受け取るさまざまなプロパティを設定するための複雑なインライン構文がサポートされています。 このトピックでは<xref:System.Windows.PropertyPath> 、バインドとアニメーションの構文に適用される構文について説明します。

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>PropertyPath を使用する場所

<xref:System.Windows.PropertyPath>は、いくつか[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の機能で使用される共通のオブジェクトです。 共通<xref:System.Windows.PropertyPath>のを使用してプロパティパス情報を伝達する場合で<xref:System.Windows.PropertyPath>も、が型として使用される各機能領域の使用方法は異なります。 そのため、機能ごとに構文を説明する方が実際的です。

主に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、 <xref:System.Windows.PropertyPath>はを使用して、オブジェクトのデータソースのプロパティを走査するためのオブジェクトモデルのパスを記述し、対象となるアニメーションのターゲットパスを記述します。

など<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType>の一部のスタイルおよびテンプレートプロパティは、 <xref:System.Windows.PropertyPath>、一見、に似た修飾プロパティ名を受け取ります。 ただし<xref:System.Windows.PropertyPath>、これは真実ではありません。これは修飾*所有者です。* WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサによって有効にされるプロパティ文字列形式の使用は、の<xref:System.Windows.DependencyProperty>型コンバーターと組み合わせて使用されます。

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>データ バインディングにおけるオブジェクトの PropertyPath

データ バインディングは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能であり、依存関係プロパティのターゲット値にバインドできます。 ただし、このようなデータ バインディングのソースが依存関係プロパティである必要はなく、適切なデータ プロバイダーで認識される任意のプロパティ型でかまいません。 プロパティパスは、共通言語ランタイム<xref:System.Windows.Data.ObjectDataProvider>(CLR) オブジェクトとそのプロパティからバインディングソースを取得するために使用される、特にに使用されます。

[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]にはを使用<xref:System.Windows.PropertyPath> <xref:System.Windows.Data.Binding.Path%2A> しないため、へのデータバインディングではが使用されないことに注意<xref:System.Windows.Data.Binding>してください。 代わりに、を使用<xref:System.Windows.Data.Binding.XPath%2A>して、データ[!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)]のに有効な XPath 構文を指定します。 <xref:System.Windows.Data.Binding.XPath%2A>も文字列として指定されていますが、ここには記載されていません。「 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。

データ バインディングにおけるプロパティ パスを理解するうえで鍵となるのは、個々のプロパティ値をバインドの対象にすることも、リストまたはコレクションを使用するターゲット プロパティにバインドすることもできるということです。 コレクション内のデータ項目の数に応じて<xref:System.Windows.Controls.ListBox>拡張されるをバインドする場合などにコレクションをバインドする場合、プロパティパスは個別のコレクションアイテムではなく、コレクションオブジェクトを参照する必要があります。 データバインディングエンジンは、データソースとして使用されるコレクションをバインディングターゲットの型に自動的に一致させます。これに<xref:System.Windows.Controls.ListBox>より、に項目配列を設定するなどの動作が行われます。

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>データ コンテキストとしての直接のオブジェクト上の単一のプロパティ

```xml
<Binding Path="propertyName" .../>
```

*propertyName*は、現在<xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Data.Binding.Path%2A>ので使用されているプロパティの名前に解決される必要があります。 バインドがソースを更新する場合、そのプロパティは読み書き可能であり、ソース オブジェクトは変更可能である必要があります。

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>データ コンテキストとしての直接のオブジェクト上の単一のインデクサー

```xml
<Binding Path="[key]" .../>
```

`key` には、ディクショナリまたはハッシュ テーブルに対する型指定されたインデックス、または配列の整数インデックスを指定する必要があります。 また、キーの値は、適用先のプロパティに直接バインドできる型である必要があります。 たとえば、文字列キーと文字列値を含むハッシュテーブルをこの方法で使用して、 <xref:System.Windows.Controls.TextBox>のテキストにバインドすることができます。 キーがコレクションまたはサブインデックスを指す場合は、この構文を使用して、ターゲット コレクション プロパティにバインドできます。 それ以外の場合は、`<Binding Path="[key].propertyName" .../>` などの構文を通じて、特定のプロパティを参照する必要があります。

必要に応じて、インデックスの型を指定できます。 インデックス付きプロパティパスのこの側面の詳細について<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>は、「」を参照してください。

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>複数プロパティ (間接的なプロパティのターゲット設定)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName`は、現在<xref:System.Windows.FrameworkElement.DataContext%2A>ののプロパティの名前に解決される必要があります。 パス プロパティ `propertyName` と `propertyName2` は、リレーションシップ内に存在する任意のプロパティにすることができます。`propertyName2` は、`propertyName` の値である型に存在するプロパティです。

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>添付または型修飾された単一のプロパティ

```xml
<object property="(ownerType.propertyName)" .../>
```

かっこは、内の<xref:System.Windows.PropertyPath>このプロパティを部分修飾を使用して構築する必要があることを示しています。 XML 名前空間を使用して、適切なマッピングを含む型を検出できます。 は`ownerType` 、各アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣言を通じて、プロセッサがアクセスできる型を検索します。 ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間にマップされた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。  `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。 この構文は、通常、次のいずれかの場合に使用されます。

- 指定されたターゲット型を持たないスタイルまたはテンプレート内の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でパスが指定されている場合。 通常、これ以外のケースでの修飾子の使用は無効です。スタイルやテンプレート以外のケースでは、プロパティは型ではなくインスタンス上に存在します。

- プロパティが添付プロパティの場合。

- 静的プロパティにバインドしている場合。

ストーリーボードターゲットとして使用するには`propertyName` 、とし<xref:System.Windows.DependencyProperty>て指定されたプロパティがである必要があります。

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>ソースの走査 (コレクションの階層へのバインド)

```xml
<object Path="propertyName/propertyNameX" .../>
```

この構文で、/ は階層的なデータ ソース オブジェクト内を移動するために使用されます。また、/ 文字を連続で使用することによる階層内での複数ステップの移動がサポートされています。 ソースの走査は現在のレコード ポインター位置に対応しており、これはデータをビューの UI と同期することによって決定されます。 階層的なデータ ソース オブジェクトのバインドおよびデータ バインディングにおける現在のレコード ポインターの概念の詳細については、「[階層データでマスター詳細パターンを使用する](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」または「[データ バインディングの概要](../data/data-binding-overview.md)」を参照してください。

> [!NOTE]
> この構文は、一見すると [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] に似ています。 データソース[!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A>にバインドするための true 式は、値として使用されず、相互排他的なプロパティに使用する必要があります。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]

### <a name="collection-views"></a>コレクション ビュー

名前付きコレクション ビューを参照するには、コレクション ビュー名の前にハッシュ記号 (`#`) を付けます。

### <a name="current-record-pointer"></a>現在のレコード ポインター

コレクション ビューまたはマスター詳細データ バインディング シナリオの現在のレコード ポインターを参照するには、パス文字列の先頭にスラッシュ (`/`) を追加します。 スラッシュより後ろのパスは、現在のレコード ポインターから開始して走査されます。

### <a name="multiple-indexers"></a>複数のインデクサー

```xaml
<object Path="[index1,index2...]" .../>
```

または

```xaml
<object Path="propertyName[index,index2...]" .../>
```

あるオブジェクトが複数のインデクサーをサポートする場合、それらのインデクサーは、配列参照構文のように、順番に指定できます。 該当のオブジェクトは、現在のコンテキスト、または複数のインデックス オブジェクトが含まれるプロパティの値です。

既定では、インデクサー値は、基になるオブジェクトの特性を使用して型指定されます。 必要に応じて、インデックスの型を指定できます。 インデクサーの入力の詳細について<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>は、「」を参照してください。

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>構文の混合

上記の各構文は、混在させることができます。 たとえば、次に示すのは、オブジェクトの`ColorGrid` <xref:System.Windows.Media.SolidColorBrush>ピクセルグリッド配列を含むプロパティの特定の x、y にある色へのプロパティパスを作成する例です。

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>プロパティ パス文字列のエスケープ

特定のビジネス オブジェクトでは、正しく解析するために、プロパティ パス文字列にエスケープ シーケンスが必要な場合があります。 このような文字の多くには、通常ビジネス オブジェクトを定義するために使用される言語において、名前付けの相互作用に関する同様の問題があるため、エスケープが必要になることはほとんどありません。

- インデクサー ([ ]) 内では、キャレット文字 (^) は次の文字をエスケープします。

- XML 言語定義で特別な意味を持つ特定の文字を (XML エンティティを使用して) エスケープする必要があります。 文字 "&" をエスケープするには、`&` を使用します。 終了タグ ">" をエスケープするには、`>` を使用します。

- マークアップ拡張機能の処理に関する WPF XAML パーサーの動作で特別な意味を持つ文字を、(バックスラッシュ `\` を使用して) エスケープする必要があります。

  - バックスラッシュ (`\`) は、それ自体がエスケープ文字です。

  - 等号 (`=`) は、プロパティ名とプロパティ値を区切ります。

  - コンマ (`,`) は、複数のプロパティを区切ります。

  - 右中かっこ (`}`) は、マークアップ拡張機能の終了を示します。

> [!NOTE]
> 厳密に言うと、これらのエスケープはストーリーボードのプロパティ パスに役立ちますが、通常は既存の WPF オブジェクトのオブジェクト モデルを走査するので、エスケープは不要です。

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>アニメーション ターゲットの PropertyPath

アニメーションの target プロパティは、 <xref:System.Windows.Freezable>またはプリミティブ型のいずれかを受け取る依存関係プロパティである必要があります。 ただし、型のターゲット プロパティと最終的なアニメーション プロパティは異なるオブジェクト上に存在できます。 アニメーションの場合は、プロパティ パスを使用して、プロパティ値内のオブジェクトとプロパティのリレーションシップを走査することによって、名前付きのアニメーション ターゲット オブジェクトのプロパティと目的のターゲット アニメーション プロパティの間の接続が定義されます。

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>アニメーションに関するオブジェクトとプロパティの一般的な注意事項

一般的なアニメーションの概念の詳細については、「[ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)」および「[アニメーションの概要](../graphics-multimedia/animation-overview.md)」を参照してください。

アニメーション化する値の型またはプロパティは、 <xref:System.Windows.Freezable>型またはプリミティブである必要があります。 パスを開始するプロパティは、指定さ<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>れた型に存在する依存関係プロパティの名前に解決される必要があります。

既に固定されているを<xref:System.Windows.Freezable>アニメーション化するための複製をサポートする<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>に<xref:System.Windows.FrameworkElement>は、に<xref:System.Windows.FrameworkContentElement>よって指定されたオブジェクトがまたは派生クラスである必要があります。

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>ターゲット オブジェクト上の単一プロパティ

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName`は、指定さ<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>れた型に存在する依存関係プロパティの名前に解決される必要があります。

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>間接的なプロパティのターゲット設定

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName`は、 <xref:System.Windows.Freezable>値型または指定された<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型に存在するプリミティブであるプロパティである必要があります。

`propertyName2` は、`propertyName` の値であるオブジェクトに存在する依存関係プロパティの名前である必要があります。 言い換えると、 `propertyName2`は、である型`propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>の依存関係プロパティとして存在する必要があります。

適用されるスタイルとテンプレートにより、アニメーションの間接的なターゲット設定が必要です。 アニメーションを対象とするには、ターゲットオブジェクト<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>にが必要です。この名前は、 [x:Name](../../xaml-services/x-name-directive.md)または<xref:System.Windows.FrameworkElement.Name%2A>によって確立されます。 テンプレート要素とスタイル要素にも名前を付けることができますが、これらの名前はスタイルとテンプレートの名前スコープ内でのみ有効です。 (テンプレートとスタイルで名前スコープがアプリケーションマークアップと共有された場合、名前を一意にすることはできません。 スタイルとテンプレートは、文字どおりインスタンス間で共有され、重複する名前が perpetuate ます。)このため、アニメーション化する要素の個々のプロパティがスタイルやテンプレートに基づく場合は、スタイル テンプレートに基づかない、名前付きの要素インスタンスで操作を開始し、スタイルまたはテンプレートのビジュアル ツリーに対象を移動し、アニメーション化する目的のプロパティにアクセスします。

たとえば、 <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Media.Brush>のプロパティ<xref:System.Windows.Media.SolidColorBrush>は、テーマテンプレートに由来する完全な (実際は) です。 <xref:System.Windows.Controls.Panel> を<xref:System.Windows.Media.Brush>完全にアニメーション化するには、BrushAnimation (おそらくすべて<xref:System.Windows.Media.Brush>の型につき1つ) である必要があり、そのような型は存在しません。 ブラシをアニメーション化するには、代わりに特定<xref:System.Windows.Media.Brush>の型のプロパティをアニメーション化します。 にを適用<xref:System.Windows.Media.SolidColorBrush.Color%2A>するに<xref:System.Windows.Media.SolidColorBrush>は<xref:System.Windows.Media.Animation.ColorAnimation> 、からにアクセスする必要があります。 この例のプロパティ パスは `Background.Color` です。

<a name="attachedanim"></a>

### <a name="attached-properties"></a>アタッチされるプロパティ

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

かっこは、内の<xref:System.Windows.PropertyPath>このプロパティを部分修飾を使用して構築する必要があることを示しています。 XML 名前空間を使用して型を検出できます。 は`ownerType` 、各アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣言を通じて、プロセッサがアクセスできる型を検索します。 ほとんどのアプリケーションは、[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間にマップされた既定の XML 名前空間を持ちます。そのため、プレフィックスは通常、カスタム型や、名前空間の外部の型に限って必要です。 `propertyName` は、`ownerType` に存在するプロパティの名前に解決される必要があります。 として`propertyName`指定された<xref:System.Windows.DependencyProperty>プロパティは、である必要があります。 添付プロパティ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はすべて依存関係プロパティとして実装されているので、この問題はカスタム添付プロパティの場合にのみ問題になります。

<a name="indexanim"></a>

### <a name="indexers"></a>インデクサー

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

ほとんどの依存関係<xref:System.Windows.Freezable>プロパティまたは型はインデクサーをサポートしていません。 そのため、アニメーション パス内でインデクサーを使用するのは、名前付きターゲット上でチェーンを開始するプロパティと、最終的にアニメーション化されるプロパティの間の中間位置に限られます。 提供される構文の中で、これは `propertyName2` です。 たとえば、中間プロパティがなどのプロパティパス<xref:System.Windows.Media.TransformGroup> `RenderTransform.Children[1].Angle`で、などのコレクションである場合、インデクサーの使用が必要になることがあります。

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>コード内の PropertyPath

の<xref:System.Windows.PropertyPath> <xref:System.Windows.PropertyPath>構築方法を含むのコードの使用方法については、「」のリファレンストピックで説明されています。 <xref:System.Windows.PropertyPath>

一般に、 <xref:System.Windows.PropertyPath>は2つの異なるコンストラクターを使用するように設計されています。1つはバインディングの使用と最も単純なアニメーションの用途用、もう1つは複雑なアニメーションの使用用です。 バインディングの使用に署名を使用します。この場合、オブジェクトは文字列です。<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> 1ステップのアニメーションパスでは、オブジェクトがであると<xref:System.Windows.DependencyProperty>いう署名を使用します。<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> 複雑な<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29>アニメーションの場合は、署名を使用します。 後者のコンストラクターでは、先頭のパラメーター用のトークン文字列と、トークン文字列内の位置に設定されるオブジェクトの配列を使用して、プロパティ パスのリレーションシップを定義します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.PropertyPath>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [ストーリーボードの概要](../graphics-multimedia/storyboards-overview.md)
