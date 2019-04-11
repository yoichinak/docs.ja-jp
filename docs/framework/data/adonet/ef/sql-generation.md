---
title: SQL 生成
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 108a68f74849c7fa1418775c2a37db06d9d947ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180573"
---
# <a name="sql-generation"></a>SQL 生成
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] のプロバイダーを作成する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] コマンド ツリーを特定のデータベースが認識できる SQL (たとえば、SQL Server の場合は Transact-SQL、Oracle の場合は PL/SQL) に変換する必要があります。 ここでは、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーの SQL 生成コンポーネント (SELECT クエリ用) の開発方法を説明します。 挿入については、更新、およびクエリの削除を参照してください[変更 SQL 生成](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)します。  
  
 このセクションの内容を理解するには、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] と ADO.NET プロバイダー モデルについての知識が必要です。 また、コマンド ツリーと <xref:System.Data.Common.CommandTrees.DbExpression> について理解している必要もあります。  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL 生成モジュールの役割  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーの SQL 生成モジュールは、指定されたクエリ コマンド ツリーを、SQL:1999 準拠のデータベースを対象とする 1 つの SQL SELECT ステートメントに変換します。 生成される SQL 内の入れ子になったクエリは、できるだけ少なくする必要があります。 SQL 生成モジュールによって出力クエリ コマンド ツリーを簡素化する必要はありません。 これは、結合の排除や連続するフィルター ノードの折りたたみなどにより、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] が実行する処理です。  
  
 <xref:System.Data.Common.DbProviderServices> クラスは、SQL 生成レイヤーにアクセスしてコマンド ツリーを <xref:System.Data.Common.DbCommand> に変換するための開始点となります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コマンド ツリーの構造](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [コマンド ツリーからの SQL の生成: ベスト プラクティス](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [サンプル プロバイダーでの SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>関連項目

- [Entity Framework データ プロバイダーの作成](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
