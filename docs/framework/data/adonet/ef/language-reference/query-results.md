---
title: クエリ結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 165fb1524daa781c29037bf1c9cb2b3013504177
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539740"
---
# <a name="query-results"></a>クエリ結果
LINQ to Entities クエリをコマンド ツリーに変換して実行すると、クエリの結果は通常、次のいずれかとして返されます。  
  
- 0 個以上の型指定されたエンティティ オブジェクトのコレクション、または概念モデルの複合型のプロジェクション。  
  
- 概念モデルでサポートされる CLR 型。  
  
- インライン コレクション。  
  
- 匿名型。  
  
 データ ソースに対してクエリを実行すると、その結果は CLR 型に具体化されてクライアントに返されます。 オブジェクトの具体化は、すべて [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] によって実行されます。 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] と CLR の間のマッピングができないことが原因でエラーが発生すると、オブジェクトの具体化中に例外がスローされます。  
  
 プリミティブ概念モデル型を返すクエリを実行した場合、その結果は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] から切り離されたスタンドアロンの CLR 型で構成されます。 ただし、クエリが <xref:System.Data.Objects.ObjectQuery%601> によって表されるエンティティ オブジェクトのコレクションを返す場合、これらの型はオブジェクト コンテキストによって追跡されます。 すべてのオブジェクトの動作 (子/親のコレクション、変更の追跡、ポリモーフィズムなど) で定義されているは、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]します。 この機能は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] で定義されるようにその機能の範囲内で使用されます。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)します。  
  
 クエリから返される構造型 (匿名型、NULL 値が許容される複合型など) は、`null` 値になります。 返されたエンティティの <xref:System.Data.Objects.DataClasses.EntityCollection%601> プロパティも `null` 値になります。 これは、要素を持たない `null` に対する <xref:System.Linq.Queryable.FirstOrDefault%2A> の呼び出しなど、<xref:System.Data.Objects.ObjectQuery%601> 値になっているエンティティのコレクション プロパティが投影されるためです。  
  
 場合によっては、特定のクエリで実行中に具体化された結果が生成されることもありますが、クエリはサーバー上で実行され、CLR でエンティティ オブジェクトが具体化されることはありません。 オブジェクトが具体化された場合、その結果に依存すると、問題が発生する可能性があります。  
  
 次の例には、`MyContact` プロパティがあるカスタム クラス `LastName` が含まれています。 `LastName` プロパティを設定すると、`count` 変数が増加します。 次の 2 つのクエリを実行した場合、最初のクエリによって `count` が増加しますが、2 つ目のクエリでは増加しません。 これは、ストアでクエリを実行する必要がないため、2 つ目のクエリで結果から `LastName` プロパティが投影され、`MyContact` クラスが作成されないことが、その理由です。  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
