---
title: 名前空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 395ffb23859be27b4897dfc352f6e44d52286b26
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249991"
---
# <a name="namespaces-entity-sql"></a>名前空間 (Entity SQL)
型名、エンティティ セット、関数など、グローバル識別子の名前の競合を防ぐために、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には名前空間が採用されています。 で[!INCLUDE[esql](../../../../../../includes/esql-md.md)]の名前空間のサポートは、.NET Framework での名前空間のサポートに似ています。  
  
 次の例のように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、2 とおりの形式で USING 句を指定できます。1 つは略称的な別名を指定する修飾名前空間、もう 1 つは別名を指定しない非修飾名前空間です。  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名前解決ルール  
 ローカルスコープで識別子を解決できない場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]はグローバルスコープ (名前空間) で名前の検索を試みます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、まず識別子 (プレフィックス) と修飾名前空間の 1 つを照合します。 一致するものがある場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 、は、指定された名前空間内の残りの識別子の解決を試みます。 一致が見つからなかった場合は、例外がスローされます。  
  
 次に[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 、は、識別子に対して (プロローグで指定された) すべての非修飾名前空間の検索を試みます。 その識別子が属している名前空間を一意に特定できた場合は、その場所が返されます。 同じ識別子に対して複数の名前空間が見つかった場合は、例外がスローされます。 識別子に対して名前空間を識別できない[!INCLUDE[esql](../../../../../../includes/esql-md.md)]場合は、次の例に示すように<xref:System.Data.Common.DbCommand> 、 <xref:System.Data.Common.DbConnection>によって次の外側のスコープ (オブジェクトまたはオブジェクト) に名前が渡されます。  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework との違い  
 .NET Framework では、部分修飾された名前空間を使用できます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では使用できません。  
  
## <a name="adonet-usage"></a>ADO.NET の使用法  
 クエリは、ADO.NET の <xref:System.Data.Common.DbCommand> オブジェクトを使用して表されます。 <xref:System.Data.Common.DbCommand> オブジェクトは、<xref:System.Data.Common.DbConnection> オブジェクトに対して構築できます。 名前空間を <xref:System.Data.Common.DbCommand> オブジェクトや <xref:System.Data.Common.DbConnection> オブジェクトの一部として指定することもできます。 が[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリ自体で識別子を解決できない場合、外部の名前空間は (同様の規則に基づいて) プローブされます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [Entity SQL の概要](entity-sql-overview.md)
