---
title: '方法: WCF サービスと WSE 3.0 クライアントを相互運用するために構成する'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045939"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>方法: WCF サービスと WSE 3.0 クライアントを相互運用するために構成する

Windows Communication Foundation (WCF) サービスは、WCF サービスが WS-ADDRESSING 仕様の8月2004バージョンを使用するように構成されている場合に、Web サービス拡張 Microsoft .NET 3.0 (WSE) クライアントとのワイヤレベルの互換性があります。

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>WCF サービスを WSE 3.0 クライアントと相互運用できるようにするには

1. WCF サービスのカスタムバインドを定義します。

    メッセージ エンコーディングに 2004 年 8 月版の WS-Addressing 仕様が使用されるように指定するには、カスタム バインディングを作成する必要があります。

    1. サービスの構成ファイルの[ \<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)に子[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)を追加します。

    2. `name` CustomBinding > に[ \<バインド](../../../../docs/framework/misc/binding.md) [> を追加し、属性を設定して、バインドの名前を指定します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

    3. 認証モードと、WSE 3.0 と互換性のあるメッセージをセキュリティで保護するために使用する ws-security 仕様のバージョンを指定します。これには、 [ \<> バインド](../../../../docs/framework/misc/binding.md)に子[ \<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を追加します。

        認証モードを設定するには、 `authenticationMode` [ \<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の属性を設定します。 認証モードは、WSE 3.0 の設定不要のセキュリティ アサーションとほぼ同等です。 次の表では、WCF の認証モードを WSE 3.0 のターンキーセキュリティアサーションにマップします。

        |WCF 認証モード|WSE 3.0 の設定不要のセキュリティ アサーション|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*`mutualCertificate10Security` と`mutualCertificate11Security`ターンキーのセキュリティアサーションの主な違いの1つは、WSE が SOAP メッセージをセキュリティで保護するために使用する ws-security 仕様のバージョンです。 `mutualCertificate10Security` では WS-Security 1.0 が使用され、`mutualCertificate11Security` では WS-Security 1.1 が使用されます。 WCF の場合、ws-security 仕様のバージョンは、 `messageSecurityVersion` [ \<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の属性で指定されます。

        SOAP メッセージのセキュリティ保護に使用する ws-security 仕様のバージョンを設定するには、 `messageSecurityVersion` [ \<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の属性を設定します。 WSE 3.0 と相互運用するには、`messageSecurityVersion` 属性の値を <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> に設定します。

    4. [ \<Textmessageencoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)を追加し、をその値<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>に設定することによって、 `messageVersion` WCF で ws-addressing 仕様の8月2004バージョンが使用されるように指定します。

        > [!NOTE]
        > SOAP 1.2 の使用時には、`messageVersion` 属性を <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> に設定します。

2. サービスがカスタム バインドを使用するように指定します。

    1. エンドポイント > 要素`binding` [の属性をに\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) `customBinding`設定します。

    2. エンドポイント > `bindingConfiguration` [ \<](../../../../docs/framework/misc/binding.md) 要素の属性を、カスタムバインドのバインド>の属性で`name`指定された値に設定します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)

## <a name="example"></a>例

次のコード例では、`Service.HelloWorldService` が WSE 3.0 クライアントと相互運用するためにカスタム バインドを使用するように指定します。 カスタム バインドには 2004 年 8 月版の WS-Addressing が指定され、WS-Security 1.1 の一連の仕様が、交換されるメッセージのエンコードに使用されます。 メッセージは、<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 認証モードを使用してセキュリティ保護されます。

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>関連項目

- [方法: システム指定のバインディングをカスタマイズする](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
