---
title: '方法: Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 8904eff39b7278b2a185cc5e2f738ece1e8e88e4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306509"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>方法: Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する
並べ替えとフィルタ リングの機能を公開する<xref:System.Windows.Forms.BindingSource>を介して制御、<xref:System.Windows.Forms.BindingSource.Sort%2A>と<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティ。 基になるデータ ソースの場合は、単純な並べ替えを適用することができます、 <xref:System.ComponentModel.IBindingList>、フィルター処理を適用することができ、高度な並べ替え、データ ソースの場合と、<xref:System.ComponentModel.IBindingListView>します。 <xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティには標準[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]構文: データ ソース内のデータの列の名前を表す文字列が続く`ASC`または`DESC`一覧を昇順または降順で並べ替える必要があるかどうかを示す。 高度な並べ替え、または各列をコンマ区切り記号で区切って複数列の並べ替えを設定することができます。 <xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティは文字列式を受け取ります。  
  
> [!NOTE]
>  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource でデータをフィルター処理  
  
-   設定、<xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティを使用する式。  
  
     次のコード例では、式は、列名の後に、列の値が。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource でデータを並べ替える  
  
1. 設定、<xref:System.Windows.Forms.BindingSource.Sort%2A>プロパティ後に必要な列名を`ASC`または`DESC`を昇順または降順を示します。  
  
2. 複数の列をコンマで区切ります。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>例  
 次のコード例に、Northwind サンプル データベースの Customers テーブルからデータを読み込みます、<xref:System.Windows.Forms.DataGridView>を制御する、フィルター処理し、表示されるデータを並べ替えます。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例を実行するには、フォームが含まれていますにコードを貼り付けます、<xref:System.Windows.Forms.BindingSource>という名前`BindingSource1`と<xref:System.Windows.Forms.DataGridView>という`dataGridView1`します。 処理、<xref:System.Windows.Forms.Form.Load>フォームに対する呼び出しイベント`InitializeSortedFilteredBindingSource`load イベント ハンドラー メソッドにします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [方法: サンプル データベースをインストールします。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource コンポーネント](bindingsource-component.md)
