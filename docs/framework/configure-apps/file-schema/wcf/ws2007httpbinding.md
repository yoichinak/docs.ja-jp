---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 9caba8dfc848a2463b1fa482ccaf55288d96af29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182148"
---
# <a name="ws2007httpbinding"></a>\<ws2007HttpBinding >
<xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession>、および <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> の各バインド要素の適切なバージョンをサポートする相互運用可能なバインディングを定義します。  
  
 \<system.serviceModel>  
\<bindings>  
\<ws2007HttpBinding >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`allowCookies`|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。 既定値は `false` です。<br /><br /> クッキーを使用する ASMX (ASP.NET Web サービス) と対話する場合に、このプロパティを使用できます。 これにより、サーバーから返されるクッキーが、このサービスに対するそれ以降のすべてのクライアント要求に自動的にコピーされます。|  
|`bypassProxyOnLocal`|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。 既定値は `false` です。|  
|`closeTimeout`|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`hostNameComparisonMode`|URI (Uniform Resource Identifier) の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|`maxBufferPoolSize`|このバインドに使用するバッファー プールの最大サイズ。 既定値は 524,288 バイト (512 × 1,024) です。 Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。 使用するたびに毎回バッファーを作成および破棄すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄によるオーバーヘッドを回避できます。|  
|`maxReceivedMessageSize`|このバインディングで構成されたチャネルで受信可能な、ヘッダーを含む最大メッセージ サイズ (バイト単位) です。 この制限を超える場合、メッセージの送信者は SOAP エラーを受け取ります。 メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。|  
|`messageEncoding`|メッセージのエンコードに使用されるエンコーダーを定義します。 以下の値が有効です。<br /><br /> -   `Text`:テキスト メッセージ エンコーダーを使用します。<br />-   `Mtom`:Message Transmission 組織 Mechanism 1.0 (MTOM) エンコーダーを使用します。<br /><br /> 既定値は `Text` です。<br /><br /> この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。|  
|`name`|バインドの構成名。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
|`openTimeout`|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`proxyAddress`|HTTP プロキシのアドレスを指定する URI。 `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は `null` です。|  
|`receiveTimeout`|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`sendTimeout`|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`textEncoding`|バインディングでメッセージの発行に使用する文字セット エンコーディングを指定します。 以下の値が有効です。<br /><br /> -   `UnicodeFffeTextEncoding`:Unicode ビッグ エンディアン エンコーディング。<br />-   `Utf16TextEncoding`:16 ビット エンコーディング。<br />-   `Utf8TextEncoding`:8 ビット エンコーディング。<br /><br /> 既定値は `Utf8TextEncoding` です。<br /><br /> この属性は <xref:System.Text.Encoding> 型です。|  
|`transactionFlow`|バインドが WS-Transactions のフローをサポートするかどうかを指定する値。 既定値は `false` です。|  
|`useDefaultWebProxy`|システムの自動設定 HTTP プロキシを使用するかどうかを示す値です。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> 型です。|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|このバインディングを使用して設定されるエンドポイントで処理できる、SOAP メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。|  
  
## <a name="remarks"></a>Remarks  
 `WS2007HttpBinding` は、`WSHttpBinding` と同様のシステム標準のバインディングを追加しますが、ReliableSession、Security、および TransactionFlow の各プロトコルの OASIS (Organization for the Advancement of Structured Information Standards) 標準バージョンを使用します。 このバインドを使用する場合、オブジェクト モデルも既定の設定も変更する必要はありません。  
  
## <a name="example"></a>例  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
