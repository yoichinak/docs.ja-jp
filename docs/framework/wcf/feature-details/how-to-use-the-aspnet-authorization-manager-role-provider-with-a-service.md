---
title: '方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184812"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する
ASP.NET Web サービスをホストする場合、承認マネージャをアプリケーションに統合して、サービスに承認を提供できます。 承認マネージャーを使用して、アプリケーション開発者は個々の操作を定義できます。また、個々の操作をグループ化してタスクを形成できます。 次に管理者は、ロールを承認して特定のタスクまたは個々の操作を実行できます。 承認マネージャーでは、ロール、タスク、操作、ユーザーを管理する管理ツールとして Microsoft 管理コンソール (MMC) スナップインが提供されます。 管理者は、承認マネージャーのポリシー ストアを XML ファイル、Active Directory、または Active Directory アプリケーション モード (ADAM) ストアに構成します。  
  
 承認マネージャは、Web サービスをホストしているASP.NET アプリケーションの承認マネージャASP.NETロール プロバイダを構成することによって、アプリケーションに統合されます。 他のASP.NET ロール プロバイダーと同様に、承認マネージャーASP.NETロール プロバイダーは`providers`、<>要素を使用して構成されます。  
  
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
  
 WCF アプリケーションとASP.NET ロール プロバイダーを統合する方法の詳細については、「[方法 : サービスでASP.NET ロール プロバイダーを使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)する 」を参照してください。 ASP.NETで承認マネージャを使用する方法の詳細については、「[方法 : ASP.NET 2.0 で承認マネージャ (AzMan) を使用](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))する方法」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
