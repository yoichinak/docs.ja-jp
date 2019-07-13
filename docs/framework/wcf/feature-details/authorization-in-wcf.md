---
title: WCF での承認
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 8c605b310f19a05f994296d8f4268b91b408fb18
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881205"
---
# <a name="authorization-in-wcf"></a>WCF での承認
承認は、サービスやファイルなどのリソースへのアクセスと権限を制御するプロセスです。 このセクションのトピックでは、Windows Communication Foundation (WCF) でさまざまな方法でこの基本的なタスクを実行する方法を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アクセス制御機構](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 推奨される使用して、WCF 承認メカニズムの概要を提供します。  
  
 [方法: PrincipalPermissionAttribute クラスでアクセスを制限します。](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用してサービスへのアクセスを制限するプロセスを示します。  
  
 [方法: サービスで ASP.NET ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 ASP.NET のロール プロバイダー機能を使用するように有効にするサービスの構成について説明します。  
  
 [方法: サービスと ASP.NET の承認マネージャー ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 ASP.NET では、承認マネージャーを使用して、Web サイトの承認を管理します。 同様に、WCF は ASP.NET/Authorization マネージャーは、クライアントの承認の組み合わせを活用できます。  
  
 [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 ID モデル インフラストラクチャをクレーム ベースの承認に使用する際の基本について説明します。  
  
 [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 委任と偽装の違いについて説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>関連項目  
 [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
