---
title: 軽減策:WCF サービスと証明書認証
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacf5fc4a5c73fc60df961432089ee65dd0cfaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079540"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>軽減策:WCF サービスと証明書認証
.NET Framework 4.6 では、WCF SSL プロトコルの既定の一覧に TLS 1.1 および TLS 1.2 が追加されます。 クライアントとサーバーの両方のマシンに .NET Framework 4.6 以降がインストールされている場合は、TLS 1.2 がネゴシエーションに使用されます。  
  
## <a name="impact"></a>影響  
 TLS 1.2 では MD5 証明書認証がサポートされません。 そのため、顧客がハッシュ アルゴリズムで MD5 を使用する SSL 証明書を使用すると、WCF クライアントは WCF サービスに接続できません。 詳細については、「[軽減策:WCF サービスと証明書認証](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md)」を参照してください。  
  
## <a name="mitigation"></a>軽減策  
 次のいずれかの操作を実行することで、この問題を回避して、WCF クライアントを WCF サーバーに接続できるようになります。  
  
-   MD5 アルゴリズムを使用しないように証明書を更新します。 この解決策をお勧めします。  
  
-   バインドがソース コードで動的に構成されていない場合は、TLS 1.1 または以前のバージョンのプロトコルを使用するようにアプリケーションの構成ファイルを更新します。 これにより、引き続き MD5 ハッシュ アルゴリズムによる証明書を使用することができます。  
  
    > [!CAUTION]
    >  MD5 ハッシュ アルゴリズムによる証明書は安全でないと見なされるため、この回避策はお勧めできません。  
  
     次の構成ファイルでこれを行います。  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   バインドがソース コードで動的に構成されている場合は、ソース コード内で TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) または以前のバージョンのプロトコルを使用するように <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> プロパティを更新します。  
  
    > [!CAUTION]
    >  MD5 ハッシュ アルゴリズムによる証明書は安全でないと見なされるため、この回避策はお勧めできません。  
  
## <a name="see-also"></a>関連項目

- [ランタイムの変更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
