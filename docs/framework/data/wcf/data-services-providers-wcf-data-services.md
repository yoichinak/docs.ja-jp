---
title: データ サービス プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 3344088aeb948edac3d3f439d729dc9d45b8b79b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537921"
---
# <a name="data-services-providers-wcf-data-services"></a>データ サービス プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] としてデータを公開するための複数のプロバイダー モデルをサポートしている、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。 このトピックでは、データ ソースに最適な [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] プロバイダーを選択するための情報を示します。  
  
## <a name="data-source-providers"></a>データ ソース プロバイダー  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] データ サービスのデータ モデルを定義するには、次のプロバイダーをサポートします。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|Entity Framework プロバイダー|このプロバイダーは、ADO.NET Entity Framework を使用して、リレーショナル データにマップするデータ モデルを定義することによってデータ サービスでリレーショナル データを使用します。 データ ソースとしては、SQL Server 以外にも、Entity Framework をサポートするサードパーティ プロバイダーのある任意のデータ ソースを使用できます。 SQL Server データベースなどのリレーショナル データ ソースの場合は、Entity Framework プロバイダーを使用してください。 詳細については、[Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)を参照してください。|  
|リフレクション プロバイダー|このプロバイダーは、リフレクションを使用して、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスとして公開できる既存のデータ クラスに基づいてデータ モデルを定義できます。 <xref:System.Data.Services.IUpdatable> インターフェイスを実装することによって更新できます。 実行時に定義される静的なデータ クラス (LINQ to SQL や型指定された DataSet によって生成されたデータ クラスなど) がある場合は、このプロバイダーを使用してください。 詳細については、[リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)を参照してください。|  
|カスタム データ サービス プロバイダー|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、遅延バインディング データ型に基づいてデータ モデルを動的に定義できるプロバイダーのセットが含まれています。 公開されるデータが不明な場合、アプリケーションを設計中の場合、または Entity Framework プロバイダーやリフレクション プロバイダーでは不十分な場合には、これらのインターフェイスを実装する必要があります。 詳細については、[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)を参照してください。|  
  
## <a name="other-data-service-providers"></a>その他のデータ サービス プロバイダー  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 他のプロバイダーのいずれかを使用して定義されているデータ ソースのパフォーマンスを強化する次の追加のデータ サービス プロバイダー。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|ストリーミング プロバイダー|このプロバイダーを使用すると、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用してバイナリ ラージ オブジェクト データ型を公開できます。 ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。 このプロバイダーは、任意のデータ ソース プロバイダーと共に実装できます。 詳細については、[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)を参照してください。|  
  
## <a name="see-also"></a>関連項目
- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
- [データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
