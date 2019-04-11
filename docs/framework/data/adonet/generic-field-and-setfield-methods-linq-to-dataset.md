---
title: ジェネリック メソッド Field および SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 7c7f1fef5d1fa575cd6d3bfdb7e6cbbea79ade28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086014"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>ジェネリック メソッド Field および SetField (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 拡張メソッドを提供、<xref:System.Data.DataRow>列の値にアクセスするためのクラス:<xref:System.Data.DataRowExtensions.Field%2A>メソッドと<xref:System.Data.DataRowExtensions.SetField%2A>メソッド。 開発者はこれらのメソッドを使用することで、列値に容易にアクセスできます。特に強化されている点は Null 値の扱いです。 <xref:System.Data.DataSet> が <xref:System.DBNull.Value> を使って Null 値を表現するのに対し、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] では、[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] で導入された Null 許容型が使用されます。 既存の列アクセサーを使用して<xref:System.Data.DataRow>戻りオブジェクトを適切な型をキャストする必要があります。 場合の特定のフィールドを<xref:System.Data.DataRow>を null にできる null 値を明示的にチェックする必要がありますを返すため、<xref:System.DBNull.Value>別の型がスローされますに暗黙的にキャストして、<xref:System.InvalidCastException>します。 次の例では場合、<xref:System.Data.DataRow.IsNull%2A>メソッドが、インデクサーが返された場合、例外がスローされます、null 値の確認に使用されなかった<xref:System.DBNull.Value>にキャストしようと、<xref:System.String>します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> は、<xref:System.Data.DataRow> の列値にアクセスするためのメソッドです。<xref:System.Data.DataRowExtensions.SetField%2A> は、<xref:System.Data.DataRow> の列値を設定するためのメソッドです。 <xref:System.Data.DataRowExtensions.Field%2A> メソッドも <xref:System.Data.DataRowExtensions.SetField%2A> メソッドも Null 許容型を扱うことができるため、前出の例のように Null 値を明示的にチェックする必要はありません。 また、どちらのメソッドもジェネリック メソッドであるため、戻り値の型をキャストする必要もありません。  
  
 次の例では、<xref:System.Data.DataRowExtensions.Field%2A> メソッドを使用します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 `T` メソッドおよび <xref:System.Data.DataRowExtensions.Field%2A> メソッドのジェネリック パラメーター <xref:System.Data.DataRowExtensions.SetField%2A> に指定するデータ型は、基になる値の型と一致している必要があります。 それ以外の場合、<xref:System.InvalidCastException> 例外がスローされます。 指定する列の名前も <xref:System.Data.DataSet> 内の列名と一致している必要があります。一致していない場合、<xref:System.ArgumentException> がスローされます。 どちらの場合も、例外は、実行時にデータが列挙されて、クエリが実行されたときにスローされます。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> メソッド自体は、型変換を一切実行しません。 ただし、型変換がまったく発生しないということではありません。 <xref:System.Data.DataRowExtensions.SetField%2A>メソッドが公開、[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]の動作、<xref:System.Data.DataRow>クラス。 によって、型変換を実行、<xref:System.Data.DataRow>にオブジェクトと変換後の値を保存するとし、<xref:System.Data.DataRow>オブジェクト。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRowExtensions>
