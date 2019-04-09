---
title: '方法: 列をデータベース生成列として表す'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2fca0c2fb1d28b5e83902f8664d1c7331774718b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148253"
---
# <a name="how-to-represent-columns-as-database-generated"></a>方法: 列をデータベース生成列として表す
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>データベース生成列を表すフィールドまたはプロパティを指定する属性。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>」を参照してください。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>データベース生成列を表すフィールドまたはプロパティを指定するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  プロパティ値を `true` に設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズする](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
