---
title: '方法: 遅延読み込みをオフにします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 9878ec468333ba79d0171d0bf96235d48273e03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669537"
---
# <a name="how-to-turn-off-deferred-loading"></a>方法: 遅延読み込みをオフにします。
<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定すると、遅延読み込みをオフにできます。 詳細については、[遅延読み込みと即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)を参照してください。  
  
> [!NOTE]
>  遅延読み込みは、オブジェクト トラッキングをオフにすると暗黙でオフになります。 詳細については、「[方法 :情報を読み取り専用として取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)します。  
  
## <a name="example"></a>例  
 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定して、遅延読み込みをオフにする方法を次の例に示します。  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目
- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
