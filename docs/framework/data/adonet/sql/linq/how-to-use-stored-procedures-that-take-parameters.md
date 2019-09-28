---
title: '方法: パラメーターを受け取るストアド プロシージャを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: c2b657f704d072b987578be5520a58d007ecac37
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353019"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>方法: パラメーターを受け取るストアド プロシージャを使用する
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、出力パラメーターを参照パラメーターに対応付け、値型はパラメーターを null 許容型として宣言します。  
  
 行セットを返すクエリで入力パラメーターを使用する方法の例については、「@no__t」を参照してください。行セット @ no__t-0 を返します。  
  
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
- [Null 許容値型の使用](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [null 許容値型](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
