---
title: <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
ms.openlocfilehash: 71b8255b9feda9854b0257528dcad85f6cf08d6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086027"
---
# <a name="webhttpbinding"></a>\<webHttpBinding>
SOAP メッセージに代わって HTTP 要求に応答する Windows Communication Foundation (WCF) Web サービスのエンドポイントを構成するために使用するバインド要素を定義します。  
  
\<system.ServiceModel >  
\<bindings>  
\<webHttpBinding>  
  
## <a name="syntax"></a>構文  
  
```xml  
<webHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxBufferSize="integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean"
           writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">
    <security mode="None/Transport/TransportCredentialOnly">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</webHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowCookies|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は false です。<br /><br /> クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は、`false` です。|  
|closeTimeout|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|maxBufferPoolSize|このバインディングに使用するバッファー プール サイズの上限を指定する整数。 既定は 524,288 バイト (512 * 1024) です。 Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxBufferSize|チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる最大メモリ量を指定する整数。 既定値は 524,288 (0x80000) バイトです。|  
|maxReceivedMessageSize|このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。 この制限を超えるメッセージの送信者はエラーを受信します。 メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。 既定値は 65536 です。 **注:** ASP.NET 互換モードでは、この値を増やすだけでは十分ではありません。 値を大きく必要がありますも`httpRuntime`(を参照してください[httpRuntime 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100)))。|  
|name|バインディングの構成名を格納する文字列です。 この値は、バインディングの ID として使用されるため、一意にする必要があります。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」と「[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
|openTimeout|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 
  `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は、`null` です。|  
|receiveTimeout|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|sendTimeout|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。 この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。 既定値は 00:01:00 です。|  
|transferMode|バインディングで構成されたサービスがメッセージ転送のストリーム モードまたはバッファー モード (あるいは両方のモード) を使用するかどうかを示す <xref:System.ServiceModel.TransferMode> 値。 既定値は、`Buffered` です。|  
|useDefaultWebProxy|システムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。 既定値は、`true` です。|  
|writeEncoding|メッセージ テキストに使用される文字エンコーディングを指定します。 以下の値が有効です。<br /><br /> UnicodeFffeTextEncoding:Unicode BigEndian エンコーディングします。<br /><br /> Utf16TextEncoding:16 ビット エンコーディング。<br /><br /> Utf8TextEncoding:8 ビット エンコーディング。<br /><br /> 既定値は Utf8TextEncoding です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|このバインディングを使用して構成されるエンドポイントにより処理可能な、POX メッセージの複雑さに対する制約を定義します。 この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|バインディングのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.WebHttpSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<bindings>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。|  
  
## <a name="remarks"></a>Remarks  
 WCF Web プログラミング モデルにより、"plain old XML"を使用する HTTP 要求を通じて WCF Web サービスを公開する開発者 (POX) スタイルの SOAP ベースのメッセージングではなくメッセージングします。 使用して HTTP 要求を使用するサービスと通信するクライアントは、サービスのエンドポイントを構成する必要があります、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)を持つ、 \<WebHttpBehavior > がアタッチされています。  
  
 WCF での配信および ASP をサポートします。AJAX の統合は、どちらも、Web プログラミング モデル上に構築されます。 モデルの詳細については、次を参照してください。 [WCF Web HTTP プログラミング モデル](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- [WCF Web HTTP プログラミング モデル](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
