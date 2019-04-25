---
title: カスタム バインディングを介したメタデータの公開と取得
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 33777358262465e9ecbadd75df8abf066bafcd01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222979"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>カスタム バインディングを介したメタデータの公開と取得
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は、サービスにメタデータ エンドポイントを追加するためのサポートを提供します。 これらのメタデータ エンドポイントがある URL に HTTP GET 要求に応答できる、`?wsdl`クエリ文字列と、Ws-metadataexchange (MEX) 仕様で定義された Ws-transfer GET 要求にします。 MEX エンドポイントは、<xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> コントラクトを実装します。  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>カスタム バインドを介したメタデータの公開  
 HTTP GET メタデータ エンドポイントと HTTPS GET メタデータ エンドポイントを有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> プロパティを `true` に設定します。 これらのエンドポイントのバインディングは構成できません。  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>コントラクト、ただしで使えるため、カスタムのバインディングを使用するものなど、任意のエンドポイント<xref:System.ServiceModel.Description.IMetadataExchange>エンドポイントは他の任意の Windows Communication Foundation (WCF) サービス エンドポイントと同じです。 システム指定のバインディングの構成を変更する方法または <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> の構成方法を理解している場合は、<xref:System.ServiceModel.Description.IMetadataExchange> エンドポイントで使用されるバインディングを構成できます。  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>カスタム バインドを介したメタデータの取得  
 メタデータは、標準の HTTP 要求または HTTPS GET 要求を使用して HTTP Get および HTTPS Get メタデータ エンドポイントから取得できます。  
  
 WCF でサポートされる標準の MEX バインディングのいずれかを使用することが一般的に、MEX メタデータ エンドポイントからメタデータを取得します。 詳細については、「 <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> 」を参照してください。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 型および Svcutil.exe ツールでは、指定したメタデータ エンドポイントのアドレスに基づいて、標準の MEX バインディングの 1 つが自動的に選択されます。  
  
 MEX メタデータ エンドポイントで標準の MEX バインディングとは異なるバインディングを使用する場合は、コードを使用するか、<xref:System.ServiceModel.Description.MetadataExchangeClient> クライアント エンドポイント構成を提供することにより、<xref:System.ServiceModel.Description.IMetadataExchange> で使用されるバインディングを構成できます。 Svcutil.exe ツールは、構成ファイルから、メタデータ エンドポイント アドレスの URI スキームと同じ名前を持つ <xref:System.ServiceModel.Description.IMetadataExchange> クライアント エンドポイント構成を自動的に読み込みます。  
  
## <a name="security"></a>セキュリティ  
 カスタム バインドを介してメタデータを公開する場合、メタデータに必要なセキュリティ サポートをそのカスタム バインドが提供することを確認してください。 たとえば、情報の漏えいを防止し、メタデータを取得するための権限がクライアントにあることを確認するには、認証および暗号化を要求するように <xref:System.ServiceModel.Description.IMetadataExchange> エンドポイントを構成することによってメタデータとアプリケーションのセキュリティを強化します。 サンプル[メタデータ エンドポイントのセキュリティで保護されたカスタム](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)このシナリオを実証します。  
  
## <a name="see-also"></a>関連項目

- [サービスのセキュリティ保護](../../../../docs/framework/wcf/securing-services.md)
- [WS-MetadataExchange のバインディング](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)
- [方法: 構成のカスタム Ws-metadata Exchange バインディング](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [方法: 非-MEX のバインディングを介してメタデータを取得します。](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
