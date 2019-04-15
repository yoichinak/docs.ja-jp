---
title: '方法: 遅延読み込みをオフにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112958"
---
# <a name="how-to-turn-off-deferred-loading"></a>方法: 遅延読み込みをオフにする
<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定すると、遅延読み込みをオフにできます。 詳細については、次を参照してください。[遅延読み込みと即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)します。  
  
> [!NOTE]
>  遅延読み込みは、オブジェクト トラッキングをオフにすると暗黙でオフになります。 詳細については、「[方法 :情報を読み取り専用として取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)します。  
  
## <a name="example"></a>例  
 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> を `false` に設定して、遅延読み込みをオフにする方法を次の例に示します。  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
