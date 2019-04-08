---
title: '方法: ASP.NET メンバーシップ プロバイダーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: df86f87bfc2456d77e3c1ee209cb8b4c61f53b21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140609"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>方法: ASP.NET メンバーシップ プロバイダーを使用する
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーを使用すると、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発者は、ユーザーが一意のユーザー名とパスワードの組み合わせを作成できる Web サイトを作成できます。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにサインインして、サービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 自分の資格情報 (ユーザー名とパスワードの組み合わせ) を提示したユーザーは、だれでもサイトとそのサービスを使用できるからです。  
  
 サンプル アプリケーションについては「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 使用方法について、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ロール プロバイダー機能を参照してください[方法。ASP.NET ロール プロバイダーを使用して、サービスと](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)します。  
  
 メンバーシップ機能では、SQL Server データベースを使用してユーザー情報を格納する必要があります。 メンバーシップ機能には、パスワードを忘れたユーザーへの質問を行うためのメソッドも含まれています。  
  
 Windows Communication Foundation (WCF) 開発者は、これらの機能のセキュリティの目的で利用できます。 WCF アプリケーションに統合すると、ユーザーは、WCF クライアント アプリケーションにユーザー名/パスワードの組み合わせを指定する必要があります。 WCF サービスにデータを転送するには、ユーザー名/パスワードの資格情報をサポートするバインディングを <xref:System.ServiceModel.WSHttpBinding> (構成では、 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) として使用して、クライアントの資格情報の種類を `UserName` に設定します。 サービスでは、WCF セキュリティがユーザー名とパスワードに基づいてユーザーを認証し、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ロール によって指定されたロールを割り当てます。  
  
> [!NOTE]
>  WCF では、ユーザー名/パスワードの組み合わせを使用してデータベースまたは他のユーザー情報を格納するメソッドは提供されません。  
  
### <a name="to-configure-the-membership-provider"></a>メンバーシップ プロバイダーを構成するには  
  
1.  Web.config ファイルで、<`system.web`> 要素の下に、<`membership`> 要素を作成します。  
  
2.  `<membership>` 要素の下に、`<providers>` 要素を作成します。  
  
3.  子として、<`providers`> 要素を追加、`<clear />`プロバイダーのコレクションをフラッシュする要素。  
  
4.  下、`<clear />`要素を作成、<`add`> 次の属性を持つ要素が適切な値に設定: `name`、 `type`、 `connectionStringName`、 `applicationName`、 `enablePasswordRetrieval`、 `enablePasswordReset`、 `requiresQuestionAndAnswer`、 `requiresUniqueEmail`、および`passwordFormat`します。 `name` 属性は、構成ファイルの値として後で使用します。 `SqlMembershipProvider` に設定する方法の例を次に示します。  
  
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
  
1.  構成ファイルでの下、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素を追加、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)要素。  
  
2.  追加、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)をバインディング セクション。 WCF のバインド要素を作成する方法の詳細については、次を参照してください。[方法。構成でサービス バインディング指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。  
  
3.  `mode` 要素の `<security>` 属性を `Message` に設定します。  
  
4.  設定、`clientCredentialType`の属性、<`message`> 要素を`UserName`します。 これにより、ユーザー名/パスワードの組み合わせがクライアントの資格情報として使用されるようになります。  
  
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
  
1.  `<system.serviceModel>`要素の子として [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素を追加  
  
2.  追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)に、<`behaviors`> 要素。  
  
3.  [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) を追加し、`name` 属性に適切な値を設定  
  
4.  ``behavior`` 要素に [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) を追加  
  
5.  ``<serviceCredentials>`` 要素に [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) を追加  
  
6.  `userNamePasswordValidationMode` 属性に `MembershipProvider` を設定  
  
    > [!IMPORTANT]
    >  `userNamePasswordValidationMode` に値が設定されていない場合、WCF は [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダー の代わりに Windows 認証を使用します。  
  
7.  `membershipProviderName` 属性をプロバイダーの名前 (このトピックの最初の手順でプロバイダーを追加したときに指定したもの) に設定します。 次の例に、この時点での `<serviceCredentials>` のフラグメントを示します。  
  
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

- [方法: ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
