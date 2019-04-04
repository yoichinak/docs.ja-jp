---
title: '方法: カスタム ユーザー名およびパスワード検証を使用して、'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 619d3e80a8206ae3ceef2d7ff822dc3bfa8f65be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700534"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>方法: カスタム ユーザー名およびパスワード検証を使用して、
既定では、ユーザー名とパスワードを使用すると認証では、Windows Communication Foundation (WCF) を使用して Windows ユーザー名とパスワードを検証します。 ただし、WCF では、カスタム ユーザー名とパスワードの認証スキームとも呼ばれます*バリデーター*します。 ユーザー名およびパスワードのカスタム検証を組み込むには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成して構成します。  
  
 サンプル アプリケーションでは、[ユーザー名パスワード検証](../../../../docs/framework/wcf/samples/user-name-password-validator.md)を参照してください。  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>カスタムのユーザー名/パスワード検証コントロールを作成するには  
  
1.  <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成します。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドして、カスタム認証方式を実装します。  
  
     次の例のコードは、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドします。稼働環境では、このようなコードを使用しないでください。 このコードをカスタムのユーザー名/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。  
  
     クライアントに認証エラーを返すには、<xref:System.ServiceModel.FaultException> メソッドで <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> をスローします。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>カスタムのユーザー名/パスワード検証コントロールを使用するようにサービスを構成するには  
  
1.  任意のトランスポート上のメッセージ セキュリティ、または HTTP(S) 上のトランスポート レベル セキュリティを使用するバインディングを構成します。  
  
     メッセージ セキュリティを使用する場合などの追加、システム指定のバインディングのいずれかを[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、または[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)メッセージ セキュリティをサポートしています、`UserName`資格情報の種類。  
  
     経由で HTTP (S) をトランスポート レベルのセキュリティを使用する場合のいずれかの追加、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)または[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)または[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) を使用して、`Basic`認証スキームです。  
  
    > [!NOTE]
    >  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降を使用する場合は、メッセージおよびトランスポート セキュリティでカスタムのユーザー名/パスワード検証コントロールを使用できます。 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] では、カスタムのユーザー名/パスワード検証コントロールを使用できるのは、メッセージ セキュリティだけです。  
  
    > [!TIP]
    >  使用しての詳細については\<netTcpBinding > このコンテキストで、次を参照してください[\<セキュリティ >。](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  構成ファイルでの下、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素。  
  
    2.  [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) または [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 要素をバインディング セクションに追加します。 WCF のバインド要素を作成する方法の詳細については、次を参照してください。[方法。構成でサービス バインディング指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。  
  
    3.  設定、`mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)または[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)に`Message`、 `Transport`、または`TransportWithMessageCredential`します。  
  
    4.  [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) または　[\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) の　`clientCredentialType` 属性を設定します。  
  
         メッセージ セキュリティを使用する場合は、設定、`clientCredentialType`の属性、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)に`UserName`します。  
  
         HTTP (S) 上のトランスポート レベルのセキュリティを使用して、設定、`clientCredentialType`の属性、 [\<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)または[\<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)に`Basic`します。  
  
        > [!NOTE]
        >  WCF サービスがホストされている場合にインターネット インフォメーション サービス (IIS) トランスポート レベルのセキュリティを使用して、<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A>プロパティに設定されて<xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>、カスタム認証方式は Windows 認証のサブセットを使用します。 このシナリオで IIS が WCF のカスタム認証システムを起動する前に Windows 認証を実行するためです。  
  
     WCF のバインド要素を作成する方法の詳細については、次を参照してください。[方法。構成でサービス バインディング指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。  
  
     次のコード例は、バインディングの構成コードを示しています。  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  受信 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> セキュリティ トークンのユーザー名とパスワードの組み合わせを検証する際に、カスタムのユーザー名/パスワード検証コントロールを使用することを指定する動作を構成します。  
  
    1.  子として、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。  
  
    2.  追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。  
  
    3.  追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素、`name`属性に適切な値。  
  
    4.  追加、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素。  
  
    5.  追加、 [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)します。  
  
    6.  `userNamePasswordValidationMode` を `Custom` に設定します。  
  
        > [!IMPORTANT]
        >  場合、`userNamePasswordValidationMode`値が設定されていない、WCF は、カスタムのユーザー名とパスワードの検証コントロールではなく Windows 認証を使用します。  
  
    7.  `customUserNamePasswordValidatorType` を、カスタムのユーザー名/パスワード検証コントロールを表す型に設定します。  
  
     次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>例  
 カスタムのユーザー名/パスワード検証コントロールを作成する方法を次のコード例に示します。 稼働環境では、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドするコードを使用しないでください。 このコードをカスタムのユーザー名/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [方法: ASP.NET メンバーシップ プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
