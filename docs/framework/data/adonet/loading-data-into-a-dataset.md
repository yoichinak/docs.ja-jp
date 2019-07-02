---
title: DataSet へのデータの読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 26b77269b21e1b365f81746ba2df66d7df91677e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504320"
---
# <a name="loading-data-into-a-dataset"></a>DataSet へのデータの読み込み
A <xref:System.Data.DataSet> LINQ to DataSet でそれを照会できる前にオブジェクトを生成する必要があります。 <xref:System.Data.DataSet> には、複数の方法でデータを読み込むことができます。 たとえば、使用することができます[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]データベース クエリを実行しに結果を読み込み、<xref:System.Data.DataSet>します。 詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
 データを <xref:System.Data.DataSet> に読み込む一般的な方法としては、他にも <xref:System.Data.Common.DataAdapter> クラスを使用してデータベースからデータを取得する方法もあります。 この例を次に示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Data.Common.DataAdapter> を使用して、2002 年度の売上情報を照会するクエリを AdventureWorks データベースに対して実行し、その結果を <xref:System.Data.DataSet> に読み込んでいます。 後に、<xref:System.Data.DataSet>が作成されますが、クエリを記述できますに対する LINQ to DataSet を使用しています。 `FillDataSet`でクエリの例でこの例ではメソッドが使用される[LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)します。 詳細については、次を参照してください。[データセットのクエリを実行する](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet の概要](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [DataSet のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
