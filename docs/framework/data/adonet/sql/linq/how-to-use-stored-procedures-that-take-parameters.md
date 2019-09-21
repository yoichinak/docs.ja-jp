---
title: '方法: パラメーターを受け取るストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793064"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>方法: パラメーターを受け取るストアド プロシージャを使用する
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、出力パラメーターを参照パラメーターに対応付け、値型はパラメーターを null 許容型として宣言します。  
  
 行セットを返すクエリで入力パラメーターを使用する方法の例については、 [「」を参照してください。行セット](how-to-return-rowsets.md)を返します。  
  
## <a name="example"></a>例  
 次の例は、単一の入力パラメーター (顧客 ID) を受け取り、出力パラメーター (その顧客の売上合計) を返します。  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>例  
 このストアド プロシージャは次のように呼び出すことができます。  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [ストアド プロシージャ](stored-procedures.md)
- [サンプル データベースのダウンロード](downloading-sample-databases.md)
- [Null 許容型の使用](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [null 許容値型](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
