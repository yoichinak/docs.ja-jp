---
title: '方法: グループ化、並べ替え、およびデータ グリッド コントロールでデータをフィルター処理'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 81fdb0a6d5602f612c55d7e790ca9a0fe56c144e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365049"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>方法: グループ、並べ替え、およびデータ グリッド コントロールでデータのフィルター選択

内のデータを表示すると便利です、<xref:System.Windows.Controls.DataGrid>でさまざまな方法でグループ化、並べ替え、およびデータのフィルター処理します。 グループ化、並べ替え、およびデータをフィルター処理、<xref:System.Windows.Controls.DataGrid>にバインドする、<xref:System.Windows.Data.CollectionView>これらの関数をサポートします。 内のデータを操作することができますし、<xref:System.Windows.Data.CollectionView>基になるソース データには影響しません。 コレクション ビューの変更に反映されます、<xref:System.Windows.Controls.DataGrid>ユーザー インターフェイス (UI)。

<xref:System.Windows.Data.CollectionView>クラスには、グループ化と並べ替えを実装するデータ ソースの機能が用意されています、<xref:System.Collections.IEnumerable>インターフェイス。 <xref:System.Windows.Data.CollectionViewSource>クラスでは、プロパティを設定することができます、 <xref:System.Windows.Data.CollectionView> XAML から。

この例では、コレクションで`Task`にオブジェクトがバインドされている、<xref:System.Windows.Data.CollectionViewSource>します。 <xref:System.Windows.Data.CollectionViewSource>として提供される、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.DataGrid>します。 グループ化、並べ替え、およびフィルター処理を実行、<xref:System.Windows.Data.CollectionViewSource>に表示されると、 <xref:System.Windows.Controls.DataGrid> UI。

![データ グリッド内のデータをグループ化](././media/wpf-datagridgroups.png "WPF_DataGridGroups")データ グリッド内のデータをグループ化

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>ItemsSource として、CollectionViewSource を使用します。

グループ、並べ替え、およびデータのフィルター処理する、<xref:System.Windows.Controls.DataGrid>コントロールをバインドする、<xref:System.Windows.Controls.DataGrid>を<xref:System.Windows.Data.CollectionView>これらの関数をサポートします。 この例で、<xref:System.Windows.Controls.DataGrid>にバインドされて、<xref:System.Windows.Data.CollectionViewSource>のこれらの関数を提供する、<xref:System.Collections.Generic.List%601>の`Task`オブジェクト。

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>データ グリッドを CollectionViewSource にバインドするには

1. 実装するデータ コレクションを作成、<xref:System.Collections.IEnumerable>インターフェイス。

    使用する場合<xref:System.Collections.Generic.List%601>、コレクションを作成するから継承する新しいクラスを作成する必要があります<xref:System.Collections.Generic.List%601>のインスタンスをインスタンス化ではなく<xref:System.Collections.Generic.List%601>します。 これにより、XAML 内のコレクションにデータをバインドすることができます。

    > [!NOTE]
    > コレクション内のオブジェクトを実装する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>変更されたインターフェイスと<xref:System.ComponentModel.IEditableObject>インターフェイスの順序で、<xref:System.Windows.Controls.DataGrid>プロパティの変更と編集に正しく応答します。 詳細については、「[プロパティの変更通知を実装する](../data/how-to-implement-property-change-notification.md)」を参照してください。

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. XAML コレクション クラスのインスタンスを作成し、設定、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)します。

3. XAML でのインスタンスを作成、<xref:System.Windows.Data.CollectionViewSource>クラス、設定、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)、として、コレクション クラスのインスタンスを設定し、 <xref:System.Windows.Data.CollectionViewSource.Source%2A>。

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. インスタンスを作成、<xref:System.Windows.Controls.DataGrid>クラスし、設定、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティを<xref:System.Windows.Data.CollectionViewSource>します。

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. アクセスする、 <xref:System.Windows.Data.CollectionViewSource> 、コードから使用して、<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A>への参照を取得するメソッド、<xref:System.Windows.Data.CollectionViewSource>します。

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>データ グリッド内の項目をグループ化

項目をグループ化する方法を指定する、<xref:System.Windows.Controls.DataGrid>を使用する、<xref:System.Windows.Data.PropertyGroupDescription>ソース ビュー内の項目をグループ化する型。

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>XAML を使用してデータ グリッド内の項目をグループ化する

1. 作成、<xref:System.Windows.Data.PropertyGroupDescription>でグループ化するプロパティを指定します。 XAML またはコードでプロパティを指定することができます。

   1. XAML、設定、<xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A>でグループ化するプロパティの名前にします。

   2. コードでは、コンス トラクターにグループ化するプロパティの名前を渡します。

2. 追加、<xref:System.Windows.Data.PropertyGroupDescription>を<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType>コレクション。

