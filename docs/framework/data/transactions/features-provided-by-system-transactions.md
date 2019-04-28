---
title: System.Transactions により提供される機能
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 6fc20f8249f37f69689fb3fc6b3144792badad3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793693"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions により提供される機能
ここでは、<xref:System.Transactions> 名前空間により提供される機能を使用して、独自のトランザクション アプリケーションとリソース マネージャーを作成する方法について説明します。 特に、1 つまたは複数の参加要素を含むローカル トランザクションまたは分散トランザクションを作成し、参加する方法について説明します。  
  
## <a name="overview-of-systemtransactions"></a>System.Transactions の概要  
 <xref:System.Transactions> 名前空間内のクラスにより提供されるインフラストラクチャは、SQL Server、ADO.NET、メッセージ キュー (MSMQ)、および Microsoft 分散トランザクション コーディネーター (MSDTC) で開始されたトランザクションをサポートすることにより、トランザクション プログラミングを単純で効率的なものにします。 <xref:System.Transactions>名前空間には明示的なプログラミング モデルに基づく、<xref:System.Transactions.Transaction>クラスだけでなく、暗黙的なプログラミング モデルを使用して、<xref:System.Transactions.TransactionScope>トランザクションを自動的にインフラストラクチャによって管理するクラス。 これら 2 つのモデルを使用してトランザクション アプリケーションを作成する方法の詳細については、次を参照してください。[トランザクション アプリケーションの作成](../../../../docs/framework/data/transactions/writing-a-transactional-application.md)です。  
  
 <xref:System.Transactions> 名前空間には、リソース マネージャーを実装するための型も用意されています。 リソース マネージャーは、トランザクションで使用する永続性データまたは揮発性データを管理し、トランザクション マネージャーと連携してアプリケーションの原子性と分離を保証します。 <xref:System.Transactions> インフラストラクチャにより提供されるトランザクション マネージャーは、複数の揮発性リソースまたは単一の永続性リソースに関連するトランザクションをサポートします。 リソース マネージャーの実装の詳細については、次を参照してください。[リソース マネージャーの実装](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md)します。  
  
 また、トランザクション マネージャーは、他の永続的リソース マネージャーがそれ自体をトランザクションに参加させた場合に、DTC などのディスク ベースのトランザクション マネージャーと連携して、ローカル トランザクションを分散トランザクションへと透過的にエスカレートします。 <xref:System.Transactions> インフラストラクチャでは、主に 2 つの方法でパフォーマンスを向上させています。  
  
- ダイナミック エスカレーション。これにより、トランザクションが複数の分散リソースにわたる場合、<xref:System.Transactions> インフラストラクチャが MSDTC のみを使用すること保証します。 ダイナミック エスカレーションの詳細については、 参照してください[Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md)トピック。  
  
- 昇格可能参加リスト。これにより、データベースなどのリソースが、トランザクションに参加している唯一のエンティティである場合に、トランザクションの所有権を取得できます。 その後、必要に応じて、<xref:System.Transactions> インフラストラクチャがトランザクションの管理を MSDTC にエスカレートすることもできます。 これにより、MSDTC の使用頻度をさらに減らすことができます。 昇格可能参加リストは、トピックで詳しく説明されて[Single Phase Commit and Promotable Single Phase Notification を使用した最適化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)します。  
  
 <xref:System.Transactions> 名前空間は、AllowPartiallyTrustedCallers (APTCA)、DistributedTransactionPermission (DTP)、および完全な信頼の 3 つの信頼レベルを定義し、公開するリソースの種類へのアクセスを制限しています。 詳細については、さまざまな信頼レベルを参照してください[リソースへのアクセスのセキュリティ信頼レベル](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
### <a name="writing-a-transactional-application"></a>トランザクション アプリケーションの作成  
 <xref:System.Transactions> 名前空間には、トランザクション アプリケーションを作成するための 2 つのモデルが用意されています。 [トランザクション スコープを使用して、暗黙のトランザクションを実装する](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)について説明しますが、どのように<xref:System.Transactions>名前空間を使用して暗黙的なトランザクションの作成をサポートしている、<xref:System.Transactions.TransactionScope>クラス。  
  
 [CommittableTransaction を使用した明示的なトランザクションを実装する](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)について説明しますが、どのように<xref:System.Transactions>名前空間を使用して明示的なトランザクションの作成をサポートしている、<xref:System.Transactions.CommittableTransaction>クラス。  
  
 トランザクション アプリケーションの作成をカバーする他のトピックでは、次を参照してください。[トランザクション アプリケーションの作成](../../../../docs/framework/data/transactions/writing-a-transactional-application.md)です。  
  
### <a name="implementing-a-resource-manager"></a>リソース マネージャーの実装  
 トランザクションに参加できるリソース マネージャーを実装するを参照してください。[リソース マネージャーの実装](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md)します。 ここでは、リソースの参加、トランザクションのコミット、障害後の回復、および最適化のベスト プラクティスについて説明しています。
