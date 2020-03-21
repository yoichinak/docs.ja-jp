---
title: 'パフォーマンスの最適化 : データ バインド'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186758"
---
# <a name="optimizing-performance-data-binding"></a>パフォーマンスの最適化 : データ バインド
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングは、アプリケーションがデータを提示し、データと対話するための簡単で一貫性のある方法を提供します。 要素は、CLR オブジェクトと XML の形式でさまざまなデータ ソースのデータにバインドできます。  
  
 このトピックでは、データ バインディングのパフォーマンスに関する推奨事項について説明します。  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>データ バインディングの参照が解決されるしくみ  
 データ バインディングのパフォーマンスの問題に入る前に、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のデータ バインディング エンジンがバインディングのオブジェクト参照をどのように解決するのかを説明します。  
  
 データ バインディングの[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ソースは、任意の CLR オブジェクトにすることができます。 CLR オブジェクトのプロパティ、サブプロパティ、またはインデクサーにバインドできます。 バインディング参照は、Microsoft .NET Framework リフレクションまたは<xref:System.ComponentModel.ICustomTypeDescriptor>. 次に、バインディングのオブジェクト参照を解決するための 3 つの方法について説明します。  
  
 1 つ目は、リフレクションを使用する方法です。 この場合、オブジェクトは<xref:System.Reflection.PropertyInfo>プロパティの属性を検出するために使用され、プロパティ メタデータへのアクセスを提供します。 インターフェイスを使用<xref:System.ComponentModel.ICustomTypeDescriptor>する場合、データ バインディング エンジンはこのインターフェイスを使用してプロパティ値にアクセスします。 この<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスは、オブジェクトにプロパティの静的セットがない場合に特に便利です。  
  
 プロパティ変更通知は、インターフェイスを実装するか、<xref:System.ComponentModel.INotifyPropertyChanged>に関連付けられている変更通知を使用して提供<xref:System.ComponentModel.TypeDescriptor>できます。 ただし、プロパティ変更通知を実装する場合は、 を<xref:System.ComponentModel.INotifyPropertyChanged>使用するのが推奨されます。  
  
 ソース オブジェクトが CLR オブジェクトで、ソース プロパティが CLR プロパティ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]である場合、データ バインディング エンジンはまずソース オブジェクトのリ<xref:System.ComponentModel.TypeDescriptor>フレクションを使用して<xref:System.ComponentModel.PropertyDescriptor>を取得し、 を取得し、 をクエリする必要があります。 パフォーマンスの観点から見た場合、このリフレクション操作のシーケンスには非常に時間がかかる可能性があります。  
  
 オブジェクト参照を解決する 2 番目の方法は、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスを実装する CLR ソース オブジェクトと、CLR プロパティであるソース プロパティを含みます。 この場合、データ バインディング エンジンは、ソースの型に対してリフレクションを直接使用して必要なプロパティを取得します。 この方法も最適な方法とは言えませんが、最初の方法よりは作業セットの要件の負荷が小さくなります。  
  
 オブジェクト参照を解決する 3 番目の方法は、 である<xref:System.Windows.DependencyObject>ソース オブジェクトと、 である<xref:System.Windows.DependencyProperty>ソース プロパティです。 この場合、データ バインディング エンジンはリフレクションを使用する必要はありません。 代わりに、プロパティ エンジンとデータ バインディング エンジンが連携してプロパティ参照を個別に解決します。 これが、データ バインディングに使用されているオブジェクト参照を解決するための最適な方法です。  
  
 次の表は、これらの 3 つのメソッド<xref:System.Windows.Controls.TextBlock.Text%2A>を使用して、1000 個<xref:System.Windows.Controls.TextBlock>の要素のプロパティをデータ バインドの速度を比較します。  
  
|**TextBlock の Text プロパティのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|CLR オブジェクトのプロパティへ|115|314|  
|実装する CLR オブジェクトのプロパティに対して<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|<xref:System.Windows.DependencyProperty>の<xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>大きな CLR オブジェクトへのバインディング  
 何千ものプロパティを持つ 1 つの CLR オブジェクトにデータをバインドすると、パフォーマンスに大きな影響が生じます。 この影響を最小限に抑えるには、プロパティの数を減らして、単一のオブジェクトを複数の CLR オブジェクトに分割します。 この表は、単一の大きな CLR オブジェクトに対するデータ バインディングと、複数の小さいオブジェクトへのデータ バインディングのバインディングとレンダリング時間を示しています。  
  
