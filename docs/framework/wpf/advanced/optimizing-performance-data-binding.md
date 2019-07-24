---
title: パフォーマンスの最適化:データ バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401454"
---
# <a name="optimizing-performance-data-binding"></a>パフォーマンスの最適化:データ バインディング
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングは、データを表示したり操作するための単純で一貫した方法をアプリケーションに提供します。 要素は、CLR オブジェクトおよび[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]の形式で、さまざまなデータソースのデータにバインドできます。  
  
 このトピックでは、データ バインディングのパフォーマンスに関する推奨事項について説明します。  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>データ バインディングの参照が解決されるしくみ  
 データ バインディングのパフォーマンスの問題に入る前に、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のデータ バインディング エンジンがバインディングのオブジェクト参照をどのように解決するのかを説明します。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]データバインディングのソースには、任意の CLR オブジェクトを指定できます。 CLR オブジェクトのプロパティ、サブプロパティ、またはインデクサーにバインドできます。 バインディング参照は Microsoft .NET Framework リフレクションまたは<xref:System.ComponentModel.ICustomTypeDescriptor>のいずれかを使用して解決されます。 次に、バインディングのオブジェクト参照を解決するための 3 つの方法について説明します。  
  
 1 つ目は、リフレクションを使用する方法です。 この場合、 <xref:System.Reflection.PropertyInfo>オブジェクトを使用してプロパティの属性を検出し、プロパティのメタデータにアクセスできるようにします。 <xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスを使用する場合、データバインディングエンジンは、このインターフェイスを使用してプロパティ値にアクセスします。 <xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスは、オブジェクトにプロパティの静的なセットがない場合に特に便利です。  
  
 プロパティの変更通知を提供するには、 <xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスを実装するか、 <xref:System.ComponentModel.TypeDescriptor>に関連付けられている変更通知を使用します。 ただし、プロパティ変更通知を実装する場合は、を使用<xref:System.ComponentModel.INotifyPropertyChanged>することをお勧めします。  
  
 ソースオブジェクトが clr オブジェクトで、source プロパティが clr プロパティの場合、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]データバインディングエンジンは、まず、 <xref:System.ComponentModel.TypeDescriptor>ソースオブジェクトに対してリフレクションを使用してを取得<xref:System.ComponentModel.PropertyDescriptor>し、次にを照会する必要があります。 パフォーマンスの観点から見た場合、このリフレクション操作のシーケンスには非常に時間がかかる可能性があります。  
  
 オブジェクト参照を解決する2番目の方法では、 <xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスを実装する clr ソースオブジェクトと、clr プロパティであるソースプロパティが必要になります。 この場合、データ バインディング エンジンは、ソースの型に対してリフレクションを直接使用して必要なプロパティを取得します。 この方法も最適な方法とは言えませんが、最初の方法よりは作業セットの要件の負荷が小さくなります。  
  
 オブジェクト参照を解決する3番目の方法では、 <xref:System.Windows.DependencyObject>ソースオブジェクトがで<xref:System.Windows.DependencyProperty>あり、がであるソースプロパティが必要です。 この場合、データ バインディング エンジンはリフレクションを使用する必要はありません。 代わりに、プロパティ エンジンとデータ バインディング エンジンが連携してプロパティ参照を個別に解決します。 これが、データ バインディングに使用されているオブジェクト参照を解決するための最適な方法です。  
  
 次の表では、これら3つの<xref:System.Windows.Controls.TextBlock.Text%2A>方法を使用<xref:System.Windows.Controls.TextBlock>して、1000要素のプロパティをバインドするデータの速度を比較しています。  
  
|**TextBlock の Text プロパティのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|CLR オブジェクトのプロパティへの|115|314|  
|を実装する CLR オブジェクトのプロパティへの<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|<xref:System.Windows.DependencyProperty> の<xref:System.Windows.DependencyObject>に対する。|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>大きな CLR オブジェクトへのバインディング  
 1つの CLR オブジェクトに何千ものプロパティを使用してデータをバインドすると、パフォーマンスに大きな影響があります。 この影響を最小限に抑えるには、1つのオブジェクトを複数の CLR オブジェクトに分割し、プロパティを減らします。 この表は、1つの大きな CLR オブジェクト、または複数の小さいオブジェクトにデータをバインドするためのバインドとレンダリング時間を示しています。  
  
