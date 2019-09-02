---
title: DataTable の制約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 68b99e834428261d59c5fb27277b24eb0f6e77e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205056"
---
# <a name="datatable-constraints"></a>DataTable の制約
制約を使用すると、データの整合性を維持するために <xref:System.Data.DataTable> のデータを強制的に制限できます。 制約は、1 つの列または関連付けられた複数の列に対して自動的に適用される規則であり、行の値がなんらかの方法で変更されたときに実行されるアクションを決定します。 のプロパティ`System.Data.DataSet.EnforceConstraints`がtrueの場合、制約が適用されます。 <xref:System.Data.DataSet> `EnforceConstraints` プロパティの設定方法のコード例については、<xref:System.Data.DataSet.EnforceConstraints%2A> のリファレンス トピックを参照してください。  
  
 ADO.NET には、<xref:System.Data.ForeignKeyConstraint> と <xref:System.Data.UniqueConstraint> の 2 種類の制約があります。 既定では、2つ以上のテーブル間のリレーションシップを作成するときに、**データセット**に<xref:System.Data.DataRelation>を追加することによって、両方の制約が自動的に作成されます。 ただし、リレーションシップの作成時に**createConstraints** = **false**を指定することで、この動作を無効にすることができます。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **ForeignKeyConstraint**は、関連テーブルの更新と削除がどのように反映されるかに関する規則を適用します。 たとえば、1つのテーブルの行の値が更新または削除され、その同じ値が1つ以上の関連テーブルでも使用されている場合、 **ForeignKeyConstraint**は関連テーブルでの処理を決定します。  
  
 ForeignKeyConstraint <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>の<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>プロパティとプロパティは、ユーザーが関連テーブル内の行を削除または更新しようとしたときに実行されるアクションを定義します。 次の表では、 **ForeignKeyConstraint**の**DeleteRule**プロパティと**UpdateRule**プロパティで使用できるさまざまな設定について説明します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|関連付けられている行を削除または更新します。|  
|**SetNull**|関連する行の値を**DBNull**に設定します。|  
|**SetDefault**|関連付けられている行の値を既定値に設定します。|  
|**None**|関連付けられている行に対してアクションは実行しません。 既定値です。|  
  
 **ForeignKeyConstraint**を使用すると、関連する列に対する変更を制限および反映することができます。 列の**ForeignKeyConstraint**に設定されているプロパティによっては、**データセット**の**EnforceConstraints**プロパティが**true**の場合、親行に対して特定の操作を実行すると例外が発生します。 たとえば、 **ForeignKeyConstraint**の**DeleteRule**プロパティが**None**の場合、子行がある場合、親行を削除することはできません。  
  
 **ForeignKeyConstraint**コンストラクターを使用して、単一の列間または列の配列間の foreign key 制約を作成できます。 結果の**ForeignKeyConstraint**オブジェクトをテーブルの**Constraints**プロパティの**Add**メソッド ( **ConstraintCollection**) に渡します。 また、 **ConstraintCollection**の**Add**メソッドのいくつかのオーバーロードにコンストラクター引数を渡して、 **ForeignKeyConstraint**を作成することもできます。  
  
 **ForeignKeyConstraint**を作成するときに、 **DeleteRule**と**UpdateRule**の値を引数としてコンストラクターに渡すか、次の例のようにプロパティとして設定できます ( **DeleteRule**の値がに**設定されている場合)。なし**)。  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 行への変更は、 **AcceptChanges**メソッドを使用して受け入れるか、 **DataSet**、 **DataTable**、または**DataRow**の**RejectChanges**メソッドを使用して取り消すことができます。 **データセット**に**ForeignKeyConstraints**が含まれている場合、 **AcceptChanges**メソッドまたは**RejectChanges**メソッドを呼び出すと、 **AcceptRejectRule**が適用されます。 **ForeignKeyConstraint**の**AcceptRejectRule**プロパティは、親行で**AcceptChanges**または**RejectChanges**が呼び出されたときに、子の行に対して実行されるアクションを決定します。  
  
 次の表に、 **AcceptRejectRule**で使用可能な設定の一覧を示します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|子の行への変更を受け入れるかまたは拒否します。|  
|**None**|子の行に対してアクションは実行しません。 既定値です。|  
  
### <a name="example"></a>例  
 次の例では、<xref:System.Data.ForeignKeyConstraint> を作成し、<xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> を含む複数のプロパティを設定して、<xref:System.Data.ConstraintCollection> オブジェクトの <xref:System.Data.DataTable> に追加します。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint**オブジェクトは、単一の列または**DataTable**内の列の配列に割り当てることができます。これにより、指定された1つまたは複数の列のすべてのデータが行ごとに一意になります。 **UniqueConstraint**コンストラクターを使用して、列または列の配列に unique 制約を作成できます。 結果の**UniqueConstraint**オブジェクトをテーブルの**Constraints**プロパティの**Add**メソッド ( **ConstraintCollection**) に渡します。 また、 **ConstraintCollection**の**Add**メソッドのいくつかのオーバーロードにコンストラクター引数を渡して、 **UniqueConstraint**を作成することもできます。 1つまたは複数の列に対して**UniqueConstraint**を作成する場合は、必要に応じて、列または列が主キーであるかどうかを指定できます。  
  
 列の**unique**プロパティを**true**に設定することによって、列に unique 制約を作成することもできます。 または、1つの列の**unique**プロパティを**false**に設定すると、存在する可能性がある一意の制約が削除されます。 1 つの列 (または複数の列) をテーブルの主キーとして定義すると、指定した列 (または複数の列) の UNIQUE 制約が自動的に作成されます。 **DataTable**の**PrimaryKey**プロパティから列を削除すると、 **UniqueConstraint**が削除されます。  
  
 次の例では、 **DataTable**の2つの列に対して**UniqueConstraint**を作成します。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [DataTable スキーマの定義](datatable-schema-definition.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
