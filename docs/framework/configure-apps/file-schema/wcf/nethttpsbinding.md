---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 400444c0346b47d86ad799d4f8f2e7531b74a94c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195229"
---
# <a name="nethttpsbinding"></a>\<netHttpsBinding >
Windows Communication Foundation (WCF) サービスが構成および HTTPS 経由で通信できるエンドポイントを公開に使用できるバインディングを表します。 双方向コントラクトで使用すると、Web ソケットが使用されます。それ以外の場合は、HTTPS が使用されます。  
  
 ルート要素  
次の要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`allowCookies`|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は `false` です。<br /><br /> クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|`bypassProxyOnLocal`|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は `false` です。<br /><br /> インターネット リソースは、ローカル アドレスを持つ場合ローカルです。 によって識別される、構文的に、Uri と同様にピリオド (.) の欠如が同じコンピューター、ローカル LAN またはイントラネット上にあり、ローカル アドレスは "http://webserver/" と "http://localhost/" です。<br /><br /> この属性の設定は、BasicHttpBinding で構成されたエンドポイントがローカル リソースへのアクセス時にプロキシ サーバーを使用するかどうかを示します。 この属性が `true` の場合、ローカル インターネット リソースへの要求はプロキシ サーバーを使用しません。 この属性を `true` に設定した場合で、同じコンピューター上のサービスと対話するクライアントがプロキシを経由するときは、(localhost ではなく) ホスト名を使用します。<br /><br /> この属性が `false` の場合、すべてのインターネット要求はプロキシ サーバー経由で行われます。|  
|`closeTimeout`|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`hostNameComparisonMode`|URI の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|`maxBufferPoolSize`|チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる、最大メモリ量を指定する整数値。 既定値は 524288 (0x80000) バイトです。<br /><br /> バッファー マネージャーは、バッファー プールを使用することで、バッファーの使用コストを最小化します。 バッファーは、チャネルから出てくるメッセージをサービスが処理するときに必要です。 メッセージの読み込み処理に十分なメモリがバッファー プールにない場合、バッファー マネージャーは、CLR ヒープから追加のメモリを割り当てる必要があります。これにより、ガベージ コレクションのオーバーヘッドが増加します。 CLR ガベージ ヒープから多大な割り当てが行われることは、バッファー プール サイズが小さすぎること、およびこの属性で指定される制限を緩めて割り当てを増やすとパフォーマンスが向上する可能性があることを示します。|  
|`maxBufferSize`|このバインディングで構成されるエンドポイントのメッセージが処理されるときのメッセージを格納するバッファーの最大サイズを指定する整数値 (バイト単位)。 既定値は 65,536 バイトです。|  
|`maxReceivedMessageSize`|このバインディングで構成されるチャネルが受信可能なメッセージの最大メッセージ サイズ (ヘッダーを含む) をバイト単位で定義する正の整数。 受信側のメッセージが大きすぎると、送信側は SOAP エラーを受け取ります。 メッセージは受信者によってドロップされ、トレース ログにこのイベントのエントリが作成されます。 既定値は 65,536 バイトです。|  
|`messageEncoding`|SOAP メッセージのエンコードに使用されるエンコーダーを定義します。 以下の値が有効です。<br /><br /> テキスト:テキスト メッセージ エンコーダーを使用します。<br />Mtom:Message Transmission 組織 Mechanism 1.0 (MTOM) エンコーダーを使用します。<br /><br /> 既定値は Text です。 この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。|  
|`name`|バインディングの構成名を格納する文字列です。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。 また、この名前は、同じ種類のバインディング間で一意です。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
|`namespace`|バインディングの XML 名前空間を指定します。 既定値は "http://tempuri.org/Bindings" です。 各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。|  
|`openTimeout`|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`proxyAddress`|HTTP プロキシのアドレスを格納する URI。 `useSystemWebProxy` が `true` に設定されている場合、この設定は `null` である必要があります。 既定値は `null` です。|  
|`receiveTimeout`|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:10:00 です。|  
|`sendTimeout`|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|`textEncoding`|バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。 以下の値が有効です。<br /><br /> -BigEndianUnicode:Unicode BigEndian エンコーディングします。<br />Unicode:16 ビット エンコーディング。<br />UTF8:8 ビット エンコード<br /><br /> 既定値は UTF8 です。 この属性は <xref:System.Text.Encoding> 型です。|  
|`transferMode`|要求または応答に対してメッセージがバッファーされるか、ストリーム配信されるかを指定する有効な <xref:System.ServiceModel.TransferMode> 値。|  
|`useDefaultWebProxy`|使用できる場合にシステムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。 既定値は `true` です。|  
|||  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement> 型です。 |  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。|  
  
## <a name="remarks"></a>Remarks  
 NetHttpsBinding では、メッセージを送信するために、HTTPS をトランスポートとして使用します。 双方向コントラクトで使用すると、Web ソケットが使用されます。  要求/応答コントラクト NetHttpsBinding と使用する場合、バイナリ エンコーダーとの BasicHttpsBinding のように動作します。  
  
 セキュリティが既定でオフにしの mode 属性を設定する追加することが、 [\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)以外の値を子要素`None`します。 サービスは、"Text" メッセージ エンコードおよび UTF-8 テキスト エンコードを既定で使用します。  
  
## <a name="example"></a>例  
 第 1 世代と第 2 世代の Web サービスで HTTPS 通信と最大限の相互運用性を実現する、<xref:System.ServiceModel.NetHttpBinding> の使用例を次に示します。 バインディングは、クライアントとサービスの構成ファイルに指定されます。 バインディングの種類は、`binding` 要素の `<endpoint>` 属性を使用して指定します。 基本的なバインディングを構成してその設定の一部を変更する場合は、バインド構成を定義する必要があります。 エンドポイントは、`bindingConfiguration` 要素の `<endpoint>` 属性を使用して、名前でバインディング構成を参照する必要があります。次のサービスの構成コードを参照してください。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>例  
 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 エンドポイント アドレスとバインディングの名前から、bindingConfiguration を削除することで、前の例では、の機能を実現できます。  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
