---
title: フレームワーク プロパティ メタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: f313c17a278a7b51379c4da9389c01eedf4a1e62
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379277"
---
# <a name="framework-property-metadata"></a>フレームワーク プロパティ メタデータ
フレームワーク プロパティ メタデータのオプションは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アーキテクチャの WPF フレームワーク レベルにあると見なされるオブジェクト要素のプロパティに対して報告されます。 一般に、WPF フレームワーク レベルが指定されている場合、レンダリング、データ バインディング、プロパティ システムの調整などの機能が、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のプレゼンテーション [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] と実行可能ファイルによって処理されます。 フレームワーク プロパティ メタデータがこれらのシステムによって照会されて、特定の要素プロパティに対する機能固有の特性が決まります。  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」トピックを通読していることを前提としています。 また、「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を読んでいる必要もあります。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>フレームワーク プロパティ メタデータによる通知内容  
 フレームワーク プロパティ メタデータは、次のように分類できます。  
  
-   要素に影響するレイアウト プロパティ (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>)。 それぞれの側面に影響を与えるプロパティとも実装している場合、メタデータでこれらのフラグを設定する可能性があります、 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>特定のレンダリング動作とレイアウト情報を指定する、クラスのメソッドシステム。 通常、そのような実装では、依存関係プロパティのメタデータでこれらのレイアウト プロパティのいずれかが true であると、プロパティの無効化があるかどうかがチェックされます。無効化があった場合にのみ、新しいレイアウト パスの要求が必要となります。  
  
-   要素の親要素に影響するレイアウト プロパティ (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>)。 既定ではこれらのフラグが設定される場所の例をいくつかは<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>と<xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>します。  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>。 既定では、依存関係プロパティは値を継承しません。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> 一部のコントロール合成シナリオに必要なビジュアル ツリーにも移動する継承のパスを使用できます。  
  
    > [!NOTE]
    >  プロパティ値のコンテキストにおける "継承" という用語は、依存関係プロパティに固有の事項を意味します。つまり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムの WPF フレームワーク レベルの機能によって、実際の依存関係プロパティ値を子要素が親要素から継承できることを意味します。 派生型を通じたマネージド コードの型およびメンバーの継承とは直接関係はありません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
-   データ バインディング特性 (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>)。 既定では、フレームワークの依存関係プロパティは、一方向のバインディング動作を持つデータ バインディングをサポートします。 必要がない場合はデータ バインディングを無効にできます (柔軟性と拡張性を目的とするため、既定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] にそのようなプロパティの例は多くありません)。 バインディングを個々 のコンポーネント間でのコントロールの動作を結び付けるプロパティの双方向の既定値を設定することがあります (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>例を示します) または双方向のバインディングがユーザーの一般的かつ期待されるシナリオ (<xref:System.Windows.Controls.TextBox.Text%2A>例を示します)。 データ バインディング関連のメタデータを変更した場合に影響を受けるのは既定値だけです。この既定値は、バインディングごとにいつでも変更できます。 バインディング モードおよびバインディング全般の詳細については、「[データ バインドの概要](../data/data-binding-overview.md)」を参照してください。  
  
