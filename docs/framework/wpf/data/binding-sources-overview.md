---
title: バインディング ソースの概要
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: fe5cb97b4802c2b638a4b218a27da05468dc50fb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505551"
---
# <a name="binding-sources-overview"></a>バインディング ソースの概要
データ バインディングでは、バインディング ソース オブジェクトは、データの取得元のオブジェクトを表します。 このトピックでは、バインディング ソースとして使用できるオブジェクトの型について説明します。  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>バインディング ソースの型  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングでは、次のバインディング ソースの型がサポートされています。  
  
|バインディング ソース|説明|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクト|任意の [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトのパブリック プロパティ、サブプロパティ、およびインデクサーにバインドできます。 バインディング エンジンは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] リフレクションを使用してプロパティの値を取得します。 または、オブジェクトを実装する<xref:System.ComponentModel.ICustomTypeDescriptor>かが登録済み<xref:System.ComponentModel.TypeDescriptionProvider>もバインディング エンジンを使用します。<br /><br /> バインディング ソースとして使用できるクラスを実装する方法の詳細については、このトピックで後述する「[バインディング ソースのクラスの実装](#classes)」を参照してください。|  
|動的オブジェクト|実装するオブジェクトの使用可能なプロパティとインデクサーにバインドすることができます、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイス。 コード内のメンバーにアクセスできる場合、これにバインドできます。 たとえば、動的オブジェクトを使用して `someObjet.AProperty` を介してコード内のメンバーにアクセスできる場合、バインディング パスを `AProperty` に設定してこのメンバーにバインドできます。|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] オブジェクト|など、ADO.NET オブジェクトにバインドできます<xref:System.Data.DataTable>します。 ADO.NET<xref:System.Data.DataView>実装、<xref:System.ComponentModel.IBindingList>インターフェイスでは、バインディング エンジンが察知する変更通知を提供します。|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] オブジェクト|バインドして実行`XPath`でクエリが実行を<xref:System.Xml.XmlNode>、 <xref:System.Xml.XmlDocument>、または<xref:System.Xml.XmlElement>します。 アクセスする便利な手段[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]マークアップでバインディング ソースであるデータは、使用する、<xref:System.Windows.Data.XmlDataProvider>オブジェクト。 詳細については、「[XMLDataProvider と XPath クエリを使用して XML データにバインドする](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。<br /><br /> バインドすることも、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>、または LINQ to XML を使用してこれらの型のオブジェクトで実行するクエリの結果にバインドします。 LINQ to XML を使用して、マークアップでバインディング ソースである XML データにアクセスする便利な方法は使用する、<xref:System.Windows.Data.ObjectDataProvider>オブジェクト。 詳細については、「[XDocument、XElement、または LINQ for XML クエリの結果にバインドする](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)」を参照してください。|  
|<xref:System.Windows.DependencyObject> オブジェクト|いずれかの依存関係プロパティにバインドできます<xref:System.Windows.DependencyObject>します。 例については、「[2 つのコントロールのプロパティをバインドする](how-to-bind-the-properties-of-two-controls.md)」を参照してください。|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>バインディング ソースのクラスの実装  
 独自のバインディング ソースを作成できます。 このセクションでは、バインディング ソースとして機能するクラスを実装する場合に認識している必要のある事項について説明します。  
  
### <a name="providing-change-notifications"></a>変更通知の提供  
 いずれかを使用している場合<xref:System.Windows.Data.BindingMode.OneWay>または<xref:System.Windows.Data.BindingMode.TwoWay>バインド (必要があるため、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]バインディング ソースのプロパティを動的に変更するときに更新する)、適切なプロパティ変更通知メカニズムを実装する必要があります。 推奨されるメカニズムは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]または動的なクラスを実装する、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス。 詳細については、「[プロパティの変更通知を実装する](how-to-implement-property-change-notification.md)」を参照してください。  
  
 作成する場合、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]を実装しないオブジェクト<xref:System.ComponentModel.INotifyPropertyChanged>、そのバインディングで使用するデータが現在のままになることを確認する通知システムに配置する必要があります。 変更通知対象にする各プロパティの `PropertyChanged` パターンをサポートすることによって、変更通知を提供できます。 このパターンをサポートするには、プロパティごとに *PropertyName*Changed イベントを定義します。*PropertyName* はプロパティの名前です。 プロパティが変更されるたびにイベントが発生します。  
  
 バインディング ソースがこれらの通知メカニズムの 1 つを実装する場合、ターゲットの更新が自動的に発生します。 使用するオプションがある場合は、バインディング ソースが適切なプロパティを提供していない何らかの理由で変更通知、<xref:System.Windows.Data.BindingExpression.UpdateTarget%2A>ターゲット プロパティを明示的に更新する方法。  
  
### <a name="other-characteristics"></a>その他の特性  
 その他の重要な点を次に示します。  
  
- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] にオブジェクトを作成する場合、クラスに既定のコンストラクターが必要です。 一部の[!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)]言語などC#、既定のコンス トラクターに作成する場合があります。  
  
- バインディングのバインディング ソース プロパティとして使用するプロパティは、クラスのパブリック プロパティである必要があります。 明示的に定義されたインターフェイスのプロパティは、バインディングの目的ではアクセスできません。また、基本実装を持たない保護されたプロパティ、プライベート プロパティ、内部プロパティ、仮想プロパティも同様にバインディングの目的ではアクセスできません。  
  
- パブリック フィールドにバインドすることはできません。  
  
