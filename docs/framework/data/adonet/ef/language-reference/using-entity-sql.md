---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 6a5b374bc253cb2deb7a9e1de942c32d8e8bbfcf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168026"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)
クエリ式で使用する名前空間を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>引数  
 `alias`  
 名前空間を修飾する短い別名。  
  
 `namespace`  
 任意の有効な名前空間。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、USING 演算子を使用して、クエリ式に使用する名前空間が指定されています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)します。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>関連項目

- [名前空間](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
