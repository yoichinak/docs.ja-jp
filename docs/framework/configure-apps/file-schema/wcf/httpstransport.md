---
title: <httpsTransport>
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: b70236e8bba93a49ca5b53538333fa63283a5f0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928521"
---
# <a name="httpstransport"></a>\<httpsTransport>
カスタム バインディングの SOAP メッセージを送信する HTTP トランスポートを指定します。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<httpsTransport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowCookies|クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。 既定値は `false` です。<br /><br /> この属性はクッキーを使用する ASMX Web サービスと対話する場合に使用できます。 この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。|  
|authenticationScheme|HTTP リスナーにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 有効な値は次のとおりです。<br /><br /> ダイジェストダイジェスト認証を指定します。<br />ネゴシエーションクライアントとネゴシエートし、認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />MlNTLM 認証を指定します。<br />Bios基本認証を指定します。<br />非同期匿名認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。 この属性は 1 回だけ設定できます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は `false` です。<br /><br /> ローカル アドレスは、ローカル LAN またはイントラネット上にあるアドレスです。<br /><br /> Windows Communication Foundation (WCF) は、サービス アドレスが始まる場合常に、プロキシを無視 `http://localhost` です。<br /><br /> クライアントが同じマシン上のサービスと対話するときにプロキシを経由させる場合は、localhost ではなくホスト名を使用する必要があります。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 有効な値は次のとおりです。<br /><br /> -StrongWildcard: ("+") は、指定されたスキーム、ポート、および相対 URI のコンテキストで使用可能なすべてのホスト名と一致します。<br />-Exact: ワイルドカードなし<br />-値のワイルドカード:\*("") は、明示的に、または厳密なワイルドカード機構を使用して一致していない、指定されたスキーム、ポート、および相対 uir のコンテキストで使用可能なすべてのホスト名と一致します。<br /><br /> 既定値は StrongWildcard です。 この属性は `System.ServiceModel.HostnameComparison` 型です。|  
|manualAddressing|ユーザーによるメッセージのアドレス指定の管理を有効にするブール値です。 このプロパティは、通常、アプリケーションが複数の宛先のどれにメッセージを送信するかを決定するルーターのシナリオで使用されます。<br /><br /> `true` に設定されている場合、チャネルではメッセージが既にアドレス指定されていると見なされ、他の情報は追加されません。 この場合、ユーザーはすべてのメッセージを別個にアドレス指定できます。<br /><br /> `false` に設定されている場合、既定の Windows Communication Foundation (WCF) アドレス指定機構により、すべてのメッセージのアドレスが自動的に作成されます。<br /><br /> 既定値は `false` です。|  
|maxBufferPoolSize|バッファー プールの最大サイズを指定する正の整数です。 既定値は 524288 です。<br /><br /> WCF の多くの部分でバッファーが使用されます。 使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。 バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。 これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|maxBufferSize|バッファーの最大サイズを指定する正の整数です。 既定値は 524288 です|  
|maxReceivedMessageSize|受信できるメッセージの最大サイズを指定する正の整数。 既定値は 65536 です。|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は `null` です。|  
|proxyAuthenticationScheme|HTTP プロキシにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 有効な値は次のとおりです。<br /><br /> 存在認証は実行されません。<br />ダイジェストダイジェスト認証を指定します。<br />ネゴシエーションクライアントとネゴシエートし、認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />MlNTLM 認証を指定します。<br />Bios基本認証を指定します。<br />非同期匿名認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。 はサポート<xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType>されていないことに注意してください。|  
|realm|プロキシおよびサーバーで使用するレルムを指定する文字列です。 既定値は空の文字列です。<br /><br /> サーバーは、レルムを使用して、保護されたリソースをパーティションに分割します。 パーティションごとに、独自の認証方式と承認データベースの両方、またはそのいずれかを指定できます。 レルムは、基本認証およびダイジェスト認証だけに使用されます。 クライアントが正常に認証されると、その認証は特定のレルムのすべてのリソースに対して有効となります。 領域の詳細については、 [IETF web サイト](https://www.ietf.org)の RFC 2617 を参照してください。|  
|requireClientCertificate|サーバーがクライアントに HTTPS ハンドシェイクの一部としてクライアント証明書の提供を要求するかどうかを指定するブール値。 既定値は `false` です。|  
|transferMode|メッセージが要求や応答をバッファーするか、ストリーミングするかを指定します。 有効な値は次のとおりです。<br /><br /> 付き要求メッセージと応答メッセージがバッファーされます。<br />配信要求メッセージと応答メッセージがストリーミングされます。<br />-StreamedRequest:要求メッセージをストリーミングし、応答メッセージをバッファーします。<br />StreamedResponse要求メッセージをバッファーし、応答メッセージをストリーミングします。<br /><br /> 既定値はバッファーです。 この属性は <xref:System.ServiceModel.TransferMode> 型です。|  
|unsafeConnectionNtlmAuthentication|サーバー上で安全ではない接続共有を有効にするかどうかを指定するブール値です。 既定値は `false` です。 有効な場合、NTLM 認証は、TCP 接続ごとに 1 回実行されます。|  
|useDefaultWebProxy|ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを指定するブール値です。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>Remarks  
 `httpsTransport` 要素は、HTTPS トランスポート プロトコルを実装するカスタム バインドを作成する場合の開始点となります。 HTTPS は、セキュリティで保護された相互運用性のために使用される主要なトランスポートです。 HTTPS は、他の Web サービススタックとの相互運用性を確保するために、Windows Communication Foundation (WCF) によってサポートされています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
