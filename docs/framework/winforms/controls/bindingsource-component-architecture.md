---
title: BindingSource コンポーネント アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364409"
---
# <a name="bindingsource-component-architecture"></a>BindingSource コンポーネント アーキテクチャ
<xref:System.Windows.Forms.BindingSource>コンポーネントを使用すると、すべての Windows フォームコントロールをデータソースにユニバーサルにバインドできます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを使用すると、コントロールをデータソースにバインドするプロセスが簡略化され、従来のデータバインドよりも次のような利点があります。  
  
- ビジネスオブジェクトに対するデザイン時のバインドを有効にします。  
  
- 機能<xref:System.Windows.Forms.CurrencyManager>をカプセル化<xref:System.Windows.Forms.CurrencyManager>し、デザイン時にイベントを公開します。  
  
- リスト変更通知をネイティブでサポート<xref:System.ComponentModel.IBindingList>していないデータソースに対してリスト変更通知を提供することにより、インターフェイスをサポートするリストの作成を簡略化します。  
  
- <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType>メソッドの機能拡張ポイントを提供します。  
  
- データソースとコントロールの間に間接的なレベルの間接参照を提供します。 この間接参照は、データソースが実行時に変更される可能性がある場合に重要です。  
  
- 他のデータ関連の Windows フォームコントロール、特<xref:System.Windows.Forms.BindingNavigator>に<xref:System.Windows.Forms.DataGridView>およびコントロールと相互運用します。  
  
 このような理由から<xref:System.Windows.Forms.BindingSource> 、Windows フォームコントロールをデータソースにバインドするには、コンポーネントを使用することをお勧めします。  
  
## <a name="bindingsource-features"></a>BindingSource の機能  
 コンポーネント<xref:System.Windows.Forms.BindingSource>には、コントロールをデータにバインドするための機能がいくつか用意されています。 これらの機能を使用すると、ほとんどのコーディングを行わずにほとんどのデータバインディングシナリオを実装できます。  
  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、さまざまな種類のデータソースにアクセスするための一貫したインターフェイスを提供することによってこれを実現します。 これは、任意の型へのバインドに同じ手順を使用することを意味します。 たとえば、 <xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティ<xref:System.Data.DataSet>をまたはビジネスオブジェクトにアタッチすることができ、どちらの場合も、同じプロパティ、メソッド、およびイベントのセットを使用してデータソースを操作します。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントによって提供される一貫したインターフェイスにより、データをコントロールにバインドするプロセスが大幅に簡略化されます。 変更通知を提供するデータソースの種類の場合<xref:System.Windows.Forms.BindingSource> 、コンポーネントはコントロールとデータソースの間の変更を自動的に伝達します。 変更通知を提供しないデータソースの種類の場合、変更通知を発生させるためのイベントが提供されます。 次の一覧に、 <xref:System.Windows.Forms.BindingSource>コンポーネントでサポートされる機能を示します。  
  
- 演算.  
  
- 通貨管理。  
  
- リストとしてのデータソース。  
  
- <xref:System.Windows.Forms.BindingSource>として。 <xref:System.ComponentModel.IBindingList>  
  
- カスタム項目の作成。  
  
- トランザクション項目の作成。  
  
- <xref:System.Collections.IEnumerable>ご.  
  
- デザイン時サポート。  
  
- 静的<xref:System.Windows.Forms.ListBindingHelper>メソッド。  
  
- <xref:System.ComponentModel.IBindingListView>インターフェイスを使用した並べ替えとフィルター処理。  
  
- との<xref:System.Windows.Forms.BindingNavigator>統合。  
  
### <a name="indirection"></a>間接  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、コントロールとデータソースの間に間接的なレベルの間接参照を提供します。 コントロールをデータソースに直接バインドするのでは<xref:System.Windows.Forms.BindingSource>なく、コントロールをにバインドし、 <xref:System.Windows.Forms.BindingSource>コンポーネントの<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティにデータソースをアタッチします。  
  
 このレベルの間接参照を使用すると、コントロールバインドをリセットせずにデータソースを変更できます。 これにより、次の機能が提供されます。  
  
- 現在のコントロールバインド<xref:System.Windows.Forms.BindingSource>を保持したまま、を別のデータソースにアタッチできます。  
  
- データソース内の項目を変更し、バインドされたコントロールに通知できます。 詳細については、「[方法 :BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)を使用して Windows フォームコントロールのデータソースの更新を反映します。  
  
- メモリ内のオブジェクトの<xref:System.Type>代わりに、にバインドできます。 詳細については、「[方法 :Windows フォームコントロールを型](how-to-bind-a-windows-forms-control-to-a-type.md)にバインドします。 その後、実行時にオブジェクトにバインドできます。  
  
