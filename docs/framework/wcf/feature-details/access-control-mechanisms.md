---
title: アクセス制御機構
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 53b20e7f11f5accd1436f29063817142681e4f74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213260"
---
# <a name="access-control-mechanisms"></a>アクセス制御機構
Windows Communication Foundation (WCF) といくつかの方法でアクセスを制御することができます。 ここでは、正しい機構を選択して使用できるように、さまざまな機構について簡単に説明し、各機構を使用するタイミングに関するヒントを提供します。 ここでは、アクセス テクノロジを単純なものから順に示します。 最も単純なのは <xref:System.Security.Permissions.PrincipalPermissionAttribute> で、最も複雑なのは ID モデルです。  
  
 これらのメカニズムに加え、WCF における偽装と委任が [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md) で説明されています。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを制限するために使用します。 この属性をメソッドに適用して使用すると、特定の呼び出し元の ID や Windows グループまたは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロールでのメンバーシップを要求できます。 クライアントが、X.509 証明書を使用して認証された場合は、サブジェクト名と証明書の拇印で構成されるプライマリ ID がクライアントに割り当てられています。  
  
 サービスのユーザーが常に、サービスが実行されているものと同じ Windows ドメインのメンバーである場合、サービスが実行されているコンピューター上のリソースへのアクセスを制御するには、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用します。 指定したアクセス レベル (なし、読み取り専用、または読み取りと書き込みなど) を持つ Windows グループを簡単に作成できます。  
  
 詳細については、属性を使用して、次を参照してください。[方法。PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)します。 Id に関する詳細については、次を参照してください。[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)します。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET メンバーシップ プロバイダー  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] の機能の 1 つに、メンバーシップ プロバイダーがあります。 メンバーシップ プロバイダーは、厳密にはアクセス制御機構ではありませんが、これを使用すると、サービスのエンドポイントにアクセスできる ID のセットを制限することで、サービスへのアクセスを制御できます。 メンバーシップ機能には、ユーザー名/パスワードの組み合わせを設定できるデータベースが含まれています。この組み合わせによって、Web サイトのユーザーはサイトのアカウントを確立できます。 ユーザーがメンバーシップ プロバイダーを使用するサービスにアクセスするには、自分の名前とパスワードを使用してログオンする必要があります。  
  
> [!NOTE]
>  使用してデータベースを設定する必要があります最初、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]機能の前に、WCF サービスを使用すると承認に使用できます。  
  
 また、このメンバーシップ機能を使用すると、既存の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サイトにメンバーシップ データベースが既にある場合に、同じユーザー名とパスワードで承認された同じユーザーがサービスを使用できるようになります。  
  
 メンバーシップ機能を使用して WCF サービスの詳細については、次を参照してください。[方法。ASP.NET メンバーシップ プロバイダーを使用して、](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)します。  
  
## <a name="aspnet-role-provider"></a>ASP.NET ロール プロバイダー  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] には、ロールを使用して承認を管理する機能もあります。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを使用すると、開発者は、ユーザーのロールを作成し、各ユーザーを 1 つまたは複数のロールに割り当てることができます。 メンバーシップ プロバイダーと同様に、ロールと割り当てはデータベースに格納され、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーの特定の実装によって提供されるツールを使用して設定できます。 として、メンバーシップ機能と WCF 開発者ことができます、情報を参照して、データベース内の役割サービスのユーザーを認証します。 たとえば、上記の `PrincipalPermissionAttribute` アクセス制御機構と組み合わせてロール プロバイダーを使用できます。  
  
 使用することも、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]が既にある場合、ロール プロバイダー[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ロール プロバイダー データベースし、WCF サービスで、同じ一連のルールとユーザーの割り当てを使用する場合。  
  
 ロール プロバイダー機能の使用に関する詳細については、次を参照してください。[方法。ASP.NET ロール プロバイダーを使用して、サービスと](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)します。  
  
## <a name="authorization-manager"></a>承認マネージャー  
 さらに、承認マネージャー (AzMan) と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを組み合わせてクライアントを承認する機能もあります。 Web サービスを [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] によってホストする場合は、サービスの承認が AzMan 経由で行われるように AzMan をアプリケーションに統合できます。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール マネージャーは、アプリケーション ロールの管理、ロールへのユーザーの追加と削除、およびロール メンバーシップのチェックを実行できるようにする API を提供しますが、指定されたタスクまたは操作の実行がユーザーに許可されているかどうかを照会する機能は提供しません。 AzMan を使用すると、個々の操作を定義してタスクに結合できます。 AZMan では、ロールのチェックだけでなく、ユーザーがタスクを実行できるかどうかをチェックすることもできます。 ロールの割り当てとタスクの承認は、アプリケーションの外部で構成することも、アプリケーション内でプログラムによって実行することもできます。 AzMan 管理 Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインにより、管理者は、ロールが実行時に実行できるタスクを変更したり、ユーザーのロール メンバーシップを管理したりできます。  
  
 また、AzMan と [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーは、既存の AzMan インストールに既にアクセスでき、AzMan とロール プロバイダーの組み合わせの機能を使用してサービス ユーザーを承認する場合にも使用できます。  
  
 AzMan の詳細については、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]ロール プロバイダーを参照してください[How To:ASP.NET 2.0 で Authorization Manager (AzMan) 使用](https://go.microsoft.com/fwlink/?LinkId=88951)します。 AzMan とロール プロバイダーを使用して WCF サービスの詳細については、次を参照してください。[方法。サービスと ASP.NET の承認マネージャー ロール プロバイダーを使用して](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)します。  
  
## <a name="identity-model"></a>ID モデル  
 ID モデルは、クライアントを承認するためのクレームとポリシーを管理できるようにする API のセットです。 ID モデルを使用すると、呼び出し元がサービスに対するそれ自体の認証に使用した資格情報に含まれるすべてのクレームを調べ、それらをサービスのポリシー セットと比較し、この比較に基づいてアクセスを許可または拒否できます。  
  
 アクセスを許可する前に、微調整と、特定の条件を設定する機能が必要な場合は、ID モデルを使用します。 たとえば、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用した場合、条件は、ユーザー ID が認証され、それが特定のロールに属するということだけになります。 これに対し、ID モデルを使用すると、ドキュメントの参照を許可されるにはユーザーが 18 才以上であり、有効な運転免許証を所有している必要があることを明確に示すポリシーを作成できます。  
  
 ID モデルのクレームに基づくアクセス制御の恩恵を受けることができる例として、発行済みトークンのシナリオでフェデレーション資格情報を使用する場合が挙げられます。 フェデレーションと発行済みトークンの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。  
  
 Id モデルの詳細については、次を参照してください。[管理クレームと Id モデルでの承認](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [方法: PrincipalPermissionAttribute クラスでアクセスを制限します。](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [方法: サービスで ASP.NET ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [方法: サービスと ASP.NET の承認マネージャー ロール プロバイダーを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
