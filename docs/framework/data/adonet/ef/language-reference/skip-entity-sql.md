---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: e8ef529ea8d2be2ef8eb3a2eb606e7ca8bf13f0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797746"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)
物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。 SKIP を ORDER BY 句と切り離して使用することはできません。  
  
## <a name="syntax"></a>構文  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>引数  
 `n`  
 スキップするアイテムの数。  
  
## <a name="remarks"></a>Remarks  
 SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。 たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。  
  
> [!NOTE]
>  TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。 TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。  
  
> [!NOTE]
>  [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]では、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返される場合があります。 キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。 これは、 [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]用に SKIP が変換される方法によるものです。 たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]でクエリを[方法。クエリの結果をページ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))を SKIP と共に SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を使用します。  
  
## <a name="see-also"></a>関連項目

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [方法: クエリ結果 ページ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [ページング](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
