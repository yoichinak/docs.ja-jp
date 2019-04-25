---
title: DataTable スキーマの定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: e8710e7d92558f525a6feaedf8d0635c5ce6e2c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163073"
---
# <a name="datatable-schema-definition"></a>DataTable スキーマの定義
テーブルのスキーマ (構造) は、列と制約で表されます。 <xref:System.Data.DataTable> のスキーマは、<xref:System.Data.DataColumn>、<xref:System.Data.ForeignKeyConstraint>、<xref:System.Data.UniqueConstraint> の各オブジェクトを使用して定義します。 テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 テーブルの列、リレーション、および制約を名前で参照する場合は、大文字と小文字が区別されます。 複数の列、リレーション、または制約の名前が同じであっても、大文字と小文字が異なっていれば、1 つのテーブルで使用できます。 たとえば、ある**Col1**と**col1**します。 この場合、列を名前で参照するときは、列名の大文字と小文字を正確に指定する必要があります。正確に指定しない場合は、例外がスローされます。 たとえば場合の表に、 **myTable**列が含まれます**Col1**と**col1**を参照する**Col1**と名前**myTable.Columns["Col1"]**、および**col1**として**myTable.Columns["col1"]** します。 列のいずれかを参照しようとして**myTable.Columns["COL1"]** 例外が生成されます。  
  
 大文字と小文字の区別の規則は、特定の名前の列、リレーション、または制約が 1 つしかない場合には適用されません。 つまり、特定の列、リレーション、または制約オブジェクトと名前が一致する列、リレーション、または制約オブジェクトがテーブルに存在しない場合は、大文字と小文字を区別せずにそのオブジェクトを名前で参照することができます。このとき、例外はスローされません。 たとえば、テーブルにのみ**Col1**を使用して参照できます**私です。列 ["COL1"]** します。  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A>のプロパティ、 **DataTable**この動作には影響しません。 **CaseSensitive**プロパティは、列、リレーション、および制約への参照ではなく、テーブルや並べ替え、検索、フィルター処理、制約の適用、内のデータに適用されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataTable への列の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 使用してテーブルの列を定義する方法について説明します**DataColumn**オブジェクト。  
  
 [式列の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 について説明しますが、どのように**式**行の他の列の値に基づいて値を計算する列のプロパティを使用できます。  
  
 [AutoIncrement 列の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 数値を自動的にインクリメントして行ごとに一意の列値が割り当てられるように列を設定する方法について説明します。  
  
 [主キーの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 1 つまたは複数のテーブルの主キーを指定する方法について説明します**DataColumn**オブジェクト。  
  
 [DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 テーブルの列の外部キー制約と UNIQUE 制約を定義する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
