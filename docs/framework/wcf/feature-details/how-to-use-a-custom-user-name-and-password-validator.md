---
title: '方法: カスタム ユーザー名およびパスワード検証を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7df6ec57204990066ce59700e5c2582701f2a81a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045909"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>方法: カスタム ユーザー名およびパスワード検証を使用する

既定では、ユーザー名とパスワードが認証に使用されると、Windows Communication Foundation (WCF) は Windows を使用してユーザー名とパスワードを検証します。 ただし、WCF では、カスタムのユーザー名とパスワードの認証方式 (*検証コントロール*とも呼ばれます) を使用できます。 ユーザー名およびパスワードのカスタム検証を組み込むには、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成して構成します。

サンプルアプリケーションについては、「[ユーザー名パスワード検証コントロール](../../../../docs/framework/wcf/samples/user-name-password-validator.md)」を参照してください。

### <a name="to-create-a-custom-user-name-and-password-validator"></a>カスタムのユーザー名/パスワード検証コントロールを作成するには

1. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> から派生するクラスを作成します。

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドして、カスタム認証方式を実装します。

    次の例のコードは、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> メソッドをオーバーライドします。稼働環境では、このようなコードを使用しないでください。 このコードをカスタムのユーザー名/パスワード検証方式に置き換えます。この場合、ユーザー名とパスワードの組み合わせをデータベースから取得する必要があります。

    クライアントに認証エラーを返すには、<xref:System.ServiceModel.FaultException> メソッドで <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> をスローします。

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>カスタムのユーザー名/パスワード検証コントロールを使用するようにサービスを構成するには

1. 任意のトランスポート上のメッセージ セキュリティ、または HTTP(S) 上のトランスポート レベル セキュリティを使用するバインディングを構成します。

    メッセージセキュリティを使用する場合は、システム指定のバインディング ( [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)など) の1つ、または`UserName` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)メッセージセキュリティと資格情報の種類をサポートする customBinding > を追加します。

    HTTP (S) でトランスポートレベルのセキュリティを使用する場合は、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)または[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) [ \<basicHttpBinding >、netTcpBinding > または customBinding のいずれかを追加し >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)HTTP (S) と`Basic`認証スキームを使用する。

    > [!NOTE]
    > [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降を使用する場合は、メッセージおよびトランスポート セキュリティでカスタムのユーザー名/パスワード検証コントロールを使用できます。 WinFX では、カスタムのユーザー名とパスワード検証コントロールは、メッセージセキュリティでのみ使用できます。

    > [!TIP]
    > このコンテキストでの netTcpBinding \<> の使用の詳細については、「 [ \<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md) 」を参照してください。

    1. 構成ファイルの[ \<system.servicemodel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素の下に、バインド > 要素を追加します。

    2. [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) または [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 要素をバインディング セクションに追加します。 WCF バインド要素の作成の詳細については[、「」を参照してください。構成](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)でサービスバインドを指定します。

    3. `Message` `TransportWithMessageCredential`[セキュリティ > または\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `mode` [の属性を、、、またはに\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)設定します。 `Transport`

    4. [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) または　[\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) の　`clientCredentialType` 属性を設定します。

        メッセージセキュリティを使用する場合は`clientCredentialType` 、 [ \<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)の属性を`UserName`に設定します。

        HTTP (S) 経由`clientCredentialType`でトランスポートレベル`Basic` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)のセキュリティを使用する場合は、トランスポート > の属性または[ \<トランスポート >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)をに設定します。

        > [!NOTE]
        > WCF サービスがトランスポートレベルのセキュリティ<xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A>を使用してインターネットインフォメーションサービス (IIS) でホストされていて、プロパティがに<xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>設定されている場合、カスタム認証スキームは Windows 認証のサブセットを使用します。 このシナリオでは、WCF がカスタム認証システムを呼び出す前に、IIS が Windows 認証を実行します。

    WCF バインド要素の作成の詳細については[、「」を参照してください。構成](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)でサービスバインドを指定します。

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

2. 受信 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> セキュリティ トークンのユーザー名とパスワードの組み合わせを検証する際に、カスタムのユーザー名/パスワード検証コントロールを使用することを指定する動作を構成します。

    1. [ \<System.servicemodel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [要素の子として、behaviors>要素を追加します。\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

    2. Behaviors > 要素に[servicebehaviors > を追加します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

    3. 動作 > 要素に追加し、属性を適切な値に設定します。`name` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)

    4. 動作 > 要素に[serviceCredentials > を追加します。 \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)

    5. UserNameAuthentication > を[serviceCredentials >に追加します\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)

    6. `userNamePasswordValidationMode` を `Custom` に設定します。

        > [!IMPORTANT]
        > `userNamePasswordValidationMode`値が設定されていない場合、WCF はカスタムユーザー名とパスワード検証コントロールではなく Windows 認証を使用します。

    7. `customUserNamePasswordValidatorType` を、カスタムのユーザー名/パスワード検証コントロールを表す型に設定します。

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
- [方法: ASP.NET メンバーシッププロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
