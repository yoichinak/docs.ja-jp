---
title: プリンシパル オブジェクトと ID オブジェクト
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5b74f2608022d48dbd7e63e4ddf6112c333e3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018746"
---
# <a name="principal-and-identity-objects"></a>プリンシパル オブジェクトと ID オブジェクト
マネージ コードには、id またはでプリンシパルの役割を検出できる、<xref:System.Security.Principal.IPrincipal>への参照を含むオブジェクトを<xref:System.Security.Principal.IIdentity>オブジェクト。 ID オブジェクトとプリンシパル オブジェクトは、ユーザーとグループ アカウントのようななじみのある概念と比較するとわかりやすいでしょう。 ほとんどのネットワーク環境で、ユーザー アカウントは人またはプログラムを表し、グループ アカウントは特定のカテゴリのユーザーやそのユーザーが所有する権限を表します。 同様に、.NET Framework の ID オブジェクトはユーザーを表し、ロールはメンバーシップやセキュリティ コンテキストを表します。 .NET Framework で、プリンシパル オブジェクトは、ID オブジェクトとロールの両方をカプセル化します。 .NET Framework アプリケーションは、ID または一般的にはロール メンバーシップに基づいてプリンシパルに権限を付与します。  
  
## <a name="identity-objects"></a>ID オブジェクト  
 ID オブジェクトは、検証対象のユーザーまたはエンティティに関する情報をカプセル化します。 ID オブジェクトの最も基本的なレベルには名前と認証の種類が含まれます。 名前はユーザー名または Windows アカウント名、認証の種類は、サポートされるログオン プロトコル (Kerberos V5 など) かカスタム値になります。 .NET Framework の定義、<xref:System.Security.Principal.GenericIdentity>のほとんどのカスタム ログオン シナリオやより特化されたために使用できるオブジェクト<xref:System.Security.Principal.WindowsIdentity>Windows 認証に依存するアプリケーションの場合に使用できるオブジェクト。 また、カスタム ユーザー情報をカプセル化する独自の ID クラスを定義することもできます。  
  
 <xref:System.Security.Principal.IIdentity>インターフェイスは、名前と認証の種類、Kerberos V5 や NTLM などにアクセスするためのプロパティを定義します。 すべての **Identity** クラスでは **IIdentity** インターフェイスが実装されます。 **ID** オブジェクトと、スレッドが現在実行している Windows NT プロセス トークンの間に関係は必要ありません。 ただし、**ID** オブジェクトが **WindowsIdentity** オブジェクトである場合、ID は Windows NT セキュリティ トークンを表すと見なされます。  
  
## <a name="principal-objects"></a>プリンシパル オブジェクト  
 プリンシパル オブジェクトは、コードが実行されているセキュリティ コンテキストを表します。 ロールベースのセキュリティを実装するアプリケーションは、プリンシパル オブジェクトに関連付けられたロールに基づいて権限を付与します。 Id オブジェクトと同様に、.NET Framework には、<xref:System.Security.Principal.GenericPrincipal>オブジェクトと<xref:System.Security.Principal.WindowsPrincipal>オブジェクト。 独自のカスタム プリンシパル クラスを定義することもできます。  
  
 <xref:System.Security.Principal.IPrincipal>インターフェイスは、関連付けられたにアクセスするためのプロパティを定義します**Identity**オブジェクトで、ユーザーが識別されるかどうかを決定するためのメソッドをおよび、**プリンシパル**オブジェクトのメンバーである、。特定のロール。 すべての**プリンシパル** クラスは、**IPrincipal** インターフェイスの他に、必要なその他のプロパティとメソッドを実装しています。 たとえば、共通言語ランタイムでは **WindowsPrincipal** クラスが提供されますが、これは Windows NT または Windows 2000 グループ メンバーシップをロールにマッピングする追加機能を実装します。  
  
 A**プリンシパル**オブジェクト呼び出しコンテキストにバインドされます (<xref:System.Runtime.Remoting.Messaging.CallContext>) アプリケーション ドメイン内のオブジェクト (<xref:System.AppDomain>)。 常に既定の呼び出しコンテキストはそれぞれ新しい **AppDomain** を使用して作成されるため、**プリンシパル** オブジェクトを受け入れる呼び出しコンテキストが常に存在します。 新しいスレッドが作成されるとき、そのスレッドの **CallContext** オブジェクトも作成されます。 **プリンシパル** オブジェクトの参照は、作成スレッドから新しいスレッドの **CallContext** に自動的にコピーされます。 スレッドの作成者に所属する**プリンシパル** オブジェクトをランタイムが判別できない場合は、**プリンシパル** オブジェクトと **ID** オブジェクトの作成で既定のポリシーに従います。  
  
 構成可能なアプリケーション ドメイン固有のポリシーによって、新しいアプリケーション ドメインに関連付ける**プリンシパル** オブジェクトの種類を決める規則が定義されます。 セキュリティ ポリシーによって許可される場合、ランタイムは、現在の実行スレッドに関連するオペレーティング システム トークンを反映する**プリンシパル** オブジェクトと **ID** オブジェクトを作成できます。 ランタイムは既定では、認証されていないユーザーを表す**プリンシパル** オブジェクトと **ID** オブジェクトを使用します。 このような既定の**プリンシパル** オブジェクトと **ID** オブジェクトは、コードがアクセスを試行するまでランタイムによって作成されることはありません。  
  
 信頼されるコードが、アプリケーション ドメインを作成して、アプリケーション ドメイン ポリシーを作成できます。このポリシーによって、既定の**プリンシパル** オブジェクトと **ID** オブジェクトのコンストラクトが制御されます。 このアプリケーション ドメイン固有ポリシーは、そのアプリケーション ドメインのすべての実行スレッドに適用されます。 管理対象外の信頼されたホストは本質的に、このポリシーを設定する権限を持ちますが、このポリシー設定を管理対象のコードが必要、<xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>ドメイン ポリシーを制御するためです。  
  
 **プリンシパル** オブジェクトを同じプロセス内 (つまり同じコンピューター上の) アプリケーション ドメイン間で送信するとき、リモート処理インフラストラクチャが、呼び出し元のコンテキストに関連する**プリンシパル** オブジェクトへの参照を呼び出し先のコンテキストにコピーします。  
  
## <a name="see-also"></a>関連項目

- [方法: WindowsPrincipal オブジェクトを作成します。](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)
- [方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成します。](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)
- [プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)
- [偽装と復帰](../../../docs/standard/security/impersonating-and-reverting.md)
- [ロール ベースのセキュリティ](../../../docs/standard/security/role-based-security.md)
- [セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)
