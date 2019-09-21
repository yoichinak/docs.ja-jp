---
title: '方法: 列をデータベース生成列として表す'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: bb9510986581ad6d3bcd0711aed681ef3a7c4e45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781780"
---
# <a name="how-to-represent-columns-as-database-generated"></a>方法: 列をデータベース生成列として表す
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 属性のプロパティを使用して、データベースによって生成される列を表すフィールドまたはプロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>指定します。 <xref:System.Data.Linq.Mapping.ColumnAttribute>  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>」を参照してください。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>データベース生成列を表すフィールドまたはプロパティを指定するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. プロパティ値を `true` に設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [方法: コードエディターを使用してエンティティクラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
