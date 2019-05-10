---
title: '方法: カスタム プリンシパル ID を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 324537ac018086669abccc21235f9a9359b413cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662843"
---
# <a name="how-to-create-a-custom-principal-identity"></a>方法: カスタム プリンシパル ID を作成する
<xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを宣言によって制御する手段として使用できます。 この属性を使用する場合、承認チェックを実行するためのモードが <xref:System.ServiceModel.Description.PrincipalPermissionMode> 列挙体で指定されます。 このモードが <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> に設定されている場合、ユーザーは、<xref:System.Security.Principal.IPrincipal> プロパティから返されるカスタムの <xref:System.Threading.Thread.CurrentPrincipal%2A> クラスを指定できます。 ここでは、<xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> を、カスタム承認ポリシーおよびカスタム プリンシパルと組み合わせて使用する場合のシナリオを説明します。  
  
 使用しての詳細については、<xref:System.Security.Permissions.PrincipalPermissionAttribute>を参照してください[方法。PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードをコンパイルするには、次の名前空間へ参照が必要です。  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [方法: サービスで ASP.NET ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [方法: PrincipalPermissionAttribute クラスでアクセスを制限します。](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
