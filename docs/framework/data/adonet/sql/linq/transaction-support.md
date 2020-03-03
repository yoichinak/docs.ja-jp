---
title: トランザクションのサポート
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792280"
---
# <a name="transaction-support"></a>トランザクションのサポート
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]では、3つの異なるトランザクションモデルがサポートされます。 チェックが行われる順に、これらのモデルを以下に示します。  
  
## <a name="explicit-local-transaction"></a>明示的なローカル トランザクション  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が呼び出されたときに <xref:System.Data.Linq.DataContext.Transaction%2A> プロパティが (`IDbTransaction`) トランザクションに設定されている場合、同じトランザクションのコンテキストで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼び出しが実行されます。  
  
 トランザクションの実行が終了したら、ユーザーがトランザクションをコミットまたはロールバックする必要があります。 トランザクションに対応する接続は、<xref:System.Data.Linq.DataContext> を構築するのに使用した接続に一致する必要があります。 異なる接続が使用されると、例外がスローされます。  
  
## <a name="explicit-distributable-transaction"></a>明示的な分散トランザクション  
 アクティブ<xref:System.Data.Linq.DataContext.SubmitChanges%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] なのスコープ内でapiを呼び出すことができます(ただし、に限定されません)。<xref:System.Transactions.Transaction> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は、呼び出しがトランザクションのスコープ内にあり、新しいトランザクションを作成しないことを検出します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]では、この場合に接続の終了も回避されます。 このようなトランザクションのコンテキストで、クエリと <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の実行が可能です。  
  
## <a name="implicit-transaction"></a>暗黙のトランザクション  
 を呼び出す<xref:System.Data.Linq.DataContext.SubmitChanges%2A>と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、は、呼び出しが`Transaction`のスコープ<xref:System.Transactions.Transaction>内にあるかどうか、またはプロパティ`IDbTransaction`() がユーザーが開始したローカルトランザクションに設定されているかどうかを確認します。 どちらのトランザクションも見つからない[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]場合、はローカルトランザクション`IDbTransaction`() を開始し、それを使用して生成された SQL コマンドを実行します。 すべての SQL コマンドが正常に完了する[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]と、はローカルトランザクションをコミットし、を返します。  
  
## <a name="see-also"></a>関連項目

- [背景情報](background-information.md)
- [方法: トランザクションを使用したデータの送信の角かっこ](how-to-bracket-data-submissions-by-using-transactions.md)
