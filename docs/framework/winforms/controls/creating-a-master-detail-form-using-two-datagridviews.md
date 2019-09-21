---
title: 'チュートリアル: 2つの Windows フォーム DataGridView コントロールを使用してマスター詳細フォームを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046097"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>チュートリアル: Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームを作成する

<xref:System.Windows.Forms.DataGridView>コントロールを使用する最も一般的なシナリオの1つは、*マスター/詳細*形式です。このフォームでは、2つのデータベーステーブル間の親子関係が表示されます。 マスターテーブル内の行を選択すると、対応する子データで詳細テーブルが更新されます。

マスター/詳細フォームの実装は、 <xref:System.Windows.Forms.DataGridView>コントロール<xref:System.Windows.Forms.BindingSource>とコンポーネントの間の相互作用を使用して簡単に行うことができます。 このチュートリアルでは、2つ<xref:System.Windows.Forms.DataGridView>のコントロールと2つ<xref:System.Windows.Forms.BindingSource>のコンポーネントを使用してフォームをビルドします。 フォームでは、Northwind SQL Server サンプルデータベース`Customers`にとと`Orders`いう2つの関連テーブルが表示されます。 完了すると、マスター <xref:System.Windows.Forms.DataGridView>内のデータベースのすべての顧客と、選択した顧客のすべての注文が詳細<xref:System.Windows.Forms.DataGridView>に表示されます。

このトピックのコードを単一のリストとしてコピーするには、「[方法:2つの Windows フォーム DataGridView コントロール](create-a-master-detail-form-using-two-datagridviews.md)を使用してマスター/詳細フォームを作成します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するための要件は次のとおりです。

- Northwind SQL Server サンプルデータベースを持つサーバーへのアクセス。

## <a name="creating-the-form"></a>フォームの作成

#### <a name="to-create-a-masterdetail-form"></a>マスター/詳細フォームを作成するには

1. から<xref:System.Windows.Forms.Form>派生するクラスを作成し、2 <xref:System.Windows.Forms.DataGridView>つのコントロール<xref:System.Windows.Forms.BindingSource>と2つのコンポーネントを格納します。 次のコードは、基本的なフォームの初期`Main`化を提供し、メソッドを含んでいます。 Visual Studio デザイナーを使用してフォームを作成する場合は、このコードの代わりにデザイナーで生成されたコードを使用できますが、ここでは変数宣言に示されている名前を使用してください。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. データベースへの接続の詳細を処理するために、フォームのクラス定義にメソッドを実装します。 この例では`GetData` 、 <xref:System.Data.DataSet>オブジェクトを設定し、 <xref:System.Data.DataRelation>オブジェクトをデータセットに追加して、 <xref:System.Windows.Forms.BindingSource>コンポーネントをバインドするメソッドを使用します。 `connectionString` 変数は、使用しているデータベースに合った値に設定してください。

    > [!IMPORTANT]
    > 接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. <xref:System.Windows.Forms.DataGridView>コントロールを<xref:System.Windows.Forms.Form.Load> コンポーネントに<xref:System.Windows.Forms.BindingSource>バインドし、 `GetData`メソッドを呼び出すフォームのイベントのハンドラーを実装します。 次の例には、表示<xref:System.Windows.Forms.DataGridView>されるデータに合わせて列のサイズを変更するコードが含まれています。

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>アプリケーションのテスト

フォームをテストして、期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

- アプリケーションをコンパイルして実行します。

  2つ<xref:System.Windows.Forms.DataGridView>のコントロールが1つ上に表示されます。 [上位] は Northwind `Customers`テーブルの顧客であり、一番下`Orders`には選択した顧客に対応するがあります。 上部<xref:System.Windows.Forms.DataGridView>で異なる行を選択すると、それに応じて下位<xref:System.Windows.Forms.DataGridView>の内容が変化します。

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
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: 2つの Windows フォーム DataGridView コントロールを使用してマスター/詳細フォームを作成する](create-a-master-detail-form-using-two-datagridviews.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
