---
title: トランザクションのサポート
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 519ddab069cf3c4ca1ccfa7b203769b8102db844
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876838"
---
# <a name="transaction-support"></a>トランザクションのサポート
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 次の 3 つの個別のトランザクション モデルをサポートしています。 チェックが行われる順に、これらのモデルを以下に示します。  
  
## <a name="explicit-local-transaction"></a>明示的なローカル トランザクション  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが (`IDbTransaction`) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。  
  
 トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。 トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。 異なる接続が使用されると、例外がスローされます。  
  
## <a name="explicit-distributable-transaction"></a>明示的な分散トランザクション  
 呼び出すことができます[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Api (これらに限定されませんが含まれます<xref:System.Data.Linq.DataContext.SubmitChanges%2A>) のアクティブなスコープで<xref:System.Transactions.Transaction>します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 呼び出しがトランザクションのスコープがあり、新しいトランザクションを作成できないことを検出します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] この場合、接続を終了してもなくなります。 このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。  
  
## <a name="implicit-transaction"></a>暗黙のトランザクション  
 呼び出すと<xref:System.Data.Linq.DataContext.SubmitChanges%2A>、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]のスコープ内の呼び出しかどうかをチェック、<xref:System.Transactions.Transaction>場合、または、`Transaction`プロパティ (`IDbTransaction`) がユーザーによって開始されたローカル トランザクションに設定します。 どちらのトランザクションが見つかった場合は[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションが開始されます (`IDbTransaction`) を使用して生成された SQL コマンドを実行するとします。 すべての SQL コマンドは正常に完了したら、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ローカル トランザクションをコミットし、返します。  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [方法: トランザクションを使用してデータ送信を角かっこ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
