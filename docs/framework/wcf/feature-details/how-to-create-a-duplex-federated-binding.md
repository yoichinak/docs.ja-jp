---
title: '方法: 双方向フェデレーション バインディングを作成する'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696211"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>方法: 双方向フェデレーション バインディングを作成する
<xref:System.ServiceModel.WSFederationHttpBinding> はデータグラムと要求/応答メッセージの交換コントラクトのみをサポートします。 双方向メッセージ交換コントラクトを使用するには、カスタム バインディングを作成する必要があります。 次の手順は、構成の中でそれを行う方法を説明します。HTTP と TCP トランスポートにはメッセージ モード セキュリティを、TCP トランスポートには混合モード セキュリティを使用します。 このトピックの最後に 3 つのバインディングすべてのサンプル コードがあります。  
  
 バインディングはコード内でも作成できます。 作成するバインド要素スタックの説明は、次を参照してください。[方法。SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)します。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>HTTP で双方向カスタム フェデレーション バインディングを作成するには  
  
1. [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 、構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。  
  
2. 内で、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインド >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexHttpMessageSecurityBinding`します。  
  
3. 内で、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`します。  
  
4. 内で、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.  
  
5. 次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素は空の作成[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素。  
  
6. 次の[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素は空の作成[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素。  
  
7. 次の[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素は空の作成[ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)要素。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>TCP メッセージ セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには  
  
1. [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 、構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。   
  
2. 内で、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインド >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexTcpMessageSecurityBinding`します。  
  
3. 内で、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`します。  
  
4. 内で、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.  
  
5. 次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素は空の作成[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素。  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>TCP 混合セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには  
  
1. [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 、構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。   
  
2. 内で、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインド >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`します。  
  
3. 内で、 [\<バインド >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`します。  
  
4. 内で、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.  
  
5. 次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素は空の作成[ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素。  
  
6. 次の[ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素は空の作成[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素。  
  
## <a name="code-sample"></a>コード サンプル  
  
#### <a name="sample-with-3-bindings"></a>3 つのバインディングの例  
  
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
