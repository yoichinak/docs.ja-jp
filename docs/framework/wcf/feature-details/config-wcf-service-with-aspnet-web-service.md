---
title: '方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 22713aba4f86fe493ba3d16ef09c2a71b6d55fe0
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389786"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する

Windows 通信基盤 (WCF) サービス エンドポイントを構成して、ASP.NET Web サービス クライアント<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>と相互運用可能にするには、サービス エンドポイントのバインディングの種類としてその型を使用します。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。 ASP.NET Web サービス クライアントは MTOM メッセージ<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>エンコーディングをサポートしていません。 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> また、ASP.Net Web サービス クライアントでは WS-Security がサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> を <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定する必要があります。  
  
 WCF サービスのメタデータを Web サービスプロキシ生成ツール (Web[サービス記述言語ツール (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100)) [、Web サービス検出ツール (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)))、および Visual Studio の**Web 参照の追加**機能で ASP.NET使用できるようにするには、HTTP/GET メタデータ エンドポイントを公開する必要があります。  
  
## <a name="add-an-endpoint-in-code"></a>コードにエンドポイントを追加する  
  
1. 新しい <xref:System.ServiceModel.BasicHttpBinding> インスタンスを作成します。  
  
2. 必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディングのトランスポート セキュリティを有効にします。 詳細については、トランスポート[セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)を参照してください。  
  
3. 上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。 コードでサービス エンドポイントを追加する方法の詳細については、「[方法 : コードでサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)」を参照してください。  
  
4. サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細については、「[方法 : コードを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)」を参照してください。  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>構成ファイルにエンドポイントを追加する  
  
1. 新しい <xref:System.ServiceModel.BasicHttpBinding> バインディング構成を作成します。 詳細については、「[方法 : 構成でサービス バインドを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。  
  
2. 必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインド構成のトランスポート セキュリティを有効にします。 詳細については、[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)を参照してください。  
  
3. 上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。 構成ファイルにサービス エンドポイントを追加する方法の詳細については、「[方法 : 構成でサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)」を参照してください。  
  
4. サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細については、「[方法 : 構成ファイルを使用してサービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)する 」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、構成ファイルで、ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加する方法を示します。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>関連項目

- [方法: コード内にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [方法: コードを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [方法: 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [方法: 構成にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [方法: 構成ファイルを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [輸送セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)
