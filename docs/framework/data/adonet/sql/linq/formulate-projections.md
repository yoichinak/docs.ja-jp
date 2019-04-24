---
title: 射影の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223304"
---
# <a name="formulate-projections"></a>射影の作成
次の例に示す方法、`select`ステートメントC#と`Select`Visual Basic でのステートメントは、クエリ射影を作成するには、その他の機能と組み合わせることができます。  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) 連絡先の名前のシーケンスを返します`Customers`します。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) と*匿名型*に連絡先の名前のシーケンスを返すし、電話番号の`Customers`します。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) と*匿名型*名前のシーケンスを返すし、従業員の電話番号にします。 `FirstName`と`LastName`フィールドが 1 つのフィールドに結合されます (`Name`)、および`HomePhone`フィールドの名前を変更する`Phone`結果のシーケンス。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) と*匿名型*すべてのシーケンスを返します`ProductID`という名前の計算値と`HalfPrice`します。 この値は、`UnitPrice` を 2 で割った値に設定されます。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) と*条件付きステートメント*製品名および製品の可用性のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>例  
 次のコードの例では、Visual Basic`Select`句 (`select`句C#) と*既知の型*従業員の名前のシーケンスを返します (名前)。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>例  
 次の例では使用`Select`と`Where`Visual basic (`select`と`where`でC#) を返す、*フィルター処理されたシーケンス*ロンドン在住の顧客の連絡先の名の。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic での句 (`select`句C#) と*匿名型*を返す、*成型されたサブセット*の顧客に関するデータ。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>例  
 次の例では、入れ子になったクエリを使用して以下の結果を返します。  
  
-   すべての注文および対応する `OrderID` のシーケンス。  
  
-   注文内で割引のある項目から成るサブシーケンス。  
  
-   出荷コストが含まれない場合に節約される費用。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>関連項目

- [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
