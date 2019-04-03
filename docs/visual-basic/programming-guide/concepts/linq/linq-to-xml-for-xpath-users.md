---
title: LINQ to XML XPath ユーザー (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 13c23eec1261700b15bea7f92f6c50e9231e900a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824248"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML XPath ユーザー (Visual Basic)

次に示す一連のトピックでは、さまざまな XPath 式、およびそれらに関連する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の式について説明します。  
  
 拡張メソッドによって [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] で使用可能になる <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> の XPath 機能をすべての例で使用します。 各例では、XPath 式と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 式の両方を実行します。 次に、両方のクエリの結果を比較して、XPath 式と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリが機能的に等価であることを検証します。 両方の種類のクエリは同じ XML ツリーからノードを返すため、クエリ結果は参照 ID を使用して比較されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XPath と LINQ to XML の比較](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の類似点および相違点についての概要を説明します。|  
|[方法: 子要素 (XPATH-LINQ to XML) を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|XPath の子要素軸と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の <xref:System.Xml.Linq.XContainer.Element%2A> メソッドを比較します。<br /><br /> 関連する XPath 式は `"DeliveryNotes"` です。|  
|[方法: 子要素 (XPATH-LINQ to XML) の一覧を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|XPath の子要素軸と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を比較します。<br /><br /> 関連する XPath 式は `"./*"` です。|  
|[方法: ルート要素 (XPATH-LINQ to XML) を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|ルート要素を取得する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"/PurchaseOrders"` です。|  
|[方法: 子孫の要素 (XPATH-LINQ to XML) を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|特定の名前を持つ子孫要素を取得する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"//Name"` です。|  
|[方法: 属性 (XPATH-LINQ to XML) をフィルター処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|指定した名前を持ち、かつ指定した値の属性を持つ子孫要素を取得する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `".//Address[@Type='Shipping']"` です。|  
|[方法: 関連する (XPATH-LINQ to XML) の要素を検索する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|別の要素の値によって参照される属性に基づいて要素を取得する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"` です。|  
|[方法: Namespace (XPATH-LINQ to XML) で要素を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|XML 名前空間の操作について、XPath の <xref:System.Xml.XmlNamespaceManager> クラスを使用する方法と、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の <xref:System.Xml.Linq.XName> クラスの <xref:System.Xml.Linq.XName.Namespace%2A> プロパティを使用する方法を比較します。<br /><br /> 関連する XPath 式は `"./aw:*"` です。|  
|[方法: 先行する (XPATH-LINQ to XML) の兄弟を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|XPath の `preceding-sibling` 軸と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の子 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 軸を比較します。<br /><br /> 関連する XPath 式は `"preceding-sibling::*"` です。|  
|[方法: (XPATH-LINQ to XML) の子要素の子孫を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|特定の名前を持つ子要素の子孫要素を取得する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"./Paragraph//Text/text()"` です。|  
|[方法: 2 つの場所のパス (XPATH-LINQ to XML) の和集合を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|XPath の UNION 演算子 <code>&#124;</code> と <xref:System.Linq.Enumerable.Concat%2A> の [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 標準クエリ演算子を比較します。<br /><br /> 関連する XPath 式は <code>"//Category&#124;//Price"</code> です。|  
|[方法: 兄弟ノード (XPATH-LINQ to XML) を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|特定の名前を持つノードのすべての兄弟を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"../Book"` です。|  
|[方法: 親 (XPATH-LINQ to XML) の属性を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|親要素に移動してその属性を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"../@id"` です。|  
|[方法: 特定の名前 (XPATH-LINQ to XML) を使用した兄弟の属性を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|コンテキスト ノードの兄弟に関する特定の属性を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"../Book/@id"` です。|  
|[方法: 特定の属性 (XPATH-LINQ to XML) を持つ要素を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|特定の属性を持つすべての要素を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"./*[@Select]"` です。|  
|[方法: (XPATH-LINQ to XML) の位置に基づいて子要素を検索 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|相対的位置に基づいて要素を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"Test[position() >= 2 and position() <= 4]"` です。|  
|[方法: 前の兄弟を検索 (XPATH-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|ノードの直前の兄弟を検索する方法を、XPath と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の間で比較します。<br /><br /> 関連する XPath 式は `"preceding-sibling::*[1]"` です。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [XML ツリー (Visual Basic) のクエリ](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [XPath データ モデルを使用した XML データの処理](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
