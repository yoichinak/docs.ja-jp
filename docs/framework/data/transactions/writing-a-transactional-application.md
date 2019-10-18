---
title: トランザクション アプリケーションの作成
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205827"
---
# <a name="writing-a-transactional-application"></a>トランザクション アプリケーションの作成
トランザクション アプリケーションのプログラマは、<xref:System.Transactions> 名前空間に用意されている 2 つのプログラミング モデルを活用して、トランザクションを作成できます。 クラスを使用<xref:System.Transactions.Transaction>することによって明示的なプログラミングモデルを利用できます。また、 <xref:System.Transactions.TransactionScope>クラスを使用して、トランザクションがインフラストラクチャによって自動的に管理される暗黙的なプログラミングモデルを使用することもできます。 開発には、暗黙のトランザクションモデルを使用することをお勧めします。 トランザクションスコープの使用方法の詳細については、「[トランザクションスコープを使用した暗黙のトランザクションの実装](implementing-an-implicit-transaction-using-transaction-scope.md)」を参照してください。  
  
 両モデルとも、プログラムが整合性の取れた状態に達した時点で、トランザクションのコミットをサポートします。 コミットが成功すると、トランザクションは永続的にコミットされます。 コミットが失敗すると、トランザクションは中止されます。 アプリケーション プログラムがトランザクションを完了できない場合は、トランザクションを中止してその処理内容を取り消すことを試みます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
### <a name="creating-a-transaction"></a>トランザクションの作成  
 <xref:System.Transactions> 名前空間には、トランザクションを作成する 2 つのモデルが用意されています。 これらのモデルは、以下のトピックで取り上げられています。  
  
 [トランザクション スコープを使用した暗黙的なトランザクションの実装](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なトランザクションの作成について説明します。  
  
 [CommittableTransaction を使用した明示的なトランザクションの実装](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <xref:System.Transactions> 名前空間がサポートする、<xref:System.Transactions.CommittableTransaction> クラスを使用した明示的なトランザクションの作成について説明します。  
  
### <a name="escalating-transaction-management"></a>トランザクション管理のエスカレート  
 トランザクションが別のアプリケーション ドメインにあるリソースにアクセスする必要がある場合、または別の永続的なリソース マネージャーに参加する場合は、トランザクションが MSDTC によって管理されるよう自動的にエスカレートされます。 トランザクションのエスカレーションについては、「[トランザクション管理のエスカレーション](transaction-management-escalation.md)」を参照してください。  
  
### <a name="concurrency"></a>コンカレンシー  
 「 [Dependenttransaction による同時実行の管理](managing-concurrency-with-dependenttransaction.md)」のトピックでは、 <xref:System.Transactions.DependentTransaction>クラスを使用して非同期タスク間で同時実行を実現する方法を示します。  
  
### <a name="com-interop"></a>COM+ 相互運用  
 「[エンタープライズサービスと COM + トランザクションの相互運用性](interoperability-with-enterprise-services-and-com-transactions.md)」では、分散トランザクションが com + トランザクションと対話できるようにする方法を説明します。  
  
### <a name="diagnostics"></a>診断  
 [診断トレース](diagnostic-traces.md)は、 <xref:System.Transactions>インフラストラクチャによって生成されるトレースコードを使用して、アプリケーションのエラーをトラブルシューティングする方法について説明します。  
  
### <a name="working-within-aspnet"></a>ASP.NET 内での使用  
 「 [ASP.NET での System.Transactions の使用](using-system-transactions-in-aspnet.md)」トピックでは、ASP.NET アプリケーション<xref:System.Transactions>内でを正常に使用する方法について説明します。
