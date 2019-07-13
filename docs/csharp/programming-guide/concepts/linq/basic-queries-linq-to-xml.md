---
title: 基本的なクエリ (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: d333bb7d-20c1-448a-95b7-e5ba07915744
ms.openlocfilehash: a77ea062889e05c598df27fb143ba34466714e12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583338"
---
# <a name="basic-queries-linq-to-xml-c"></a>基本的なクエリ (LINQ to XML) (C#)
ここでは、基本的な [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの例について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[方法: 特定の属性を持つ要素を検索する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md)|特定の値を含む属性を持つ特定の要素を検索する方法について説明します。|  
|[方法: 特定の子要素を持つ要素を検索する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-child-element.md)|特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。|  
|[XDocument のクエリと XElement のクエリ (C#)](../../../../csharp/programming-guide/concepts/linq/querying-an-xdocument-vs-querying-an-xelement.md)|<xref:System.Xml.Linq.XElement> をルートとする XML ツリーに対するクエリの記述と、<xref:System.Xml.Linq.XDocument> をルートとする XML ツリーに対するクエリの記述の違いについて説明します。|  
|[方法: 特定の要素名を持つ子孫を検索する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-with-a-specific-element-name.md)|特定の名前を持つ要素のすべての子孫を検索する方法について説明します。 この例では、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用します。|  
|[方法: Descendants メソッドを使用して単一の子孫を検索する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-single-descendant-using-the-descendants-method.md)|<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸メソッドを使用して一意の名前を持つ単一の要素を検索する方法について説明します。|  
|[方法: 複雑なフィルターを使用してクエリを記述する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)|複雑なフィルターを使用してクエリを記述する方法について説明します。|  
|[方法: 省略可能な要素をフィルター処理する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-optional-element.md)|不規則な形のツリーでノードを検索する方法について説明します。|  
|[方法: 名前空間内のすべてのノードを検索する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-all-nodes-in-a-namespace.md)|特定の名前空間内のすべてのノードを検索する方法について説明します。|  
|[方法: 要素を並べ替える (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements.md)|結果を並べ替えるクエリを記述する方法について説明します。|  
|[方法: 複数のキーに基づいて要素を並べ替える (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)|複数のキーに基づく並べ替えの方法について説明します。|  
|[方法: 中間値を計算する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)|`Let` 句を使って [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの中間値を計算する方法について説明します。|  
|[方法: コンテキストに基づいて要素を検索するクエリを記述する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-query-that-finds-elements-based-on-context.md)|ツリー内の他の要素に基づいて要素を選択する方法について説明します。|  
|[方法: 空のクエリ結果セットをデバッグする (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md)|既定の名前空間の XML に対するクエリをデバッグする際の適切な修正方法について説明します。|  
  
## <a name="see-also"></a>関連項目

- [XML ツリーのクエリ (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
