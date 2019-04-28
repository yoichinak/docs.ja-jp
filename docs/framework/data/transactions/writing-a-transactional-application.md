---
title: トランザクション アプリケーションの作成
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793492"
---
# <a name="writing-a-transactional-application"></a>トランザクション アプリケーションの作成
トランザクション アプリケーションのプログラマは、<xref:System.Transactions> 名前空間に用意されている 2 つのプログラミング モデルを活用して、トランザクションを作成できます。 使用して、明示的なプログラミング モデルを利用することができます、<xref:System.Transactions.Transaction>クラス、または暗黙的なプログラミング モデルでのトランザクションは自動的に管理のインフラストラクチャでを使用して、<xref:System.Transactions.TransactionScope>クラス。 開発のため、暗黙のトランザクション モデルを使用することをお勧めします。 トランザクション スコープの使用方法の詳細を見つけることができます、 [Implementing an Implicit Transaction のトランザクション スコープを使用して](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)トピック。  
  
 両モデルとも、プログラムが整合性の取れた状態に達した時点で、トランザクションのコミットをサポートします。 コミットが成功すると、トランザクションは永続的にコミットされます。 コミットが失敗すると、トランザクションは中止されます。 アプリケーション プログラムがトランザクションを完了できない場合は、トランザクションを中止してその処理内容を取り消すことを試みます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
### <a name="creating-a-transaction"></a>トランザクションの作成  
 <xref:System.Transactions> 名前空間には、トランザクションを作成する 2 つのモデルが用意されています。 これらのモデルは、以下のトピックで取り上げられています。  
  
 [トランザクション スコープを使用した暗黙的なトランザクションの実装](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なトランザクションの作成について説明します。  
  
 [CommittableTransaction を使用した明示的なトランザクションの実装](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.CommittableTransaction> クラスを使用した明示的なトランザクションの作成について説明します。  
  
### <a name="escalating-transaction-management"></a>トランザクション管理のエスカレート  
 トランザクションが別のアプリケーション ドメインにあるリソースにアクセスする必要がある場合、または別の永続的なリソース マネージャーに参加する場合は、トランザクションが MSDTC によって管理されるよう自動的にエスカレートされます。 トランザクションのエスカレーションの詳細については、 [Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md)トピック。  
  
### <a name="concurrency"></a>コンカレンシー  
 トピック[DependentTransaction による同時実行を管理する](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md)を使用して非同期タスク間の同時実行の実現方法を示します、<xref:System.Transactions.DependentTransaction>クラス。  
  
### <a name="com-interop"></a>COM+ 相互運用  
 トピック[Enterprise Services および COM + トランザクションとの相互運用性](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)分散トランザクションを COM + トランザクションとの対話を作成する方法を示しています。  
  
### <a name="diagnostics"></a>診断  
 [診断トレース](../../../../docs/framework/data/transactions/diagnostic-traces.md)によって生成されるトレース コードを使用する方法について説明します、<xref:System.Transactions>インフラストラクチャ、アプリケーションでエラーをトラブルシューティングします。  
  
### <a name="working-within-aspnet"></a>ASP.NET 内での使用  
 [Using System.Transactions in ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md)トピックでは、正常を使用する方法について説明します<xref:System.Transactions>ASP.NET アプリケーション内で。
