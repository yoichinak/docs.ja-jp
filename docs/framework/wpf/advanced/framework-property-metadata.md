---
title: フレームワーク プロパティ メタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964216"
---
# <a name="framework-property-metadata"></a>フレームワーク プロパティ メタデータ
フレームワーク プロパティ メタデータのオプションは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アーキテクチャの WPF フレームワーク レベルにあると見なされるオブジェクト要素のプロパティに対して報告されます。 一般に、WPF フレームワークレベルの指定では、表示、データバインディング、プロパティシステムの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]調整などの機能がプレゼンテーション api と実行可能ファイルによって処理されます。 フレームワーク プロパティ メタデータがこれらのシステムによって照会されて、特定の要素プロパティに対する機能固有の特性が決まります。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」トピックを通読していることを前提としています。 また、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を読んでいる必要もあります。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>フレームワーク プロパティ メタデータによる通知内容  
 フレームワーク プロパティ メタデータは、次のように分類できます。  
  
- 要素 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>) に影響を与えるレポートレイアウトプロパティ。 プロパティがそれぞれの側面に影響する場合は、メタデータにこれらのフラグを設定できます<xref:System.Windows.FrameworkElement.MeasureOverride%2A> 。また、クラスの<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドを実装 / して、特定のレンダリング動作と情報をレイアウトに提供することもできます。system. 通常、そのような実装では、依存関係プロパティのメタデータでこれらのレイアウト プロパティのいずれかが true であると、プロパティの無効化があるかどうかがチェックされます。無効化があった場合にのみ、新しいレイアウト パスの要求が必要となります。  
  
- 要素の親要素 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>) に影響を与えるレポートレイアウトプロパティ。 これらのフラグが既定で設定される例<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>と<xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>して、とがあります。  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>。 既定では、依存関係プロパティは値を継承しません。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>継承の経路をビジュアルツリーにも移動できるようにします。これは、いくつかのコントロールの複合シナリオに必要です。  
  
    > [!NOTE]
    > プロパティ値のコンテキストにおける "継承" という用語は、依存関係プロパティに固有の事項を意味します。つまり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムの WPF フレームワーク レベルの機能によって、実際の依存関係プロパティ値を子要素が親要素から継承できることを意味します。 派生型を通じたマネージド コードの型およびメンバーの継承とは直接関係はありません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
- レポートデータバインディング特性 (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>)。 既定では、フレームワークの依存関係プロパティは、一方向のバインディング動作を持つデータ バインディングをサポートします。 データバインディングを無効にすることもできます (柔軟性と拡張性を目的としているため、既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の api ではこのようなプロパティの例は多数ありません)。 コンポーネント間でコントロールの動作を関連付けるプロパティ (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>など) や、ユーザーにとって双方向のバインディングが一般的で期待されるシナリオであるプロパティ (<xref:System.Windows.Controls.TextBox.Text%2A>が例) に対して、バインディングを双方向に設定することもできます。 データ バインディング関連のメタデータを変更した場合に影響を受けるのは既定値だけです。この既定値は、バインディングごとにいつでも変更できます。 バインディング モードおよびバインディング全般の詳細については、「[データ バインドの概要](../data/data-binding-overview.md)」を参照してください。  
  
