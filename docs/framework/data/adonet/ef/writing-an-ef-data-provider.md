---
title: Entity Framework データ プロバイダーの作成
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248187"
---
# <a name="writing-an-entity-framework-data-provider"></a>Entity Framework データ プロバイダーの作成
このセクションでは、SQL Server 以外[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]のデータソースをサポートするプロバイダーを作成する方法について説明します。 に[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]は、SQL Server をサポートするプロバイダーが含まれています。  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework プロバイダー モデルの概要  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はデータベースに依存しません。ADO.NET プロバイダー モデルを使用して、さまざまなデータ ソースに接続するプロバイダーを作成できます。  
  
 ADO.NET データ プロバイダー モデルを使用して構築された Entity Framework データ プロバイダーは、次の機能を実行します。  
  
- Entity Data Model (EDM) プリミティブ型をプロバイダー型にマップします。  
  
- プロバイダー固有の関数を公開します。  
  
- 指定された DbQueryCommandTree に対してプロバイダー固有のコマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] クエリをサポートします。  
  
- 指定された DbModificationCommandTree に対してプロバイダー固有の更新コマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を介した更新をサポートします。  
  
- ストア スキーマ定義のマッピング ファイルを公開して、データベースに基づくモデルの生成をサポートします。  
  
- 概念モデルを使用してメタデータ (テーブルとビューなど) を公開します。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>サンプル  
 SQL Server 以外のデータソースをサポートする[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]プロバイダーのサンプルについては、 [Entity Framework サンプルプロバイダー](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL 生成](sql-generation.md)  
  
 [変更 SQL 生成](modification-sql-generation.md)  
  
 [プロバイダー マニフェストの仕様](provider-manifest-specification.md)  
  
## <a name="see-also"></a>関連項目

- [データ プロバイダーの操作](working-with-data-providers.md)
