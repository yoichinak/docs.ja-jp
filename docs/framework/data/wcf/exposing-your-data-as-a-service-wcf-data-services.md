---
title: サービスとしてのデータの公開 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 3c0763f21940831f401194356dc25b0d99c8d6f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308537"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>サービス (WCF Data Services) として、データを公開します。

WCF Data Services としてデータを公開するサービスをより簡単に定義するための Visual Studio と統合[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。 OData フィードを公開するデータ サービスを作成するには、次の基本的な手順が含まれます。

1. **データ モデルを定義します。** WCF Data Services に基づくデータ モデルをネイティブでサポート、 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)します。 詳細については、「[方法 :ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)します。

     WCF Data Services は、のインスタンスを返す共通言語ランタイム (CLR) オブジェクトに基づくデータ モデルもサポートしています。、<xref:System.Linq.IQueryable%601>インターフェイス。 そのため、.NET Framework のリスト、配列、およびコレクションに基づいてデータ サービスを配置できます。 これらのデータ構造での作成、更新、および削除操作を有効にするには、<xref:System.Data.Services.IUpdatable> インターフェイスも実装する必要があります。 詳細については、「[方法 :リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)します。

     高度なシナリオでは、WCF Data Services には、遅延バインディング データ型に基づいてデータ モデルを定義するためのプロバイダーのセットが含まれています。 詳細については、次を参照してください。[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)します。

2. **データ サービスを作成します。** 最も基本的なデータ サービスでは、 <xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 (エンティティ コンテナーの名前空間修飾名) と一緒に公開します。 詳細については、「 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)の開発と配置について説明します。

3. **データ サービスを構成します。** 既定では、WCF Data Services には、エンティティ コンテナーによって公開されているリソースへのアクセスが無効にします。 <xref:System.Data.Services.DataServiceConfiguration>インターフェイスでは、リソースへのアクセスを構成し、サービス操作、OData のサポートされているバージョンを指定して、バッチ動作や返されるエンティティの最大数など、他のサービス全体の動作を定義できます。1 つの応答。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。

Northwind サンプル データベースに基づいている単純なデータ サービスを作成する方法の例は、次を参照してください。[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。

## <a name="see-also"></a>関連項目

- [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)