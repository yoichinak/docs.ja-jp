---
title: '方法: 主キーを表す'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793432"
---
# <a name="how-to-represent-primary-keys"></a>方法: 主キーを表す
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 属性のプロパティを使用して、データベース列の主キーを表すプロパティまたはフィールドを<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>指定します。 <xref:System.Data.Linq.Mapping.ColumnAttribute>  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>」を参照してください。  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、計算列は主キーとしてサポートされません。  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>プロパティまたはフィールドを主キーとして指定するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. 値として `true` を指定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
- [方法: コードエディターを使用してエンティティクラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
