---
title: '方法: ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880199"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>方法: ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する
ASP.NET では、Web サービスをホストする場合は、サービスに承認を提供するアプリケーションに承認マネージャーを統合できます。 承認マネージャーを使用して、アプリケーション開発者は個々の操作を定義できます。また、個々の操作をグループ化してタスクを形成できます。 次に管理者は、ロールを承認して特定のタスクまたは個々の操作を実行できます。 承認マネージャーでは、ロール、タスク、操作、ユーザーを管理する管理ツールとして Microsoft 管理コンソール (MMC) スナップインが提供されます。 管理者は、承認マネージャーのポリシー ストアを XML ファイル、Active Directory、または Active Directory アプリケーション モード (ADAM) ストアに構成します。  
  
 承認マネージャーは、Web サービスをホストする ASP.NET アプリケーションの承認マネージャーの ASP.NET ロール プロバイダーを構成することで、アプリケーションに統合します。 使用して、承認マネージャーの ASP.NET ロール プロバイダーを構成の他の ASP.NET ロール プロバイダーと同様に、<`providers`> 要素。  
  
 承認マネージャーをアプリケーションに統合する Web サービスの構成ファイルの一部を示すコード例を次に示します。  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 WCF アプリケーションと、ASP.NET ロール プロバイダーの統合についての詳細については、次を参照してください。[方法。ASP.NET ロール プロバイダーを使用して、サービスと](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)します。 ASP.NET で承認マネージャーの使用に関する詳細については、次を参照してください。[方法。ASP.NET 2.0 で Authorization Manager (AzMan) 使用](https://go.microsoft.com/fwlink/?LinkId=71303)します。  
  
## <a name="see-also"></a>関連項目

- [方法: サービスで ASP.NET ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
