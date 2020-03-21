---
title: フレームワーク プロパティ メタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186656"
---
# <a name="framework-property-metadata"></a>フレームワーク プロパティ メタデータ
フレームワーク プロパティ メタデータのオプションは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アーキテクチャの WPF フレームワーク レベルにあると見なされるオブジェクト要素のプロパティに対して報告されます。 一般に、WPF フレームワーク レベルの指定では、表示、データ バインディング、プロパティ システムの絞り込みなどの機能は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、プレゼンテーション API と実行可能ファイルによって処理されます。 フレームワーク プロパティ メタデータがこれらのシステムによって照会されて、特定の要素プロパティに対する機能固有の特性が決まります。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」を読んでいることを前提としています。 また、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を読んでいる必要もあります。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>フレームワーク プロパティ メタデータによる通知内容  
 フレームワーク プロパティ メタデータは、次のように分類できます。  
  
- 要素に影響を与えるレポート<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>レイアウト<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A><xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>プロパティ ( , ) プロパティがそれぞれの側面に影響を与える場合、およびレイアウト システムに特定の<xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>レンダリング動作と情報を提供するクラスのメソッドを実装している場合は、メタデータにこれらのフラグを設定できます。 通常、そのような実装では、依存関係プロパティのメタデータでこれらのレイアウト プロパティのいずれかが true であると、プロパティの無効化があるかどうかがチェックされます。無効化があった場合にのみ、新しいレイアウト パスの要求が必要となります。  
  
- 要素の親要素に影響を与えるレポート レイアウト<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A><xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>プロパティ ( 、) これらのフラグが既定で設定されている例としては<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>、<xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>と があります。  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. 既定では、依存関係プロパティは値を継承しません。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>継承の経路もビジュアル ツリーに移動でき、これはコントロール合成のシナリオに必要です。  
  
    > [!NOTE]
    > プロパティ値のコンテキストにおける "継承" という用語は、依存関係プロパティに固有の事項を意味します。つまり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムの WPF フレームワーク レベルの機能によって、実際の依存関係プロパティ値を子要素が親要素から継承できることを意味します。 派生型を通じたマネージド コードの型およびメンバーの継承とは直接関係はありません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
- データ バインディング特性<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>( <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>、 ) のレポートを作成します。 既定では、フレームワークの依存関係プロパティは、一方向のバインディング動作を持つデータ バインディングをサポートします。 データ バインディングのシナリオがまったくない場合は、データ バインディングを無効にできます (柔軟性と拡張性を備えた場合、既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の API にはそのようなプロパティの例はあまりありません)。 コントロールの動作をコンポーネントの部分 (例) に結び付けるプロパティのバインディングの既定値を設定するか、<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>双方向バインディングがユーザーに共通して予想されるシナリオ (<xref:System.Windows.Controls.TextBox.Text%2A>例) である場合があります。 データ バインディング関連のメタデータを変更した場合に影響を受けるのは既定値だけです。この既定値は、バインディングごとにいつでも変更できます。 バインディング モードおよびバインディング全般の詳細については、「[データ バインドの概要](../../../desktop-wpf/data/data-binding-overview.md)」を参照してください。  
  
