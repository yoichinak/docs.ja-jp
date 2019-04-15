---
title: <httpTransport>
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 7a06772f078f9187298ad0b4b9c8b0f51c849928
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122734"
---
# <a name="httptransport"></a>\<httpTransport>
カスタム バインディングの SOAP メッセージを送信する HTTP トランスポートを指定します。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<httpTransport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<httpTransport allowCookies="Boolean"
               authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
               bypassProxyOnLocal="Boolean"
               hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
               keepAliveEnabled="Boolean"
               maxBufferSize="Integer"
               proxyAddress="Uri"
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
               realm="String"
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
|authenticationScheme|HTTP リスナーにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 以下の値が有効です。<br /><br /> -Digest:ダイジェスト認証を指定します。<br />-Negotiate:クライアントとネゴシエートし、認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />-Ntlm:NTLM 認証を指定します。<br />-基本。基本認証を指定します。<br />匿名。匿名認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。 この属性は 1 回だけ設定できます。|  
|bypassProxyOnLocal|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。 既定値は `false` です。<br /><br /> ローカル アドレスは、ローカル LAN またはイントラネット上にあるアドレスです。<br /><br /> Windows Communication Foundation (WCF) は、サービス アドレスが始まる場合常に、プロキシを無視 `http://localhost` です。<br /><br /> クライアントが同じマシン上のサービスと対話するときにプロキシを経由させる場合は、localhost ではなくホスト名を使用する必要があります。|  
|hostnameComparisonMode|URI の解析に使用する HTTP ホスト名比較モードを指定します。 有効な値は次のとおりです。<br /><br /> -StrongWildcard: (「+」)、指定したスキーム、ポート、および相対 URI のコンテキストですべてのホスト名と一致します。<br />-Exact: ワイルドカードなし<br />-WeakWildcard: ("\*")、強いワイルドカード メカニズムを通じて指定されたスキーム、ポート、および明示的が一致しない相対のはっきりのコンテキストで使用可能なすべてのホスト名と一致します。<br /><br /> この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型です。 既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> です。|  
|keepAliveEnabled|インターネット リソースへの永続的な接続を行うかどうかを示すブール値。|  
|maxBufferSize|バッファーの最大サイズを指定する正の整数です。 既定値は 524288 です|  
|proxyAddress|HTTP プロキシのアドレスを指定する URI。 
  `useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。 既定値は `null` です。|  
|proxyAuthenticationScheme|HTTP プロキシにより処理されているクライアント要求の認証に使用するプロトコルを指定します。 以下の値が有効です。<br /><br /> -None。認証は実行されません。<br />-Digest:ダイジェスト認証を指定します。<br />-Negotiate:クライアントとネゴシエートし、認証方式を決定します。 クライアントとサーバーの両方が Kerberos をサポートする場合は、この方式が使用されます。それ以外の場合は NTLM が使用されます。<br />-Ntlm:NTLM 認証を指定します。<br />-基本。基本認証を指定します。<br />匿名。匿名認証を指定します。<br /><br /> 既定は Anonymous です。 この属性は <xref:System.Net.AuthenticationSchemes> 型です。 なお<xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType>はサポートされていません。|  
|realm|プロキシおよびサーバーで使用するレルムを指定する文字列です。 既定値は空の文字列です。<br /><br /> サーバーは、レルムを使用して、保護されたリソースをパーティションに分割します。 パーティションごとに、独自の認証方式と承認データベースの両方、またはそのいずれかを指定できます。 レルムは、基本認証およびダイジェスト認証だけに使用されます。 クライアントが正常に認証されると、その認証は特定のレルムのすべてのリソースに対して有効となります。 レルムの詳細についてでの RFC 2617 を参照してください、 [IETF web サイト](https://www.ietf.org)します。|  
|transferMode|メッセージが要求や応答をバッファーするか、ストリーミングするかを指定します。 以下の値が有効です。<br /><br /> -バッファー。要求および応答メッセージをバッファーします。<br />ストリーム。要求および応答メッセージをストリーミングします。<br />-StreamedRequest:要求メッセージをストリーミングし、応答メッセージをバッファーします。<br />-StreamedResponse:要求メッセージをバッファーし、応答メッセージをストリーミングします。<br /><br /> 既定値はバッファーです。 この属性は <xref:System.ServiceModel.TransferMode> 型です。|  
|unsafeConnectionNtlmAuthentication|サーバー上で安全ではない接続共有を有効にするかどうかを指定するブール値です。 既定値は `false` です。 有効な場合、NTLM 認証は、TCP 接続ごとに 1 回実行されます。|  
|useDefaultWebProxy|ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを指定するブール値です。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>Remarks  
 `httpTransport` 要素は、HTTP トランスポート プロトコルを実装するカスタム バインドを作成する場合の開始点となります。 HTTP は、相互運用性のために使用される主要なトランスポートです。 このトランスポートには、その他の WCF 以外の Web サービス スタックとの相互運用する Windows Communication Foundation (WCF) ではサポートされています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.HttpTransportElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)
- [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
