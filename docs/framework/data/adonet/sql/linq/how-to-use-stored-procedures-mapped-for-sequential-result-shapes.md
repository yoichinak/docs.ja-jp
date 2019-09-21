---
title: '方法: シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: bae10e823a274304f21292cf55947a4d4eaccc10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781458"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>方法: シーケンシャルな結果形状が割り当てられたストアド プロシージャを使用する
この種類のストアド プロシージャでは、複数の結果形状が生成されますが、どの順序で結果が返されるかがわかります。 このシナリオは、返される結果のシーケンスがわからないシナリオと対照的です。 詳細については、「[方法 :複数の結果形状](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)にマップされたストアドプロシージャを使用します。  
  
## <a name="example"></a>例  
 次は、複数の結果形状をシーケンシャルに返すストアド プロシージャの T-SQL です。  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>例  
 このストアド プロシージャを実行するには、次のようなコードを使用します。  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [ストアド プロシージャ](stored-procedures.md)
