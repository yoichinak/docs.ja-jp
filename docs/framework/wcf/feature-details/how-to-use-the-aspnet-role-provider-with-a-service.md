---
title: '方法: ASP.NET のロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: f989252c7dd9b2ccdce8331e7cdd987042230ded
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880242"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>方法: ASP.NET のロール プロバイダーとサービスを使用する
(ASP.NET メンバーシップ プロバイダーと組み合わせて) ASP.NET ロール プロバイダーは、ASP.NET 開発者サイトでアカウントを作成し、承認のためのロールを割り当てられるようにすることが Web サイトを作成することができる機能です。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにログインしてサービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 自分の資格情報 (ユーザー名とパスワードの組み合わせ) を提示したユーザーは、だれでもサイトとそのサービスを使用できます。  
  
 サンプル アプリケーションについては「[メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 ASP.NET メンバーシップ プロバイダー機能の詳細については、次を参照してください。[方法。ASP.NET メンバーシップ プロバイダーを使用して、](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)します。  
  
 ロール プロバイダー機能では、SQL Server データベースを使用してユーザー情報を格納します。 Windows Communication Foundation (WCF) 開発者は、これらの機能のセキュリティの目的で利用できます。 WCF アプリケーションに統合すると、ユーザーは、WCF クライアント アプリケーションにユーザー名/パスワードの組み合わせを指定する必要があります。 データベースを使用する WCF を有効にするには、インスタンスを作成する必要があります、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>クラス、設定、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>プロパティを<xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>、に対する動作のコレクションにインスタンスを追加し、<xref:System.ServiceModel.ServiceHost>サービスをホストしています。  
  
### <a name="to-configure-the-role-provider"></a>ロール プロバイダーを構成するには  
  
1. Web.config ファイルでの下、<`system.web`> 要素を追加、<`roleManager`> 要素の`enabled`属性を`true`。  
  
2. `defaultProvider` 属性に `SqlRoleProvider` を設定  
  
3. 子として、<`roleManager`> 要素を追加する <`providers`> 要素。  
  
4. 子として、<`providers`> 要素を追加、<`add`> 次の属性を持つ要素が適切な値に設定: `name`、 `type`、`connectionStringName`と`applicationName`次の例のようにします。  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>ロール プロバイダーを使用するようにサービスを構成するには  
  
1. Web.config ファイルで、追加、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)要素。  
  
2. 追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素を <`system.ServiceModel`> 要素。  
  
3. 追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)に、<`behaviors`> 要素。  
  
4. 追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素、`name`属性に適切な値。  
  
5. 追加、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)に、<`behavior`> 要素。  
  
6. `principalPermissionMode` 属性に `UseAspNetRoles` を設定  
  
7. `roleProviderName` 属性に `SqlRoleProvider` を設定 この構成の一部を次の例に示します。  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a>関連項目

- [メンバーシップとロール プロバイダー](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [方法: ASP.NET メンバーシップ プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
