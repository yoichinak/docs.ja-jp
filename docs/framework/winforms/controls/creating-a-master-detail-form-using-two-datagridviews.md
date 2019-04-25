---
title: 'チュートリアル: 2 つの Windows フォーム DataGridView コントロールを使用してマスター/詳細フォームを作成します。'
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
ms.openlocfilehash: a887dacfcb83b4b6ea4cb2690ab09b0d1b20b4fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295797"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>チュートリアル: Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームを作成する
使用するための最も一般的なシナリオの 1 つ、<xref:System.Windows.Forms.DataGridView>コントロールが、*マスター/詳細*フォーム、2 つのデータベース テーブル間の親/子リレーションシップが表示されます。 マスター テーブルの行を選択すると、対応する子データで更新する詳細テーブル。  
  
 間の相互作用を使用して、簡単では、マスター/詳細フォームを実装する、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネント。 このチュートリアルでは、2 つを使用してフォームをビルドします<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネント。 Northwind SQL Server のサンプル データベースのテーブルに関連する 2 つ、フォームが表示されます:`Customers`と`Orders`します。 マスター データベースで、すべての顧客を表示するフォームが完了したら、<xref:System.Windows.Forms.DataGridView>および詳細に選択した顧客のすべての注文<xref:System.Windows.Forms.DataGridView>します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法:2 つの Windows フォーム DataGridView コントロールを使用してマスター/詳細フォームを作成する](create-a-master-detail-form-using-two-datagridviews.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind SQL Server のサンプル データベースが存在するサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-create-a-masterdetail-form"></a>マスター/詳細フォームを作成するには  
  
1. 派生するクラスを作成<xref:System.Windows.Forms.Form>は 2 つと<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネント。 次のコードは、基本的なフォームの初期化を提供しが含まれています、`Main`メソッド。 Visual Studio デザイナーを使用して、フォームを作成する場合は、デザイナー生成コードを使用して、このコードではなくが、変数の宣言には、ここに表示される名前を使用してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2. データベースへの接続の詳細を処理するためのフォームのクラス定義でメソッドを実装します。 この例では、`GetData`を設定するメソッド、<xref:System.Data.DataSet>オブジェクトを追加、<xref:System.Data.DataRelation>データ セット、およびバインドするオブジェクト、<xref:System.Windows.Forms.BindingSource>コンポーネント。 `connectionString` 変数は、使用しているデータベースに合った値に設定してください。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3. フォームのハンドラーを実装<xref:System.Windows.Forms.Form.Load>をバインドするイベント、<xref:System.Windows.Forms.DataGridView>にコントロールを<xref:System.Windows.Forms.BindingSource>コンポーネントと呼び出し、`GetData`メソッド。 次の例には、サイズを変更するコードが含まれています。<xref:System.Windows.Forms.DataGridView>に合わせて表示されるデータの列。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     2 つが表示されます<xref:System.Windows.Forms.DataGridView>上、他のいずれかの制御します。 上部には、Northwind から顧客`Customers`テーブル、および下部には、`Orders`選択した顧客に対応します。 上で別の行を選択すると<xref:System.Windows.Forms.DataGridView>、下の内容<xref:System.Windows.Forms.DataGridView>適宜変更します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
-   罫線とヘッダーのスタイルを変更します。 詳細については、「[方法 :罫線を変更して、グリッド線のスタイルで、Windows フォーム DataGridView コントロール](change-the-border-and-gridline-styles-in-the-datagrid.md)します。  
  
-   有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[方法 :行の追加を回避し、削除を Windows フォーム DataGridView コントロール](prevent-row-addition-and-deletion-datagridview.md)、および[方法。列を読み取り専用の Windows フォーム DataGridView コントロール](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)します。  
  
-   ユーザー入力を検証、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、「[チュートリアル:フォームの DataGridView コントロールを Windows のデータの検証](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。  
  
-   仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、「[チュートリアル:仮想モードの実装で、Windows フォーム DataGridView コントロール](implementing-virtual-mode-wf-datagridview-control.md)します。  
  
-   セルの外観をカスタマイズします。 詳細については、「[方法 :Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)と[方法。Windows フォーム DataGridView コントロールの既定のセル スタイルを設定](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [方法: 2 つの Windows フォーム DataGridView コントロールを使用してマスター/詳細フォームを作成します。](create-a-master-detail-form-using-two-datagridviews.md)
- [接続情報の保護](../../data/adonet/protecting-connection-information.md)
