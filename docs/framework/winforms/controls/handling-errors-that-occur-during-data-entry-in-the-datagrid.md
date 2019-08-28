---
title: 'チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046077"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理

データ入力アプリケーションでは、基になるデータストアからのエラーを処理する必要があります。 Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールは、 <xref:System.Windows.Forms.DataGridView.DataError>イベントを公開することによってこれを簡単にします。これは、データストアが制約違反または分割されたビジネスルールを検出したときに発生します。

このチュートリアルでは、Northwind サンプルデータベースの`Customers`テーブルから行を取得し、 <xref:System.Windows.Forms.DataGridView>コントロールに表示します。 新しい行また`CustomerID`は編集済みの既存の行<xref:System.Windows.Forms.DataGridView.DataError>で重複する値が検出されると、イベントが発生します。これは<xref:System.Windows.Forms.MessageBox> 、例外を説明するを表示することによって処理されます。

このトピックのコードを単一のリストとしてコピーするには、「[方法:Windows フォーム DataGridView コントロール](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)でのデータ入力中に発生したエラーを処理します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するための要件は次のとおりです。

- Northwind SQL Server サンプルデータベースを持つサーバーへのアクセス。

## <a name="creating-the-form"></a>フォームの作成

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView コントロールでのデータ入力エラーを処理するには

1. から<xref:System.Windows.Forms.Form>派生するクラスを作成し、コントロール<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>コンポーネントを格納します。

    次のコード例では、基本的な初期化`Main`を行い、メソッドを含めています。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. データベースへの接続の詳細を処理するために、フォームのクラス定義にメソッドを実装します。

    このコード例では`GetData` 、設定<xref:System.Data.DataTable>されたオブジェクトを返すメソッドを使用します。 `connectionString`変数には、データベースに適した値を設定してください。

    > [!IMPORTANT]
    > 接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. と<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.Form.Load> を初期化し、データバインディングを設定するフォームのイベントのハンドラーを<xref:System.Windows.Forms.BindingSource>実装します。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. でイベント<xref:System.Windows.Forms.DataGridView.DataError>を処理します。<xref:System.Windows.Forms.DataGridView>

    エラーのコンテキストがコミット操作の場合は、エラーをに<xref:System.Windows.Forms.MessageBox>表示します。

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>アプリケーションのテスト

フォームをテストして、期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

- F5 キーを押してアプリケーションを実行します。

  Customers テーブルのデータ<xref:System.Windows.Forms.DataGridView>が入力されたコントロールが表示されます。 に`CustomerID`重複する値を入力して編集をコミットすると、セルの値は自動的に元に戻り<xref:System.Windows.Forms.MessageBox> 、データエントリエラーを示すが表示されます。

## <a name="next-steps"></a>次の手順

このアプリケーションを使用すると、コントロールの<xref:System.Windows.Forms.DataGridView>機能についての基本的な理解を得ることができます。 <xref:System.Windows.Forms.DataGridView>コントロールの外観と動作は、次のいくつかの方法でカスタマイズできます。

- 罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)の境界線とグリッド線のスタイルを変更します。

- コントロールへの<xref:System.Windows.Forms.DataGridView>ユーザー入力を有効または制限します。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)で行が追加および削除されない[ようにする方法と、次の操作を実行する方法について説明します。Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)で列を読み取り専用にします。

- コントロールへの<xref:System.Windows.Forms.DataGridView>ユーザー入力を検証します。 詳細については、「[チュートリアル:Windows フォーム DataGridView コントロール](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)でデータを検証しています。

- 仮想モードを使用して非常に大きなデータセットを処理します。 詳細については、「[チュートリアル:Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)での仮想モードの実装。

- セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](customize-the-appearance-of-cells-in-the-datagrid.md)でのセルの外観と、次[の操作方法をカスタマイズします。Windows フォーム DataGridView コントロール](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)の既定のセルスタイルを設定します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーを処理します](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [チュートリアル: Windows フォーム DataGridView コントロールでのデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