### <a name="currency-management"></a>通貨管理  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、通貨<xref:System.Windows.Forms.ICurrencyManagerProvider>管理を処理するためのインターフェイスを実装します。 インターフェイスを使用すると、同じ<xref:System.Windows.Forms.BindingSource.DataMember%2A>にバインドされている別<xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource>の通貨マネージャーに加えて、の通貨マネージャーにアクセスすることもできます。 <xref:System.Windows.Forms.ICurrencyManagerProvider>  
  
 コンポーネント<xref:System.Windows.Forms.BindingSource>には<xref:System.Windows.Forms.CurrencyManager> 、機能がカプセル化さ<xref:System.Windows.Forms.CurrencyManager>れており、最も一般的なプロパティとイベントが公開されています。 次の表では、通貨管理に関連する一部のメンバーについて説明します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> プロパティ  
 に関連付けられている<xref:System.Windows.Forms.BindingSource>通貨マネージャーを取得します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> メソッド  
 指定された<xref:System.Windows.Forms.BindingSource>データメンバーに別のバインドがある場合は、その通貨マネージャーを取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> プロパティ  
 データソースの現在の項目を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティ  
 基になるリストでの現在の位置を取得または設定します。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッド  
 基になるデータ ソースに保留中の変更を適用します。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> メソッド  
 現在の編集操作をキャンセルします。  
  
### <a name="data-source-as-a-list"></a>リストとしてのデータソース  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、インターフェイス<xref:System.ComponentModel.IBindingListView>と<xref:System.ComponentModel.ITypedList>インターフェイスを実装します。 この実装では、外部ストレージを<xref:System.Windows.Forms.BindingSource>使用せずに、コンポーネント自体をデータソースとして使用できます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントがデータソースにアタッチされると、データソースがリストとして公開されます。  
  
 プロパティ<xref:System.Windows.Forms.BindingSource.DataSource%2A>は、複数のデータソースに設定できます。 これには、型、オブジェクト、および型のリストが含まれます。 結果として得られるデータソースはリストとして公開されます。 次の表は、いくつかの一般的なデータソースと結果の一覧の評価を示しています。  
  
|DataSource プロパティ|結果の一覧表示|  
|-------------------------|------------------|  
|null 参照 (Visual Basic の場合は `Nothing`)。|オブジェクトの<xref:System.ComponentModel.IBindingList>空の。 項目を追加すると、追加した項目の種類にリストが設定されます。|  
|Set を使用し`Nothing`た<xref:System.Windows.Forms.BindingSource.DataMember%2A> null 参照 (Visual Basic)|サポートされていません。を<xref:System.ArgumentException>発生させます。|  
|非リスト型または型 "T" のオブジェクト|型 " <xref:System.ComponentModel.IBindingList> T" の空の。|  
|配列インスタンス|配列<xref:System.ComponentModel.IBindingList>要素を格納している。|  
|<xref:System.Collections.IEnumerable>instance|項目を格納している<xref:System.Collections.IEnumerable>。 <xref:System.ComponentModel.IBindingList>|  
|型 "T" を含むリストインスタンス|型 "T" を格納しているインスタンス。<xref:System.ComponentModel.IBindingList>|  
  
 また、 <xref:System.Windows.Forms.BindingSource.DataSource%2A>は、 <xref:System.ComponentModel.IListSource>や<xref:System.ComponentModel.ITypedList>などの他の種類のリストにも設定でき、では適切に処理されます。<xref:System.Windows.Forms.BindingSource> この場合、リストに含まれる型には、パラメーターなしのコンストラクターが必要です。  
  
### <a name="bindingsource-as-an-ibindinglist"></a>IBindingList としての BindingSource  
 コンポーネント<xref:System.Windows.Forms.BindingSource>には、基になるデータにアクセスし<xref:System.ComponentModel.IBindingList>て操作するためのメンバーが用意されています。 次の表では、これらのメンバーの一部について説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> プロパティ|プロパティ<xref:System.Windows.Forms.BindingSource.DataSource%2A>または<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティの評価の結果として得られるリストを取得します。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> メソッド|基になるリストに新しい項目を追加します。 <xref:System.ComponentModel.IBindingList>インターフェイスを実装し、項目の<xref:System.Windows.Forms.BindingSource.AllowNew%2A>追加を許可する (つまり、プロパティがに`true`設定されている) データソースに適用されます。|  
  
### <a name="custom-item-creation"></a>カスタム項目の作成  
 <xref:System.Windows.Forms.BindingSource.AddingNew>イベントを処理して、独自の項目作成ロジックを提供できます。 イベント<xref:System.Windows.Forms.BindingSource.AddingNew>は、 <xref:System.Windows.Forms.BindingSource>に新しいオブジェクトが追加される前に発生します。 このイベントは、 <xref:System.Windows.Forms.BindingSource.AddNew%2A>メソッドが呼び出された後、新しい項目が基になるリストに追加される前に発生します。 このイベントを処理することにより、 <xref:System.Windows.Forms.BindingSource>クラスから派生せずにカスタムの項目作成動作を提供できます。 詳細については、「[方法 :Windows フォーム BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)を使用して項目の追加をカスタマイズします。  
  
### <a name="transactional-item-creation"></a>トランザクション項目の作成  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、トランザクション<xref:System.ComponentModel.ICancelAddNew>アイテムの作成を可能にするインターフェイスを実装します。 の呼び出し<xref:System.Windows.Forms.BindingSource.AddNew%2A>を使用して新しい項目を仮に作成した後は、次の方法で追加をコミットまたはロールバックできます。  
  
