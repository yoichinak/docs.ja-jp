---
title: '方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 92b0d8cf2c4904fabc17241ef2c31175f0c87baf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878537"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ADO.NET ファミリのテクノロジの一部であるし、ADO.NET、ADO.NET コマンド間の接続を再利用できます提供されるサービスに基づいて、<xref:System.Data.Linq.DataContext>します。  
  
## <a name="example"></a>例  
 次の例では、ADO.NET コマンドの間で同じ接続を再利用する方法を示していますと<xref:System.Data.Linq.DataContext>します。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [ADO.NET および LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [データベースとの通信](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
