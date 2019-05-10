---
title: '方法: クラスとしてテーブルを表す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: ff943fbc7ae137128d6c635fd2366ad14cf70d15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620032"
---
# <a name="how-to-represent-tables-as-classes"></a>方法: クラスとしてテーブルを表す
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute>データベース テーブルに関連付けられたエンティティ クラスとしてクラスを指定する属性。  
  
### <a name="to-map-a-class-to-a-database-table"></a>データベース テーブルにクラスを対応付けるには  
  
- クラス宣言に <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。  
  
## <a name="example"></a>例  
 次のコードでは、`Customer` データベース テーブルに関連付けられたエンティティ クラスとして、`Customers` クラスを確立します。  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 名前が推論できる場合は、<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> プロパティを指定する必要はありません。 名前を指定しない場合は、プロパティまたはフィールドと同じ名前であると見なされます。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