- クラスで宣言されたプロパティの型は、バインディングに渡される型です。 ただし、最終的にバインディングによって使用される型は、バインディング ソース プロパティの型ではなく、バインディング ターゲット プロパティの型によって決まります。 型の違いがある場合は、バインディングにカスタム プロパティを最初に渡す方法を処理するコンバーターを作成する必要があります。 詳細については、「 <xref:System.Windows.Data.IValueConverter> 」を参照してください。  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>バインディング ソースとしてオブジェクト全体を使用する  
 バインディング ソースとしてオブジェクト全体を使用できます。 使用してバインディング ソースを指定することができます、<xref:System.Windows.Data.Binding.Source%2A>または<xref:System.Windows.FrameworkElement.DataContext%2A>プロパティ、空白のバインディング宣言を指定:`{Binding}`します。 これが便利なシナリオには、文字列型のオブジェクトへのバインディング、対象とするプロパティが複数あるオブジェクトへのバインディング、またはコレクション オブジェクトへのバインディングなどがあります。 コレクション オブジェクト全体へのバインディングの例は、「[階層データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。  
  
 データがバインドされているターゲット プロパティにとって意味のあるものになるように、カスタム ロジックの適用が必要になる場合があることに注意してください。 カスタム ロジックがカスタムのコンバーターの形式にすることがあります (既定の型変換が存在しない) 場合、または<xref:System.Windows.DataTemplate>します。 コンバーターの詳細については、「[データ バインディングの概要](data-binding-overview.md)」の「データ変換」セクションを参照してください。 データ テンプレートの詳細については「 [データ テンプレートの概要](data-templating-overview.md)」を参照してください。  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>バインディング ソースとしてコレクション オブジェクトを使用する  
 多くの場合、バインディング ソースとして使用するオブジェクトは、カスタム オブジェクトのコレクションです。 各オブジェクトは、反復されるバインディングの 1 つのインスタンスのソースとして機能します。 たとえば、`CustomerOrder` オブジェクトから構成される `CustomerOrders` コレクションがあり、アプリケーションが注文数およびそれぞれに含まれているデータを判別するためにコレクションとやり取りするとします。  
  
 実装するコレクションを列挙することができます、<xref:System.Collections.IEnumerable>インターフェイス。 ただし、コレクションの挿入や削除が更新されるように、動的バインドを設定する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コレクションが自動的に実装する必要があります、<xref:System.Collections.Specialized.INotifyCollectionChanged>インターフェイス。 このインターフェイスは、基盤のコレクションが変更されたときに必ず発生する必要があるイベントを公開します。  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601>クラスが公開するデータ コレクションの組み込みの実装、<xref:System.Collections.Specialized.INotifyCollectionChanged>インターフェイス。 コレクション内の個々のデータ オブジェクトは、前の各セクションで説明されている要件を満たす必要があります。 例については、「[ObservableCollection を作成およびバインドする](how-to-create-and-bind-to-an-observablecollection.md)」を参照してください。 独自のコレクションを実装する前に、使用を検討して<xref:System.Collections.ObjectModel.ObservableCollection%601>またはなどの既存のコレクションの 1 つのクラス<xref:System.Collections.Generic.List%601>、 <xref:System.Collections.ObjectModel.Collection%601>、および<xref:System.ComponentModel.BindingList%601>、多数あります。  
  
 WPF はコレクションに直接バインドすることはありません。 バインディング ソースとしてコレクションを指定すると、WPF は実際にはコレクションの既定のビューにバインドします。 既定のビューの詳細については、「[データ バインディングの概要](data-binding-overview.md)」を参照してください。  
  
 高度なシナリオがあり、独自のコレクションを実装する場合は、使用を検討して、<xref:System.Collections.IList>インターフェイス。 <xref:System.Collections.IList> パフォーマンスを向上させることができます、インデックスによって個別にアクセスできるオブジェクトの非ジェネリック コレクションを提供します。  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>データ バインディングでのアクセス許可要件  
 データ バインディング時、アプリケーションの信頼レベルを考慮する必要があります。 次の表は、完全信頼または部分信頼で実行しているアプリケーションにおいてバインドできるプロパティの型のまとめです。  
  
|プロパティの型<br /><br /> (すべてのアクセス修飾子)|動的オブジェクトのプロパティ|動的オブジェクトのプロパティ|CLR プロパティ|CLR プロパティ|依存関係プロパティ|依存関係プロパティ|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**信頼レベル**|**完全信頼**|**部分信頼**|**完全信頼**|**部分信頼**|**完全信頼**|**部分信頼**|  
|パブリック クラス|[はい]|はい|はい|はい|はい|[はい]|  
|非パブリック クラス|[はい]|×|はい|×|[はい]|[はい]|  
  
 この表では、データ バインディングのアクセス許可要件について次の重要事項を説明します。  
  
- [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティでは、バインディング エンジンが、リフレクションを使用してバインディング ソースのプロパティにアクセスできる限り、データ バインディングは機能します。 それ以外の場合、バインディング エンジンは、プロパティを検出できないという警告を発行し、フォールバック値または既定値を使用します (使用できる場合)。  
  
- コンパイル時または実行時に定義されている動的オブジェクトのプロパティにバインドできます。  
  
- 依存関係プロパティには常にバインドできます。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] バインディングのアクセス許可要件は同様です。 部分的に信頼されたサンド ボックスで<xref:System.Windows.Data.XmlDataProvider>指定されたデータにアクセスする権限があるない場合は失敗します。  
  
 匿名型のオブジェクトは内部です。 完全信頼で実行されている場合にのみ、匿名型のプロパティにバインドできます。 匿名型の詳細については、「[Anonymous Types (C# Programming Guide)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md)」または「[Anonymous Types (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
 部分信頼セキュリティの詳細については、「[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [バインディング ソースを指定する](how-to-specify-the-binding-source.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
- [LINQ to XML による WPF のデータ バインディングの概要](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [データ バインディング](../advanced/optimizing-performance-data-binding.md)
