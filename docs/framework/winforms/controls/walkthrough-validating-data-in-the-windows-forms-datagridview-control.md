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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046379"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査

データ入力機能をユーザーに表示する場合は、フォームに入力されたデータを頻繁に検証する必要があります。 クラス<xref:System.Windows.Forms.DataGridView>は、データがデータストアにコミットされる前に検証を実行する便利な方法を提供します。 現在の<xref:System.Windows.Forms.DataGridView.CellValidating> <xref:System.Windows.Forms.DataGridView>セルが変更されたときにによって発生するイベントを処理することで、データを検証できます。

このチュートリアルでは、Northwind サンプルデータベースの`Customers`テーブルから行を取得し、 <xref:System.Windows.Forms.DataGridView>コントロールに表示します。 ユーザーが`CompanyName`列のセルを編集し、セルから離れようとすると<xref:System.Windows.Forms.DataGridView.CellValidating> 、イベントハンドラーは新しい会社名の文字列を調べて空でないことを確認します。新しい値が空の文字列<xref:System.Windows.Forms.DataGridView>の場合、はユーザーのカーソルを防止します。空でない文字列が入力されるまで、セルから離れます。

このトピックのコードを単一のリストとしてコピーするには、「[方法:Windows フォーム DataGridView コントロール](how-to-validate-data-in-the-windows-forms-datagridview-control.md)でデータを検証します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するための要件は次のとおりです。

- Northwind SQL Server サンプルデータベースを持つサーバーへのアクセス。

## <a name="creating-the-form"></a>フォームの作成

#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView に入力されたデータを検証するには

1. から<xref:System.Windows.Forms.Form>派生するクラスを作成し、コントロール<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>コンポーネントを格納します。

    次のコード例では、基本的な初期化`Main`を行い、メソッドを含めています。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. データベースへの接続の詳細を処理するために、フォームのクラス定義にメソッドを実装します。

    このコード例では`GetData` 、設定<xref:System.Data.DataTable>されたオブジェクトを返すメソッドを使用します。 `connectionString`変数には、データベースに適した値を設定してください。

    > [!IMPORTANT]
    > 接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 Windows 認証 (統合セキュリティとも呼ばれます) を使用すると、データベースへのアクセスをより安全に制御することができます。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. と<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.Form.Load> を初期化し、データバインディングを設定するフォームのイベントのハンドラーを<xref:System.Windows.Forms.BindingSource>実装します。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. <xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellValidating>イベントと<xref:System.Windows.Forms.DataGridView.CellEndEdit>イベントのハンドラーを実装します。

    イベントハンドラーでは、 `CompanyName`列のセルの値が空かどうかを判断します。 <xref:System.Windows.Forms.DataGridView.CellValidating> セル値が検証に失敗した場合<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>は、 <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>クラスのプロパティ`true`をに設定します。 これにより<xref:System.Windows.Forms.DataGridView> 、コントロールによって、カーソルがセルから離れるのを防ぐことができます。 行の<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>プロパティを説明の文字列に設定します。 エラーアイコンと、エラーテキストを含むツールヒントが表示されます。 イベントハンドラーで、行の<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>プロパティを空の文字列に設定します。 <xref:System.Windows.Forms.DataGridView.CellEndEdit> イベント<xref:System.Windows.Forms.DataGridView.CellEndEdit>は、セルが編集モードを終了したときにのみ発生します。これは、検証に失敗した場合には実行できません。

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>アプリケーションのテスト

フォームをテストして、期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

- アプリケーションをコンパイルして実行します。

  `Customers`テーブルのデータが<xref:System.Windows.Forms.DataGridView>いっぱいになっていることがわかります。 `CompanyName`列のセルをダブルクリックすると、値を編集できます。 すべての文字を削除し、TAB キーを押してセルを終了すると<xref:System.Windows.Forms.DataGridView> 、で終了できなくなります。 空でない文字列をセルに入力すると、コントロールに<xref:System.Windows.Forms.DataGridView>よってセルを終了できます。

## <a name="next-steps"></a>次の手順

このアプリケーションを使用すると、コントロールの<xref:System.Windows.Forms.DataGridView>機能についての基本的な理解を得ることができます。 <xref:System.Windows.Forms.DataGridView>コントロールの外観と動作は、次のいくつかの方法でカスタマイズできます。

- 罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)の境界線とグリッド線のスタイルを変更します。

- コントロールへの<xref:System.Windows.Forms.DataGridView>ユーザー入力を有効または制限します。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)で行が追加および削除されない[ようにする方法と、次の操作を実行する方法について説明します。Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)で列を読み取り専用にします。

- データベース関連のエラーについては、ユーザー入力を確認してください。 詳細については、「[チュートリアル:Windows フォーム DataGridView コントロール](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)でのデータ入力中に発生したエラーを処理します。

- 仮想モードを使用して非常に大きなデータセットを処理します。 詳細については、「[チュートリアル:Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)での仮想モードの実装。

- セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](customize-the-appearance-of-cells-in-the-datagrid.md)でのセルの外観と、次[の操作方法をカスタマイズします。Windows フォーム DataGridView コントロール](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)でフォントと色のスタイルを設定します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでデータを検証する](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
