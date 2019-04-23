---
title: '方法: データベースの名前を指定する'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335278"
---
# <a name="how-to-specify-database-names"></a>方法: データベースの名前を指定する
<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性の <xref:System.Data.Linq.Mapping.DatabaseAttribute> プロパティを使用すると、接続によってデータベースの名前が提供されない場合に、名前を指定できます。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>」を参照してください。  
  
### <a name="to-specify-the-name-of-the-database"></a>データベースの名前を指定するには  
  
1. データベースのクラス宣言に <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性を追加します。  
  
2. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性に <xref:System.Data.Linq.Mapping.DatabaseAttribute> プロパティを追加します。  
  
3. <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> プロパティ値を目的の名前に設定します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
