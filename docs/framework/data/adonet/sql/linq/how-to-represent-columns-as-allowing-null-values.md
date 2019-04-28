---
title: '方法: null 値を許可する列として列を表す'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ef8fa87963b91ef7140fbaefb657fc7904604b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902916"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>方法: null 値を許可する列として列を表す
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>属性に関連付けられているデータベース列が null 値を保持できることを指定します。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>」を参照してください。  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>null 値を許可する列を指定するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> プロパティ値を `true` に設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
