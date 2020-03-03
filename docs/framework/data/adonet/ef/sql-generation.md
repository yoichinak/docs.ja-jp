---
title: SQL 生成
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854360"
---
# <a name="sql-generation"></a>SQL 生成
Entity Framework のプロバイダーを作成する場合は、Entity Framework コマンドツリーを、SQL Server や PL/SQL for Oracle など、特定のデータベースで認識できる SQL に変換する必要があります。 このセクションでは、Entity Framework プロバイダーの SQL 生成コンポーネント (SELECT クエリ用) を開発する方法について説明します。 Insert、update、および delete クエリの詳細については、「 [SQL 生成の変更](modification-sql-generation.md)」を参照してください。  
  
 このセクションを理解するには、Entity Framework と ADO.NET プロバイダーモデルについて理解している必要があります。 また、コマンド ツリーと <xref:System.Data.Common.CommandTrees.DbExpression> について理解している必要もあります。  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL 生成モジュールの役割  
 Entity Framework プロバイダーの SQL 生成モジュールは、指定されたクエリコマンドツリーを、SQL: 1999 に準拠したデータベースを対象とする1つの SQL SELECT ステートメントに変換します。 生成される SQL 内の入れ子になったクエリは、できるだけ少なくする必要があります。 SQL 生成モジュールによって出力クエリ コマンド ツリーを簡素化する必要はありません。 この操作を行うには、結合をなくし、連続するフィルターノードを折りたたむなど Entity Framework します。  
  
 <xref:System.Data.Common.DbProviderServices> クラスは、SQL 生成レイヤーにアクセスしてコマンド ツリーを <xref:System.Data.Common.DbCommand> に変換するための開始点となります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コマンド ツリーの構造](the-shape-of-the-command-trees.md)  
  
 [コマンド ツリーからの SQL の生成: ベスト プラクティス](generating-sql-from-command-trees-best-practices.md)  
  
 [サンプル プロバイダーでの SQL 生成](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>関連項目

- [Entity Framework データ プロバイダーの作成](writing-an-ef-data-provider.md)
