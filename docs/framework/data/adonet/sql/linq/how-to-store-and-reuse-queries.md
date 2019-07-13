---
title: '方法: クエリを格納および再利用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: 1aac20c3f9c421d353938a83b9e321d35abd244e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033645"
---
# <a name="how-to-store-and-reuse-queries"></a>方法: クエリを格納および再利用する
同じ構造のクエリを何回も実行するアプリケーションでは、1 回コンパイルしたクエリを、パラメーターを変えて何回も実行する方が、多くの場合にパフォーマンスを向上できます。 たとえば、特定の市に住むすべての顧客を取得するアプリケーションで、ユーザーが、対象の市を実行時にフォームで指定するとします。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はこの目的のために *コンパイル済みクエリ* の使用をサポートしています。  
  
> [!NOTE]
>  コンパイル済みクエリは、このパターンの使用法が最も一般的です。 その他にも方法は考えられます。 たとえば、デザイナーによって生成されたコードを継承した部分クラスの静的メンバーとしてコンパイル済みクエリを格納するなどです。  
  
## <a name="example"></a>例  
 スレッド境界を越えてクエリを再利用することが必要となる場合もよくあります。 その場合には、コンパイル済みクエリを静的変数に格納することは特に有効です。 次のコード例では、`Queries` クラスはコンパイル済みクエリを格納するためのクラスで、厳密に型指定された <xref:System.Data.Linq.DataContext> を表す Northwind クラスを使用することを想定しています。  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>例  
 現在できません (静的変数) 内のストアのクエリを返す、*匿名型*型はジェネリック引数として指定する名前があるないため、します。 この問題を回避する方法を次の例に示します。結果を表すことのできる型を作成し、それを汎用引数として使用しています。  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.Linq.CompiledQuery>
- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
