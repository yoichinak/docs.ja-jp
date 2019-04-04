---
title: GUID と uniqueidentifier 値の比較
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: d773b6e49a9f3c2909b2479abdc498d4b059f660
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674063"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>GUID と uniqueidentifier 値の比較
SQL Server のグローバル一意識別子 (GUID: Globally Unique Identifier) データ型は、16 バイトのバイナリ値を格納する `uniqueidentifier` データ型で表現されます。 GUID は、2 進数の値です。GUID は主に、多数のコンピューターが多数のサイトに存在するネットワーク内で、一意である必要のある識別子として使用されます。 GUID は、Transact-SQL NEWID 関数を呼び出すことにより生成され、世界中のコンピューターの中で一意であることが保証されています。 詳細については、[一意識別子 (TRANSACT-SQL)](/sql/t-sql/data-types/uniqueidentifier-transact-sql)を参照してください。  
  
## <a name="working-with-sqlguid-values"></a>SqlGuid 値の使用  
 GUID の値は長くて不可解な値であるため、ユーザーには意味がわかりません。 ランダムに生成された GUID をキー値として使用して多数の行を挿入した場合に、ランダムな I/O をインデックスにすると、パフォーマンスに悪影響を及ぼします。 また、GUID は、その他のデータ型に比べてサイズが大きくなります。 通常、GUID は、その他のデータ型が適さないような非常に限られた場合にのみ使用することをお勧めします。  
  
### <a name="comparing-guid-values"></a>GUID 値の比較  
 `uniqueidentifier` 型の値には比較演算子が使用できます。 ただし、順序付けは、2 つの値のビット パターンの比較によっては実装されません。 に対して実行可能な唯一の操作を`uniqueidentifier`値には比較 (=、<>、 \<、>、 \<=、> =) と NULL (IS NULL と IS NOT NULL) をチェックします。 これ以外の算術演算子を使用することはできません。  
  
 <xref:System.Guid> と <xref:System.Data.SqlTypes.SqlGuid> のいずれも、異なる GUID 値を比較するための `CompareTo` メソッドを持っています。 ただし、`System.Guid.CompareTo` と `SqlTypes.SqlGuid.CompareTo` では実装方法が異なります。 <xref:System.Data.SqlTypes.SqlGuid> は、値の末尾 6 バイトが最上位になる SQL Server の動作に従って `CompareTo` を実装します。 <xref:System.Guid> は、16 バイトすべてを評価します。 次の例は、この動作の違いを示しています。 コードの最初のセクションは、並べ替えられていない <xref:System.Guid> 値を表示し、コードの 2 つ目のセクションは、並べ替えられた <xref:System.Guid> 値を示します。 3 つ目のセクションは、並べ替えられた <xref:System.Data.SqlTypes.SqlGuid> 値を示します。 出力は、コードの一覧の下に表示されます。  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 この例を実行すると、次の結果が得られます。  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](sql-server-data-types.md)
- [ADO.NET の概要](../ado-net-overview.md)
