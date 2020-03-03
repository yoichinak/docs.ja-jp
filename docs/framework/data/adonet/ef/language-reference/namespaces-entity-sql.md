---
title: 名前空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319554"
---
# <a name="namespaces-entity-sql"></a>名前空間 (Entity SQL)
型名、エンティティ セット、関数など、グローバル識別子の名前の競合を防ぐために、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には名前空間が採用されています。 @No__t-0 での名前空間のサポートは、.NET Framework での名前空間のサポートに似ています。  
  
 次の例のように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、2 とおりの形式で USING 句を指定できます。1 つは略称的な別名を指定する修飾名前空間、もう 1 つは別名を指定しない非修飾名前空間です。  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名前解決ルール  
 ローカルスコープで識別子を解決できない場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] はグローバルスコープ (名前空間) で名前を検索しようとします。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、まず識別子 (プレフィックス) と修飾名前空間の 1 つを照合します。 一致するものがある場合は、指定した名前空間内の残りの識別子の解決が [!INCLUDE[esql](../../../../../../includes/esql-md.md)] によって試行されます。 一致が見つからなかった場合は、例外がスローされます。  
  
 次に、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、識別子に対して (プロローグで指定された) すべての非修飾名前空間を検索しようとします。 その識別子が属している名前空間を一意に特定できた場合は、その場所が返されます。 同じ識別子に対して複数の名前空間が見つかった場合は、例外がスローされます。 識別子の名前空間を識別できない場合は、次の例に示すように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は次の外側のスコープ (<xref:System.Data.Common.DbCommand> または <xref:System.Data.Common.DbConnection> のオブジェクト) に名前を渡します。  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework との違い  
 .NET Framework では、部分修飾された名前空間を使用できます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では使用できません。  
  
## <a name="adonet-usage"></a>ADO.NET の使用法  
 クエリは、ADO.NET の <xref:System.Data.Common.DbCommand> オブジェクトを使用して表されます。 <xref:System.Data.Common.DbCommand> オブジェクトは、<xref:System.Data.Common.DbConnection> オブジェクトに対して構築できます。 名前空間を <xref:System.Data.Common.DbCommand> オブジェクトや <xref:System.Data.Common.DbConnection> オブジェクトの一部として指定することもできます。 @No__t-0 でクエリ自体の識別子を解決できない場合は、(同様のルールに基づいて) 外部の名前空間がプローブされます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [Entity SQL の概要](entity-sql-overview.md)
