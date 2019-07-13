---
title: 'チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: c14edebb7fd5ee133ce60769327e6b32dac1c7af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623706"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査
データ エントリの機能をユーザーに表示するときに頻繁に、フォームに入力されたデータを検証する必要があります。 <xref:System.Windows.Forms.DataGridView>クラスには、データがデータ ストアにコミットする前に検証を実行する便利な方法が用意されています。 データを検証するには、処理することによって、<xref:System.Windows.Forms.DataGridView.CellValidating>によって発生するイベント、<xref:System.Windows.Forms.DataGridView>現在のセルが変更されたとき。  
  
 このチュートリアルから行を取得、`Customers`テーブルに Northwind サンプル データベースとその表示、<xref:System.Windows.Forms.DataGridView>コントロール。 ユーザーが内のセルを編集するときに、`CompanyName`列と、セルのままにする、<xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーは新しい値が空の文字列である場合は空ではありませんかどうかを確認する新しい会社名の文字列を調べて、<xref:System.Windows.Forms.DataGridView>により、ユーザーのカーソル。空でない文字列が入力されるまで、セルのままです。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:Windows フォーム DataGridView コントロールでデータを検証する](how-to-validate-data-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
- Northwind SQL Server のサンプル データベースが存在するサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView に入力されたデータを検証するには  
  
1. 派生するクラスを作成<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
     次のコード例は基本的な初期化を提供しが含まれています、`Main`メソッド。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. データベースへの接続の詳細を処理するためのフォームのクラス定義でメソッドを実装します。  
  
     このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。 設定することを必ず、`connectionString`変数は、データベースの適切な値にします。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御するより安全な方法とも呼ばれる統合セキュリティは、Windows 認証を使用します。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. フォームのハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. ハンドラーを実装、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellValidating>と<xref:System.Windows.Forms.DataGridView.CellEndEdit>イベント。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーが判断したかどうかのセルの値、`CompanyName`列が空です。 セルの値には、検証が失敗した場合、設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>クラスを`true`します。 これにより、<xref:System.Windows.Forms.DataGridView>コントロールをセルから、カーソルを防ぐためにします。 設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>の行に、説明文字列のプロパティ。 これには、エラー テキストを含むツールヒントにエラー アイコンが表示されます。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>イベント ハンドラーでは、設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>の行に空の文字列のプロパティ。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>セルに編集モードは、検証が失敗した場合に行うことはできませんが終了したときにのみイベントが発生します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
- アプリケーションをコンパイルして実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>からのデータが格納された、`Customers`テーブル。 内のセルをダブルクリックすると、`CompanyName`列、値を編集することができます。 すべての文字を削除して、セルを終了する TAB キーを押して、<xref:System.Windows.Forms.DataGridView>を終了することはできません。 セルに空でない文字列を入力すると、<xref:System.Windows.Forms.DataGridView>コントロールでは、セルを終了することができます。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
- 罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :罫線を変更して、グリッド線のスタイルで、Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)します。  
  
- 有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[方法 :行の追加を回避し、削除を Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)、および[方法。列を読み取り専用の Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)します。  
  
- データベース関連のエラーをユーザー入力を確認します。 詳細については、「[チュートリアル:フォームの DataGridView コントロールを Windows でのデータ入力中に発生したエラーの処理](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)します。  
  
- 仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、「[チュートリアル:仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
- セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)と[方法。Windows フォームの DataGridView コントロールのフォントと色のスタイルを設定する](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでデータを検証します。](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [チュートリアル: Windows フォームの DataGridView コントロールでのデータ入力中に発生したエラーの処理](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
