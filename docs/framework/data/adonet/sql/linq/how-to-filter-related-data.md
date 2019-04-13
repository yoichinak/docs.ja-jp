---
title: '方法: 関連データをフィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218226"
---
# <a name="how-to-filter-related-data"></a>方法: 関連データをフィルター処理する
取得したデータの量を制限するサブクエリを指定するには、<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドを使用します。  
  
## <a name="example"></a>例  
 次の例の <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッドは、取得した `Orders` を、その日に出荷されていないものに限定します。 この処理を行わないと、サブセットのみが必要な場合でも、すべての `Orders` が取得されることになります。  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [データベースに対するクエリの実行](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
