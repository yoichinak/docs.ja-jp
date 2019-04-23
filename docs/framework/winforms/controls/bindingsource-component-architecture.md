---
title: BindingSource コンポーネント アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 81559444b6e3da2861e48bdc637ae01d246c0758
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165348"
---
# <a name="bindingsource-component-architecture"></a>BindingSource コンポーネント アーキテクチャ
<xref:System.Windows.Forms.BindingSource>コンポーネント、ユニバーサル データ ソースにすべての Windows フォーム コントロールをバインドできます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントがデータ ソースにコントロールをバインドするプロセスを簡略化し、従来のデータ バインドに次の利点を提供します。  
  
-   ビジネス オブジェクトをデザイン時のバインドを有効にします。  
  
-   カプセル化<xref:System.Windows.Forms.CurrencyManager>機能と公開<xref:System.Windows.Forms.CurrencyManager>デザイン時にイベント。  
  
-   サポートするリストの作成を簡素化、<xref:System.ComponentModel.IBindingList>変更通知の一覧をネイティブにサポートしないデータ ソースの一覧変更通知を提供することでインターフェイス。  
  
-   機能拡張ポイントを提供します、<xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType>メソッド。  
  
-   データ ソースとコントロールの間の間接参照のレベルを提供します。 実行時に、データ ソースを変更することがありますこの間接指定は重要です。  
  
-   具体的には、他のデータに関連する Windows フォーム コントロールと相互運用、<xref:System.Windows.Forms.BindingNavigator>と<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 これらの理由から、<xref:System.Windows.Forms.BindingSource>コンポーネントは、Windows フォーム コントロールをデータ ソースにバインドすることをお勧めします。  
  
## <a name="bindingsource-features"></a>BindingSource の機能  
 <xref:System.Windows.Forms.BindingSource>コンポーネント コントロールをデータにバインドするためのいくつかの機能を提供します。 これらの機能では、ほとんどコーディングとせず、一部のほとんどのデータ バインディング シナリオを実装できます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントがさまざまな種類のデータ ソースにアクセスするための一貫したインターフェイスを提供することでこれを実現します。 これは、任意の型にバインドするため、同じ手順を使用することを意味します。 たとえば、アタッチすることができます、<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティを<xref:System.Data.DataSet>またはデータ ソースを操作するのには、プロパティ、メソッド、およびイベントの同じセットを使用するビジネス オブジェクトに、どちらの場合もします。  
  
 によって提供される一貫性のあるインターフェイス、<xref:System.Windows.Forms.BindingSource>コンポーネントは、データをコントロールにバインドするプロセスを大幅に簡略化します。 データ ソースの種類を提供する変更の通知を<xref:System.Windows.Forms.BindingSource>コンポーネントは、コントロールとデータ ソース間の変更を自動的に通信します。 変更通知を提供しないデータ ソースの種類のイベントが変更通知を生成するための提供されます。 次に示しますでサポートされる機能、<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
-   間接参照します。  
  
-   通貨管理します。  
  
-   データ ソースを一覧として。  
  
-   <xref:System.Windows.Forms.BindingSource> として、<xref:System.ComponentModel.IBindingList>します。  
  
-   カスタム アイテムを作成します。  
  
-   トランザクションのアイテムを作成します。  
  
-   <xref:System.Collections.IEnumerable> サポート。  
  
-   デザイン時サポートします。  
  
-   静的<xref:System.Windows.Forms.ListBindingHelper>メソッド。  
  
-   並べ替えとフィルタ リングを<xref:System.ComponentModel.IBindingListView>インターフェイス。  
  
-   統合<xref:System.Windows.Forms.BindingNavigator>します。  
  
### <a name="indirection"></a>間接  
 <xref:System.Windows.Forms.BindingSource>コンポーネントは、コントロールとデータ ソース間の間接参照のレベルを提供します。 コントロールをバインドするデータ ソースへの直接のコントロールをバインドするのではなく、<xref:System.Windows.Forms.BindingSource>とにデータ ソースのアタッチ、<xref:System.Windows.Forms.BindingSource>コンポーネントの<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティ。  
  
 このレベルの間接参照では、コントロールのバインドをリセットせず、データ ソースを変更できます。 これにより、次の機能。  
  
-   アタッチすることができます、<xref:System.Windows.Forms.BindingSource>さまざまなデータ ソース コントロールの現在のバインドを維持したままにします。  
  
-   データ ソース内の項目を変更し、バインドされたコントロールに通知できます。 詳細については、「[方法 :BindingSource で Windows フォーム コントロール内のデータ ソースの更新を反映](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)します。  
  
-   バインドすることができます、<xref:System.Type>メモリ内のオブジェクトの代わりにします。 詳細については、「[方法 :Windows フォーム コントロールを型にバインド](how-to-bind-a-windows-forms-control-to-a-type.md)します。 実行時にオブジェクトにバインドできます。  
  