|**1000 個の TextBlock オブジェクトのデータ バインディングのバインド先**|**バインディング時間 (ミリ秒)**|**レンダリング時間 -- バインディングを含む (ミリ秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|1000 個のプロパティを持つ CLR オブジェクトへ|950|1200|  
|1 つのプロパティを持つ 1000 個の CLR オブジェクトに|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>ItemsSource へのバインディング  
 に表示する従業員のリストを保持する<xref:System.Collections.Generic.List%601>CLR オブジェクトがあるシナリオを考えてみます<xref:System.Windows.Controls.ListBox>。 これら 2 つのオブジェクト間の対応を作成するには、従業員リストを<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティに<xref:System.Windows.Controls.ListBox>バインドします。 ここで、グループに新しい従業員が加わったとします。 この新しい人をバインドされた<xref:System.Windows.Controls.ListBox>値に挿入するには、このユーザーを従業員リストに追加するだけで、この変更がデータ バインド エンジンによって自動的に認識されることを期待すると思うかもしれません。 その仮定は誤りを証明するでしょう。実際には、変更は<xref:System.Windows.Controls.ListBox>自動的には反映されません。 これは、CLR<xref:System.Collections.Generic.List%601>オブジェクトがコレクション変更イベントを自動的に発生しないためです。 変更<xref:System.Windows.Controls.ListBox>を取得するには、従業員のリストを再作成し、 の<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティに再度アタッチする<xref:System.Windows.Controls.ListBox>必要があります。 この解決方法で問題は解決されますが、パフォーマンスへの影響はきわめて大きくなります。 を新しいオブジェクト<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A><xref:System.Windows.Controls.ListBox>に再割り当てするたびに、最初<xref:System.Windows.Controls.ListBox>のアイテムは以前のアイテムを削除し、リスト全体が再生成されます。 複雑<xref:System.Windows.Controls.ListBox><xref:System.Windows.DataTemplate>な にマップすると、パフォーマンスへの影響が拡大します。  
  
 この問題に対する非常に効率的な解決策は、従業員リスト<xref:System.Collections.ObjectModel.ObservableCollection%601>を . オブジェクト<xref:System.Collections.ObjectModel.ObservableCollection%601>は、データ バインディング エンジンが受け取ることができる変更通知を発生させます。 イベントは、リスト全体を再生成する必要<xref:System.Windows.Controls.ItemsControl>なしに、 に項目を追加または削除します。  
  
 次の表は、1 つの項目が追加<xref:System.Windows.Controls.ListBox>されたときに (UI 仮想化がオフになっている状態で) 更新にかかる時間を示しています。 最初の行の数値は、CLR<xref:System.Collections.Generic.List%601>オブジェクトが<xref:System.Windows.Controls.ListBox>要素の . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 2 行目の数値は、 要素<xref:System.Collections.ObjectModel.ObservableCollection%601>の に バインドされた経過時間<xref:System.Windows.Controls.ListBox>を表<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>します。 データ バインディング戦略を使用すると<xref:System.Collections.ObjectModel.ObservableCollection%601>、大幅な時間の節約に注意してください。  
  
|**ItemsSource のデータ バインディングのバインド先**|**1 項目の更新時間 (ミリ秒)**|  
|--------------------------------------|---------------------------------------|  
|CLR<xref:System.Collections.Generic.List%601>オブジェクトへ|1656|  
|に<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>IEnumerable ではなく IList を ItemsControl にバインドする  
 オブジェクトに<xref:System.Collections.Generic.IList%601>バインドするか、 をバインドするかを<xref:System.Collections.IEnumerable>選択できる<xref:System.Windows.Controls.ItemsControl>場合は、オブジェクト<xref:System.Collections.Generic.IList%601>を選択します。 <xref:System.Windows.Controls.ItemsControl>強制<xref:System.Collections.IEnumerable>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にバインドしてラッパー<xref:System.Collections.Generic.IList%601>オブジェクトを作成する場合、2 番目のオブジェクトの不要なオーバーヘッドによってパフォーマンスが影響を受けます。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>データ バインディングのためだけに CLR オブジェクトを XML に変換しない  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XML コンテンツにデータバインドを実行できます。ただし、XML コンテンツへのデータ バインディングは、CLR オブジェクトへのデータ バインディングよりも低速です。 唯一の目的がデータ バインディングの場合は、CLR オブジェクト データを XML に変換しないでください。  
  
## <a name="see-also"></a>関連項目

- [WPF アプリケーションのパフォーマンスの最適化](optimizing-wpf-application-performance.md)
- [アプリケーション パフォーマンスの計画](planning-for-application-performance.md)
- [ハードウェアの活用](optimizing-performance-taking-advantage-of-hardware.md)
- [レイアウトとデザイン](optimizing-performance-layout-and-design.md)
- [2D グラフィックスとイメージング](optimizing-performance-2d-graphics-and-imaging.md)
- [オブジェクトの動作](optimizing-performance-object-behavior.md)
- [アプリケーション リソース](optimizing-performance-application-resources.md)
- [テキスト](optimizing-performance-text.md)
- [パフォーマンスに関するその他の推奨事項](optimizing-performance-other-recommendations.md)
- [データバインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](walkthrough-caching-application-data-in-a-wpf-application.md)
