---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489854"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
WHERE 句は、直後に適用、 [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)句。  
  
## <a name="syntax"></a>構文  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 ブール型です。  
  
## <a name="remarks"></a>Remarks  
 TRANSACT-SQL の説明に従って、WHERE 句は同じ意味を持ちます。 ソース コレクションの要素を条件を満たすものに制限することで、クエリ式によって生成されるオブジェクトを制限します。  
  
```  
select c from cs as c where e  
```  
  
 式 `e` には Boolean 型が含まれる必要があります。  
  
 WHERE 句は、FROM 句の直後、およびグループ化、順序付け、または投影が実行される前に適用されます。 FROM 句で定義されたすべての要素名は、WHERE 句の式に対して表示されます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [クエリ式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
