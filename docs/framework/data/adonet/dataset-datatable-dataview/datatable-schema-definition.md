---
title: DataTable スキーマの定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 20fee4316ad95c0f8716a0f374410009ea129222
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952359"
---
# <a name="datatable-schema-definition"></a>DataTable スキーマの定義
テーブルのスキーマ (構造) は、列と制約で表されます。 <xref:System.Data.DataTable> のスキーマは、<xref:System.Data.DataColumn>、<xref:System.Data.ForeignKeyConstraint>、<xref:System.Data.UniqueConstraint> の各オブジェクトを使用して定義します。 テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 テーブルの列、リレーション、および制約を名前で参照する場合は、大文字と小文字が区別されます。 複数の列、リレーション、または制約の名前が同じであっても、大文字と小文字が異なっていれば、1 つのテーブルで使用できます。 たとえば、 **col1**と**col1**を使用できます。 この場合、列を名前で参照するときは、列名の大文字と小文字を正確に指定する必要があります。正確に指定しない場合は、例外がスローされます。 たとえば、テーブル**mytable**に**col1**列と**col1**列が含まれている場合、 **col1**を名前によって Mytable として参照し**ます。 Columns ["col1"]** , **col1** as **mytable ["col1"]** です。 列のいずれかを MyTable として参照しようとしてい**ます。列 ["COL1"]** は例外を生成します。  
  
 大文字と小文字の区別の規則は、特定の名前の列、リレーション、または制約が 1 つしかない場合には適用されません。 つまり、特定の列、リレーション、または制約オブジェクトと名前が一致する列、リレーション、または制約オブジェクトがテーブルに存在しない場合は、大文字と小文字を区別せずにそのオブジェクトを名前で参照することができます。このとき、例外はスローされません。 たとえば、テーブルに**Col1**しかない場合は、my を使用して参照でき**ます。列 ["COL1"]** 。  
  
> [!NOTE]
> DataTable <xref:System.Data.DataTable.CaseSensitive%2A>のプロパティは 、この動作に影響しません。 **CaseSensitive**プロパティは、テーブル内のデータに適用され、並べ替え、検索、フィルター処理、制約の適用などに影響しますが、列、リレーション、および制約への参照には影響しません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataTable への列の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 **DataColumn**オブジェクトを使用してテーブルの列を定義する方法について説明します。  
  
 [式列の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 列の**式**プロパティを使用して、行の他の列の値に基づいて値を計算する方法について説明します。  
  
 [AutoIncrement 列の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 数値を自動的にインクリメントして行ごとに一意の列値が割り当てられるように列を設定する方法について説明します。  
  
 [主キーの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 1つ以上の**DataColumn**オブジェクトからテーブルの主キーを指定する方法について説明します。  
  
 [DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 テーブルの列の外部キー制約と UNIQUE 制約を定義する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
