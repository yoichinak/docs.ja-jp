---
title: DataTable の制約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 254f486fa19d8af30759d9a9fd6642a1a40e82a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165179"
---
# <a name="datatable-constraints"></a>DataTable の制約
制約を使用すると、データの整合性を維持するために <xref:System.Data.DataTable> のデータを強制的に制限できます。 制約は、1 つの列または関連付けられた複数の列に対して自動的に適用される規則であり、行の値がなんらかの方法で変更されたときに実行されるアクションを決定します。 制約はときに、`System.Data.DataSet.EnforceConstraints`のプロパティ、<xref:System.Data.DataSet>は**true**します。 `EnforceConstraints` プロパティの設定方法のコード例については、<xref:System.Data.DataSet.EnforceConstraints%2A> のリファレンス トピックを参照してください。  
  
 ADO.NET には、<xref:System.Data.ForeignKeyConstraint> と <xref:System.Data.UniqueConstraint> の 2 種類の制約があります。 既定では、両方の制約が自動的に作成を追加して 2 つ以上のテーブル間のリレーションシップを作成するときに、<xref:System.Data.DataRelation>を**データセット**します。 指定することでこの動作を無効にするただし、 **createConstraints** = **false**リレーションシップを作成するときにします。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint**更新プログラムと関連テーブルの削除を反映する方法に関する規則を適用します。 たとえば、1 つのテーブルの行の値を更新または削除すると同じ値が 1 つの使用も、またはその他の関連テーブル、 **ForeignKeyConstraint**関連テーブルの動作を決定します。  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>と<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>のプロパティ、 **ForeignKeyConstraint**ユーザーが削除または関連テーブルの行を更新しようとしたときに実行されるアクションを定義します。 次の表に、使用できるさまざまな設定、 **DeleteRule**と**UpdateRule**のプロパティ、 **ForeignKeyConstraint**します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|関連付けられている行を削除または更新します。|  
|**SetNull**|関連付けられている行の値を設定**DBNull**します。|  
|**SetDefault**|関連付けられている行の値を既定値に設定します。|  
|**なし**|関連付けられている行に対してアクションは実行しません。 既定値です。|  
  
 A **ForeignKeyConstraint**制限することができますも反映されるまでへの変更が関連する列。 設定されたプロパティに応じて、 **ForeignKeyConstraint** 、列の場合、 **EnforceConstraints**のプロパティ、**データセット**は**true**、親の行に対して操作を実行する、例外が発生します。 たとえば場合、 **DeleteRule**のプロパティ、 **ForeignKeyConstraint**は**None**、子の行がある場合、親の行を削除できません。  
  
 1 つの列間または配列を使用して列の間の外部キー制約を作成することができます、 **ForeignKeyConstraint**コンス トラクター。 結果を渡す**ForeignKeyConstraint**オブジェクトを**追加**メソッド テーブルの**制約**であるプロパティを**ConstraintCollection**. いくつかのオーバー ロードにコンス トラクターの引数を渡すことができますも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **ForeignKeyConstraint**します。  
  
 作成するときに、 **ForeignKeyConstraint**を渡すことができます、 **DeleteRule**と**UpdateRule**するか、引数としてコンス トラクターに値としてのプロパティとして設定できます、次の例 (場所、 **DeleteRule**値に設定されて**None**)。  
  
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
 使用して行への変更を受け入れることができます、 **AcceptChanges**メソッドまたは取り消しを使用して、 **RejectChanges**のメソッド、**データセット**、 **DataTable**、または**DataRow**します。 ときに、**データセット**が含まれています**ForeignKeyConstraints**呼び出すと、 **AcceptChanges**または**RejectChanges**メソッド、を強制します。**AcceptRejectRule**します。 **AcceptRejectRule**のプロパティ、 **ForeignKeyConstraint**子に対して実行されるアクションを決定するときに行**AcceptChanges**または**RejectChanges**は親の行に対して呼び出されます。  
  
 次の表に、利用可能な設定、 **AcceptRejectRule**します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**Cascade**|子の行への変更を受け入れるかまたは拒否します。|  
|**なし**|子の行に対してアクションは実行しません。 既定値です。|  
  
### <a name="example"></a>例  
 次の例では、<xref:System.Data.ForeignKeyConstraint> を作成し、<xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> を含む複数のプロパティを設定して、<xref:System.Data.ConstraintCollection> オブジェクトの <xref:System.Data.DataTable> に追加します。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint**オブジェクトは、1 つの列または列の配列のいずれかに割り当てることができます、 **DataTable**、指定された列または列のすべてのデータが行ごとに一意です。 使用して、列または列の配列に対する unique 制約を作成することができます、 **UniqueConstraint**コンス トラクター。 結果を渡す**UniqueConstraint**オブジェクトを**追加**メソッド テーブルの**制約**であるプロパティを**ConstraintCollection**. いくつかのオーバー ロードにコンス トラクターの引数を渡すことができますも、**追加**のメソッド、 **ConstraintCollection**を作成する、 **UniqueConstraint**します。 作成するときに、 **UniqueConstraint**または複数の列のことができます必要に応じて指定するかどうか、または複数の列が主キー。  
  
 設定して、列の unique 制約を作成することも、 **Unique**プロパティには、列の**true**します。 または、設定、 **Unique**プロパティを 1 つの列の**false**可能性のある任意の unique 制約を削除します。 1 つの列 (または複数の列) をテーブルの主キーとして定義すると、指定した列 (または複数の列) の UNIQUE 制約が自動的に作成されます。 列を削除する場合、 **PrimaryKey**のプロパティを**DataTable**、 **UniqueConstraint**が削除されます。  
  
 次の例では、作成、 **UniqueConstraint**の 2 つの列に、 **DataTable**します。  
  
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
- [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
