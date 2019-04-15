---
title: '方法: DataGrid コントロールに行の詳細を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317893"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>方法: DataGrid コントロールに行の詳細を追加する
使用する場合、<xref:System.Windows.Controls.DataGrid>コントロール、行の詳細セクションを追加してデータの表示をカスタマイズすることができます。 行の詳細セクションを追加するには、必要に応じて表示されるか、折りたたまれたテンプレートの一部のデータをグループ化することができます。 行の詳細を追加するなど、<xref:System.Windows.Controls.DataGrid>内の各行のデータの概要のみを提示する、<xref:System.Windows.Controls.DataGrid>行を選択すると、他のデータ フィールドを表示しますが、します。 行の詳細」セクションのテンプレートを定義する、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティ。 次の図は、行の詳細セクションの例を示します。  
  
 ![行の詳細を表示する DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 行詳細テンプレートは、インライン XAML、またはリソースとして定義します。 どちらの方法は、次の手順で表示されます。 テンプレートを再作成せず、プロジェクト全体でリソースとして追加されるデータ テンプレートを使用できます。 インライン XAML が定義されているコントロールからアクセス可能なだけ追加されるデータ テンプレート。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>インライン XAML を使用して行の詳細を表示するには  
  
1. 作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。  
  
2. <xref:System.Windows.Controls.DataGrid> 要素に、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 要素を追加します。  
  
3. 作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。  
  
     次の XAML に示す、<xref:System.Windows.Controls.DataGrid>および定義する方法、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>インラインです。 <xref:System.Windows.Controls.DataGrid>表示 3 つの値行ごとに 3 つ以上の値、行が選択されているときにします。  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     次のコードに表示されるデータを選択するために使用するクエリを示しています、<xref:System.Windows.Controls.DataGrid>します。 この例では、クエリは、顧客情報を含むエンティティからデータを選択します。  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>リソースを使用して行の詳細を表示するには  
  
1. 作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。  
  
2. 追加、<xref:System.Windows.FrameworkElement.Resources%2A>要素をルート要素など、<xref:System.Windows.Window>コントロールまたは<xref:System.Windows.Controls.Page>制御、または追加を<xref:System.Windows.Application.Resources%2A>要素を<xref:System.Windows.Application>App.xaml (または Application.xaml) ファイル内のクラス。  
  
3. リソースの要素で作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。  
  
     次の XAML に示す、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>で定義されている、<xref:System.Windows.Application>クラス。  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <xref:System.Windows.DataTemplate>、設定、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)データ テンプレートを一意に識別する値にします。  
  
5. <xref:System.Windows.Controls.DataGrid>要素、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>前の手順で定義されたリソースへのプロパティ。 静的リソースとしてリソースを割り当てます。  
  
     次の XAML に示す、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティが、前の例のリソースに設定します。  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>可視性を設定し、行の詳細を水平方向にスクロールできないようにするには  
  
1. 必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>プロパティを<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>値。  
  
     値の設定既定では、<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>します。 設定することができます<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>すべての行の詳細を表示または<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>すべての行の詳細を非表示にします。  
  
2. 必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>プロパティを`true`行を防ぐための詳細セクションの水平方向にスクロールします。
