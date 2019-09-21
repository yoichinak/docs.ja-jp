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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960422"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>方法: Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する
プロパティ<xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.Sort%2A>とプロパティ<xref:System.Windows.Forms.BindingSource.Filter%2A>を使用して、コントロールの並べ替えとフィルター処理の機能を公開できます。 基になるデータソースが<xref:System.ComponentModel.IBindingList>である場合は、単純な並べ替えを適用でき<xref:System.ComponentModel.IBindingListView>ます。また、データソースがの場合は、フィルター処理や高度な並べ替えを適用できます。 プロパティ<xref:System.Windows.Forms.BindingSource.Sort%2A>には、標準の ADO.NET 構文が必要です。これに`ASC`は、データソース内のデータ列の名前`DESC`を表す文字列、またはリストを昇順と降順のどちらで並べ替えるかを示す、またはが必要です。 各列をコンマ区切り記号で区切ることによって、高度な並べ替えまたは複数列の並べ替えを設定できます。 プロパティ<xref:System.Windows.Forms.BindingSource.Filter%2A>は、文字列式を受け取ります。  
  
> [!NOTE]
> 接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../data/adonet/protecting-connection-information.md)」を参照してください。  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource を使用してデータをフィルター処理するには  
  
- <xref:System.Windows.Forms.BindingSource.Filter%2A>プロパティを目的の式に設定します。  
  
     次のコード例では、式は列名の後に列に必要な値を指定しています。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource を使用してデータを並べ替えるには  
  
1. プロパティに、または`DESC`を使用して`ASC`昇順または降順を示す列名を設定します。 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
  
2. 複数の列をコンマで区切ります。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>例  
 次のコード例では、Northwind サンプルデータベースの Customers テーブルから<xref:System.Windows.Forms.DataGridView>コントロールにデータを読み込み、表示されるデータをフィルター処理して並べ替えます。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例を実行するには、と<xref:System.Windows.Forms.BindingSource>いう名前`BindingSource1`のと<xref:System.Windows.Forms.DataGridView>という`dataGridView1`名前のを含むフォームにコードを貼り付けます。 フォームの`InitializeSortedFilteredBindingSource`イベントを処理し、load イベントハンドラーメソッドでを呼び出します。 <xref:System.Windows.Forms.Form.Load>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [方法: サンプルデータベースのインストール](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource コンポーネント](bindingsource-component.md)
