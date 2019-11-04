---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: dda712d58a4ff956de074ecd416402ba0aece5f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912237"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>コントロールでは、 SQL データベース、LINQ クエリ、またはその他のバインド可能なデータ ソースからなど、さまざまなソースからデータを表示および編集することができます。 詳しくは、「[バインディング ソースの概要](../data/binding-sources-overview.md)」をご覧ください。  
  
 列がなど、コントロールのテキストを表示できます、 <xref:System.Windows.Controls.ComboBox>、またはイメージ、ボタン、またはテンプレートに含まれるすべてのコンテンツなどの他の WPF コンテンツ。 使用することができます、<xref:System.Windows.Controls.DataGridTemplateColumn>テンプレートで定義されているデータを表示します。 次の表では、既定で用意されている列の型を示します。  
  
|生成された列の型|データの種類|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> セルのフォント、色、サイズなどの外観をカスタマイズできます。 <xref:System.Windows.Controls.DataGrid> その他の WPF コントロールのすべてのスタイルとテンプレートの機能をサポートしています。 <xref:System.Windows.Controls.DataGrid> 既定とカスタマイズ可能な動作の編集、並べ替え、および検証も含まれています。  
  
 次の表に、<xref:System.Windows.Controls.DataGrid> を使用して実現できる、いくつかの一般的なタスクの一覧を示します。 関連する API を表示することで、詳細情報とサンプル コードを取得できます。  
  
|シナリオ|方法|  
|--------------|--------------|  
|代替背景色|設定、 <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> 2 以上のプロパティを割り当てます、<xref:System.Windows.Media.Brush>を<xref:System.Windows.Controls.DataGrid.RowBackground%2A>と<xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>プロパティ。|  
|セルと行の選択の動作を定義します。|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティと <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> プロパティを設定します。|  
|ヘッダーとセル、および行の外観をカスタマイズします。|新規の <xref:System.Windows.Style> を <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.CellStyle%2A>、<xref:System.Windows.Controls.DataGrid.RowStyle%2A> プロパティに適用します。|  
|サイズ変更オプションを設定します。|設定、 <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>、 <xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、または<xref:System.Windows.FrameworkElement.MinWidth%2A>プロパティ。 詳細については、次を参照してください。 [DataGrid コントロールのサイズ変更オプション](sizing-options-in-the-datagrid-control.md)します。|  
|項目にアクセスする選択|チェック、 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> 、選択したセルを取得するプロパティと<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A>プロパティを選択した行を取得します。 詳細については、「 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> 」を参照してください。|  
|エンドユーザーの相互作用をカスタマイズします。|<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>、<xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>、<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>、<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> プロパティを設定します。|  
|自動生成された列をキャンセルまたは変更します。|<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> イベントをハンドルします。|  
|列を固定します。|<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> プロパティを 1 に設定し、<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> プロパティを 0 に設定して、列を左端に移動します。|  
|XML データをデータ ソースとして使用します|<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 上の <xref:System.Windows.Controls.DataGrid> を項目のコレクションを表す XPath クエリにバインドします。 <xref:System.Windows.Controls.DataGrid> に各列を作成します。 項目のソースのプロパティを取得するクエリへのバインドで、XPath を設定して、各列をバインドします。 例については、「<xref:System.Windows.Controls.DataGridTextColumn>」を参照してください。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: DataGrid コントロールでの SQL Server データベースのデータを表示](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|エンティティ フレームワーク要素を追加する新しい WPF プロジェクトをセットアップ、設定、ソース内のデータを表示する方法について説明します、<xref:System.Windows.Controls.DataGrid>します。|  
|[方法: DataGrid コントロールに行の詳細を追加します。](how-to-add-row-details-to-a-datagrid-control.md)|行の詳細を作成する方法について説明します、<xref:System.Windows.Controls.DataGrid>します。|  
|[方法: DataGrid コントロールに検証を実装します。](how-to-implement-validation-with-the-datagrid-control.md)|値を検証する方法について説明します<xref:System.Windows.Controls.DataGrid>セルと行、および検証のフィードバックを表示します。|  
|[DataGrid コントロールの既定のキーボード動作とマウス動作](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|対話する方法について説明します、<xref:System.Windows.Controls.DataGrid>キーボードとマウスを使用して制御します。|  
|[方法: グループ、並べ替え、およびデータ グリッド コントロールでデータのフィルター選択](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|データを表示する方法について説明します、<xref:System.Windows.Controls.DataGrid>でさまざまな方法でグループ化、並べ替え、およびデータのフィルター処理します。|  
|[DataGrid コントロールのサイズ変更方法](sizing-options-in-the-datagrid-control.md)|絶対と自動サイズ設定を制御する方法について説明します、<xref:System.Windows.Controls.DataGrid>します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataGrid>
- [スタイルとテンプレート](styling-and-templating.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
- [コントロール](index.md)
- [WPF のコンテンツ モデル](wpf-content-model.md)