- ジャーナリングをサポートするアプリケーションまたはサービスによって、プロパティをジャーナル処理する<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>必要があるかどうかを報告する ( ) 一般的な要素に対しては、ジャーナリングは既定で有効になりませんが、特定のユーザー入力コントロールに対しては選択的に有効になります。 これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のジャーナリングの実装を含む、ジャーナリング サービスによって読み取られるプロパティです。通常は、複数のナビゲーション ステップにわたって永続化する必要があるユーザー コントロール (一覧におけるユーザー選択など) に設定します。 ジャーナリングの詳細については、「[ナビゲーションの概要](../app-development/navigation-overview.md)」を参照してください。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata の読み取り  
 上記のリンクされた各プロパティは、その直接の基本<xref:System.Windows.FrameworkPropertyMetadata>クラス に追加される特定<xref:System.Windows.UIPropertyMetadata>のプロパティです。 これらのプロパティの既定値はいずれも `false` です。 これらのプロパティの値を知ることが重要なプロパティのメタデータ要求は、返されたメタデータを に<xref:System.Windows.FrameworkPropertyMetadata>キャストし、必要に応じて個々のプロパティの値を確認する必要があります。  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>メタデータの指定  
 メタデータを新しい依存関係プロパティ登録に適用するために新しいメタデータ インスタンスを作成する場合、使用するメタデータ クラス (基本<xref:System.Windows.PropertyMetadata>クラスまたは<xref:System.Windows.FrameworkPropertyMetadata>など一部の派生クラス) を選択できます。 一般に、 プロパティ<xref:System.Windows.FrameworkPropertyMetadata>がプロパティ システムや、レイアウトや[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]データ バインディングなどの関数と対話する場合は、特に を使用します。 より高度なシナリオの別のオプションは、メンバー<xref:System.Windows.FrameworkPropertyMetadata>に追加の情報を持つ独自のメタデータ レポート クラスを作成するから派生することです。 または、実装の<xref:System.Windows.PropertyMetadata>機能<xref:System.Windows.UIPropertyMetadata>のサポートの程度を使用するか、または伝達することができます。  
  
 既存のプロパティ<xref:System.Windows.DependencyProperty.AddOwner%2A>(<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>または呼び出し) の場合は、元の登録で使用されるメタデータ型で常にオーバーライドする必要があります。  
  
 インスタンスを作成する<xref:System.Windows.FrameworkPropertyMetadata>場合、フレームワークのプロパティ特性を伝える特定のプロパティの値をメタデータに設定するには、次の 2 つの方法があります。  
  
1. パラメーターを<xref:System.Windows.FrameworkPropertyMetadata>許可するコンストラクターシグネチャを`flags`使用します。 このパラメーターには、列挙フラグの必要な合計値をすべて入力<xref:System.Windows.FrameworkPropertyMetadataOptions>する必要があります。  
  
2. `flags`パラメータを指定せずに署名のいずれかを使用し、各レポートブールプロパティを、必要な特性<xref:System.Windows.FrameworkPropertyMetadata>変更`true`ごとにに設定します。 この場合、この依存関係プロパティを持つすべての要素の構築前に、これらのプロパティを設定する必要があります。`flags` パラメーターを使用せずに引き続きメタデータを読み込めるよう、これらのブール型プロパティは読み書き可能な状態ですが、プロパティの使用前にメタデータを事実上シールする必要があります。 そのため、メタデータの要求後にこれらのプロパティを設定しようとすると、無効な操作となります。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>フレームワーク プロパティ メタデータのマージ動作  
 フレームワーク プロパティ メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>がマージされます。 新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>しい を追加すると、そのコールバックはメタデータに格納されます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、 の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>値は、メタデータで指定した最も近い先祖からの参照として昇格されます。  
  
- 実際の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>プロパティ システムの動作では、階層内のすべてのメタデータ所有者の実装が保持され、テーブルに追加され、プロパティ システムによって実行される順序は、最も深い派生クラスのコールバックが最初に呼び出されることです。 継承されたコールバックは、それらをメタデータに配置したクラスによって所有されていると見なされ、それぞれ 1 回だけ実行されます。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>が置き換えられます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、値<xref:System.Windows.PropertyMetadata.DefaultValue%2A>はメタデータで指定された最も近い先祖から取得されます。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>実装は置き換えられます。 新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>しい を追加すると、そのコールバックはメタデータに格納されます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>指定しない場合、 の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>値は、メタデータで指定した最も近い先祖からの参照として昇格されます。  
  
- プロパティ システムの動作では、直接<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>メタデータ内の の のみが呼び出されます。 階層内の他<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>の実装への参照は保持されません。  
  
- 列挙型の<xref:System.Windows.FrameworkPropertyMetadataOptions>フラグは、ビットごとの OR 演算として結合されます。  を指定<xref:System.Windows.FrameworkPropertyMetadataOptions>した場合、元のオプションは上書きされません。  オプションを変更するには、対応するプロパティを<xref:System.Windows.FrameworkPropertyMetadata>に設定します。 <xref:System.Windows.FrameworkPropertyMetadata>たとえば、元のオブジェクトがフラグを設定<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>している場合は、 に<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>`false`設定して変更できます。  
  
 この動作は によって<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>実装され、派生メタデータ クラスでオーバーライドできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
