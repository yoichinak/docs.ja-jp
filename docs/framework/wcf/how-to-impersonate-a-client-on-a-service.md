---
title: '方法: サービスでクライアントに偽装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 3dd40efe27687b048984c4592db0d3787d061eeb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402318"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>方法: サービスでクライアントに偽装する
Windows Communication Foundation (WCF) サービスでクライアントを偽装してにより、サービスは、クライアントに代わってアクションを実行します。 コンピューター上のディレクトリやファイルへのアクセス、または SQL Server データベースへのアクセスなど、アクセス制御リスト (ACL) のチェックを受けるアクションでは、ACL のチェックがクライアントのユーザー アカウントに対して行われます。 ここでは、Windows ドメインのクライアントで、クライアント偽装レベルを設定できるようにするために必要な基本的な手順について説明します。 このパターンの実施例については、「 [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md)」を参照してください。 クライアントの権限借用の詳細については、次を参照してください。[委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)します。  
  
> [!NOTE]
>  クライアントとサービスが同じコンピューター上で実行されており、クライアントがシステム アカウント ( `Local System` や `Network Service`など) で実行されているときに、ステートレスなセキュリティ コンテキスト トークンを使用してセキュリティで保護されたセッションを確立した場合、クライアントを偽装することはできません。 通常、WinForms アプリケーションやコンソール アプリケーションは、現在ログインしているアカウントで実行されるため、既定でそのアカウントを偽装できます。 ただし、ときに、ASP.NET ページは、クライアントはそのページが IIS 6.0 または IIS 7.0 でホストされているし、クライアントで実行、`Network Service`アカウントで実行します。 セキュリティで保護されたセッションをサポートするシステム提供のすべてのバインディングは、ステートフルなセキュリティ コンテキスト トークンを既定で使用します。 ただし、クライアントが、ASP.NET ページであり、ステートフルなセキュリティ コンテキスト トークンをセキュリティで保護されたセッションを使用する場合、クライアントを偽装できません。 セキュリティで保護されたセッションでステートフルなセキュリティ コンテキスト トークンの使用に関する詳細については、次を参照してください。[方法。セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)します。  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>サービスにキャッシュされた Windows トークンでクライアントの偽装を有効にするには  
  
1. サービスを作成します。 この基本的な手順のチュートリアルについては、「 [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
2. Windows 認証を使用してセッションを作成するバインディング ( <xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.WSHttpBinding>など) を使用します。  
  
3. サービスのインターフェイスの実装を作成するときには、クライアントの偽装を必要とするメソッドに <xref:System.ServiceModel.OperationBehaviorAttribute> クラスを適用します。 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> プロパティを <xref:System.ServiceModel.ImpersonationOption.Required>に設定します。  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>クライアントに許可される偽装レベルを設定するには  
  
1. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービス クライアント コードを作成します。 詳細については、次を参照してください。[にアクセスするサービスの WCF クライアントを使用して](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)します。  
  
2. WCF クライアントを作成すると、設定、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>のプロパティ、<xref:System.ServiceModel.Security.WindowsClientCredential>クラスのいずれかを<xref:System.Security.Principal.TokenImpersonationLevel>列挙値。  
  
    > [!NOTE]
    >  <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>を使用するには、ネゴシエート Kerberos 認証 ( *"マルチレッグ"* Kerberos または *"マルチステップ"* Kerberos と呼ぶこともあります) を使用する必要があります。 これを実装する方法については、次を参照してください。[セキュリティのベスト プラクティス](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)します。  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [クライアントの偽装](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
