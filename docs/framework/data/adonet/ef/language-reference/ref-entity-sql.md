---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 08bcaad4fdc0cf5324ff9976fcf48c23b206e72f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319393"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
エンティティ インスタンスへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```sql  
REF( expression )   
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 エンティティ型のインスタンスを生成する任意の有効な式。  
  
## <a name="return-value"></a>戻り値  
 指定されたエンティティ インスタンスへの参照。  
  
## <a name="remarks"></a>Remarks  
 エンティティ参照は、エンティティ キーとエンティティ セット名で構成されます。 異なるエンティティ セットが同じエンティティ型に基づくことができるので、特定のエンティティ キーが複数のエンティティ セットで使用される場合があります。 ただし、エンティティ参照は常に一意です。 入力式が永続エンティティを表す場合、このエンティティへの参照が返されます。 入力式が永続エンティティではない場合は、NULL 参照が返されます。  
  
 プロパティ抽出演算子 (.) を使用してエンティティのプロパティにアクセスすると、参照は自動的に逆参照されます。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは、REF 演算子を使用して入力エンティティ引数の参照を返します。 プロパティ抽出演算子 (.) を使用して Product エンティティのプロパティにアクセスすることにより、同じクエリでこの参照が逆参照されます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法: PrimitiveType の結果を返すクエリを実行](../how-to-execute-a-query-that-returns-primitivetype-results.md)する」の手順に従います。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>関連項目

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Entity SQL リファレンス](entity-sql-reference.md)
- [型定義](type-definitions-entity-sql.md)
