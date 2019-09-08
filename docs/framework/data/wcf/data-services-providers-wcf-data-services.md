---
title: データ サービス プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7623c2b743d6a61362c8cf0e1228b4663c9e7d48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780389"
---
# <a name="data-services-providers-wcf-data-services"></a>データ サービス プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]では、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]データをフィードとして公開するための複数のプロバイダーモデルがサポートされています。 このトピックでは、データ ソースに最適な [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] プロバイダーを選択するための情報を示します。  
  
## <a name="data-source-providers"></a>データ ソース プロバイダー  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]では、データサービスのデータモデルを定義するための次のプロバイダーがサポートされています。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|Entity Framework プロバイダー|このプロバイダーは、ADO.NET Entity Framework を使用して、リレーショナル データにマップするデータ モデルを定義することによってデータ サービスでリレーショナル データを使用します。 データ ソースとしては、SQL Server 以外にも、Entity Framework をサポートするサードパーティ プロバイダーのある任意のデータ ソースを使用できます。 SQL Server データベースなどのリレーショナル データ ソースの場合は、Entity Framework プロバイダーを使用してください。 詳細については、「 [Entity Framework プロバイダー](entity-framework-provider-wcf-data-services.md)」を参照してください。|  
|リフレクション プロバイダー|このプロバイダーは、リフレクションを使用して、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスとして公開できる既存のデータ クラスに基づいてデータ モデルを定義できます。 <xref:System.Data.Services.IUpdatable> インターフェイスを実装することによって更新できます。 実行時に定義される静的なデータ クラス (LINQ to SQL や型指定された DataSet によって生成されたデータ クラスなど) がある場合は、このプロバイダーを使用してください。 詳細については、「[リフレクションプロバイダー](reflection-provider-wcf-data-services.md)」を参照してください。|  
|カスタム データ サービス プロバイダー|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、遅延バインディング データ型に基づいてデータ モデルを動的に定義できるプロバイダーのセットが含まれています。 公開されるデータが不明な場合、アプリケーションを設計中の場合、または Entity Framework プロバイダーやリフレクション プロバイダーでは不十分な場合には、これらのインターフェイスを実装する必要があります。 詳細については、「[カスタムデータサービスプロバイダー](custom-data-service-providers-wcf-data-services.md)」を参照してください。|  
  
## <a name="other-data-service-providers"></a>その他のデータ サービス プロバイダー  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]には、他のプロバイダーのいずれかを使用して定義されたデータソースのパフォーマンスを向上させる、次の追加データサービスプロバイダーが用意されています。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|ストリーミング プロバイダー|このプロバイダーを使用すると、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用してバイナリ ラージ オブジェクト データ型を公開できます。 ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。 このプロバイダーは、任意のデータ ソース プロバイダーと共に実装できます。 詳細については、[ストリーミング プロバイダー](streaming-provider-wcf-data-services.md)を参照してください。|  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](defining-wcf-data-services.md)
- [データ サービスの構成](configuring-the-data-service-wcf-data-services.md)
- [データ サービスのホスティング](hosting-the-data-service-wcf-data-services.md)
