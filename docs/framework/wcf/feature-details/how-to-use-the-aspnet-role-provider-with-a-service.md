---
title: '方法 : ASP.NET のロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184770"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>方法 : ASP.NET のロール プロバイダーとサービスを使用する

ASP.NET ロール プロバイダ (ASP.NET メンバーシップ プロバイダーと組み合わせた) は、ASP.NET開発者が、ユーザーがサイトを持つアカウントを作成したり、承認用にロールを割り当てたりできる Web サイトを作成できるようにする機能です。 この機能を使用すれば、ユーザーはだれでもサイトでアカウントを作成し、そのサイトにログインしてサービスに排他的にアクセスできます。 これは、ユーザーが Windows ドメイン内にアカウントを持っていることが必要な Windows セキュリティとは対照的です。 代わりに、資格情報 (ユーザー名とパスワードの組み合わせ) を提供するすべてのユーザーが、サイトとそのサービスを使用できます。  
  
サンプル アプリケーションについては、「[メンバーシップとロール プロバイダ](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)」を参照してください。 ASP.NET メンバーシップ プロバイダ機能の詳細については、「[方法 : ASP.NET メンバーシップ プロバイダを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)」を参照してください。  
  
ロール プロバイダー機能では、SQL Server データベースを使用してユーザー情報を格納します。 Windows 通信基盤 (WCF) の開発者は、セキュリティ上の目的でこれらの機能を利用できます。 WCF アプリケーションに統合する場合、ユーザーは、WCF クライアント アプリケーションにユーザー名とパスワードの組み合わせを指定する必要があります。 WCF<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>でデータベースを使用できるようにするには、クラスのインスタンスを作成し、その<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>プロパティを に<xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>設定し、サービスをホスト<xref:System.ServiceModel.ServiceHost>している動作のコレクションにインスタンスを追加する必要があります。  
  
## <a name="configure-the-role-provider"></a>ロール プロバイダーを構成する  
  
1. Web.config ファイルの`system.web`<>要素の下に、<>`roleManager`要素を追加し、`enabled`その属性`true`を に設定します。  
  
2. `defaultProvider` 属性を `SqlRoleProvider` に設定します。  
  
3. <`roleManager`>要素の子として、<>`providers`要素を追加します。  
  
4. `providers` <>要素の子として、次の例に示`add`すように、次の属性を適切な値`name` `type`、、、、`connectionStringName`および`applicationName`に設定した<>要素を追加します。  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>ロール プロバイダーを使用するようにサービスを構成する  
  
1. Web.config ファイルに[\<、システム.サービスモデル>要素を](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)追加します。  
  
2. `system.ServiceModel` <>[\<要素に、動作>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素を追加します。  
  
3. [\<サービス](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)`behaviors`を追加する><>要素にします。  
  
4. 要素[\<>動作を](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)追加し、属性`name`を適切な値に設定します。  
  
5. サービス認証>を<>`behavior`要素に追加します。 [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)  
  
6. `principalPermissionMode` 属性を `UseAspNetRoles` に設定します。  
  
7. `roleProviderName` 属性を `SqlRoleProvider` に設定します。 この構成の一部を次の例に示します。  
  
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
- [方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
