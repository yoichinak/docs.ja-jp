---
title: アクセス制御機構
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185499"
---
# <a name="access-control-mechanisms"></a>アクセス制御機構
アクセスは、WCF (WCF) で複数の方法で制御できます。 ここでは、正しい機構を選択して使用できるように、さまざまな機構について簡単に説明し、各機構を使用するタイミングに関するヒントを提供します。 ここでは、アクセス テクノロジを単純なものから順に示します。 最も単純なのは <xref:System.Security.Permissions.PrincipalPermissionAttribute> で、最も複雑なのは ID モデルです。  
  
 これらのメカニズムに加えて、 WCF を使用した偽装と委任については、「[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)」で説明します。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> は、サービス メソッドへのアクセスを制限するために使用します。 属性がメソッドに適用される場合、この属性を使用して、Windows グループまたはASP.NETロール内の特定の呼び出し元の ID またはメンバーシップを要求できます。 クライアントが、X.509 証明書を使用して認証された場合は、サブジェクト名と証明書の拇印で構成されるプライマリ ID がクライアントに割り当てられています。  
  
 サービスのユーザーが常に、サービスが実行されているものと同じ Windows ドメインのメンバーである場合、サービスが実行されているコンピューター上のリソースへのアクセスを制御するには、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用します。 指定したアクセス レベル (なし、読み取り専用、または読み取りと書き込みなど) を持つ Windows グループを簡単に作成できます。  
  
 属性の使用の詳細については、「方法[: クラスを使用してアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)」を参照してください。 ID の詳細については、「[サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET メンバーシップ プロバイダー  
 ASP.NETの機能は、メンバーシップ プロバイダーです。 メンバーシップ プロバイダーは、厳密にはアクセス制御機構ではありませんが、これを使用すると、サービスのエンドポイントにアクセスできる ID のセットを制限することで、サービスへのアクセスを制御できます。 メンバーシップ機能には、ユーザー名/パスワードの組み合わせを設定できるデータベースが含まれています。この組み合わせによって、Web サイトのユーザーはサイトのアカウントを確立できます。 メンバーシップ プロバイダーを使用するサービスにアクセスするには、ユーザーが自分のユーザー名とパスワードを使用してログオンする必要があります。  
  
> [!NOTE]
> WCF サービスが承認目的で使用できるようにするには、まず、ASP.NET機能を使用してデータベースを設定する必要があります。  
  
 既存の ASP.NET Web サイトのメンバーシップ データベースが既に存在し、同じユーザーが同じユーザー名とパスワードで承認されたサービスを使用できるようにする場合にも、メンバーシップ機能を使用できます。  
  
 WCF サービスでメンバーシップ機能を使用する方法の詳細については、「[方法 : ASP.NET メンバーシップ プロバイダーを使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)する 」を参照してください。  
  
## <a name="aspnet-role-provider"></a>ASP.NET ロール プロバイダー  
 ASP.NETのもう 1 つの機能は、ロールを使用して承認を管理できることです。 ASP.NET ロール プロバイダーを使用すると、開発者はユーザーのロールを作成し、各ユーザーをロールに割り当てることができます。 メンバーシップ プロバイダーと同様に、ロールと割り当てはデータベースに格納され、ASP.NET ロール プロバイダーの特定の実装によって提供されるツールを使用して設定できます。 メンバーシップ機能と同様に、WCF 開発者はデータベース内の情報を使用して、ロールによってサービス ユーザーを承認できます。 たとえば、上記の `PrincipalPermissionAttribute` アクセス制御機構と組み合わせてロール プロバイダーを使用できます。  
  
 既存のASP.NET ロール プロバイダー データベースがあり、WCF サービスで同じルールとユーザー割り当てのセットを使用する場合は、ASP.NET ロール プロバイダーを使用することもできます。  
  
 ロール プロバイダ機能の使用方法の詳細については、「[方法 : サービスでASP.NET ロール プロバイダを使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)する 」を参照してください。  
  
## <a name="authorization-manager"></a>承認マネージャー  
 もう 1 つの機能は、承認マネージャ (AzMan) とASP.NET ロール プロバイダを組み合わせてクライアントを承認します。 ASP.NETが Web サービスをホストする場合、AzMan をアプリケーションに統合して、AzMan を通じてサービスへの承認を行うことができます。 ロール マネージャーASP.NET、アプリケーション ロールの管理、ロールへのユーザーの追加と削除、ロール メンバーシップの確認を行う API を提供しますが、ユーザーが名前付きタスクまたは操作の実行を承認されているかどうかを照会することはできません。 AzMan を使用すると、個々の操作を定義してタスクに結合できます。 AZMan では、ロールのチェックだけでなく、ユーザーがタスクを実行できるかどうかをチェックすることもできます。 ロールの割り当てとタスクの承認は、アプリケーションの外部で構成することも、アプリケーション内でプログラムによって実行することもできます。 AzMan 管理 Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインにより、管理者は、ロールが実行時に実行できるタスクを変更したり、ユーザーのロール メンバーシップを管理したりできます。  
  
 既存の AzMan インストールにすでにアクセス権があり、AzMan/ロールプロバイダーの組み合わせの機能を使用してサービスユーザーを承認する場合は、AzMan とASP.NETロールプロバイダーを使用することもできます。  
  
 AzMan とASP.NETロール プロバイダの詳細については、「[方法: ASP.NET 2.0 で承認マネージャ (AzMan) を使用](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))する」を参照してください。 AzMan と WCF サービスのロール プロバイダーの使用の詳細については、「[方法 : サービスでASP.NET承認マネージャー ロール プロバイダーを使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)する 」を参照してください。  
  
## <a name="identity-model"></a>ID モデル  
 ID モデルは、クライアントを承認するためのクレームとポリシーを管理できるようにする API のセットです。 ID モデルを使用すると、呼び出し元がサービスに対するそれ自体の認証に使用した資格情報に含まれるすべてのクレームを調べ、それらをサービスのポリシー セットと比較し、この比較に基づいてアクセスを許可または拒否できます。  
  
 アクセスを許可する前に、微調整と、特定の条件を設定する機能が必要な場合は、ID モデルを使用します。 たとえば、<xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用した場合、条件は、ユーザー ID が認証され、それが特定のロールに属するということだけになります。 これに対し、ID モデルを使用すると、ドキュメントの参照を許可されるにはユーザーが 18 才以上であり、有効な運転免許証を所有している必要があることを明確に示すポリシーを作成できます。  
  
 ID モデルのクレームに基づくアクセス制御の恩恵を受けることができる例として、発行済みトークンのシナリオでフェデレーション資格情報を使用する場合が挙げられます。 フェデレーションと発行済みトークンの詳細については、「[フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。  
  
 ID モデルの詳細については、「ID モデルを[使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [方法: PrincipalPermissionAttribute クラスでアクセスを制限する](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [方法 : ASP.NET のロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [方法 : ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
