---
title: メタデータの公開
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 54ab05f32320f3084fc609d8107f2892ffe6efbd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424577"
---
# <a name="publishing-metadata"></a>メタデータの公開
Windows Communication Foundation (WCF) サービスは、1 つまたは複数のメタデータ エンドポイントを発行することによって、メタデータを公開します。 サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータのエンドポイントはアドレス、バインディング、コントラクトを持つ他のサービス エンドポイントに類似し、それらは構成か命令コードを使用してサービス ホストに追加することができます。  
  
## <a name="publishing-metadata-endpoints"></a>メタデータ エンドポイントを公開する  
 WCF サービスのメタデータ エンドポイントを公開する必要がありますを追加、<xref:System.ServiceModel.Description.ServiceMetadataBehavior>サービス、サービスに動作します。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> インスタンスを追加すると、サービスからメタデータ エンドポイントを公開できます。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> サービス動作を追加すると、MEX プロトコルをサポートするメタデータ エンドポイント、または HTTP/GET 要求に応答するメタデータ エンドポイントを公開できます。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は <xref:System.ServiceModel.Description.WsdlExporter> を使用して、サービス内のすべてのサービス エンドポイント用のメタデータをエクスポートします。 サービスからメタデータをエクスポートする方法の詳細については、次を参照してください。[エクスポートおよびインポートするメタデータ](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)します。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は、<xref:System.ServiceModel.Description.ServiceMetadataExtension> インスタンスをサービス ホストへの拡張として追加します。 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> により、メタデータ公開プロトコルを実装することができます。 また、<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> を使用して、<xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> プロパティにアクセスすることにより、実行時にサービスのメタデータを取得できます。  
  
### <a name="mex-metadata-endpoints"></a>MEX メタデータ エンドポイント  
 MEX プロトコルを使用するメタデータ エンドポイントを追加するには、`IMetadataExchange` サービス コントラクトを使用するサービス エンドポイントをサービス ホストに追加します。 WCF が含まれています、 <xref:System.ServiceModel.Description.IMetadataExchange> WCF プログラミング モデルの一部として使用できるこのサービス コントラクト名を持つインターフェイスです。 Ws-metadataexchange のエンドポイント、または、MEX エンドポイントはで静的ファクトリ メソッドを公開する 4 つの既定のバインディングのいずれかで使用できます、<xref:System.ServiceModel.Description.MetadataExchangeBindings>クラス Svcutil.exe などの WCF ツールで使用される既定のバインディングを照合します。 また、独自のカスタム バインドを使用して MEX メタデータ エンドポイントを構成することもできます。  
  
### <a name="http-get-metadata-endpoints"></a>HTTP GET メタデータ エンドポイント  
 HTTP/GET 要求に応答するメタデータ エンドポイントをサービスに追加するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> プロパティを `true` に設定します。 また、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> の <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> プロパティを `true` に設定することで、HTTPS を使用するメタデータ エンドポイントを構成することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 構成ファイルを使用してサービスのメタデータを公開します。](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 クライアントは、Ws-metadataexchange または HTTP/GET 要求を使用して、使用してメタデータを取得できるように、メタデータを公開する WCF サービスを構成する方法を示します、`?wsdl`クエリ文字列。  
  
 [方法: コードを使用してサービスのメタデータを公開します。](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 クライアントは、Ws-metadataexchange または HTTP/GET 要求を使用して、使用してメタデータを取得できるように、コード内の WCF サービスのメタデータの公開を有効にする方法を示します、`?wsdl`クエリ文字列。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>関連項目

- [メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
