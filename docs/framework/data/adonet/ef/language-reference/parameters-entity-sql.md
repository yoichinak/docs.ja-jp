---
title: パラメーター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187675"
---
# <a name="parameters-entity-sql"></a>パラメーター (Entity SQL)
パラメーターは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の外部で定義される変数です。通常は、ホスト言語で使用されるバインド API を通じて定義されます。 それぞれのパラメーターには、名前と型があります。 パラメーター名が使用してクエリ式で定義されているので (@) 記号をプレフィックスとして。 これにより、クエリ内で定義されている他の名前 (プロパティ名など) と明確に区別されます。  
  
 パラメーターをバインドするための API は、ホスト言語によって提供されます。  
  
## <a name="example"></a>例  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
