---
title: Entity Framework 用 SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: d81499961e7e47bba3b2594ddddd192c87a4a936
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879120"
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework 用 SqlClient
このセクションでは、.NET Framework Data Provider for SQL Server (SqlClient) について説明します。これによって、Microsoft SQL Server 上で Entity Framework が機能できるようになります。  
  
## <a name="provider-schema-attribute"></a>Provider スキーマ属性  
 `Provider` は、ストア スキーマ定義言語 (SSDL) の `Schema` 要素の属性です。  
  
 SqlClient を使用するには、文字列 "System.Data.SqlClient" を `Provider` 要素の `Schema` 属性に割り当てます。  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken スキーマ属性  
 `ProviderManifestToken` は、SSDL の`Schema` 要素の必須の属性です。 このトークンは、オフライン シナリオ用のプロバイダー マニフェストを読み込むために使用されます。 詳細については`ProviderManifestToken`属性は、「[スキーマ要素 (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl)します。  
  
 SqlClient は、異なるバージョンの SQL Server 用データ プロバイダーとして使用できます。 これらのバージョンでは機能が異なります。 たとえば、[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] では、`varchar(max)` で導入された `nvarchar(max)` 型および [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 型をサポートしていません。  
  
 SqlClient は、SQL Server の各バージョンに対応する次のプロバイダー マニフェスト トークンを生成し、受け取ります。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Visual Studio 2010 以降で、 [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))SQL Server 2000 をサポートしていません。  
  
## <a name="provider-namespace-name"></a>プロバイダーの名前空間名  
 すべてのプロバイダーで名前空間を指定する必要があります。 このプロパティによって、型や関数など、プロバイダーが特定のコンストラクターに使用するプレフィックスを Entity Framework に通知できます。 SqlClient プロバイダー マニフェストの名前空間は `SqlServer` です。 名前空間の詳細については、次を参照してください。[名前空間](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)します。  
  
## <a name="types"></a>種類  
 Entity Framework 用の SqlClient プロバイダーは、概念モデルの型と SQL Server 型の間のマッピング情報を提供します。 詳細については、次を参照してください。[エンティティ FrameworkTypes 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)します。  
  
## <a name="functions"></a>関数  
 Entity Framework 用の SqlClient プロバイダーは、プロバイダーがサポートする関数の一覧を定義します。 サポートされている関数の一覧は、次を参照してください。 [Entity Framework の関数の SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity Framework 型用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>関連項目

- [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [言語リファレンス](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Entity Framework 用 SqlClient プロバイダーの既知の問題](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