|**1000 個の TextBlock オブジェクトのデータ バインディングのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000プロパティを持つ CLR オブジェクト|950|1200|  
|1つのプロパティを持つ 1000 CLR オブジェクト|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>ItemsSource へのバインディング  
 に表示する従業員の一覧を保持する<xref:System.Collections.Generic.List%601> CLR オブジェクトがあるシナリオについて考えてみます。<xref:System.Windows.Controls.ListBox> これら2つ<xref:System.Windows.Controls.ListBox>のオブジェクト間の対応を作成するには、従業員リストを<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティにバインドします。 ここで、グループに新しい従業員が加わったとします。 この新しい人をバインド<xref:System.Windows.Controls.ListBox>された値に挿入するには、この人を従業員リストに追加するだけで、この変更がデータバインディングエンジンによって自動的に認識されることが期待できます。 この想定は偽であることを前提としています。実際には、変更は<xref:System.Windows.Controls.ListBox>自動的にに反映されません。 これは、CLR <xref:System.Collections.Generic.List%601>オブジェクトがコレクションの変更イベントを自動的に生成しないためです。 で変更を取得<xref:System.Windows.Controls.ListBox>するには、従業員のリストを再作成し、の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>プロパティに再アタッチする必要があります。 この解決方法で問題は解決されますが、パフォーマンスへの影響はきわめて大きくなります。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.ListBox>を新しいオブジェクトに再割り当てするたびに、最初に前の項目が破棄され、リスト全体が再生成されます。 <xref:System.Windows.Controls.ListBox> が複雑<xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>なにマップされると、パフォーマンスへの影響が拡大されます。  
  
 この問題の非常に効率的な解決策は、従業員リスト<xref:System.Collections.ObjectModel.ObservableCollection%601>をにすることです。 オブジェクト<xref:System.Collections.ObjectModel.ObservableCollection%601>は、データバインディングエンジンが受け取ることができる変更通知を発生させます。 イベントは、リスト全体を再生成する<xref:System.Windows.Controls.ItemsControl>必要なく、から項目を追加または削除します。  
  
 次の表は、 <xref:System.Windows.Controls.ListBox> 1 つの項目が追加されたときに (UI 仮想化がオフになっている) を更新するためにかかる時間を示しています。 最初の行の数値は、CLR <xref:System.Collections.Generic.List%601>オブジェクトが要素の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>に<xref:System.Windows.Controls.ListBox>バインドされている場合の経過時間を表します。 2番目の行の数値は、 <xref:System.Collections.ObjectModel.ObservableCollection%601>が<xref:System.Windows.Controls.ListBox>要素の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>にバインドされている場合の経過時間を表します。 <xref:System.Collections.ObjectModel.ObservableCollection%601>データバインディング戦略を使用して時間を大幅に節約できることに注意してください。  
  
|**ItemsSource のデータ バインディングのバインド先**|**1 項目の更新時間 (ミリ秒)**|  
|--------------------------------------|---------------------------------------|  
|CLR <xref:System.Collections.Generic.List%601>オブジェクトへの|1656|  
|に<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IEnumerable ではなく IList を ItemsControl にバインドする  
 またはを<xref:System.Windows.Controls.ItemsControl> <xref:System.Collections.Generic.IList%601>オブジェクトにバインドするかどうかを選択できる場合は、オブジェクトを選択します。 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IList%601> をに<xref:System.Collections.IEnumerable> バインドして<xref:System.Collections.Generic.IList%601>ラッパーオブジェクトを作成します。これは、2番目のオブジェクトの不要なオーバーヘッドによってパフォーマンスが影響を受けることを意味します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ItemsControl>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>データ バインディングのためだけに CLR オブジェクトを XML に変換しない  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツへのデータバインドを可能にします。ただし、 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]コンテンツへのデータバインディングは、CLR オブジェクトへのデータバインドよりも低速です。 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 唯一の目的がデータバインディング用である場合は、CLR オブジェクトデータを XML に変換しないでください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [チュートリアル: WPF アプリケーションでのアプリケーションデータのキャッシュ](walkthrough-caching-application-data-in-a-wpf-application.md)
