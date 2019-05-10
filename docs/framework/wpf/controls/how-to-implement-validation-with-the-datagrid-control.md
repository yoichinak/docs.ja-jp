---
title: '方法: DataGrid コントロールを使用して検証を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 6175e60b1dbdbdb31500f484da24b0f94990b2d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663341"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>方法: DataGrid コントロールを使用して検証を実装する
<xref:System.Windows.Controls.DataGrid>コントロールでは、セルと行の両方のレベルでの検証を実行することができます。 セル レベルの検証、ユーザーが値を更新したときに、バインドされたデータ オブジェクトの個々 のプロパティを検証します。 行レベルの検証、ユーザーが行への変更をコミット時に、データ オブジェクト全体を検証します。 検証エラーの場合は、カスタマイズされた視覚的なフィードバックを提供したり、既定の視覚的フィードバックを使用したりできる<xref:System.Windows.Controls.DataGrid>コントロールを提供します。  
  
 次の手順の検証ルールを適用する方法について説明<xref:System.Windows.Controls.DataGrid>バインドと、視覚的なフィードバックをカスタマイズします。  
  
### <a name="to-validate-individual-cell-values"></a>個々 のセルの値を検証するには  
  
- 列で使用されるバインディングの 1 つまたは複数の検証規則を指定します。 」の説明に従って、単純なコントロールのデータの検証に似ています[データ バインディングの概要](../data/data-binding-overview.md)します。  
  
     次の例は、<xref:System.Windows.Controls.DataGrid>ビジネス オブジェクトのさまざまなプロパティにバインドされている 4 つの列を持つコントロール。 3 つの列の指定、<xref:System.Windows.Controls.ExceptionValidationRule>を設定して、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>プロパティを`true`します。  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     (非整数コース ID 列) などの無効な値を入力すると、セルの周囲に赤い境界線が表示されます。 この既定の検証のフィードバックの次の手順に従って変更できます。  
  
### <a name="to-customize-cell-validation-feedback"></a>セルの検証のフィードバックをカスタマイズするには  
  
- セットの列の<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>列の編集コントロールのスタイル プロパティが適切な。 編集コントロールは、実行時に作成、ために使用できません、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>添付プロパティの単純なコントロールの場合と同様です。  
  
     次の例では、検証規則を次の 3 つの列で共有されるエラー スタイルを追加することで、前の例を更新します。 無効な値を入力すると、スタイルはセルの背景色を変更し、ツールヒントを追加します。 検証エラーがあるかどうかを判断するトリガーの使用に注意してください。 現在のセルのエラー テンプレートがないために必要です。  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     置き換えることより広範囲にわたるカスタマイズを実装することができます、<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>列で使用します。  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>1 つの行で複数の値を検証するには  
  
1. 実装を<xref:System.Windows.Controls.ValidationRule>バインドされたデータ オブジェクトの複数のプロパティをチェックするサブクラスです。 <xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドの実装のキャスト、`value`パラメーター値を<xref:System.Windows.Data.BindingGroup>インスタンス。 使用してデータ オブジェクトにアクセスできます、<xref:System.Windows.Data.BindingGroup.Items%2A>プロパティ。  
  
     次の例では、このプロセスを検証するかどうか、`StartDate`のプロパティの値を`Course`オブジェクトが以前よりもその`EndDate`プロパティの値。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. 検証規則の追加、<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>コレクション。 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>プロパティへの直接アクセスを提供する、<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>のプロパティを<xref:System.Windows.Data.BindingGroup>コントロールによって使用されるすべてのバインディングをグループ化するインスタンス。  
  
     次の例のセット、 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML プロパティ。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>プロパティに設定されて<xref:System.Windows.Controls.ValidationStep.UpdatedValue>バインドされたデータ オブジェクトが更新された後にのみ、検証が行われるようにします。  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     ユーザーは、開始日より前である終了日を指定する場合、行ヘッダーに赤色の感嘆符 (!) が表示されます。 この既定の検証のフィードバックの次の手順に従って変更できます。  
  
### <a name="to-customize-row-validation-feedback"></a>行の検証のフィードバックをカスタマイズするには  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> プロパティを設定します。 このプロパティでは、個々 の行の検証のフィードバックをカスタマイズできます。<xref:System.Windows.Controls.DataGrid>コントロール。 複数のコントロールを設定する、暗黙の行のスタイルを使用しても影響、<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>プロパティ。  
  
     次の例は、既定行の検証のフィードバックをよりわかりやすいインジケーターに置き換えます。 無効な値を入力すると、行ヘッダーに白い感嘆符の付いた赤い円が表示されます。 これは、行とセルの両方の検証エラーに対して発生します。 関連付けられたエラー メッセージは、ツールヒントに表示されます。  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>例  
 次の例では、セルと行の検証の完全なデモを提供します。 `Course`クラスを実装するサンプル データ オブジェクトを提供する<xref:System.ComponentModel.IEditableObject>トランザクションをサポートします。 <xref:System.Windows.Controls.DataGrid>コントロールとやり取り<xref:System.ComponentModel.IEditableObject>ESC キーを押して変更を元に戻すにユーザーを有効にします。  
  
> [!NOTE]
>  Visual Basic では、MainWindow.xaml の最初の行でを使用している場合は置き換えます`x:Class="DataGridValidation.MainWindow"`で`x:Class="MainWindow"`します。  
  
 検証をテストするには、次を試してください。  
  
- コース ID 列で整数以外の値を入力します。  
  
- 終了日列で、開始日より前の日付を入力します。  
  
- コース ID、開始日または終了日の値を削除します。  
  
- 無効なセル値を元に戻すには、セルにカーソルを置くし、ESC キーを押します。  
  
- 現在のセルが編集モードのときは、全体の行の変更を元に戻したり、ESC キーを 2 回押します。  
  
- 検証エラーが発生したときに、関連するエラー メッセージを表示する行ヘッダーのインジケーターの上にマウス ポインターを移動します。  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [データ バインディング](../data/data-binding-wpf.md)
- [バインディングの検証の実装](../data/how-to-implement-binding-validation.md)
- [カスタム オブジェクトに検証ロジックを実装する](../data/how-to-implement-validation-logic-on-custom-objects.md)
