---
title: ジェネリック メソッド Field および SetField (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249104"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>ジェネリック メソッド Field および SetField (LINQ to DataSet)
LINQ to DataSet は、<xref:System.Data.DataRow>列の値 (メソッドとメソッド<xref:System.Data.DataRowExtensions.Field%2A>) に<xref:System.Data.DataRowExtensions.SetField%2A>アクセスするためのクラスに拡張メソッドを提供します。 開発者はこれらのメソッドを使用することで、列値に容易にアクセスできます。特に強化されている点は Null 値の扱いです。 NULL <xref:System.Data.DataSet> <xref:System.DBNull.Value?displayProperty=nameWithType>値を表すために使用されますが、LINQ<xref:System.Nullable>では<xref:System.Nullable%601>と の型が使用されます。 の既存の列アクセサーを使用<xref:System.Data.DataRow>するには、戻りオブジェクトを適切な型にキャストする必要があります。 内の特定のフィールドが<xref:System.Data.DataRow>null である可能性がある場合は、null 値を明示的<xref:System.DBNull.Value?displayProperty=nameWithType>にチェックする必要があります。 <xref:System.InvalidCastException> 次の例では、メソッドが<xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType>null 値のチェックに使用されなかった場合、インデクサーが返されて<xref:System.DBNull.Value?displayProperty=nameWithType>それをにキャストしようとした場合に例外が<xref:System.String>スローされます。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> は、<xref:System.Data.DataRow> の列値にアクセスするためのメソッドです。<xref:System.Data.DataRowExtensions.SetField%2A> は、<xref:System.Data.DataRow> の列値を設定するためのメソッドです。 メソッドと<xref:System.Data.DataRowExtensions.Field%2A><xref:System.Data.DataRowExtensions.SetField%2A>メソッドの両方が null 許容値型を処理するため、前の例のように null 値を明示的にチェックする必要はありません。 また、どちらのメソッドもジェネリック メソッドであるため、戻り値の型をキャストする必要もありません。  
  
 次の例では、<xref:System.Data.DataRowExtensions.Field%2A> メソッドを使用します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 `T` メソッドおよび <xref:System.Data.DataRowExtensions.Field%2A> メソッドのジェネリック パラメーター <xref:System.Data.DataRowExtensions.SetField%2A> に指定するデータ型は、基になる値の型と一致している必要があります。 それ以外の場合、<xref:System.InvalidCastException> 例外がスローされます。 指定する列の名前も <xref:System.Data.DataSet> 内の列名と一致している必要があります。一致していない場合、<xref:System.ArgumentException> がスローされます。 どちらの場合も、例外は、実行時にデータが列挙されて、クエリが実行されたときにスローされます。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> メソッド自体は、型変換を一切実行しません。 ただし、型変換がまったく発生しないということではありません。 この<xref:System.Data.DataRowExtensions.SetField%2A>メソッドは、クラスのADO.NET動作を<xref:System.Data.DataRow>公開します。 オブジェクトによって型変換を<xref:System.Data.DataRow>実行し、変換された値をオブジェクトに<xref:System.Data.DataRow>保存できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRowExtensions>
