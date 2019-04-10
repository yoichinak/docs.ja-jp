---
title: 'チュートリアル: バインドされていない Windows フォーム DataGridView コントロールを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: 99561490786f3f3569f272138001ea5ad8937410
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343469"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>チュートリアル: バインドされていない Windows フォーム DataGridView コントロールを作成する
頻繁にデータベースから表形式のデータを表示することがあります。 たとえば、文字列の 2 次元配列の内容を表示したい場合があります。 <xref:System.Windows.Forms.DataGridView>クラスには、データ ソースにバインドせずにデータを表示する簡単で高度にカスタマイズ可能な方法が用意されています。 このチュートリアルで作成する方法、<xref:System.Windows.Forms.DataGridView>加算と「バインドされていない」モードでの行の削除制御および管理します。 既定では、ユーザーは、新しい行を追加できます。 行の追加を防ぐためには、設定、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>プロパティは`false`します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:バインドされていない Windows フォーム DataGridView コントロールの作成](how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>バインドされていない DataGridView コントロールを使用するには  
  
1. 派生するクラスを作成<xref:System.Windows.Forms.Form>次の変数宣言が含まれていると`Main`メソッド。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. 実装を`SetupLayout`フォームのレイアウトを設定するフォームのクラス定義内のメソッド。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. 作成、`SetupDataGridView`を設定するメソッド、<xref:System.Windows.Forms.DataGridView>列とプロパティ。  
  
     このメソッドを追加、<xref:System.Windows.Forms.DataGridView>コントロールをフォームの<xref:System.Windows.Forms.Control.Controls%2A>コレクション。 次に、表示する列の数を使用してを設定するが、<xref:System.Windows.Forms.DataGridView.ColumnCount%2A>プロパティ。 設定して、列ヘッダーの既定のスタイルを設定、 <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>、 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>、および<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>によって返される、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>プロパティ。  
  
     レイアウトと外観のプロパティが設定されてし、し、列名が割り当てられます。 このメソッドの終了時に、<xref:System.Windows.Forms.DataGridView>コントロールが事前設定する準備ができています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. 作成、`PopulateDataGridView`行を追加する方法、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     各行は、曲とその関連情報を表します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. インプレース ユーティリティ メソッドを使って、イベント ハンドラーをアタッチできます。  
  
     処理する、**追加**と**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベント、フォームの<xref:System.Windows.Forms.Form.Load>イベント、および<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。  
  
     ときに、**追加**ボタンの<xref:System.Windows.Forms.Control.Click>イベントが発生すると、新しい空の行を追加する、<xref:System.Windows.Forms.DataGridView>します。  
  
     ときに、**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベントは、選択した行が削除されたである場合を除き、ユーザーは、新しいレコードの行が新しい行を追加します。 この行は、最後の行では常に、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     ときに、フォームの<xref:System.Windows.Forms.Form.Load>イベントが発生、 `SetupLayout`、 `SetupDataGridView`、および`PopulateDataGridView`ユーティリティ メソッドが呼び出されます。  
  
     ときに、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベントが発生すると、各セルに、`Date`セルの値を解析できない場合を除き、列が長い日付として書式設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>記載曲を表示するコントロール`PopulateDataGridView`します。 新しい行を追加することができます、**行の追加**で選択した行を削除できます、クリックして、**行の削除**ボタン。 バインドされていない<xref:System.Windows.Forms.DataGridView>コントロールは、データ ストアとそのデータは任意の外部ソースに依存しないなど、<xref:System.Data.DataSet>または配列。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
-   罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :罫線を変更して、グリッド線のスタイルで、Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)します。  
  
-   有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[方法 :行の追加を回避し、削除を Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)、および[方法。列を読み取り専用の Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)します。  
  
-   データベース関連のエラーをユーザー入力を確認します。 詳細については、「[チュートリアル:フォームの DataGridView コントロールを Windows でのデータ入力中に発生したエラーの処理](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)します。  
  
-   仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、「[チュートリアル:仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
-   セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)と[方法。Windows フォーム DataGridView コントロールの既定のセル スタイルを設定](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: 連結されていない Windows フォーム DataGridView コントロールを作成する](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)