### <a name="currency-management"></a>通貨の管理  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.Windows.Forms.ICurrencyManagerProvider>通貨管理を処理するインターフェイス。 <xref:System.Windows.Forms.ICurrencyManagerProvider>インターフェイス、アクセスすることも、通貨用のマネージャーに、 <xref:System.Windows.Forms.BindingSource>、別の通貨マネージャーだけでなく<xref:System.Windows.Forms.BindingSource>に同じバインド<xref:System.Windows.Forms.BindingSource.DataMember%2A>します。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントをカプセル化<xref:System.Windows.Forms.CurrencyManager>機能と、最も一般的な公開<xref:System.Windows.Forms.CurrencyManager>プロパティおよびイベント。 次の表では、通貨管理に関連するメンバーの一部について説明します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> プロパティ  
 関連付けられた currencymanager を取得、<xref:System.Windows.Forms.BindingSource>します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> メソッド  
 他を使用する必要がある場合<xref:System.Windows.Forms.BindingSource>指定したデータ メンバーにバインドされている、その currencymanager を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> プロパティ  
 データソースの現在の項目を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティ  
 基になるリストでの現在の位置を取得または設定します。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッド  
 基になるデータ ソースに保留中の変更を適用します。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> メソッド  
 現在の編集操作をキャンセルします。  
  
### <a name="data-source-as-a-list"></a>データ ソースとして一覧  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.IBindingListView>と<xref:System.ComponentModel.ITypedList>インターフェイス。 この実装で使用できます、<xref:System.Windows.Forms.BindingSource>コンポーネント自体をデータ ソースとして任意の外部ストレージなし。  
  
 ときに、<xref:System.Windows.Forms.BindingSource>コンポーネントがデータ ソースに接続されている、リストとしてデータ ソースを公開します。  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティは、いくつかのデータ ソースに設定することができます。 型、オブジェクト、および種類のリストが含まれます。 結果として得られるデータ ソースは、一覧として公開されます。 次の表は、いくつかの一般的なデータ ソースと結果のリストの評価を示します。  
  
|データ ソースのプロパティ|結果のリスト|  
|-------------------------|------------------|  
|null 参照 (Visual Basic の場合は `Nothing`)。|空<xref:System.ComponentModel.IBindingList>のオブジェクト。 追加された項目の種類にリストを設定する項目を追加します。|  
|Null 参照 (`Nothing` Visual basic) で<xref:System.Windows.Forms.BindingSource.DataMember%2A>設定|サポートされていません。発生させる<xref:System.ArgumentException>します。|  
|リスト以外の型または"T"型のオブジェクト|空<xref:System.ComponentModel.IBindingList>型"T"のです。|  
|配列インスタンス|<xref:System.ComponentModel.IBindingList>配列の要素を格納します。|  
|<xref:System.Collections.IEnumerable> インスタンス|<xref:System.ComponentModel.IBindingList>を含む、<xref:System.Collections.IEnumerable>項目|  
|"T"型を含むインスタンスを一覧表示します。|<xref:System.ComponentModel.IBindingList>型"T"を格納しているインスタンス。|  
  
 さらに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>などの他のリストの種類を設定できます<xref:System.ComponentModel.IListSource>と<xref:System.ComponentModel.ITypedList>、および<xref:System.Windows.Forms.BindingSource>適切に処理されます。 この場合、リストに格納されている型には、既定のコンス トラクターが必要です。  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource は、IBindingList として  
 <xref:System.Windows.Forms.BindingSource>コンポーネントへのアクセスおよびとして基になるデータを操作するためのメンバーを提供する、<xref:System.ComponentModel.IBindingList>します。 次の表では、これらのメンバーの一部について説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> プロパティ|評価の結果一覧の取得、<xref:System.Windows.Forms.BindingSource.DataSource%2A>または<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティ。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> メソッド|基になるリストに新しい項目を追加します。 実装するデータ ソースに適用されます、<xref:System.ComponentModel.IBindingList>インターフェイスし、項目の追加を許可する (つまり、<xref:System.Windows.Forms.BindingSource.AllowNew%2A>プロパティに設定されて`true`)。|  
  
### <a name="custom-item-creation"></a>カスタムの項目の作成  
 処理することができます、<xref:System.Windows.Forms.BindingSource.AddingNew>独自のアイテム作成ロジックを提供するイベントです。 <xref:System.Windows.Forms.BindingSource.AddingNew>に新しいオブジェクトを追加する前に、イベントが発生した、<xref:System.Windows.Forms.BindingSource>します。 このイベントが発生した後、<xref:System.Windows.Forms.BindingSource.AddNew%2A>メソッドが呼び出されると、基底のリストに新しい項目を追加する前にします。 このイベントを処理することから派生することがなくカスタム項目の作成の動作を行うことができます、<xref:System.Windows.Forms.BindingSource>クラス。 詳細については、「[方法 :項目の追加、Windows フォーム BindingSource をカスタマイズする](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)します。  
  
### <a name="transactional-item-creation"></a>トランザクションのアイテムの作成  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.ICancelAddNew>インターフェイスで、トランザクションの項目を作成できるようにします。 新しい項目は仮の呼び出しを使用して作成した後<xref:System.Windows.Forms.BindingSource.AddNew%2A>追加のコミットまたはロールバックし、次の方法で可能性があります。  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A>メソッドは、保留中の追加を明示的にコミットします。  
  
