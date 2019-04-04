---
title: '方法: トランザクションを使用してデータ送信を角かっこ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 2cbb50cc8762780849c337b597bbb36631c6ac1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584533"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>方法: トランザクションを使用してデータ送信を角かっこ
データベースへの送信を <xref:System.Transactions.TransactionScope> で囲むことができます。 詳細については、[トランザクション サポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)を参照してください。  
  
## <a name="example"></a>例  
 次のコードでは、データベース送信を <xref:System.Transactions.TransactionScope> で囲みます。  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目
- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [トランザクションのサポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