- ジャーナリングをサポートするアプリケーションまたはサービスによってプロパティをジャーナル<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>処理する必要があるかどうかを報告する ()。 一般的な要素に対しては、ジャーナリングは既定で有効になりませんが、特定のユーザー入力コントロールに対しては選択的に有効になります。 これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のジャーナリングの実装を含む、ジャーナリング サービスによって読み取られるプロパティです。通常は、複数のナビゲーション ステップにわたって永続化する必要があるユーザー コントロール (一覧におけるユーザー選択など) に設定します。 ジャーナリングの詳細については、「[ナビゲーションの概要](../app-development/navigation-overview.md)」を参照してください。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata の読み取り  
 上にリンクされた各プロパティは、が直接<xref:System.Windows.FrameworkPropertyMetadata>の基底クラス<xref:System.Windows.UIPropertyMetadata>に追加する特定のプロパティです。 これらのプロパティの既定値はいずれも `false` です。 これらのプロパティの値がわかっているプロパティのメタデータ要求では、返されたメタデータを<xref:System.Windows.FrameworkPropertyMetadata>にキャストし、必要に応じて個々のプロパティの値を確認する必要があります。  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>メタデータの指定  
 新しい依存関係プロパティの登録にメタデータを適用するために新しいメタデータインスタンスを作成する場合、使用するメタデータクラスを選択できます<xref:System.Windows.PropertyMetadata> 。これには、基本<xref:System.Windows.FrameworkPropertyMetadata>クラスまたはその他の派生クラス (など) があります。 一般に、プロパティにプロパティ<xref:System.Windows.FrameworkPropertyMetadata>システムおよびレイアウトやデータバインディングなどの関数と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の相互作用がある場合は、特にを使用する必要があります。 より高度なシナリオを実現するためのもう<xref:System.Windows.FrameworkPropertyMetadata> 1 つのオプションは、から派生させ、メンバーに追加情報を含む独自のメタデータレポートクラスを作成することです。 または、また<xref:System.Windows.PropertyMetadata>は<xref:System.Windows.UIPropertyMetadata>を使用して、実装の機能のサポートレベルを伝達することもできます。  
  
 既存のプロパティ (<xref:System.Windows.DependencyProperty.AddOwner%2A>また<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>はを呼び出す場合) の場合は、常に元の登録で使用されるメタデータ型でオーバーライドする必要があります。  
  
 <xref:System.Windows.FrameworkPropertyMetadata>インスタンスを作成する場合は、次の2つの方法で、フレームワークのプロパティ特性を伝える特定のプロパティの値をそのメタデータに設定できます。  
  
1. パラメーターを`flags`許可するコンストラクターシグネチャを使用します。<xref:System.Windows.FrameworkPropertyMetadata> このパラメーターには、 <xref:System.Windows.FrameworkPropertyMetadataOptions>列挙フラグのすべての必要な結合値を入力する必要があります。  
  
2. パラメーターを`flags`指定せずにいずれかの署名を使用し、必要な特性の`true`変更ごとにに対して<xref:System.Windows.FrameworkPropertyMetadata>各レポートのブール型プロパティをに設定します。 この場合、この依存関係プロパティを持つすべての要素の構築前に、これらのプロパティを設定する必要があります。`flags` パラメーターを使用せずに引き続きメタデータを読み込めるよう、これらのブール型プロパティは読み書き可能な状態ですが、プロパティの使用前にメタデータを事実上シールする必要があります。 そのため、メタデータの要求後にこれらのプロパティを設定しようとすると、無効な操作となります。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>フレームワーク プロパティ メタデータのマージ動作  
 フレームワーク プロパティ メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>マージされます。 新しい<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>を追加すると、そのコールバックがメタデータに格納されます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>値はメタデータで指定された最も近い先祖から参照として昇格されます。  
  
- の実際の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>プロパティシステムの動作では、階層内のすべてのメタデータ所有者の実装が保持され、テーブルに追加されます。これは、プロパティシステムによって、最も深い派生クラスのコールバックが行われるという順序で実行されます。最初に呼び出されます。 継承されたコールバックは、それらをメタデータに配置したクラスによって所有されていると見なされ、それぞれ 1 回だけ実行されます。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>が置き換えられます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.DefaultValue%2A>値は、メタデータで指定された最も近い先祖から取得されます。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>実装は置き換えられます。 新しい<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>を追加すると、そのコールバックがメタデータに格納されます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>値はメタデータで指定された最も近い先祖から参照として昇格されます。  
  
- プロパティシステムの動作は、直接の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>メタデータ内ののみが呼び出されることを示します。 階層内の他<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>の実装への参照は保持されません。  
  
- 列挙体の<xref:System.Windows.FrameworkPropertyMetadataOptions>フラグは、ビットごとの or 演算として結合されます。  を指定<xref:System.Windows.FrameworkPropertyMetadataOptions>した場合、元のオプションは上書きされません。  オプションを変更するには、に<xref:System.Windows.FrameworkPropertyMetadata>対応するプロパティを設定します。 たとえば、元<xref:System.Windows.FrameworkPropertyMetadata>のオブジェクトでフラグが<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>設定されている場合は、を<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>に`false`設定することによって変更できます。  
  
 この動作はによっ<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>て実装され、派生メタデータクラスでオーバーライドできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
