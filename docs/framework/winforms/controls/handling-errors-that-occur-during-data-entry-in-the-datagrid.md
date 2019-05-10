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
ms.openlocfilehash: b2fafdd9959123e27c4b58484281408c3115e4d1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624168"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理
基になるデータ ストアからのエラーの処理は、データ入力アプリケーションの必要な機能です。 Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールによって、この簡単に公開することで、<xref:System.Windows.Forms.DataGridView.DataError>制約違反または壊れているビジネス ルールをデータ ストアを検出したときに発生するイベントです。  
  
 このチュートリアルから行を取得、`Customers`テーブルに Northwind サンプル データベースとその表示、<xref:System.Windows.Forms.DataGridView>コントロール。 重複しているときに`CustomerID`新しい行または編集された既存の行で値が検出された、<xref:System.Windows.Forms.DataGridView.DataError>は、表示することで処理するイベントが発生、<xref:System.Windows.Forms.MessageBox>例外を説明します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:フォームの DataGridView コントロールを Windows でのデータ入力中に発生するエラーを処理](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
- Northwind SQL Server のサンプル データベースが存在するサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView コントロールでのデータ エントリ エラーを処理するには  
  
1. 派生するクラスを作成<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
     次のコード例は基本的な初期化を提供しが含まれています、`Main`メソッド。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2. データベースへの接続の詳細を処理するためのフォームのクラス定義でメソッドを実装します。  
  
     このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。 設定することを必ず、`connectionString`変数は、データベースの適切な値にします。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3. フォームのハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4. 処理、<xref:System.Windows.Forms.DataGridView.DataError>上のイベント、<xref:System.Windows.Forms.DataGridView>します。  
  
     コミット操作の場合は、エラーのコンテキストでエラーを表示、<xref:System.Windows.Forms.MessageBox>します。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
- F5 キーを押してアプリケーションを実行します。  
  
     表示されます、 <xref:System.Windows.Forms.DataGridView> Customers テーブルからデータが格納されたコントロール。 重複する値を入力する場合`CustomerID`編集をコミットし、セルの値が自動的に元に戻すおよびが表示されます、<xref:System.Windows.Forms.MessageBox>データ エントリ エラーを表示します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
- 罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :罫線を変更して、グリッド線のスタイルで、Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)します。  
  
- 有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[方法 :行の追加を回避し、削除を Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)、および[方法。列を読み取り専用の Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)します。  
  
- ユーザー入力を検証、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[チュートリアル:フォームの DataGridView コントロールを Windows のデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。  
  
- 仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、「[チュートリアル:仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
- セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)と[方法。Windows フォーム DataGridView コントロールの既定のセル スタイルを設定](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールでのデータ入力中に発生したエラーを処理します。](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [チュートリアル: Windows フォームの DataGridView コントロールのデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