-   レポートのプロパティをジャーナリングをサポートするアプリケーションまたはサービスをジャーナリングするかどうか (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>)。 一般的な要素に対しては、ジャーナリングは既定で有効になりませんが、特定のユーザー入力コントロールに対しては選択的に有効になります。 これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のジャーナリングの実装を含む、ジャーナリング サービスによって読み取られるプロパティです。通常は、複数のナビゲーション ステップにわたって永続化する必要があるユーザー コントロール (一覧におけるユーザー選択など) に設定します。 ジャーナリングの詳細については、「[ナビゲーションの概要](../app-development/navigation-overview.md)」を参照してください。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>FrameworkPropertyMetadata の読み取り  
 上のリンクのプロパティは、特定のプロパティを<xref:System.Windows.FrameworkPropertyMetadata>直接の基本クラスに追加<xref:System.Windows.UIPropertyMetadata>します。 これらのプロパティの既定値はいずれも `false` です。 これらのプロパティの値を知ることが重要となるプロパティのメタデータの要求が返されたメタデータをキャストを試行する<xref:System.Windows.FrameworkPropertyMetadata>、必要に応じて、個々 のプロパティの値を確認します。  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>メタデータの指定  
 新しい依存関係プロパティの登録にメタデータを適用する目的で新しいメタデータ インスタンスを作成するときに使用するメタデータ クラスの選択がある: 基本<xref:System.Windows.PropertyMetadata>いくつかの派生クラスまたは<xref:System.Windows.FrameworkPropertyMetadata>します。 一般に、使用する必要があります<xref:System.Windows.FrameworkPropertyMetadata>、プロパティがプロパティ システムとの対話がある場合に特にと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトとデータ バインドなどの関数。 派生する高度なシナリオの別のオプションは、<xref:System.Windows.FrameworkPropertyMetadata>独自のメタデータを作成するレポート クラス情報と共にそのメンバーに含まれます。 使用する場合がありますまたは<xref:System.Windows.PropertyMetadata>または<xref:System.Windows.UIPropertyMetadata>実装の機能のサポートの程度を通信するためにします。  
  
 既存のプロパティ (<xref:System.Windows.DependencyProperty.AddOwner%2A>または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>呼び出し)、元の登録で使用されるメタデータ型により常にオーバーライドする必要があります。  
  
 作成する場合、<xref:System.Windows.FrameworkPropertyMetadata>インスタンス、フレームワーク プロパティの特性を通信する特定のプロパティの値をそのメタデータを設定する 2 つの方法があります。  
  
1.  使用して、<xref:System.Windows.FrameworkPropertyMetadata>できるコンス トラクターのシグネチャを`flags`パラメーター。 このパラメーターは必要なすべての値の組み合わせを入力する必要があります、<xref:System.Windows.FrameworkPropertyMetadataOptions>列挙フラグ。  
  
2.  持たないシグネチャのいずれかを使用して、`flags`パラメーター、し、設定のブール型プロパティを報告する各<xref:System.Windows.FrameworkPropertyMetadata>に`true`特性の変更が必要な各。 この場合、この依存関係プロパティを持つすべての要素の構築前に、これらのプロパティを設定する必要があります。`flags` パラメーターを使用せずに引き続きメタデータを読み込めるよう、これらのブール型プロパティは読み書き可能な状態ですが、プロパティの使用前にメタデータを事実上シールする必要があります。 そのため、メタデータの要求後にこれらのプロパティを設定しようとすると、無効な操作となります。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>フレームワーク プロパティ メタデータのマージ動作  
 フレームワーク プロパティ メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 結合されます。 新しく追加した場合<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>はメタデータでそれを指定した最も近い先祖からの参照として昇格します。  
  
-   実際のプロパティ システム動作<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>される実装で、階層内のすべてのメタデータ所有者が保持され、テーブルに追加の派生クラスのコールバックがプロパティ システムによる実行の順序で最初に呼び出されます。 継承されたコールバックは、それらをメタデータに配置したクラスによって所有されていると見なされ、それぞれ 1 回だけ実行されます。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> 置き換えられます。 指定しない場合、<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.DefaultValue%2A>メタデータでそれを指定した最も近い先祖します。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 実装は置き換えられます。 新しく追加した場合<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>はメタデータでそれを指定した最も近い先祖からの参照として昇格します。  
  
-   プロパティ システム動作はのみですが、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>直接のメタデータが呼び出されます。 その他への参照<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>階層内の実装が保持されます。  
  
-   フラグ<xref:System.Windows.FrameworkPropertyMetadataOptions>列挙体はビットごとの OR 演算として組み合わされます。  指定した場合<xref:System.Windows.FrameworkPropertyMetadataOptions>、元のオプションは上書きされません。  オプションを変更するには対応するプロパティを設定します。<xref:System.Windows.FrameworkPropertyMetadata>します。 などの場合、元<xref:System.Windows.FrameworkPropertyMetadata>オブジェクト セット、<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>フラグを設定して変更できます<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>に`false`。  
  
 この動作を実装して<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>、派生メタデータ クラスでオーバーライドすることができます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
