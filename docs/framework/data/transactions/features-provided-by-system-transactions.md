---
title: System.Transactions により提供される機能
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: c3ef924edf34ae19be9eace85aaee5340025de7d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205965"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions により提供される機能
ここでは、<xref:System.Transactions> 名前空間により提供される機能を使用して、独自のトランザクション アプリケーションとリソース マネージャーを作成する方法について説明します。 特に、1 つまたは複数の参加要素を含むローカル トランザクションまたは分散トランザクションを作成し、参加する方法について説明します。  
  
## <a name="overview-of-systemtransactions"></a>System.Transactions の概要  
 <xref:System.Transactions> 名前空間内のクラスにより提供されるインフラストラクチャは、SQL Server、ADO.NET、メッセージ キュー (MSMQ)、および Microsoft 分散トランザクション コーディネーター (MSDTC) で開始されたトランザクションをサポートすることにより、トランザクション プログラミングを単純で効率的なものにします。 <xref:System.Transactions>名前空間には明示的なプログラミング モデルに基づく、<xref:System.Transactions.Transaction>クラスだけでなく、暗黙的なプログラミング モデルを使用して、<xref:System.Transactions.TransactionScope>トランザクションを自動的にインフラストラクチャによって管理するクラス。 これら2つのモデルを使用してトランザクションアプリケーションを作成する方法の詳細については、「[トランザクションアプリケーションの](writing-a-transactional-application.md)作成」を参照してください。  
  
 <xref:System.Transactions> 名前空間には、リソース マネージャーを実装するための型も用意されています。 リソース マネージャーは、トランザクションで使用する永続性データまたは揮発性データを管理し、トランザクション マネージャーと連携してアプリケーションの原子性と分離を保証します。 <xref:System.Transactions> インフラストラクチャにより提供されるトランザクション マネージャーは、複数の揮発性リソースまたは単一の永続性リソースに関連するトランザクションをサポートします。 リソースマネージャーの実装の詳細については、「[リソースマネージャーの実装](implementing-a-resource-manager.md)」を参照してください。  
  
 また、トランザクション マネージャーは、他の永続的リソース マネージャーがそれ自体をトランザクションに参加させた場合に、DTC などのディスク ベースのトランザクション マネージャーと連携して、ローカル トランザクションを分散トランザクションへと透過的にエスカレートします。 <xref:System.Transactions> インフラストラクチャでは、主に 2 つの方法でパフォーマンスを向上させています。  
  
- ダイナミック エスカレーション。これにより、トランザクションが複数の分散リソースにわたる場合、<xref:System.Transactions> インフラストラクチャが MSDTC のみを使用すること保証します。 ダイナミック エスカレーションの詳細については、 「[トランザクション管理のエスカレーション](transaction-management-escalation.md)」を参照してください。  
  
- 昇格可能参加リスト。これにより、データベースなどのリソースが、トランザクションに参加している唯一のエンティティである場合に、トランザクションの所有権を取得できます。 その後、必要に応じて、<xref:System.Transactions> インフラストラクチャがトランザクションの管理を MSDTC にエスカレートすることもできます。 これにより、MSDTC の使用頻度をさらに減らすことができます。 昇格可能な参加リストの詳細については、「[単一フェーズコミットと昇格可能単一フェーズ通知を使用した最適化](optimization-spc-and-promotable-spn.md)」を参照してください。  
  
 <xref:System.Transactions> 名前空間は、AllowPartiallyTrustedCallers (APTCA)、DistributedTransactionPermission (DTP)、および完全な信頼の 3 つの信頼レベルを定義し、公開するリソースの種類へのアクセスを制限しています。 さまざまな信頼レベルの詳細については、「[リソースにアクセスする場合のセキュリティの信頼レベル](security-trust-levels-in-accessing-resources.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
### <a name="writing-a-transactional-application"></a>トランザクション アプリケーションの作成  
 <xref:System.Transactions> 名前空間には、トランザクション アプリケーションを作成するための 2 つのモデルが用意されています。 [トランザクションスコープを使用した暗黙のトランザクション](implementing-an-implicit-transaction-using-transaction-scope.md)の<xref:System.Transactions>実装では、 <xref:System.Transactions.TransactionScope>クラスを使用した暗黙的なトランザクションの作成を名前空間でサポートする方法について説明します。  
  
 [Committabletransaction を使用した明示的なトランザクションの実装](implementing-an-explicit-transaction-using-committabletransaction.md)では、 <xref:System.Transactions> <xref:System.Transactions.CommittableTransaction>クラスを使用した明示的なトランザクションの作成を名前空間がサポートする方法を説明します。  
  
 トランザクションアプリケーションの作成に関するその他のトピックについては、「[トランザクションアプリケーションの作成](writing-a-transactional-application.md)」を参照してください。  
  
### <a name="implementing-a-resource-manager"></a>リソース マネージャーの実装  
 トランザクションに参加できるリソースマネージャーを実装するには、「[リソースマネージャーの実装](implementing-a-resource-manager.md)」を参照してください。 ここでは、リソースの参加、トランザクションのコミット、障害後の回復、および最適化のベスト プラクティスについて説明しています。
