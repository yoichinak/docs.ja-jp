---
title: データ バインディング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: f07053c9fba194138467bbf8664e2f5fe1f667ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352819"
---
# <a name="data-binding"></a>データ バインディング

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] グリッド コントロールなどの一般的なコントロールへのバインドをサポートします。 具体的には、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]データ グリッドにバインドし、マスター/詳細バインド、両方の表示と更新点の処理の基本的なパターンを定義します。

## <a name="underlying-principle"></a>基本原則

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 変換[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]to SQL のクエリがデータベース上で実行します。 その結果は、厳密に型指定された `IEnumerable` になります。 これらのオブジェクトは通常の共通言語ランタイム (CLR: Common Language Runtime) オブジェクトであるため、一般的なオブジェクト データ バインディングを使用して結果を表示できます。 一方、変更操作 (挿入、更新、および削除) には、追加的な手順が必要です。

## <a name="operation"></a>操作

Windows フォーム コントロールに対する暗黙バインディングは、<xref:System.ComponentModel.IListSource> を実装することで実現されます。 データ ソース ジェネリック<xref:System.Data.Linq.Table%601>(`Table<T>`でC#または`Table(Of T)`Visual basic) と汎用`DataQuery`が実装するために更新されました<xref:System.ComponentModel.IListSource>します。 ユーザー インターフェイス (UI) データ バインディング エンジン (Windows フォームおよび Windows Presentation Foundation) はいずれも、データ ソースが <xref:System.ComponentModel.IListSource> を実装しているかどうかをテストします。 そのため、直接表示を作成、クエリのコントロールのデータ ソースに暗黙的に呼び出し[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]次の例のように、コレクションの生成。

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Windows Presentation Foundation でも同じようになります。

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

コレクション生成は、ジェネリック <xref:System.Data.Linq.Table%601> およびジェネリック `DataQuery` によって <xref:System.ComponentModel.IListSource.GetList%2A> で実装されます。

## <a name="ilistsource-implementation"></a>IListSource の実装

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 実装<xref:System.ComponentModel.IListSource>2 つの場所。

- データ ソースが、 <xref:System.Data.Linq.Table%601>:[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]設定するテーブルを参照する、`DataBindingList`テーブル参照を保持するコレクション。

- データ ソースが <xref:System.Linq.IQueryable%601> の場合 :  次の 2 つのシナリオがあります。

    - 場合[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、基になる検索<xref:System.Data.Linq.Table%601>から、 <xref:System.Linq.IQueryable%601>edition により、ソース、および、状況は、最初の箇条書きの場合と同様です。

    - 場合[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、基になるを見つけることができません<xref:System.Data.Linq.Table%601>、エディション、ソースは許可されません (たとえば、 `groupby`)。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ジェネリック型を格納するクエリを参照する`SortableBindingList`、これは、単純な<xref:System.ComponentModel.BindingList%601>による T エンティティの特定のプロパティの並べ替え機能を実装します。

## <a name="specialized-collections"></a>専用コレクション

このドキュメントでここまでに説明した多くの機能について、<xref:System.ComponentModel.BindingList%601> を特化したクラスが用意されています。 ジェネリック `SortableBindingList` クラスと、ジェネリック `DataBindingList` クラスです。 いずれも内部クラスとして宣言されています。

### <a name="generic-sortablebindinglist"></a>ジェネリック SortableBindingList

これは <xref:System.ComponentModel.BindingList%601> を継承したクラスで、並べ替え可能な <xref:System.ComponentModel.BindingList%601> です。 並べ替えはメモリ内で処理され、データベース自体とのやり取りは行われません。 <xref:System.ComponentModel.BindingList%601> は <xref:System.ComponentModel.IBindingList> を実装していますが、既定では並べ替えをサポートしていません。 ただし、<xref:System.ComponentModel.BindingList%601>実装<xref:System.ComponentModel.IBindingList>仮想*core*メソッド。 これらのメソッドを簡単にオーバーライドできます。 ジェネリック `SortableBindingList` は、<xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>、<xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>、<xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>、および <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A> をオーバーライドします。 `ApplySortCore` は <xref:System.ComponentModel.IBindingList.ApplySort%2A> によって呼び出され、指定のプロパティで T の項目のリストを並べ替えます。

そのプロパティが T にない場合、例外が発生します。

並べ替えなどを実現するために[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ジェネリック型を作成します。`SortableBindingList.PropertyComparer`ジェネリックから継承するクラスを<xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A>し、指定された型 T の既定の比較子を実装、 `PropertyDescriptor`、と方向。 このクラスは、T の `Comparer` を動的に作成します (T は `PropertyType` の `PropertyDescriptor`)。 そして、静的なジェネリック `Comparer` から既定の比較子が取得されます。 既定のインスタンスはリフレクションを使用して取得されます。

ジェネリック `SortableBindingList` は `DataBindingList` の基本クラスでもあります。 ジェネリック `SortableBindingList` には、項目の追加と削除の追跡を中断および再開するための 2 つの仮想メソッドがあります。 これら 2 つのメソッドは、並べ替えなどの基本機能にも使用できますが、実際にはジェネリック `DataBindingList` などの上位クラスによって実装されます。

### <a name="generic-databindinglist"></a>ジェネリック DataBindingList

このクラスは、ジェネリック `SortableBindingLIst` を継承しています。 ジェネリック `DataBindingList` は、最初にコレクションの読み込みに使用したジェネリック `Table` の基になるジェネリック `IQueryable` に対する参照を保持しています。 ジェネリック `DatabindingList` では、`InsertItem`() と `RemoveItem`() がオーバーライドされて、コレクションに対する項目の追加と削除を追跡する処理が追加されています。 また、追跡を中断および再開する機能の抽象メソッドが実装され、条件に応じた追跡が可能となっています。 この結果、ジェネリック `DataBindingList` では、親クラスが持つ追跡機能のポリモーフィックな使用法がすべて活用されています。

## <a name="binding-to-entitysets"></a>EntitySet へのバインディング


  `EntitySet` へのバインディングは特別なケースです。`EntitySet` は既に、<xref:System.ComponentModel.IBindingList> を実装したコレクションであるためです。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 並べ替えとキャンセルを追加します (<xref:System.ComponentModel.ICancelAddNew>) をサポートします。 
  `EntitySet` クラスは内部リストを使用してエンティティを格納します。 このリストは、ジェネリック配列 (ジェネリック `ItemList` クラス) を基にした低水準のコレクションです。

### <a name="adding-a-sorting-feature"></a>並べ替え機能の追加

Array には、T の `Array.Sort()` を使用できる並べ替えメソッド (`Comparer`) があります。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、このトピックで前に説明したジェネリック `SortableBindingList.PropertyComparer` クラスを使用して、プロパティに応じた `Comparer` と、並べ替えの方向を取得します。 ジェネリック `ApplySort` には、この機能を呼び出すための `ItemList` メソッドが追加されています。

`EntitySet` 側では、並べ替えのサポートを次のように宣言する必要があります。

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> は、`true` を返します。

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> では、`entities.ApplySort()` を呼び出した後で `OnListChanged()` を呼び出します。

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> プロパティおよび <xref:System.ComponentModel.IBindingList.SortProperty%2A> プロパティでは、現在の並べ替えの定義を公開します。これはローカル メンバーに格納されています。

System.Windows.Forms.BindingSource を使用し、entityset\<TEntity >、System.Windows.Forms.BindingSource.DataSource に EntitySet を呼び出す必要があります\<TEntity >。GetNewBindingList BindingSource.List を更新します。

System.Windows.Forms.BindingSource を使用して、BindingSource.DataMember プロパティを設定してかどうかを EntitySet を公開する BindingSource.DataMember でという名前のプロパティを持つクラスに BindingSource.DataSource を設定した\<TEntity > をします。EntitySet を呼び出す必要はありません\<TEntity >。GetNewBindingList、BindingSource.List を更新するには、並べ替え機能が失われます。

## <a name="caching"></a>キャッシュ

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの実装<xref:System.ComponentModel.IListSource.GetList%2A>します。 Windows フォームの BindingSource クラスは、このインターフェイスがあると、1 つの接続に対して GetList() を 3 回呼び出します。 このような状況を回避する[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]を格納し、常に生成された、同じコレクションを返しますのインスタンスごとにキャッシュを実装します。

## <a name="cancellation"></a>キャンセル

<xref:System.ComponentModel.IBindingList> には <xref:System.ComponentModel.IBindingList.AddNew%2A> メソッドが定義されています。バインドされたコレクションから新しい項目を作成するためにコントロールが使用するメソッドです。 `DataGridView` コントロールでは、表示されている最後の行のヘッダーにアスタリスクが表示されている状況で、この機能が明確に示されます。 このアスタリスクは、新しい項目を追加できることを示します。

コレクションは、この機能に加えて、<xref:System.ComponentModel.ICancelAddNew> も実装することができます。 この機能によって、コントロールでは、キャンセルを行ったり、新しく編集された項目が検証されているかどうかを確認したりできるようになります。

<xref:System.ComponentModel.ICancelAddNew> は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のすべてのデータ バインド コレクション (ジェネリック `SortableBindingList` およびジェネリック `EntitySet`) に実装されます。 どちらの実装でも、コードは次のように動作します。

- いったん挿入した項目をコレクションから削除できます。

- UI が編集をコミットしていない場合、変更を追跡しません。

- 編集がキャンセルされた場合 (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>)、変更を追跡しません。

- 編集がコミットされた場合 (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>)、追跡を行うことができます。

- 新しい項目が <xref:System.ComponentModel.IBindingList.AddNew%2A> で追加されたものでない場合、コレクションは通常どおり動作します。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のデータ バインディング アプリケーションのトラブルシューティングに役立つ可能性がある項目について説明します。

- プロパティを使用する必要があります。フィールドのみの使用では不十分です。 この使用は Windows フォームで必要です。

- 既定では、 `image`、 `varbinary`、および`timestamp`データベース型はバイト配列にマップします。 このシナリオでは `ToString()` がサポートされていないため、これらのオブジェクトは表示できません。

- 主キーにマップされているクラスのメンバーは setter が[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト id の変更をサポートしていません。 したがって、対応付けで使用されているデータベースの主キー/一意キーは更新できません。 グリッド内の変更を呼び出すと、例外の原因<xref:System.Data.Linq.DataContext.SubmitChanges%2A>します。

- 1 つのエンティティが 2 つの別個のグリッド (たとえばマスター グリッドと詳細グリッド) にバインドされている場合、マスター グリッドで `Delete` を行っても、詳細グリッドには反映されません。

## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
