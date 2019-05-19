---
title: '方法: データベースに接続する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: d38965288884bb72e102d6ec09deca57296c9b0f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882022"
---
# <a name="how-to-connect-to-a-database"></a>方法: データベースに接続する
データベースへの接続、データベースからのオブジェクトの取得、およびデータベースへの変更内容の反映において、<xref:System.Data.Linq.DataContext> は主要な仲介役です。 使用する、 <xref:System.Data.Linq.DataContext> ADO.NET を使用する場合と同じ<xref:System.Data.SqlClient.SqlConnection>します。 つまり、接続または接続文字列を指定して <xref:System.Data.Linq.DataContext> を初期化します。 詳細については [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer) を参照してください。  
  
 <xref:System.Data.Linq.DataContext> の役割は、オブジェクトを求める要求を、データベースに対して発行する SQL クエリに変換し、その結果からオブジェクトを組み立てることです。 <xref:System.Data.Linq.DataContext> では、標準クエリ演算子と同じ演算子パターン ([!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] や `Where` など) を実装することで、`Select` を使用できます。  
  
> [!IMPORTANT]
>  セキュリティで保護された接続を確立することは、最も重要です。 詳細については、次を参照してください。 [LINQ to SQL におけるセキュリティ](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Linq.DataContext> を使用して、Northwind サンプル データベースに接続し、市が London である顧客の行を取得しています。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 各データベース テーブルは `Table` コレクションとして表され、テーブルを識別するエンティティ クラスを使用して <xref:System.Data.Linq.DataContext.GetTable%2A> メソッドでアクセスできます。  
  
## <a name="example"></a>例  
 基本的な <xref:System.Data.Linq.DataContext> クラスおよび <xref:System.Data.Linq.DataContext> メソッドを使用するのではなく、厳密に型指定された <xref:System.Data.Linq.DataContext.GetTable%2A> を宣言するのがベスト プラクティスです。 厳密に型指定された <xref:System.Data.Linq.DataContext> では、次の例のように、すべての `Table` コレクションをそのコンテキストのメンバーとして宣言します。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 この場合、London の顧客を取得するクエリは、次のように簡単に表せます。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [データベースとの通信](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
