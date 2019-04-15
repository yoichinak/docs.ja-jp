---
title: '方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: 9f87ff28c4da864df8004f3baa1a8339503fb351
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324744"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する
このトピックでは、実行する方法を示します、[!INCLUDE[esql](../../../../../includes/esql-md.md)]クエリを使用してパラメーターを持つ、<xref:System.Data.EntityClient.EntityCommand>オブジェクト。  
  
### <a name="to-run-the-code-in-this-example"></a>この例のコードを実行するには  
  
1. 追加、 [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)をプロジェクトに使用するプロジェクトを構成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 詳細については、「[方法 :エンティティ データ モデル ウィザードを使用して](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))します。  
  
2. アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>例  
 次の例では、2 つのパラメーターを持つクエリ文字列を作成する方法を示します。 次に、<xref:System.Data.EntityClient.EntityCommand> を作成した後、2 つのパラメーターを <xref:System.Data.EntityClient.EntityParameter> の <xref:System.Data.EntityClient.EntityCommand> コレクションに追加し、`Contact` アイテムのコレクションに対して反復処理を実行します。  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>関連項目

- [方法: パラメーター化クエリを実行します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
