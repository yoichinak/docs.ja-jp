---
title: '方法 : ASP.NET メンバーシップ プロバイダーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184788"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>方法 : ASP.NET メンバーシップ プロバイダーを使用する

ASP.NET メンバーシップ プロバイダは、ASP.NET開発者が、ユーザーが一意のユーザー名とパスワードの組み合わせを作成できる Web サイトを作成できるようにする機能です。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにサインインして、サービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 代わりに、資格情報 (ユーザー名とパスワードの組み合わせ) を提供するすべてのユーザーが、サイトとそのサービスを使用できます。

サンプル アプリケーションについては、「[メンバーシップとロール プロバイダ](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 ASP.NET ロール プロバイダ機能の使用方法については、「[方法 : サービスでASP.NET ロール プロバイダを使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)する 」を参照してください。

メンバーシップ機能では、SQL Server データベースを使用してユーザー情報を格納する必要があります。 メンバーシップ機能には、パスワードを忘れたユーザーへの質問を行うためのメソッドも含まれています。

Windows 通信基盤 (WCF) の開発者は、セキュリティ上の目的でこれらの機能を利用できます。 WCF アプリケーションに統合する場合、ユーザーは、WCF クライアント アプリケーションにユーザー名とパスワードの組み合わせを指定する必要があります。 データを WCF サービスに転送するには、ユーザー名とパスワードの資格情報をサポートするバインディングを<xref:System.ServiceModel.WSHttpBinding>使用します ( 構成では、 [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) し、クライアント資格情報の種類を に`UserName`設定します。 サービスでは、WCF セキュリティはユーザー名とパスワードに基づいてユーザーを認証し、ASP.NET ロールで指定されたロールも割り当てます。

> [!NOTE]
> WCF では、ユーザー名とパスワードの組み合わせやその他のユーザー情報をデータベースに設定するメソッドは提供されません。

### <a name="to-configure-the-membership-provider"></a>メンバーシップ プロバイダーを構成するには

1. Web.config ファイルの`system.web`<>要素の下に、<>`membership`要素を作成します。

2. `<membership>` 要素を作成します。

3. <>`providers`要素の子として、プロバイダーのコレクションを`<clear />`フラッシュする要素を追加します。

4. 要素の`<clear />`下に、次の`add`属性を適切な値に設定した<>要素`name`を`type`作成`connectionStringName``requiresUniqueEmail``passwordFormat`します`applicationName`。 `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `name` 属性は、構成ファイルの値として後で使用します。 `SqlMembershipProvider` に設定する方法の例を次に示します。

    次の例は構成セクションを示します。

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>ユーザー名/パスワードの組み合わせを受け入れるようにサービス セキュリティを構成するには

1. 構成ファイルの[\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素の下に[\<、バインディング>要素を](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)追加します。

2. バインド セクションに[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を追加します。 WCF バインド要素の作成の詳細については、「[方法 : 構成でサービス バインドを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。

3. `mode` 要素の `<security>` 属性を `Message` に設定します。

4. <>`clientCredentialType``message`要素の属性を に`UserName`設定します。 これにより、ユーザー名/パスワードの組み合わせがクライアントの資格情報として使用されるようになります。

    次のコード例は、バインディングの構成コードを示しています。

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>メンバーシップ プロバイダーを使用するようにサービスを構成するには

1. `<system.serviceModel>`要素の子として、要素[\<に動作>追加します。](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

2. [\<サービス](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)`behaviors`を追加する><>要素にします。

3. [\<動作を>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)追加し、属性`name`を適切な値に設定します。

4. <`behavior`の[\<>要素にサービス資格情報>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)を追加します。

5. 要素に[\<ユーザー名認証>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)を追加`<serviceCredentials>`します。

6. `userNamePasswordValidationMode` 属性を `MembershipProvider` に設定します。

    > [!IMPORTANT]
    > 値が`userNamePasswordValidationMode`設定されていない場合、WCF は、メンバーシップ プロバイダーの代わりに Windows 認証ASP.NET使用します。

7. `membershipProviderName` 属性をプロバイダーの名前 (このトピックの最初の手順でプロバイダーを追加したときに指定したもの) に設定します。 次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>例

次のコードは、ASP メンバーシップ機能を使用するサービスの構成を示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>関連項目

- [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
