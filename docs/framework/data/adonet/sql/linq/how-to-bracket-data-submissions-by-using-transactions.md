---
title: '方法: データ送信をトランザクションで囲む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 3e58c6f2849ed9714b3356662dae313ab9d11696
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134005"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>方法: データ送信をトランザクションで囲む
データベースへの送信を <xref:System.Transactions.TransactionScope> で囲むことができます。 詳細については、次を参照してください。[トランザクション サポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)します。  
  
## <a name="example"></a>例  
 次のコードでは、データベース送信を <xref:System.Transactions.TransactionScope> で囲みます。  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [トランザクションのサポート](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