3. インスタンスを追加<xref:System.Windows.Data.PropertyGroupDescription>を<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>複数レベルのグループ化を追加するコレクション。

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. グループを削除するには、削除、<xref:System.Windows.Data.PropertyGroupDescription>から、<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>コレクション。

5. すべてのグループを削除するには、呼び出し、<xref:System.Collections.ObjectModel.Collection%601.Clear%2A>のメソッド、<xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A>コレクション。

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

項目をグループ化するときに、 <xref:System.Windows.Controls.DataGrid>、定義することができます、<xref:System.Windows.Controls.GroupStyle>各グループの外観を指定します。 適用する、<xref:System.Windows.Controls.GroupStyle>に追加することによって、 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> DataGrid のコレクション。 複数のレベルのグループ化した場合は、グループ レベルごとに異なるスタイルを適用できます。 スタイルが定義されている順序で適用されます。 たとえば、2 つのスタイルを定義する場合、最初適用して、最上位レベルの行グループには。 2 番目のスタイルは、2 番目のレベルですべての行グループに適用されると下限になります。 <xref:System.Windows.FrameworkElement.DataContext%2A>の<xref:System.Windows.Controls.GroupStyle>は、<xref:System.Windows.Data.CollectionViewGroup>グループを表す。

### <a name="to-change-the-appearance-of-row-group-headers"></a>行グループ ヘッダーの外観を変更するには

1. 作成、<xref:System.Windows.Controls.GroupStyle>行グループの外観を定義します。

2. 配置、<xref:System.Windows.Controls.GroupStyle>内で、`<DataGrid.GroupStyle>`タグ。

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>データ グリッド内の項目を並べ替え

項目の並べ替え方法を指定する、<xref:System.Windows.Controls.DataGrid>を使用する、<xref:System.ComponentModel.SortDescription>ソース ビューの項目を並べ替える型。

### <a name="to-sort-items-in-a-datagrid"></a>DataGrid の項目を並べ替える

1. 作成、<xref:System.ComponentModel.SortDescription>を並べ替えるには、プロパティを指定します。 XAML またはコードでプロパティを指定することができます。

    1. XAML では、設定、<xref:System.ComponentModel.SortDescription.PropertyName%2A>を並べ替えるには、プロパティの名前にします。

    2. コードを並べ替えるにはプロパティの名前を渡すと、<xref:System.ComponentModel.ListSortDirection>コンス トラクターにします。

2. 追加、<xref:System.ComponentModel.SortDescription>を<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType>コレクション。

3. インスタンスを追加<xref:System.ComponentModel.SortDescription>を<xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A>コレクションに追加のプロパティを並べ替えます。

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>データ グリッド内の項目をフィルター処理

項目をフィルター処理する、<xref:System.Windows.Controls.DataGrid>を使用して、 <xref:System.Windows.Data.CollectionViewSource>、用のハンドラーでフィルタ リング ロジックを提供する、<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>イベント。

### <a name="to-filter-items-in-a-datagrid"></a>データ グリッド内の項目をフィルター処理するには

1. ハンドラーを追加、<xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType>イベント。

2. <xref:System.Windows.Data.CollectionViewSource.Filter>イベント ハンドラーでは、フィルタ リング ロジックを定義します。

    ビューが更新されるたびに、フィルターを適用します。

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

内の項目をフィルター処理する代わりに、<xref:System.Windows.Controls.DataGrid>フィルター処理のロジックと設定を提供するメソッドを作成して、<xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType>フィルターを適用するプロパティ。 このメソッドの例を表示するには、次を参照してください。[ビュー内のフィルター データ](../data/how-to-filter-data-in-a-view.md)します。

## <a name="example"></a>例

次の例は、グループ化、並べ替え、およびフィルター処理`Task`内のデータを<xref:System.Windows.Data.CollectionViewSource>表示、並べ替え、フィルターにグループ化、および`Task`内のデータを<xref:System.Windows.Controls.DataGrid>します。 <xref:System.Windows.Data.CollectionViewSource>として提供される、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.DataGrid>します。 グループ化、並べ替え、およびフィルター処理を実行、<xref:System.Windows.Data.CollectionViewSource>に表示されると、 <xref:System.Windows.Controls.DataGrid> UI。

この例をテストするには、プロジェクト名と一致する DGGroupSortFilterExample 名前を調整する必要があります。 Visual Basic を使用している場合は、クラス名を変更する必要があります。<xref:System.Windows.Window>以下。

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>関連項目

- [データ バインディングの概要](../data/data-binding-overview.md)
- [ObservableCollection を作成およびバインドする](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [ビュー内のデータをフィルター処理する](../data/how-to-filter-data-in-a-view.md)
- [ビュー内のデータの並べ替え](../data/how-to-sort-data-in-a-view.md)
- [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
