---
title: DataTable の制約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151287"
---
# <a name="datatable-constraints"></a>DataTable の制約
制約を使用すると、データの整合性を維持するために <xref:System.Data.DataTable> のデータを強制的に制限できます。 制約は、1 つの列または関連付けられた複数の列に対して自動的に適用される規則であり、行の値がなんらかの方法で変更されたときに実行されるアクションを決定します。 制約は、 の`System.Data.DataSet.EnforceConstraints`プロパティ<xref:System.Data.DataSet>が true**の**場合に適用されます。 `EnforceConstraints` プロパティの設定方法のコード例については、<xref:System.Data.DataSet.EnforceConstraints%2A> のリファレンス トピックを参照してください。  
  
 ADO.NET には、<xref:System.Data.ForeignKeyConstraint> と <xref:System.Data.UniqueConstraint> の 2 種類の制約があります。 既定では<xref:System.Data.DataRelation>**、DataSet**に a を追加して、2 つ以上のテーブル間のリレーションシップを作成すると、両方の制約が自動的に作成されます。 ただし、リレーションシップの作成時に**createConstraints** = **false**を指定することで、この動作を無効にできます。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **外部キー制約**は、更新と削除を関連するテーブルに伝達する方法に関する規則を適用します。 たとえば、あるテーブルの行の値が更新または削除され、その同じ値が 1 つ以上の関連テーブルでも使用されている場合 **、ForeignKeyConstraint は**関連テーブルでの動作を決定します。  
  
 **ForeignKeyConstraint**の プロパティ<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A><xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>は、ユーザーが関連テーブルの行を削除または更新しようとしたときに実行されるアクションを定義します。 次の表に、**外部キー制約**の**DeleteRule**プロパティと**UpdateRule**プロパティで使用できるさまざまな設定を示します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**カスケード**|関連付けられている行を削除または更新します。|  
|**SetNull**|関連する行の値を**DBNull**に設定します。|  
|**SetDefault**|関連付けられている行の値を既定値に設定します。|  
|**なし**|関連付けられている行に対してアクションは実行しません。 これは既定値です。|  
  
 **外部キー制約**は、関連する列への変更を制限するだけでなく、反映することもできます。 列の**ForeignKeyConstraint**プロパティに設定されているプロパティに応じて **、DataSet**の**EnforceConstraints**プロパティが**true の**場合、親行に対して特定の操作を実行すると例外が発生します。 たとえば、**外部キー制約**の**DeleteRule**プロパティが**None**の場合、親行に子行がある場合は削除できません。  
  
 単一の列間、または列の配列間に**外部キー制約を作成するには、ForeignKeyConstraint**コンストラクターを使用します。 結果として生成された**ForeignKeyConstraint**オブジェクトを、テーブルの**制約**プロパティの**Add**メソッドに渡**します**。 また、コンストラクタ引数を、外部**キー制約**を作成するために **、制約コレクション**の**Add**メソッドの複数のオーバーロードに渡すこともできます。  
  
 **外部キー制約**を作成するときに、**引数として、コンストラクターに DeleteRule**値と**UpdateRule**値を渡すか、次の例のようにプロパティとして設定できます **(DeleteRule**値が**None**に設定されている場合)。  
  
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
 行への変更は **、AcceptChanges**メソッドを使用して受け入れるか、**データセット**、データセット、データ**テーブル**、または**データ行**の**RejectChanges**メソッドを使用してキャンセルできます。 **データセット**に**外部キー制約**が含まれている場合 **、AcceptChanges**メソッドまたは**RejectChanges**メソッドを呼び出すと **、AcceptRejectRule**が強制的に適用されます。 **外部キー制約**の**AcceptRejectRule**プロパティは、親行に対して**AcceptChanges**または**RejectChanges**が呼び出されたときに、子行に対して実行されるアクションを決定します。  
  
 次の表に **、AcceptRejectRule**で使用できる設定を示します。  
  
|規則の設定|説明|  
|------------------|-----------------|  
|**カスケード**|子の行への変更を受け入れるかまたは拒否します。|  
|**なし**|子の行に対してアクションは実行しません。 これは既定値です。|  
  
### <a name="example"></a>例  
 次の例では、<xref:System.Data.ForeignKeyConstraint> を作成し、<xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> を含む複数のプロパティを設定して、<xref:System.Data.ConstraintCollection> オブジェクトの <xref:System.Data.DataTable> に追加します。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 1 つの列または**DataTable**内の列の配列に割り当てることができる**UniqueConstraint**オブジェクトは、指定した列または列のすべてのデータが行ごとに一意であることを保証します。 UNIQUEConstraint コンストラクターを使用して、列または列の配列に対して**一意の**制約を作成できます。 結果の**一意制約**オブジェクトを、テーブルの**制約**プロパティの**Add**メソッドに渡**します**。 また、コンストラクタ引数を **、制約コレクション**の**Add**メソッドの複数のオーバーロードに渡して **、UniqueConstraint**を作成することもできます。 列に**対して一意性制約**を作成する場合、列が主キーであるかどうかをオプションで指定できます。  
  
 列の Unique プロパティを**true**に設定して、列に**対する一意**の制約を作成することもできます。 または、単一列の**Unique**プロパティを**false**に設定すると、存在する可能性のある UNIQUE 制約が削除されます。 1 つの列 (または複数の列) をテーブルの主キーとして定義すると、指定した列 (または複数の列) の UNIQUE 制約が自動的に作成されます。 **列をデータ テーブル**の**主キー**プロパティから削除すると、**一意制約**が削除されます。  
  
 次の例では **、DataTable**の 2 つの列に対して**一意の制約**を作成します。  
  
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
- [ADO.NET の概要](../ado-net-overview.md)
