---
title: '方法: ユーザー定義関数をインラインで呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: ed8071352902b8f97445cbfa5ff0ebe8fead9bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163710"
---
# <a name="how-to-call-user-defined-functions-inline"></a>方法: ユーザー定義関数をインラインで呼び出す
ユーザー定義関数はインラインで呼び出すことができますが、遅延実行のクエリに含まれる関数は、そのクエリが実行されるまで実行されません。 詳細については、「[LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
 同じ関数をクエリの外部で呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって、メソッド呼び出し式から単純なクエリが作成されます。 この SQL 構文を次に示します (`@p0` パラメーターは渡される定数にバインドされます)。  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 次を作成します。  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>例  
 次に[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]クエリ、生成されたユーザー定義関数メソッドの呼び出しをインラインにご覧`ReverseCustName`します。 クエリは遅延実行されるので、この関数は即座には実行されません。 このクエリ用に作成される SQL は、データベース内のユーザー定義関数の呼び出しに変換されます (クエリの後の SQL コードを参照してください)。  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>関連項目

- [ユーザー定義関数](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
