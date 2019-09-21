---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248482"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
WHERE 句は、 [from](from-entity-sql.md)句の直後に適用されます。  
  
## <a name="syntax"></a>構文  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 ブール型です。  
  
## <a name="remarks"></a>Remarks  
 WHERE 句には、「Transact-sql」で説明されているセマンティクスと同じ意味があります。 ソース コレクションの要素を条件を満たすものに制限することで、クエリ式によって生成されるオブジェクトを制限します。  
  
```  
select c from cs as c where e  
```  
  
 式 `e` には Boolean 型が含まれる必要があります。  
  
 WHERE 句は、FROM 句の直後、およびグループ化、順序付け、または投影が実行される前に適用されます。 FROM 句で定義されたすべての要素名は、WHERE 句の式に対して表示されます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
- [クエリ式](query-expressions-entity-sql.md)
