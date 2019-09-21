---
title: '方法: 双方向フェデレーション バインディングを作成する'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972056"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>方法: 双方向フェデレーション バインディングを作成する

<xref:System.ServiceModel.WSFederationHttpBinding> はデータグラムと要求/応答メッセージの交換コントラクトのみをサポートします。 双方向メッセージ交換コントラクトを使用するには、カスタム バインディングを作成する必要があります。 次の手順は、構成の中でそれを行う方法を説明します。HTTP と TCP トランスポートにはメッセージ モード セキュリティを、TCP トランスポートには混合モード セキュリティを使用します。 このトピックの最後に 3 つのバインディングすべてのサンプル コードがあります。

バインディングはコード内でも作成できます。 作成するバインド要素スタックの説明については、 [「方法:の設定を使用してカスタム](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)バインディングを作成します。

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP で双方向カスタム フェデレーション バインディングを作成するには

1. 構成ファイルの  [バインド>ノードで、customBinding>要素を作成します。\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. CustomBinding > `name` `FederationDuplexHttpMessageSecurityBinding`要素内で、属性がに設定された[バインド > 要素を作成します。 \<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. バインド > `authenticationMode` `SecureConversation`要素内で、属性がに設定された[セキュリティ > 要素を作成します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `authenticationMode` `IssuedTokenForCertificate` [ Security>\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)要素内で、属性をまたは`IssuedTokenForSslNegotiated`に設定して、secureConversationBootstrap > 要素を作成します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

5. [ \<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素の後に、空[ \<の compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素を作成します。

6. [ \<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素の後に、空[ \<の oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素を作成します。

7. [ \<OneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素の後に、空[ \<の httptransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)要素を作成します。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>TCP メッセージ セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには

1. 構成ファイルの  [バインド>ノードで、customBinding>要素を作成します。\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. CustomBinding > `name` `FederationDuplexTcpMessageSecurityBinding`要素内で、属性がに設定された[バインド > 要素を作成します。 \<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. バインド > `authenticationMode` `SecureConversation`要素内で、属性がに設定された[セキュリティ > 要素を作成します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `authenticationMode` `IssuedTokenForCertificate` [ Security>\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)要素内で、属性をまたは`IssuedTokenForSslNegotiated`に設定して、secureConversationBootstrap > 要素を作成します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

5. [ \<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素の後に、空[ \<の tcptransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素を作成します。

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>TCP 混合セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには

1. 構成ファイルの  [バインド>ノードで、customBinding>要素を作成します。\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

2. CustomBinding > `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`要素内で、属性がに設定された[バインド > 要素を作成します。 \<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. バインド > `authenticationMode` `SecureConversation`要素内で、属性がに設定された[セキュリティ > 要素を作成します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `authenticationMode` `IssuedTokenForCertificate` [ Security>\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)要素内で、属性をまたは`IssuedTokenForSslNegotiated`に設定して、secureConversationBootstrap > 要素を作成します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

5. [ \<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素の後に、空[ \<の sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素を作成します。

6. [ \<Sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素の後に、空[ \<の tcptransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素を作成します。

## <a name="code-sample"></a>コード サンプル

### <a name="sample-with-3-bindings"></a>3 つのバインディングの例

1. 次のコードを構成ファイルに挿入します。

## <a name="example"></a>例

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
