---
title: DataSet へのデータの読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794960"
---
# <a name="loading-data-into-a-dataset"></a>DataSet へのデータの読み込み
LINQ to DataSet <xref:System.Data.DataSet>でクエリを実行する前に、まずオブジェクトに値を設定する必要があります。 <xref:System.Data.DataSet> には、複数の方法でデータを読み込むことができます。 たとえば、を使用[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]してデータベースに対してクエリを実行し、その<xref:System.Data.DataSet>結果をに読み込むことができます。 詳細については、「[LINQ to SQL](./sql/linq/index.md)」を参照してください。  
  
 データを <xref:System.Data.DataSet> に読み込む一般的な方法としては、他にも <xref:System.Data.Common.DataAdapter> クラスを使用してデータベースからデータを取得する方法もあります。 この例を次に示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Data.Common.DataAdapter> を使用して、2002 年度の売上情報を照会するクエリを AdventureWorks データベースに対して実行し、その結果を <xref:System.Data.DataSet> に読み込んでいます。 に値<xref:System.Data.DataSet>が設定されたら、LINQ to DataSet を使用して、そのデータに対するクエリを作成できます。 この例の `FillDataSet` メソッドは [LINQtoDataSet 例](linq-to-dataset-examples.md)のクエリ例で使用されています。 詳細については、「[データセットのクエリ](querying-datasets-linq-to-dataset.md)」を参照してください。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet の概要](linq-to-dataset-overview.md)
- [DataSet のクエリ](querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet の例](linq-to-dataset-examples.md)
