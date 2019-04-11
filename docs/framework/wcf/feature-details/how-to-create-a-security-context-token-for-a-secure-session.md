---
title: '方法: セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 0b0da7e60cb54a1c3d6eb6d2d557f7312da1e9ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189342"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>方法: セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する
セキュリティで保護されたセッションでステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用すると、そのセッションでサービスを再利用できます。 たとえば、セキュリティで保護されたセッションでステートレスな SCT を使用しているときにインターネット インフォメーション サービス (IIS) をリセットすると、サービスに関連付けられているセッション データが失われます。 このセッション データには、SCT キャッシュが含まれています。 このため、クライアントが次回ステートレスな SCT をサービスに送信すると、エラーが返されます。これは、SCT に関連付けられているキーを取得できないためです。 しかし、ステートフルな SCT を使用した場合、SCT に関連付けられているキーは、その SCT 内に格納されます。 キーが SCT 内、つまりメッセージ内に格納されているため、セキュリティで保護されたセッションは、サービスの再使用の影響を受けません。 既定では、Windows Communication Foundation (WCF) は、セキュリティで保護されたセッションでステートレスな Sct を使用します。 ここでは、セキュリティで保護されたセッションでステートフルな SCT を使用する方法について詳しく説明します。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Channels.IDuplexChannel> から派生したコントラクトに関係する、セキュリティで保護されたセッションでは、ステートフルな SCT を使用できません。  
  
> [!NOTE]
>  セキュリティで保護されたセッションでステートフルな SCT を使用するアプリケーションでは、サービスのスレッド ID は、関連付けられたユーザー プロファイルを持つユーザー アカウントである必要があります。 ユーザー プロファイルを持たないアカウント (`Local Service` など) でサービスを実行すると、例外がスローされる場合があります。  
  
> [!NOTE]
>  Windows XP で偽装が必要な場合は、ステートフルな SCT を使用しない、セキュリティで保護されたセッションを使用します。 ステートフルな SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。 詳細については、次を参照してください。[サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)します。  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>セキュリティで保護されたセッションでステートフルな SCT を使用するには  
  
-   ステートフルな SCT を使用する、セキュリティで保護されたセッションによって SOAP メッセージを保護するように指定するカスタム バインドを作成します。  
  
    1.  追加することで、カスタム バインディングを定義、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)サービスの構成ファイルにします。  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  追加、 [\<バインド >](../../../../docs/framework/misc/binding.md)の子要素を[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)します。  
  
         `name` 属性を、構成ファイル内で一意の名前に設定してバンディング名を指定します。  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  このサービスとの間を追加することによって送信されたメッセージの認証モードを指定、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)の子要素を[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)します。  
  
         `authenticationMode` 属性を `SecureConversation` に設定して、セキュリティで保護されたセッションを指定します。 `requireSecurityContextCancellation` 属性を `false` に設定して、ステートフルな SCT を使用するように指定します。  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  追加することで、セキュリティで保護されたセッションが確立されている間に、クライアントを認証する方法を指定、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)の子要素を[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)します。  
  
         クライアントの認証方法は、`authenticationMode` 属性を設定して指定します。  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  などのエンコーディング要素を追加して、メッセージ エンコーディングを指定[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)します。  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  など、トランスポート要素を追加することで、トランスポートを指定、 [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)します。  
  
        ```xml  
        <httpTransport />  
        ```  
  
     次のコード例では、構成を使用して、セキュリティで保護されたセッションでメッセージがステートフルな SCT と共に使用できるカスタム バインドを指定します。  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>例  
 セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインドを作成するコード例を次に示します。  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Windows 認証をステートフルな SCT と組み合わせて使用すると、ときに WCF が設定されません、<xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>プロパティに実際の呼び出し元の身元が代わりにプロパティを設定して匿名。 WCF セキュリティは、すべての要求、受信 SCT からのサービスのセキュリティ コンテキストの内容を再作成する必要があります、ため、サーバーはいないの追跡、メモリ内でセキュリティ セッション。 また、<xref:System.Security.Principal.WindowsIdentity> インスタンスは SCT にシリアル化できないため、<xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティは匿名 ID を返します。  
  
 次の構成は、この動作を示します。  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>関連項目

- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
