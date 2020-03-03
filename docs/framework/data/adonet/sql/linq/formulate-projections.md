---
title: 射影の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793820"
---
# <a name="formulate-projections"></a>射影の作成
次の例では、 `select` Visual Basic のC#ステートメント`Select`とステートメントを他の機能と組み合わせることによってクエリの射影を作成する方法を示します。  
  
## <a name="example"></a>例  
 次の例では`Select` 、Visual Basic (`select`の句句C#) で句を使用して、の`Customers`一連の連絡先名を返します。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>例  
 次の例では`Select` 、句を使用`select`してC#Visual Basic (の句) と*匿名型*の一連の連絡先名と電話`Customers`番号を返します。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>例  
 次の例では`Select` 、句を使用`select`してC#Visual Basic (の句) と*匿名型*の一連の名前と電話番号を返します従業員です。 `Phone` `Name` `HomePhone`フィールドとフィールドが1つのフィールド()に結合され、結果のシーケンスでフィールドの名前がに変更されます。`LastName` `FirstName`  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>例  
 次の例では`Select` 、句を使用`select`してC#Visual Basic (の句) と*匿名型*は、 `ProductID`すべてののシーケンスとと`HalfPrice`いう名前の計算された値を返します。 この値は、`UnitPrice` を 2 で割った値に設定されます。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>例  
 次の例では`Select` 、句を使用`select`してC#Visual Basic (の句) と*条件付きステートメント*を使用して、製品名と製品の可用性のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>例  
 次の例では、 `Select` Visual Basic 句`select` (でC#は句) と*既知の型*(名前) を使用して、従業員の名前のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>例  
 次の例で`Select`は`Where` 、Visual Basic (`select`と`where` C#) のおよびを使用して、ロンドンの顧客の連絡先名の*フィルター処理*されたシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>例  
 次の例では`Select` 、句を使用`select`してC#Visual Basic (の句) と*匿名型*は、顧客に関するデータの整形された*サブセット*を返します。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>例  
 次の例では、入れ子になったクエリを使用して以下の結果を返します。  
  
- すべての注文および対応する `OrderID` のシーケンス。  
  
- 注文内で割引のある項目から成るサブシーケンス。  
  
- 出荷コストが含まれない場合に節約される費用。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>関連項目

- [クエリの例](query-examples.md)