- メソッド<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>は、保留中の加算を明示的にコミットします。  
  
- 挿入、削除、移動などの別のコレクション操作を実行すると、保留中の追加が暗黙的にコミットされます。  
  
- メソッド<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>がまだコミットされていない場合、メソッドは保留中の加算をロールバックします。  
  
### <a name="ienumerable-support"></a>IEnumerable のサポート  
 コンポーネント<xref:System.Windows.Forms.BindingSource>により、データソース<xref:System.Collections.IEnumerable>へのバインドコントロールが有効になります。 このコンポーネントを使用すると、などのデータソース<xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>にバインドできます。  
  
 <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.IBindingList> <xref:System.Collections.IEnumerable>データソースがコンポーネント<xref:System.Windows.Forms.BindingSource>に割り当てられると、によってが作成され、データソースの内容がリストに追加されます。 <xref:System.Collections.IEnumerable>  
  
### <a name="design-time-support"></a>デザイン時サポート  
 ファクトリクラスから作成されたオブジェクトや Web サービスによって返されるオブジェクトなど、デザイン時に作成できないオブジェクトの種類もあります。 コントロールをバインドできるメモリ内にオブジェクトがない場合でも、デザイン時にコントロールをこれらの型にバインドすることが必要になることがあります。 たとえば、 <xref:System.Windows.Forms.DataGridView>コントロールの列ヘッダーにカスタム型のパブリックプロパティの名前を付ける必要がある場合があります。  
  
 このシナリオをサポートするため<xref:System.Windows.Forms.BindingSource>に、コンポーネントはへ<xref:System.Type>のバインドをサポートしています。 を<xref:System.Type> <xref:System.Windows.Forms.BindingSource> <xref:System.ComponentModel.BindingList%601> <xref:System.Type>プロパティに割り当てると、コンポーネントによって空の項目が作成されます。 <xref:System.Windows.Forms.BindingSource.DataSource%2A> その後、 <xref:System.Windows.Forms.BindingSource>コンポーネントにバインドするコントロールは、デザイン時または実行時に型のプロパティまたはスキーマの存在について警告されます。 詳細については、「[方法 :Windows フォームコントロールを型](how-to-bind-a-windows-forms-control-to-a-type.md)にバインドします。  
  
### <a name="static-listbindinghelper-methods"></a>静的 ListBindingHelper メソッド  
 、 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType> `DataSource` / 、および型<xref:System.Windows.Forms.BindingSource>はすべて、 `DataMember`ペアからリストを生成するための共通のロジックを共有します。 <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType> また、この共通のロジックは、次`static`の方法でコントロールの作成者や他のサードパーティが使用するために公開されています。  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>。  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>IBindingListView インターフェイスを使用した並べ替えとフィルター処理  
 コンポーネント<xref:System.Windows.Forms.BindingSource>は、インターフェイス<xref:System.ComponentModel.IBindingListView>を拡張<xref:System.ComponentModel.IBindingList>するインターフェイスを実装します。 で<xref:System.ComponentModel.IBindingList>は、単一列の並べ替え<xref:System.ComponentModel.IBindingListView>と、による高度な並べ替えとフィルター処理が提供されています。 で<xref:System.ComponentModel.IBindingListView>は、データソースがこれらのインターフェイスのいずれかを実装している場合に、データソース内の項目の並べ替えとフィルター処理を行うことができます。 コンポーネント<xref:System.Windows.Forms.BindingSource>には、これらのメンバーの参照実装が用意されていません。 代わりに、呼び出しが基になるリストに転送されます。  
  
 次の表では、並べ替えとフィルター処理に使用するプロパティについて説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingListView> である場合は、表示する行のフィルター処理に使用する式を取得または設定します。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingList> である場合は、並べ替えに使用する列名と並べ替え順序情報を取得または設定します。<br /><br /> \- または -<br /><br /> データソースが<xref:System.ComponentModel.IBindingListView>で、高度な並べ替えをサポートしている場合、並べ替えと並べ替えの順序に使用される複数の列名を取得します。|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator との統合  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを使用すると、任意の Windows フォームコントロールをデータソースにバインドできます<xref:System.Windows.Forms.BindingNavigator>が、コントロールは<xref:System.Windows.Forms.BindingSource>特にコンポーネントを操作するように設計されています。 コントロール<xref:System.Windows.Forms.BindingNavigator>には、コンポーネントの現在の項目<xref:System.Windows.Forms.BindingSource>を制御するためのユーザーインターフェイスが用意されています。 既定<xref:System.Windows.Forms.BindingNavigator>では、コントロールには、 <xref:System.Windows.Forms.BindingSource>コンポーネントのナビゲーションメソッドに対応するボタンが用意されています。 詳細については、「[方法 :Windows フォーム BindingNavigator コントロール](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)を使用してデータを移動します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource コンポーネントの概要](bindingsource-component-overview.md)
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [方法: Windows フォームコントロールを型にバインドする](how-to-bind-a-windows-forms-control-to-a-type.md)
- [方法: BindingSource を使用して Windows フォームコントロールのデータソースの更新を反映する](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
