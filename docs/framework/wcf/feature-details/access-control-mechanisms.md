---
title: アクセス制御機構
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 9ebd1489c35bb3b023ed73cd86fac1b6a352012b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882170"
---
# <a name="access-control-mechanisms"></a>アクセス制御機構
Windows Communication Foundation (WCF) といくつかの方法でアクセスを制御することができます。 ここでは、正しい機構を選択して使用できるように、さまざまな機構について簡単に説明し、各機構を使用するタイミングに関するヒントを提供します。 ここでは、アクセス テクノロジを単純なものから順に示します。 最も単純なのは <xref:System.Security.Permissions.PrincipalPermissionAttribute> で、最も複雑なのは ID モデルです。  
  
 これらのメカニズムに加え、WCF における偽装と委任が [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md) で説明されています。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを制限するために使用します。 メソッドに属性が適用されると、特定の呼び出し元の id または Windows グループまたは ASP.NET のロールのメンバーシップを要求する使用できます。 クライアントが、X.509 証明書を使用して認証された場合は、サブジェクト名と証明書の拇印で構成されるプライマリ ID がクライアントに割り当てられています。  
  
 サービスのユーザーが常に、サービスが実行されているものと同じ Windows ドメインのメンバーである場合、サービスが実行されているコンピューター上のリソースへのアクセスを制御するには、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用します。 指定したアクセス レベル (なし、読み取り専用、または読み取りと書き込みなど) を持つ Windows グループを簡単に作成できます。  
  
 詳細については、属性を使用して、次を参照してください。[方法。PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)します。 Id に関する詳細については、次を参照してください。[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)します。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET メンバーシップ プロバイダー  
 ASP.NET の機能は、メンバーシップ プロバイダーです。 メンバーシップ プロバイダーは、厳密にはアクセス制御機構ではありませんが、これを使用すると、サービスのエンドポイントにアクセスできる ID のセットを制限することで、サービスへのアクセスを制御できます。 メンバーシップ機能には、ユーザー名/パスワードの組み合わせを設定できるデータベースが含まれています。この組み合わせによって、Web サイトのユーザーはサイトのアカウントを確立できます。 ユーザーがメンバーシップ プロバイダーを使用するサービスにアクセスするには、自分の名前とパスワードを使用してログオンする必要があります。  
  
> [!NOTE]
>  WCF サービスが承認に使用できる前に、ASP.NET の機能を使用してデータベースを読み込んでおく必要があります。  
  
 既存の ASP.NET Web サイトがメンバーシップ データベースが既にあるし、サービスは、同じユーザー名とパスワードで承認を使用する同じユーザーを有効にする場合は、メンバーシップ機能を使用することもできます。  
  
 メンバーシップ機能を使用して WCF サービスの詳細については、次を参照してください。[方法。ASP.NET メンバーシップ プロバイダーを使用して、](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)します。  
  
## <a name="aspnet-role-provider"></a>ASP.NET ロール プロバイダー  
 ASP.NET のもう 1 つの機能は、ロールを使用して承認を管理する機能です。 ASP.NET ロール プロバイダーには、ユーザーのロールを作成して、各ユーザー ロールまたはロールを割り当てるには、開発者ができます。 メンバーシップ プロバイダーは、データベースに格納されているロールと割り当てと、ASP.NET ロール プロバイダーの特定の実装によって提供されるツールを使用して設定できます。 として、メンバーシップ機能と WCF 開発者ことができます、情報を参照して、データベース内の役割サービスのユーザーを認証します。 たとえば、上記の `PrincipalPermissionAttribute` アクセス制御機構と組み合わせてロール プロバイダーを使用できます。  
  
 既存の ASP.NET ロール プロバイダー データベースがあり、WCF サービスで、同じ一連のルールとユーザーの割り当てを使用する場合は、ASP.NET ロール プロバイダーを使用することもできます。  
  
 ロール プロバイダー機能の使用に関する詳細については、次を参照してください。[方法。ASP.NET ロール プロバイダーを使用して、サービスと](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)します。  
  
## <a name="authorization-manager"></a>承認マネージャー  
 別の機能は、クライアントを承認するために、ASP.NET ロール プロバイダーと、承認マネージャー (AzMan) を結合します。 ASP.NET では、Web サービスをホストするサービスに承認が AzMan を通じて行われるように AzMan は、アプリケーションに統合できます。 ASP.NET ロール マネージャー API を使用すると、アプリケーション ロールの管理を追加、ロールからユーザーを削除し、ロール メンバーシップのチェックを提供しますが、名前付きのタスクまたは操作を実行する権限があるかどうかを照会することはできません。 AzMan を使用すると、個々の操作を定義してタスクに結合できます。 AZMan では、ロールのチェックだけでなく、ユーザーがタスクを実行できるかどうかをチェックすることもできます。 ロールの割り当てとタスクの承認は、アプリケーションの外部で構成することも、アプリケーション内でプログラムによって実行することもできます。 AzMan 管理 Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインにより、管理者は、ロールが実行時に実行できるタスクを変更したり、ユーザーのロール メンバーシップを管理したりできます。  
  
 既に既存の AzMan インストールにアクセスする AzMan とロール プロバイダーの組み合わせの機能を使用してサービス ユーザーを承認する場合にも、AzMan と ASP.NET ロール プロバイダーを使用できます。  
  
 AzMan と ASP.NET ロール プロバイダーの詳細については、次を参照してください[How To:。ASP.NET 2.0 で Authorization Manager (AzMan) 使用](https://go.microsoft.com/fwlink/?LinkId=88951)します。 AzMan とロール プロバイダーを使用して WCF サービスの詳細については、次を参照してください。[方法。サービスと ASP.NET の承認マネージャー ロール プロバイダーを使用して](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)します。  
  
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
