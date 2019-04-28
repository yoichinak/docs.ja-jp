---
title: '方法: セキュリティ モードを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 5a4550e4c914dcdbc9908e766c67a2efa53e6e9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928896"
---
# <a name="how-to-set-the-security-mode"></a>方法: セキュリティ モードを設定する
Windows Communication Foundation (WCF) のセキュリティは、ほとんどの定義済みバインド上にある 3 つの一般的なセキュリティ モード: トランスポート、メッセージ、および「メッセージ資格情報付きトランスポート」。 これ以外に、2 つのバインディングに固有の 2 つのモードがあります。<xref:System.ServiceModel.BasicHttpBinding> の "トランスポート資格情報専用" モードと、<xref:System.ServiceModel.NetMsmqBinding> の "両方" モードです。 ここでは、3 つの共通のセキュリティモードである <xref:System.ServiceModel.SecurityMode.Transport>、<xref:System.ServiceModel.SecurityMode.Message>、および <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> に重点を置いて説明します。  
  
 ただし、これらのモードがすべての定義済みバインディングでサポートされるわけではありません。 ここでは、<xref:System.ServiceModel.WSHttpBinding> クラスと <xref:System.ServiceModel.NetTcpBinding> クラスでモードを設定し、プログラムと構成の両方を使用してモードを設定する方法を示します。  
  
 詳細についてを参照してください、WCF のセキュリティを参照してください。[セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)、 [Securing Services](../../../docs/framework/wcf/securing-services.md)、と[Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)します。 トランスポート モードとメッセージの詳細については、次を参照してください。[トランスポート セキュリティ](../../../docs/framework/wcf/feature-details/transport-security.md)と[メッセージ セキュリティ](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)します。  
  
### <a name="to-set-the-security-mode-in-code"></a>コードでセキュリティ モードを設定するには  
  
1. 使用しているバインディング クラスのインスタンスを作成します。 定義済みバインディングの一覧は、次を参照してください。 [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)します。 この例では、<xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成します。  
  
2. `Mode` プロパティから返されるオブジェクトの `Security` プロパティを設定します。  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     または、モードを Message (メッセージ) に設定します。コードは次のようになります。  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     または、モードを TransportWithMessageCredential (メッセージ資格情報付きトランスポート) に設定します。コードは次のようになります。  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3. 次のコードに示すように、バインディングのコンストラクターでモードを設定することもできます。  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>ClientCredentialType プロパティの設定  
 モードを上記の 3 つの値のいずれかに設定すると、`ClientCredentialType` プロパティの設定方法が決まります。 たとえば、<xref:System.ServiceModel.WSHttpBinding> クラスを使用し、モードを `Transport` に設定した場合、<xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> クラスの <xref:System.ServiceModel.HttpTransportSecurity> プロパティを適切な値に設定する必要があります。  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>トランスポート モードの ClientCredentialType プロパティを設定するには  
  
1. バインディングのインスタンスを作成します。  
  
2. `Mode` プロパティを `Transport`に設定します。  
  
3. `ClientCredential` プロパティに適切な値を設定します。 プロパティを `Windows` に設定するコードを次に示します。  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>メッセージ モードの ClientCredentialType プロパティを設定するには  
  
1. バインディングのインスタンスを作成します。  
  
2. `Mode` プロパティを `Message`に設定します。  
  
3. `ClientCredential` プロパティに適切な値を設定します。 プロパティを `Certificate` に設定するコードを次に示します。  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>構成でモードと ClientCredentialType プロパティを設定するには  
  
1. 適切なバインド要素を追加、 [\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素。 次の例では、追加、 [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。  
  
2. 追加、`<binding>`要素とその`name`属性に適切な値。  
  
3. `<security>` 要素を追加し、`mode` 属性を `Message`、`Transport`、または `TransportWithMessageCredential` に設定します。  
  
4. モードを `Transport` に設定した場合は、`<transport>` 要素を追加し、`clientCredential` 属性を適切な値に設定します。  
  
     モードを "`Transport"` に設定し、`clientCredentialType` 要素の `<transport>` 属性を "`Windows"` に設定する例を次に示します。  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     または、`security mode` を "`Message"` に設定し、その後に `<"message">` 要素を指定します。 この例では、`clientCredentialType` を "`Certificate"` に設定しています。  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     次に説明する <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> 値は、特殊なケースで使用されます。  
  
### <a name="using-transportwithmessagecredential"></a>TransportWithMessageCredential の使用  
 セキュリティ モードを `TransportWithMessageCredential` に設定した場合、トランスポート レベルのセキュリティを提供する実際の機構はトランスポートによって決まります。 たとえば、HTTP プロトコルでは SSL (Secure Sockets Layer) over HTTP (HTTPS) を使用します。 このため、トランスポート セキュリティ オブジェクト (`ClientCredentialType` など) の <xref:System.ServiceModel.HttpTransportSecurity> プロパティを設定しても無視されます。  つまり、メッセージ セキュリティ オブジェクト (`ClientCredentialType` バインディングの場合は `WSHttpBinding` オブジェクト) の <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> だけを設定できます。  
  
 詳細については、「[方法 :トランスポート セキュリティの使用とメッセージ資格情報](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)します。  
  
## <a name="see-also"></a>関連項目

- [方法: SSL 証明書でポートを構成します。](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [方法: トランスポート セキュリティの使用とメッセージ資格情報](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [トランスポート セキュリティ](../../../docs/framework/wcf/feature-details/transport-security.md)
- [メッセージのセキュリティ](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)
- [システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
