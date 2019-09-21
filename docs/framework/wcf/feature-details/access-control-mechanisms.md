---
title: アクセス制御機構
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 14f348300d8ab9276a86b4cf8d91823d39b9aba3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964997"
---
# <a name="access-control-mechanisms"></a>アクセス制御機構
Windows Communication Foundation (WCF) を使用して、いくつかの方法でアクセスを制御できます。 ここでは、正しい機構を選択して使用できるように、さまざまな機構について簡単に説明し、各機構を使用するタイミングに関するヒントを提供します。 ここでは、アクセス テクノロジを単純なものから順に示します。 最も単純なのは <xref:System.Security.Permissions.PrincipalPermissionAttribute> で、最も複雑なのは ID モデルです。  
  
 これらのメカニズムに加え、WCF における偽装と委任が [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md) で説明されています。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを制限するために使用します。 属性をメソッドに適用すると、特定の呼び出し元の id、または Windows グループまたは ASP.NET ロールのメンバーシップを要求するために使用できます。 クライアントが、X.509 証明書を使用して認証された場合は、サブジェクト名と証明書の拇印で構成されるプライマリ ID がクライアントに割り当てられています。  
  
 サービスのユーザーが常に、サービスが実行されているものと同じ Windows ドメインのメンバーである場合、サービスが実行されているコンピューター上のリソースへのアクセスを制御するには、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用します。 指定したアクセス レベル (なし、読み取り専用、または読み取りと書き込みなど) を持つ Windows グループを簡単に作成できます。  
  
 属性の使用方法の詳細について[は、「方法:PrincipalPermissionAttribute クラス](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)を使用してアクセスを制限します。 Id の詳細については、「[サービス id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET メンバーシップ プロバイダー  
 ASP.NET の機能は、メンバーシッププロバイダーです。 メンバーシップ プロバイダーは、厳密にはアクセス制御機構ではありませんが、これを使用すると、サービスのエンドポイントにアクセスできる ID のセットを制限することで、サービスへのアクセスを制御できます。 メンバーシップ機能には、ユーザー名/パスワードの組み合わせを設定できるデータベースが含まれています。この組み合わせによって、Web サイトのユーザーはサイトのアカウントを確立できます。 ユーザーがメンバーシップ プロバイダーを使用するサービスにアクセスするには、自分の名前とパスワードを使用してログオンする必要があります。  
  
> [!NOTE]
> まず、ASP.NET 機能を使用してデータベースにデータを設定してから、WCF サービスが承認のためにそれを使用できるようにする必要があります。  
  
 また、既存の ASP.NET Web サイトからメンバーシップデータベースを既に所有していて、同じユーザー名とパスワードで承認されたサービスを同じユーザーが使用できるようにする場合は、メンバーシップ機能を使用することもできます。  
  
 WCF サービスでメンバーシップ機能を使用する方法の詳細について[は、次を参照してください。ASP.NET メンバーシッププロバイダー](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)を使用します。  
  
## <a name="aspnet-role-provider"></a>ASP.NET ロール プロバイダー  
 ASP.NET のもう1つの機能は、ロールを使用して承認を管理する機能です。 ASP.NET ロールプロバイダーを使用すると、開発者はユーザーのロールを作成し、各ユーザーをロールまたはロールに割り当てることができます。 メンバーシッププロバイダーと同様に、ロールと割り当てはデータベースに格納され、ASP.NET ロールプロバイダーの特定の実装によって提供されるツールを使用して設定できます。 メンバーシップ機能と同様に、WCF 開発者はデータベース内の情報を使用して、サービスユーザーをロール別に承認することができます。 たとえば、上記の `PrincipalPermissionAttribute` アクセス制御機構と組み合わせてロール プロバイダーを使用できます。  
  
 また、既存の ASP.NET ロールプロバイダーデータベースがあり、WCF サービスで同じルールとユーザー割り当てのセットを使用する場合は、ASP.NET ロールプロバイダーを使用することもできます。  
  
 ロールプロバイダー機能の使用方法の詳細について[は、「」を参照してください。ASP.NET ロールプロバイダーとサービス](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)を使用します。  
  
## <a name="authorization-manager"></a>承認マネージャー  
 もう1つの機能は、承認マネージャー (AzMan) と ASP.NET 役割プロバイダーを組み合わせてクライアントを承認します。 ASP.NET が Web サービスをホストする場合、AzMan をアプリケーションに統合して、サービスへの承認が AzMan を介して行われるようにすることができます。 ASP.NET ロールマネージャーには、アプリケーションロールの管理、ロールからのユーザーの追加と削除、ロールのメンバーシップの確認を行うことができる API が用意されていますが、ユーザーが名前付きタスクまたは操作を実行する権限を持っているかどうかを照会することはできません。 AzMan を使用すると、個々の操作を定義してタスクに結合できます。 AZMan では、ロールのチェックだけでなく、ユーザーがタスクを実行できるかどうかをチェックすることもできます。 ロールの割り当てとタスクの承認は、アプリケーションの外部で構成することも、アプリケーション内でプログラムによって実行することもできます。 AzMan 管理 Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインにより、管理者は、ロールが実行時に実行できるタスクを変更したり、ユーザーのロール メンバーシップを管理したりできます。  
  
 また、既存の AzMan インストールへのアクセス権を既に持っていて、AzMan/role プロバイダーの組み合わせの機能を使用してサービスユーザーを承認する場合は、AzMan および ASP.NET ロールプロバイダーを使用することもできます。  
  
 AzMan および ASP.NET ロールプロバイダーの詳細については、 [「方法:ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=88951)で承認マネージャー (AzMan) を使用します。 WCF サービスの AzMan とロールプロバイダーの使用方法の詳細について[は、「」を参照してください。ASP.NET Authorization Manager ロールプロバイダーとサービス](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)を使用します。  
  
## <a name="identity-model"></a>ID モデル  
 ID モデルは、クライアントを承認するためのクレームとポリシーを管理できるようにする API のセットです。 ID モデルを使用すると、呼び出し元がサービスに対するそれ自体の認証に使用した資格情報に含まれるすべてのクレームを調べ、それらをサービスのポリシー セットと比較し、この比較に基づいてアクセスを許可または拒否できます。  
  
 アクセスを許可する前に、微調整と、特定の条件を設定する機能が必要な場合は、ID モデルを使用します。 たとえば、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用した場合、条件は、ユーザー ID が認証され、それが特定のロールに属するということだけになります。 これに対し、ID モデルを使用すると、ドキュメントの参照を許可されるにはユーザーが 18 才以上であり、有効な運転免許証を所有している必要があることを明確に示すポリシーを作成できます。  
  
 ID モデルのクレームに基づくアクセス制御の恩恵を受けることができる例として、発行済みトークンのシナリオでフェデレーション資格情報を使用する場合が挙げられます。 フェデレーションと発行済みトークンの詳細については、「[フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。  
  
 Id モデルの詳細については、「 [Id モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [方法: PrincipalPermissionAttribute クラスを使用してアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [方法: ASP.NET ロールプロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [方法: ASP.NET Authorization Manager ロールプロバイダーをサービスと共に使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
