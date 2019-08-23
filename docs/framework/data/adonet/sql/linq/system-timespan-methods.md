---
title: System.TimeSpan メソッド
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: ec27f8f17a6709efef1a8230b521778095ae1257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947092"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan メソッド
<xref:System.TimeSpan?displayProperty=nameWithType> のメンバー サポートは、使用している .NET Framework と Microsoft SQL Server のバージョンに大きく依存します。  
  
 メソッド、演算子、またはプロパティがサポートされていなければ、LINQ to SQL でメンバーを変換して SQL Server で実行することができません。 それでもこれらのメンバーをコードで使用することはできますが、 クエリが Transact-SQL に変換される前か、データベースから結果が取得された後で評価する必要があります。  
  
## <a name="previous-limitations"></a>以前の制限  
 .NET Framework 3.5 SP1 より前のバージョンの .NET Framework で LINQ to SQL を使用すると、SQL Server のデータベース フィールドを <xref:System.TimeSpan?displayProperty=nameWithType> にマッピングできません。 ただし、<xref:System.TimeSpan> 値を <xref:System.TimeSpan> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.DateTime> の操作はサポートされています。  
  
## <a name="supported-systemtimespan-member-support"></a>サポートされている TimeSpan メンバーサポート

 LINQ to SQL でサポートされている以下のメソッド、演算子、およびプロパティは、LINQ to SQL のクエリで使用できます。 オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、LINQ to SQL クエリ内で <xref:System.TimeSpan?displayProperty=nameWithType> メンバーの多くを呼び出すことができます。  
  
|サポートされている <xref:System.TimeSpan> メソッド|サポートされている <xref:System.TimeSpan> 演算子|サポートされている <xref:System.TimeSpan> プロパティ|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> LINQ to SQL で <xref:System.TimeSpan?displayProperty=nameWithType> を SQL の `TIME` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。 SQL の `TIME` データ型は Microsoft SQL Server 2008 以降でのみ使用可能です。  
  
### <a name="addition-and-subtraction"></a>加算と減算  
 加算と減算は、CLR の <xref:System.TimeSpan?displayProperty=nameWithType> 型ではサポートされていますが、SQL の `TIME` 型ではサポートされていません。 そのため、LINQ to SQL クエリにより、SQL の `TIME` 型にマッピングしたときに加算や減算を試みると、エラーが発生します。 Sql の日付と時刻の型の使用に関するその他の考慮事項については、 [「SQL CLR 型のマッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [オブジェクト モデルの作成](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [SQL と CLR の型マッピング](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [データ型と関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
