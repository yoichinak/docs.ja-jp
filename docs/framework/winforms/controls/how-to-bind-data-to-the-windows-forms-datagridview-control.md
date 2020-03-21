---
title: データをデータ グリッド ビュー コントロールにバインドする
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182272"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>方法 : データをバインドするコントロール

コントロール<xref:System.Windows.Forms.DataGridView>は、標準の Windows フォーム データ バインディング モデルをサポートするため、さまざまなデータ ソースにバインドできます。 通常は、データ ソース<xref:System.Windows.Forms.BindingSource>との対話を管理する にバインドします。 は<xref:System.Windows.Forms.BindingSource>、任意の Windows フォーム データ ソースを使用でき、データの場所を選択または変更する際に柔軟性を高めることができます。 コントロールがサポートするデータ ソース<xref:System.Windows.Forms.DataGridView>の詳細については、「 [DataGridView コントロールの概要](datagridview-control-overview-windows-forms.md)」を参照してください。  

コントロールへのデータ バインディングに対する広範なサポートがあります。 詳細については、「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールにデータをバインドする」を参照してください](bind-data-to-the-datagrid-using-the-designer.md)。  

コントロールをデータに接続するには、次の手順を実行します。

1. データの取得の詳細を処理するメソッドを実装します。 を初期化し、それを使用して`GetData`を設定するメソッド<xref:System.Data.SqlClient.SqlDataAdapter>を実装するコード例を次<xref:System.Data.DataTable>に示します。 次に、 を<xref:System.Data.DataTable>に<xref:System.Windows.Forms.BindingSource>バインドします。

2. フォームの<xref:System.Windows.Forms.Form.Load>イベント ハンドラで、コントロールを<xref:System.Windows.Forms.DataGridView><xref:System.Windows.Forms.BindingSource>にバインドし、メソッドを`GetData`呼び出してデータを取得します。  

## <a name="example"></a>例

この完全なコード例では、データベースからデータを取得して、Windows フォームに DataGridView コントロールを設定します。 フォームには、データを再読み込みし、データベースに変更を送信するためのボタンもあります。  

この例で必要な要素は次のとおりです。

- ノースウィンド SQL サーバー サンプル データベースへのアクセス。 Northwind サンプル データベースのインストールの詳細については[、「ADO.NETコード サンプルのサンプル データベースを取得する](../../data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。

- システム、システム.Windows.フォーム、システム.データ、およびシステム.Xml アセンブリへの参照。  

この例をビルドして実行するには、新しい Windows フォーム プロジェクトの*Form1*コード ファイルにコードを貼り付けます。 C# または Visual Basic コマンド ラインからのビルドについては[、「csc.exe を使用したコマンド ラインのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」または「[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」を参照してください。  
  
例の`connectionString`変数に、ノースウィンド SQL Server サンプル データベース接続の値を設定します。 Windows 認証は統合セキュリティとも呼ばれ、接続文字列にパスワードを格納するよりも、データベースに接続する方が安全な方法です。 接続セキュリティの詳細については、[接続情報の保護](../../data/adonet/protecting-connection-information.md)を参照してください。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [コントロールにデータを表示します。](displaying-data-in-the-windows-forms-datagridview-control.md)
- [接続情報を保護する](../../data/adonet/protecting-connection-information.md)
