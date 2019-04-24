---
title: '方法: 列をタイムスタンプ列またはバージョン列として表現する'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: db73bf4880d8f5556247f7b037fca24b0ddc56d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297890"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>方法: 列をタイムスタンプ列またはバージョン列として表現する
使用して、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>のプロパティ、<xref:System.Data.Linq.Mapping.ColumnAttribute>データベース タイムスタンプまたはバージョン番号を保持するデータベース列を表すフィールドまたはプロパティを指定する属性。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>タイムスタンプ列またはバージョン列を表すフィールドまたはプロパティを指定するには  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> プロパティ値を `true` に設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [方法: 同時実行の競合を検査するメンバーを指定します。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
