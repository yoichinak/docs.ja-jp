---
title: リソースへのアクセス時のセキュリティ信頼レベル
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 8e7d632c361ea73cb65668e43506d9e1128d31ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793602"
---
# <a name="security-trust-levels-in-accessing-resources"></a>リソースへのアクセス時のセキュリティ信頼レベル
ここでは、<xref:System.Transactions> が公開するリソースの種類に対して、アクセスがどのように制限されるかについて説明します。  
  
 <xref:System.Transactions> には、主に 3 つの信頼レベルがあります。 信頼レベルは、<xref:System.Transactions> が公開するリソースの種類と、そのリソースにアクセスするために必要な信頼レベルに基づいて定義されます。 <xref:System.Transactions> がアクセスを提供するリソースは、システム メモリ、プロセス全体の共有リソース、およびシステム全体のリソースです。 次のようなレベルがあります。  
  
- **AllowPartiallyTrustedCallers** (APTCA) 1 つのアプリケーション ドメイン内でトランザクションを使用するアプリケーション。  
  
- **DistributedTransactionPermission** (DTP) 分散トランザクションを使用するアプリケーション。  
  
- 永続性リソース、構成管理アプリケーション、およびレガシ相互運用アプリケーション用の完全信頼。  
  
> [!NOTE]
>  偽装されたコンテキストで参加インターフェイスを呼び出さないでください。  
  
## <a name="trust-levels"></a>信頼レベル  
  
### <a name="aptca-partial-trust"></a>APTCA (部分的信頼)  
 <xref:System.Transactions>付いているために、部分的に信頼されたコードによってアセンブリを呼び出すことが、 **AllowPartiallyTrustedCallers**属性 (APTCA)。 この属性は基本的に、暗黙的な削除<xref:System.Security.Permissions.SecurityAction.LinkDemand>の**FullTrust**アクセス許可が設定されているそれ以外の場合に自動的に配置の種類ごとのパブリックにアクセスできる各メソッドにします。 ただし、種類やメンバーによっては、さらに強力なアクセス許可が必要となります。  
  
 APTCA 属性により、アプリケーションは単一のアプリケーション ドメイン内で、部分的に信頼してトランザクションを使用できます。 これにより、エラー処理で使用できる非エスカレーション トランザクションと揮発性の参加リストが有効になります。 こうした例の 1 つが、トランザクション処理されたハッシュ テーブルとそれを使用するアプリケーションです。 単一トランザクション下で、ハッシュ テーブルに対してデータを追加および削除できます。 トランザクションが後でロール バックされた場合、そのトランザクション下でハッシュ テーブルに加えられたすべての変更を元に戻すことができます。  
  
### <a name="distributedtransactionpermission-dtp"></a>DTP (DistributedTransactionPermission)  
 MSDTC で管理されるように <xref:System.Transactions> トランザクションがエスカレーションされた場合、<xref:System.Transactions> は分散トランザクションを作成するために <xref:System.Transactions.DistributedTransactionPermission> (DTP) を要求します。 これは、(シリアル化や追加の永続参加リストなどを介して) トランザクションをエスカレーションするコードに DTP を付与する必要があることを意味します。 <xref:System.Transactions> トランザクションを最初に作成したコードでは、このアクセス許可を必ずしも所有する必要はありません。  
  
### <a name="fulltrust-link-demands"></a>FullTrust リンク要求  
 このアクセス許可レベルは、永続性リソースに書き込むアプリケーションを制限することを目的としています。 エラー発生時に、アプリケーションはトランザクション マネージャーにより回復し、トランザクションの最終結果を判定して永続的なデータを更新できるようにする必要があります。 この種類のアプリケーションは、永続的リソース マネージャーと呼ばれています。 この種類のアプリケーションの典型的な例が SQL です。  
  
 回復を有効にするため、この種類のアプリケーションにはシステム リソースを永続的に消費する機能があります。 これは、トランザクションに参加しているすべての永続的リソース マネージャーが結果を受信したことを確認するまで、回復可能なトランザクション マネージャーはコミットしたトランザクションを記憶する必要があるためです。 したがって、この種類のアプリケーションには完全な信頼が必要です。完全な信頼レベルが付与されない限り、実行しないでください。  
  
 永続参加リストと回復の詳細については、次を参照してください。、[トランザクションの参加者として参加リソース](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)と[Performing Recovery](../../../../docs/framework/data/transactions/performing-recovery.md)トピック。  
  
 COM+ とのレガシ相互運用を実行するアプリケーションにも、完全な信頼が必要です。  
  
 型の一覧を次で装飾されているため、信頼されたコードの一部によって呼び出し可能なメンバー、 **FullTrust**宣言セキュリティ属性。  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 直前の呼び出し元が所有する必要がのみ、 **FullTrust**上記の型またはメソッドを使用するアクセス許可セットします。