-   挿入、削除、移動などの別のコレクション操作を実行すると、保留中の追加を暗黙的にコミットされます。  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>メソッドは元に戻す保留中の追加、メソッドは既にコミットされていない場合。  
  
### <a name="ienumerable-support"></a>IEnumerable のサポート  
 <xref:System.Windows.Forms.BindingSource>コンポーネントへコントロールのバインドを使用する<xref:System.Collections.IEnumerable>データ ソース。 このコンポーネントとにバインドできますデータ ソースなど、<xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>します。  
  
 ときに、<xref:System.Collections.IEnumerable>に割り当てられているデータ ソース、<xref:System.Windows.Forms.BindingSource>コンポーネント、<xref:System.Windows.Forms.BindingSource>を作成、<xref:System.ComponentModel.IBindingList>の内容を追加し、<xref:System.Collections.IEnumerable>リストにデータ ソース。  
  
### <a name="design-time-support"></a>デザイン時サポート  
 オブジェクトの種類によっては、ファクトリ クラスから作成されたオブジェクトまたは Web サービスによって返されるオブジェクトなどのデザイン時に作成できません。 コントロールをバインドできるメモリ内オブジェクトが存在しない場合でも、デザイン時にこれらの型にコントロールをバインドする必要がある場合があります。 列ヘッダー ラベル付けする必要があります、たとえば、<xref:System.Windows.Forms.DataGridView>カスタム型のパブリック プロパティの名前を持つコントロール。  
  
 このシナリオをサポートするために、<xref:System.Windows.Forms.BindingSource>コンポーネントへのバインドをサポートする、<xref:System.Type>します。 割り当てると、<xref:System.Type>を<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティ、<xref:System.Windows.Forms.BindingSource>コンポーネントは、空を作成します<xref:System.ComponentModel.BindingList%601>の<xref:System.Type>項目。 すべてのコントロールにバインドする、その後、<xref:System.Windows.Forms.BindingSource>コンポーネントは、デザイン時または実行時にプロパティまたは型のスキーマが存在する警告されます。 詳細については、「[方法 :Windows フォーム コントロールを型にバインド](how-to-bind-a-windows-forms-control-to-a-type.md)します。  
  
### <a name="static-listbindinghelper-methods"></a>静的 ListBindingHelper メソッド  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>、 <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>、および<xref:System.Windows.Forms.BindingSource>からリストを生成するすべての共有の共通ロジックの種類、 `DataSource` / `DataMember`ペア。 さらに、この共通のロジックがパブリックに公開用にコントロールを作成して、次に他のサード パーティ`static`メソッド。  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>。  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>並べ替えとフィルタ リングを IBindingListView インターフェイス  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.IBindingListView>インターフェイスで、拡張、<xref:System.ComponentModel.IBindingList>インターフェイス。 <xref:System.ComponentModel.IBindingList>は 1 つの列の並べ替えおよび<xref:System.ComponentModel.IBindingListView>先進的な並べ替えとフィルター処理を提供します。 <xref:System.ComponentModel.IBindingListView>場合は、データ ソースも、データ ソースの項目をフィルター処理を実装してこれらのインターフェイスのいずれか、並べ替えることができます。 <xref:System.Windows.Forms.BindingSource>コンポーネントがこれらのメンバーの参照の実装を提供していません。 代わりに、呼び出しは、基になるリストに転送されます。  
  
 次の表では、並べ替えとフィルター処理に使用するプロパティについて説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingListView> である場合は、表示する行のフィルター処理に使用する式を取得または設定します。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingList> である場合は、並べ替えに使用する列名と並べ替え順序情報を取得または設定します。<br /><br /> - または -<br /><br /> データ ソースがある場合、<xref:System.ComponentModel.IBindingListView>し並べ替え、高度なサポートは、並べ替えと並べ替え順序を使用する複数の列名を取得します。|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator の統合  
 使用することができます、<xref:System.Windows.Forms.BindingSource>任意の Windows フォーム コントロールをデータ ソースにバインドするコンポーネントが、<xref:System.Windows.Forms.BindingNavigator>コントロールが操作専用にデザインされた、<xref:System.Windows.Forms.BindingSource>コンポーネント。 <xref:System.Windows.Forms.BindingNavigator>コントロールを制御するためのユーザー インターフェイスを提供する、<xref:System.Windows.Forms.BindingSource>コンポーネントの現在の項目。 既定で、<xref:System.Windows.Forms.BindingNavigator>コントロールのナビゲーション メソッドに対応するボタンを提供する、<xref:System.Windows.Forms.BindingSource>コンポーネント。 詳細については、「[方法 :Windows フォーム BindingNavigator コントロールでデータ間を移動](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource コンポーネントの概要](bindingsource-component-overview.md)
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [方法: Windows フォーム コントロールを型にバインドします。](how-to-bind-a-windows-forms-control-to-a-type.md)
- [方法: BindingSource で Windows フォーム コントロール内のデータ ソースの更新が反映されます。](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
