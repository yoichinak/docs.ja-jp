---
title: '方法: 取得する関連データの量を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215444"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>方法: 取得する関連データの量を制御する
メイン ターゲットと一緒にどの関連データを取得するかを指定するには、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッドを使用します。 たとえば、顧客の注文に関する情報が必要になることがわかっている場合は、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> を使用して、顧客情報と同時に注文情報を取得できます。 この方法によって、データベースへの 1 回のアクセスで 2 種類の情報セットを両方とも取得できます。  
  
> [!NOTE]
>  メイン ターゲットである顧客に関連して注文データも取得する場合など、クエリのメイン ターゲットに関連するデータを取得するには、クロス積を 1 つの大きな投影として取得する方法もあります。 ただし、多くの場合、この方法には欠点があります。 たとえば、この結果は単なる射影であり、エンティティではないため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で変更して永続化することはできません。 また、不要なデータが大量に取得される可能性もあります。  
  
## <a name="example"></a>例  
 次の例では、クエリを実行すると、ロンドンに住んでいるすべての `Orders` のすべての `Customers` が取得されます。 その結果、それ以降 `Orders` オブジェクトの `Customer` プロパティにアクセスしても、新しいデータベース クエリは実行されません。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
